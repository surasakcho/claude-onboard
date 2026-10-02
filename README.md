# claude-onboard

**For a Claude Code session on a new or reinstalled machine.** This page is step 0: it gets you
GitHub access, then hands you the full onboarding manual, which lives in a private repo.

Follow the steps in order. Each ends on a check; go on only when it passes. Where a step says the
user does it, ask the user and wait.

## 1. Install the GitHub CLI (`gh`) and Git

First check: `gh --version` and `git --version`. Install only what is missing.

| OS | install |
|---|---|
| Windows | `winget install --id GitHub.cli` and `winget install --id Git.Git`, then open a new terminal |
| Ubuntu / Debian | `sudo apt install gh git` (if `gh` is not found: <https://github.com/cli/cli/blob/trunk/docs/install_linux.md>) |
| other Linux | <https://github.com/cli/cli/blob/trunk/docs/install_linux.md> |

**Done when:** `gh --version` and `git --version` both print a version.

## 2. Log in to GitHub (the user does this)

The login is interactive, so ask the user to run it in this session:

```text
! gh auth login
```

Choose GitHub.com, HTTPS, and log in with the browser. Never ask the user to paste a token into
the chat.

**Done when:** `gh auth status` shows a logged-in account.

## 3. Check access to the private rules repo

```sh
gh repo view surasakcho/agentic-ai-rules-and-skills --json name
```

If it fails, the account has no access: tell the user, and stop.

**Done when:** it prints the repo name.

## 4. Fetch the onboarding manual and follow it

```sh
gh api -H "Accept: application/vnd.github.raw" repos/surasakcho/agentic-ai-rules-and-skills/contents/SETUP.md
```

Read the whole output, then follow it from its step 1. It sets up the rules, Matt Pocock's skills
and our shared skills, and ends by proving all of them in a new session.

**Done when:** `SETUP.md`'s own last step passes.

---

To start a fresh Claude Code on this page, tell it:

> Follow https://github.com/surasakcho/claude-onboard step by step on this machine. Ask me
> whenever it says the user does a step.
