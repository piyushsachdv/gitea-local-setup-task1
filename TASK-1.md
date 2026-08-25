# Task 1: Gitea Local Setup & Understanding

## Objective

Set up the Gitea project locally from source, run it without Docker, verify the application, and document the setup and Git workflow.

## 1. Repository Setup

The official Gitea repository was cloned from:

https://github.com/go-gitea/gitea

The repository was cloned to:

C:\Users\Piyush\gitea

## 2. Environment Setup

The local environment was prepared on Windows with:

- Git 2.51.0
- Go 1.27.0
- Node.js 22.23.2
- pnpm 11.22.0
- GNU Make 4.4.1
- uv 0.12.5
- Python 3.13.5

MSYS2 UCRT64 was used to provide GNU Make and to run the project's Make commands.

## 3. Project Documentation and Structure

The repository documentation was reviewed, including:

- README.md
- docs/build-setup.md
- docs/build-source.md
- docs/development.md
- docs/testing.md

Gitea is a self-hosted Git service written primarily in Go. The repository contains backend code, API and web routers, frontend assets, command-line components, tests, documentation, and build tooling.

## 4. Dependency Setup

The project dependencies were installed using:

make deps

The first attempt failed because uv was not available inside the MSYS2 environment:

make: uv: No such file or directory
make: *** [Makefile:597: .venv] Error 127

uv was installed on Windows and located at:

C:\Users\Piyush\.local\bin\uv.exe

Its directory was added to the MSYS2 UCRT64 PATH.

The required Windows tools were also made available in the MSYS2 environment.

After correcting the environment, make deps completed successfully.

The process downloaded the Go dependencies and created the Python virtual environment using Python 3.13.5.

## 5. Building Gitea

Gitea was built from source using:

make build

The build completed successfully.

The generated executable was verified with:

ls -lh gitea.exe

The resulting executable was approximately 111 MB.

## 6. Running Gitea Without Docker

Gitea was started directly from the generated executable using:

./gitea.exe web

The startup logs confirmed:

Gitea version: 1.28.0+dev-409-gd17ccd4434 built with go1.27.0

Listen: http://0.0.0.0:3000

AppURL(ROOT_URL): http://localhost:3000/

The application was therefore successfully running locally without Docker.

## 7. Initial Configuration

The Gitea installation page was opened at:

http://localhost:3000

SQLite3 was selected for the local database.

The local administrator account was created and the installation was completed successfully.

The repository root was configured under:

C:\Users\Piyush\gitea\data\gitea-repositories

The Git LFS root was configured under:

C:\Users\Piyush\gitea\data\lfs

The server domain was:

localhost

The HTTP port was:

3000

The base URL was:

http://localhost:3000/

## 8. Application Verification

After installation, the Gitea dashboard was successfully accessed through:

http://localhost:3000

To verify actual Git functionality, a test repository was created in the local Gitea instance:

piyush/local-gitea-test

The repository was cloned and a test file named verification.txt was created.

The file was committed and pushed using:

git add verification.txt
git commit -m "test: verify local Gitea repository"
git push origin main

The commit and file were then visible in the local Gitea web interface.

This verified the local Gitea Git workflow.

## 9. GitHub Submission Repository

A separate GitHub repository was created for the task:

https://github.com/piyushsachdv/gitea-local-setup-task1

This repository will contain the required task documentation and project work for submission.

## 10. Issues Encountered and Resolutions

### Go initially unavailable

Go was initially unavailable from PowerShell. It was installed and verified with:

go version

Result:

go version go1.27.0 windows/amd64

### pnpm initially unavailable

pnpm was installed using:

npm install --global pnpm@11.22.0

It was then verified successfully.

### GNU Make initially unavailable

GNU Make was initially unavailable from Git Bash.

MSYS2 UCRT64 was used to provide GNU Make.

### Windows tools initially unavailable inside MSYS2

Git, Go, Node.js and pnpm were installed on Windows but were initially unavailable inside the MSYS2 shell.

The required directories were added to PATH so they could be used by the Make build process.

### uv initially unavailable

The first make deps attempt failed because uv was not available.

uv was installed and its directory was added to the MSYS2 PATH. The dependency installation then completed successfully.

## 11. Final Result

The Gitea project was successfully:

1. Cloned from the official repository.
2. Studied through its documentation and structure.
3. Configured with the required dependencies.
4. Built successfully from source.
5. Run locally without Docker.
6. Accessed through localhost:3000.
7. Configured with a local administrator account.
8. Verified through an actual Git clone, commit, and push workflow.
9. Prepared for submission through the dedicated GitHub repository.

## 12. What I Learned

I learned how to set up a large open-source Go project from source, understand its repository structure and development documentation, configure a Windows development environment using MSYS2, install project dependencies, build the application, run Gitea without Docker, troubleshoot PATH and environment issues, and verify Git operations using a locally hosted Git service.

## 13. Submission Verification

The final Task 1 branch was pushed to the dedicated GitHub submission repository. The documentation and source tree can be reviewed through the `task-1-local-setup` branch and its pull request against `main`.
