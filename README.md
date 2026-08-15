# Harness

A GitHub template for repositories built with AI agents. It gives a new project
isolated worktrees, reviewable PRs, portable CI, opt-in CD, and releases from
conventional commits.

Create a repository from this template, replace `{{REPOSITORY_NAME}}` in
`AGENTS.md`, and install the workflow skills:

```bash
npx skills@latest add victoremnm/skills
```

Use the installed `avoid-ai-writing` skill before publishing original prose in
docs, commits, PRs, and releases.

## Included baseline

- `AGENTS.md` defines agent boundaries, evidence, secret handling, and the
  human merge gate.
- `.github/PULL_REQUEST_TEMPLATE.md` requires proof, exact verification, and
  the remaining human checks.
- `.github/workflows/ci.yml` detects Node, Python, Go, and Rust projects and
  runs each stack’s standard checks.
- `.github/workflows/cd.yml` deploys only after `main` changes and skips safely
  until `DEPLOY_COMMAND` is configured as a repository Actions variable.
- `.github/workflows/release.yml` creates tags and GitHub releases without
  writing generated files to protected `main`.

## Configure delivery

Set the `DEPLOY_COMMAND` Actions variable only after you have a verified target
platform and stored its credentials as Actions secrets. The variable must not
contain credentials. For database work, add a project-specific migration step
that first runs against a disposable local or preview service.

## Customize per project

The language scripts in `scripts/ci/` are deliberately small. Add project test
commands, browser checks, migrations, and deployment validation when the stack
is known. Keep those changes explicit and documented in the PR template.
