web project jenkins
# step 1 build
1.New Item → Name: MavenWeb_Build
2.Select Freestyle Project → OK
✅ STEP 2 — Source Code Management
Select Git add git repo
✅ STEP 3 — Build Steps
1.Add build step → Invoke top-level Maven targets
Goals:clean
2.Add another build step → Invoke top-level Maven targets
goals:install
✅ STEP 4 — Post Build Actions 
1.Add post-build action → Archive the artifacts:**/*
2.Add post-build action → Build other projects
MavenWeb_Test
✅ STEP 5 — Save & Build
Apply → Save
Build Now
# step 2 test
STEP 1 — Create Job
1.New Item → Name: MavenWeb_Test
2.Freestyle Project → OK
STEP 2 — Source Code Management
3.Select None
STEP 3 — Build Environment
4.Check: Delete workspace before build starts
STEP 4 — Build Steps
1.Add build step → Copy artifacts from another project
MavenWeb_Build
Artifacts:**/*
2.Add build step → Invoke top-level Maven targets
Goals:test
STEP 5 — Post Build
1.Archive artifacts: **/*
2.Add post-build action → Build other projects
MavenWeb_Deploy
STEP 6 — Save
Apply → Save
# step 3 JENKINS – DEPLOY JOB
STEP 1 — Create Job
1.New Item → Name: MavenWeb_Deploy
2.Freestyle Project → OK
STEP 2 — Build Environment
1.Check: Delete workspace before build starts
STEP 3 — Build Step
1.Add step → Copy artifacts from another project
MavenWeb_Test
2.Artifacts: **/*
STEP 4 — Deployment Step
1.Add post-build action → Deploy war/ear to container
2.WAR files: **/*.war
3.Context path: webapp
4.Tomcat URL + credentials
STEP 5 — Save
1.Apply → Save → Build Now













