# README

I have a self-hosted instance of renovate that is working for several repositories.

However, I can't get it to create PRs for Swift Package Manager (SPM) dependencies.
PRs for docker dependency updates are successfully created for the same repository as is the dependency dashboard.

For each SPM dependency, renovate issues the following warning:

> WARN: Error updating branch: update failure (repository=<repo>, branch=<branch>)

This is a simple reproduction repository, on Github here, renovate is able to create PRs for the SPM dependency,
with my self-hosted renovate instance using gitea, it fails:

```
 INFO: Repository started (repository=jnosh/renovate-spm-issue)
       "renovateVersion": "32.194.3"
DEBUG: Using localDir: /tmp/renovate/repos/gitea/jnosh/renovate-spm-issue (repository=jnosh/renovate-spm-issue)
DEBUG: PackageFiles.clear() - Package files deleted (repository=jnosh/renovate-spm-issue)
       "baseBranches": []
DEBUG: No concurrency limits (repository=jnosh/renovate-spm-issue)
       "host": "<host>"
DEBUG: jnosh/renovate-spm-issue default branch = main (repository=jnosh/renovate-spm-issue)
DEBUG: using HTTP URL (repository=jnosh/renovate-spm-issue)
       "url": "https://<host>/jnosh/renovate-spm-issue.git"
DEBUG: Resetting npmrc (repository=jnosh/renovate-spm-issue)
DEBUG: detectSemanticCommits() (repository=jnosh/renovate-spm-issue)
DEBUG: Initializing git repository into /tmp/renovate/repos/gitea/jnosh/renovate-spm-issue (repository=jnosh/renovate-spm-issue)
DEBUG: Performing blobless clone (repository=jnosh/renovate-spm-issue)
DEBUG: git clone completed (repository=jnosh/renovate-spm-issue)
       "durationMs": 1636
DEBUG: latest repository commit (repository=jnosh/renovate-spm-issue)
       "latestCommit": {
         "hash": "a164d022ee83205563e1a7ee8b9541d34fc936da",
         "date": "2022-09-16T13:33:39+02:00",
         "message": "Add a minimal vapor project",
         "refs": "HEAD -> main, origin/main, origin/HEAD",
         "body": "",
         "author_name": "Janosch Hildebrand",
         "author_email": "jnosh@jnosh.com"
       }
DEBUG: getCommitMessages (repository=jnosh/renovate-spm-issue)
DEBUG: Semantic commits detection: unknown (repository=jnosh/renovate-spm-issue)
DEBUG: No semantic commits detected (repository=jnosh/renovate-spm-issue)
DEBUG: checkOnboarding() (repository=jnosh/renovate-spm-issue)
DEBUG: isOnboarded() (repository=jnosh/renovate-spm-issue)
DEBUG: findFile(renovate.json) (repository=jnosh/renovate-spm-issue)
DEBUG: Config file exists (repository=jnosh/renovate-spm-issue)
       "fileName": "renovate.json"
DEBUG: ensureIssueClosing(Action required: Add a Renovate config) (repository=jnosh/renovate-spm-issue)
DEBUG: Retrieved 0 Issues (repository=jnosh/renovate-spm-issue)
DEBUG: Repo is onboarded (repository=jnosh/renovate-spm-issue)
DEBUG: Found renovate.json config file (repository=jnosh/renovate-spm-issue)
DEBUG: Repository config (repository=jnosh/renovate-spm-issue)
       "fileName": "renovate.json",
       "config": {
         "$schema": "https://docs.renovatebot.com/renovate-schema.json",
         "extends": ["config:base", "docker:enableMajor"]
       }
DEBUG: migrateAndValidate() (repository=jnosh/renovate-spm-issue)
DEBUG: No config migration necessary (repository=jnosh/renovate-spm-issue)
DEBUG: massaged config (repository=jnosh/renovate-spm-issue)
       "config": {
         "$schema": "https://docs.renovatebot.com/renovate-schema.json",
         "extends": ["config:base", "docker:enableMajor"]
       }
DEBUG: migrated config (repository=jnosh/renovate-spm-issue)
       "config": {
         "$schema": "https://docs.renovatebot.com/renovate-schema.json",
         "extends": ["config:base", "docker:enableMajor"]
       }
DEBUG: Setting hostRules from config (repository=jnosh/renovate-spm-issue)
DEBUG: Found repo ignorePaths (repository=jnosh/renovate-spm-issue)
       "ignorePaths": [
         "**/node_modules/**",
         "**/bower_components/**",
         "**/vendor/**",
         "**/examples/**",
         "**/__tests__/**",
         "**/test/**",
         "**/tests/**",
         "**/__fixtures__/**"
       ]
DEBUG: No vulnerability alerts found (repository=jnosh/renovate-spm-issue)
DEBUG: No baseBranches (repository=jnosh/renovate-spm-issue)
DEBUG: extract() (repository=jnosh/renovate-spm-issue)
DEBUG: Setting current branch to main (repository=jnosh/renovate-spm-issue)
DEBUG: latest commit (repository=jnosh/renovate-spm-issue)
       "branchName": "main",
       "latestCommitDate": "2022-09-16T13:33:39+02:00"
DEBUG: Using file match: (^|/)tasks/[^/]+\.ya?ml$ for manager ansible (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)requirements\.ya?ml$ for manager ansible-galaxy (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)galaxy\.ya?ml$ for manager ansible-galaxy (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: azure.*pipelines?.*\.ya?ml$ for manager azure-pipelines (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)batect(-bundle)?\.yml$ for manager batect (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)batect$ for manager batect-wrapper (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)WORKSPACE(|\.bazel)$ for manager bazel (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.bzl$ for manager bazel (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)\.bazelversion$ for manager bazelisk (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.?bitbucket-pipelines\.ya?ml$ for manager bitbucket-pipelines (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: buildkite\.ya?ml for manager buildkite (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.buildkite/.+\.ya?ml$ for manager buildkite (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)Gemfile$ for manager bundler (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.cake$ for manager cake (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)Cargo\.toml$ for manager cargo (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.circleci/config\.yml$ for manager circleci (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)cloudbuild\.ya?ml for manager cloudbuild (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)Podfile$ for manager cocoapods (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)([\w-]*)composer\.json$ for manager composer (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)conanfile\.(txt|py)$ for manager conan (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)(?:deps|bb)\.edn$ for manager deps-edn (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)(?:docker-)?compose[^/]*\.ya?ml$ for manager docker-compose (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/|\.)Dockerfile$ for manager dockerfile (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)Dockerfile[^/]*$ for manager dockerfile (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.drone\.yml$ for manager droneci (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)fleet\.ya?ml for manager fleet (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)flux-system/gotk-components\.yaml$ for manager flux (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)\.fvm\/fvm_config\.json$ for manager fvm (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.gitmodules$ for manager git-submodules (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: ^(workflow-templates|\.github\/workflows)\/[^/]+\.ya?ml$ for manager github-actions (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)action\.ya?ml$ for manager github-actions (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.gitlab-ci\.yml$ for manager gitlabci (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.gitlab-ci\.yml$ for manager gitlabci-include (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)go\.mod$ for manager gomod (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.gradle(\.kts)?$ for manager gradle (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)gradle\.properties$ for manager gradle (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)gradle\/.+\.toml$ for manager gradle (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.versions\.toml$ for manager gradle (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)gradle/wrapper/gradle-wrapper\.properties$ for manager gradle-wrapper (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)requirements\.yaml$ for manager helm-requirements (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)values\.yaml$ for manager helm-values (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)helmfile\.yaml$ for manager helmfile (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)Chart\.yaml$ for manager helmv3 (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)bin/hermit$ for manager hermit (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: ^Formula/[^/]+[.]rb$ for manager homebrew (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.html?$ for manager html (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)plugins\.(txt|ya?ml)$ for manager jenkins (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)jsonnetfile\.json$ for manager jsonnet-bundler (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: ^.+\.main\.kts$ for manager kotlin-script (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)kustomization\.ya?ml$ for manager kustomize (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)project\.clj$ for manager leiningen (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/|\.)pom\.xml$ for manager maven (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: ^(((\.mvn)|(\.m2))/)?settings\.xml$ for manager maven (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)package\.js$ for manager meteor (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)Mintfile$ for manager mint (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)mix\.exs$ for manager mix (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.node-version$ for manager nodenv (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)package\.json$ for manager npm (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.(?:cs|fs|vb)proj$ for manager nuget (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.(?:props|targets)$ for manager nuget (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)dotnet-tools\.json$ for manager nuget (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)global\.json$ for manager nuget (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.nvmrc$ for manager nvm (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)([\w-]*)requirements\.(txt|pip)$ for manager pip_requirements (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)setup\.py$ for manager pip_setup (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)Pipfile$ for manager pipenv (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)pyproject\.toml$ for manager poetry (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.pre-commit-config\.yaml$ for manager pre-commit (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)pubspec\.ya?ml$ for manager pub (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)Puppetfile$ for manager puppet (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.python-version$ for manager pyenv (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.ruby-version$ for manager ruby-version (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.sbt$ for manager sbt (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: project/[^/]*.scala$ for manager sbt (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)setup\.cfg$ for manager setup-cfg (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)Package\.swift for manager swift (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: \.tf$ for manager terraform (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.terraform-version$ for manager terraform-version (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)terragrunt\.hcl$ for manager terragrunt (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.terragrunt-version$ for manager terragrunt-version (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: ^\.travis\.yml$ for manager travis (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|/)\.vela\.ya?ml$ for manager velaci (repository=jnosh/renovate-spm-issue)
DEBUG: Using file match: (^|\/)\.woodpecker[^/]*\.ya?ml$ for manager woodpecker (repository=jnosh/renovate-spm-issue)
DEBUG: Matched 1 file(s) for manager swift: Package.swift (repository=jnosh/renovate-spm-issue)
DEBUG: Found swift package files (repository=jnosh/renovate-spm-issue)
DEBUG: Found 1 package file(s) (repository=jnosh/renovate-spm-issue)
 INFO: Dependency extraction complete (repository=jnosh/renovate-spm-issue, baseBranch=main)
       "stats": {
         "managers": {"swift": {"fileCount": 1, "depCount": 1}},
         "total": {"fileCount": 1, "depCount": 1}
       }
DEBUG: PackageFiles.add() - Package file saved for branch (repository=jnosh/renovate-spm-issue, baseBranch=main)
DEBUG: Package releases lookups complete (repository=jnosh/renovate-spm-issue, baseBranch=main)
DEBUG: branchifyUpgrades (repository=jnosh/renovate-spm-issue)
DEBUG: 1 flattened updates found: vapor/vapor (repository=jnosh/renovate-spm-issue)
DEBUG: Returning 1 branch(es) (repository=jnosh/renovate-spm-issue)
DEBUG: config.repoIsOnboarded=true (repository=jnosh/renovate-spm-issue)
DEBUG: packageFiles with updates (repository=jnosh/renovate-spm-issue, baseBranch=main)
       "config": {
         "swift": [
           {
             "packageFile": "Package.swift",
             "deps": [
               {
                 "datasource": "git-tags",
                 "depName": "vapor/vapor",
                 "packageName": "https://github.com/vapor/vapor.git",
                 "currentValue": "from: \"4.0.0\"",
                 "depIndex": 0,
                 "updates": [
                   {
                     "bucket": "non-major",
                     "newVersion": "4.65.2",
                     "newValue": "from: \"4.65.2\"",
                     "newDigest": "dda0de537e7906414dccd551e77095be1e34e3da",
                     "newMajor": 4,
                     "newMinor": 65,
                     "updateType": "minor",
                     "isRange": true,
                     "isBump": true,
                     "branchName": "renovate/vapor-vapor-4.x"
                   }
                 ],
                 "warnings": [],
                 "versioning": "swift",
                 "sourceUrl": "https://github.com/vapor/vapor",
                 "currentVersion": "4.0.0",
                 "isSingleVersion": false
               }
             ]
           }
         ]
       }
DEBUG: processRepo() (repository=jnosh/renovate-spm-issue)
DEBUG: Processing 1 branch: renovate/vapor-vapor-4.x (repository=jnosh/renovate-spm-issue)
DEBUG: Calculating hourly PRs remaining (repository=jnosh/renovate-spm-issue)
DEBUG: No concurrency limits (repository=jnosh/renovate-spm-issue)
       "host": "<host>"
DEBUG: Retrieved 0 Pull Requests (repository=jnosh/renovate-spm-issue)
DEBUG: currentHourStart=2022-09-16T11:00:00.000+00:00 (repository=jnosh/renovate-spm-issue)
DEBUG: PR hourly limit remaining: 2 (repository=jnosh/renovate-spm-issue)
DEBUG: Calculating prConcurrentLimit (10) (repository=jnosh/renovate-spm-issue)
DEBUG: getBranchPr(renovate/vapor-vapor-4.x) (repository=jnosh/renovate-spm-issue)
DEBUG: findPr(renovate/vapor-vapor-4.x, undefined, open) (repository=jnosh/renovate-spm-issue)
DEBUG: 0 PRs are currently open (repository=jnosh/renovate-spm-issue)
DEBUG: PR concurrent limit remaining: 10 (repository=jnosh/renovate-spm-issue)
DEBUG: Calculated maximum PRs remaining this run (repository=jnosh/renovate-spm-issue)
       "prsRemaining": 2
DEBUG: PullRequests limit = 2 (repository=jnosh/renovate-spm-issue)
DEBUG: Calculating hourly PRs remaining (repository=jnosh/renovate-spm-issue)
DEBUG: currentHourStart=2022-09-16T11:00:00.000+00:00 (repository=jnosh/renovate-spm-issue)
DEBUG: PR hourly limit remaining: 2 (repository=jnosh/renovate-spm-issue)
DEBUG: Calculating branchConcurrentLimit (10) (repository=jnosh/renovate-spm-issue)
DEBUG: 0 already existing branches found:  (repository=jnosh/renovate-spm-issue)
DEBUG: Branch concurrent limit remaining: 10 (repository=jnosh/renovate-spm-issue)
DEBUG: Calculated maximum branches remaining this run (repository=jnosh/renovate-spm-issue)
       "branchesRemaining": 2
DEBUG: Branches limit = 2 (repository=jnosh/renovate-spm-issue)
DEBUG: getBranchPr(renovate/vapor-vapor-4.x) (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: findPr(renovate/vapor-vapor-4.x, undefined, open) (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: branchExists=false (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: dependencyDashboardCheck=undefined (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: recreateClosed is false (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: findPr(renovate/vapor-vapor-4.x, Update dependency vapor/vapor to from: "4.65.2", !open) (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: prAlreadyExisted=false (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: Checking schedule(at any time, null) (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: No schedule defined (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: Branch needs creating (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: Using reuseExistingBranch: false (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: Setting current branch to main (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: latest commit (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
       "branchName": "main",
       "latestCommitDate": "2022-09-16T13:33:39+02:00"
DEBUG: manager.getUpdatedPackageFiles() reuseExistingBranch=false (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: Starting search at index 278 (repository=jnosh/renovate-spm-issue, packageFile=Package.swift, branch=renovate/vapor-vapor-4.x)
       "depName": "vapor/vapor"
DEBUG: Found match at index 278 (repository=jnosh/renovate-spm-issue, packageFile=Package.swift, branch=renovate/vapor-vapor-4.x)
       "depName": "vapor/vapor"
 WARN: Error updating branch: update failure (repository=jnosh/renovate-spm-issue, branch=renovate/vapor-vapor-4.x)
DEBUG: Ensuring Dependency Dashboard (repository=jnosh/renovate-spm-issue)
DEBUG: ensureIssue(Dependency Dashboard) (repository=jnosh/renovate-spm-issue)
DEBUG: Created new Issue #1 (repository=jnosh/renovate-spm-issue)
DEBUG: Removing any stale branches (repository=jnosh/renovate-spm-issue)
DEBUG: config.repoIsOnboarded=true (repository=jnosh/renovate-spm-issue)
DEBUG: No renovate branches found (repository=jnosh/renovate-spm-issue)
DEBUG: ensureIssueClosing(Action Required: Fix Renovate Configuration) (repository=jnosh/renovate-spm-issue)
DEBUG: Retrieved 1 Issues (repository=jnosh/renovate-spm-issue)
DEBUG: PackageFiles.clear() - Package files deleted (repository=jnosh/renovate-spm-issue)
       "baseBranches": ["main"]
DEBUG: Renovate repository PR statistics (repository=jnosh/renovate-spm-issue)
       "stats": {"total": 0, "open": 0, "closed": 0, "merged": 0}
DEBUG: Repository result: done, status: onboarded, enabled: true, onboarded: true (repository=jnosh/renovate-spm-issue)
DEBUG: Repository timing splits (milliseconds) (repository=jnosh/renovate-spm-issue)
       "splits": {"init": 3543, "extract": 667, "lookup": 240, "onboarding": 0, "update": 313},
       "total": 5873
DEBUG: http statistics (repository=jnosh/renovate-spm-issue)
       "urls": {
         "https://<host>/api/v1/repos/jnosh/renovate-spm-issue/issues (GET,200)": 2,
         "https://<host>/api/v1/repos/jnosh/renovate-spm-issue/issues (POST,201)": 1,
         "https://<host>/api/v1/repos/jnosh/renovate-spm-issue/pulls (GET,200)": 1
       },
       "hostStats": {
         "<host>": {
           "requestCount": 4,
           "requestAvgMs": 332,
           "queueAvgMs": 1
         }
       },
       "totalRequests": 4
 INFO: Repository finished (repository=jnosh/renovate-spm-issue)
       "durationMs": 5873
DEBUG: dns cache (repository=jnosh/renovate-spm-issue)
       "hosts": []
