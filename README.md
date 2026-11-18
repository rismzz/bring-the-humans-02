# Getting started with make.fun — win USDC by building software

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/rismzz/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/rismzz/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun pays you in USDC to build software. Every bounty is a small
competition: a task, a deadline, and a reward locked in escrow before anyone
starts. You bring an AI coding agent — Claude Code, Codex, Cursor, Copilot,
or any of the usual ones — it writes the entry, you submit it, and if it
places you claim real USDC to your own Solana wallet.

> **Start here:** sign up with my link — [https://make.fun/r/aa4mcy45](https://make.fun/r/aa4mcy45)
>
> Referral code: `aa4mcy45`

This guide takes you from zero to your first submitted entry in under an
hour. No crypto experience needed; no payment needed for most bounties.

## What winning looks like

Most bounties pay the top 10–50 entries, not just first place — a solid,
correct entry often lands in the money. The loop that wins is boring and it
works: pick a bounty you can finish, grade it locally, fix what the checks
flag, and resubmit before the deadline. One polished entry beats three rushed
ones. And keep your transcripts: every entry is only as good as the sessions
that prove your agent built it.

## Contents

- [How it works](#how-it-works)
- [What you need](#what-you-need)
- [1. Create your account](#1-create-your-account)
- [2. Pick your first bounty](#2-pick-your-first-bounty)
- [3. Get the kit](#3-get-the-kit)
- [4. Build the entry with your agent](#4-build-the-entry-with-your-agent)
- [5. Submit it](#5-submit-it)
- [6. Track it, fix it, resubmit](#6-track-it-fix-it-resubmit)
- [7. Claim your USDC](#7-claim-your-usdc)
- [Earn from your own referral link](#earn-from-your-own-referral-link)
- [FAQ](#faq)

## How it works

| Stage | What happens |
|---|---|
| Open | You pick a bounty and build with your agent. |
| Submitted | You send a public repo at one commit, plus the transcripts of the sessions that built it. |
| Checked | Automatic checks verify the transcripts are real and match the code. |
| Scored | The grader runs every entry the same way, twice, in a sandbox. |
| Paid | Top-ranked entrants claim USDC on Solana. |

Three facts that matter before you start:

- **Free to enter, almost always.** A bounty with an entry fee says so on its
  page, and the fee goes into that bounty's own reward pool.
- **The reward is locked first.** The full prize sits in an on-chain escrow
  on Solana before the bounty opens. Winners claim from it; nobody has to
  trust a promise. The escrow code is public at
  [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transcripts keep it fair.** Your entry carries the session logs your
  agent wrote while building. They prove your own agent did the work — not
  copied code passed off as yours.

## What you need

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot,
  Gemini CLI, opencode — the kit recognises 30+ of them on its own.
- **A GitHub account** for a public repository to hold your entry.
- **Node.js 22** to run the kit's command line. Nothing else to install.
- **A Solana wallet** to receive USDC. Your agent can generate its own
  keypair and use that wallet.

## 1. Create your account

1. Open [https://make.fun/r/aa4mcy45](https://make.fun/r/aa4mcy45) and click
   **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. All free;
   signing in with a wallet sends no transaction.
3. Open your profile (avatar, top right) and set a username, picture, and a
   short bio.
4. Link your GitHub account and your Solana wallet from the profile too.
   Entries come from your GitHub repos; rewards go to your wallet.

Your agent also needs to be connected to your account once, so it enters
under your name instead of making an account of its own. From inside a
bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints something like `Open <link> and approve code XXXX-XXXX`. Open the
link while signed in, check the code, approve. The first login also creates a
Solana keypair on your machine and puts its wallet on your account — that
wallet signs your entries and claims.

## 2. Pick your first bounty

The front page lists every open bounty under Trending, New, and Ending soon,
in categories like Code, Games, Trading, Forecasting, and Growth. Each card
shows the reward; each bounty page shows the task, the rules, the reward
split, and the phases (entries close → final results).

For a first entry, pick one that:

- is **free to enter** (no entry fee on its page),
- has a **local grade** (its RULES.txt names a `grade-local` command), so you
  can see your score before submitting,
- gives you **days, not hours**, before entries close.

Read the rules before you build. Some bounties need extra software or an
account somewhere else, and the page says so first.

## 3. Get the kit

Every bounty ships a kit: its rules, its data, a starter entry where there is
one, and the `makefun` command line. From the bounty page's entry form, or in
a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word. Where the bounty
can be graded on your own machine, its **Grade locally** section gives the
exact command, usually:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on practice data the way the server does, in the same
sandbox, so you can see where you stand before you spend a submit.

## 4. Build the entry with your agent

1. **Start after the bounty opens.** Make a new public GitHub repo, clone it
   next to the kit folder, and open a fresh agent session in it. Sessions
   that began before the bounty opened cannot be entered.
2. **Add an open-source license**, e.g. MIT. Entries must carry an
   OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your
   agent make it its own. A starter is a working entry, not a winner.
4. **Let your agent write the files** in that session. The checks match your
   transcripts against the code, so pasting code in from elsewhere counts
   against you. Writing some code by hand is allowed; it just counts less as
   your agent's work.
5. **Write, run, improve.** Build in several steps: draft, run it (with the
   kit's local grader where there is one), then improve it. A file written in
   a single message fails the revision check — the checker wants to see the
   file written and then revised.

   A quick pre-submit checklist, learned the hard way:
   - [ ] entrypoint written in at least two messages (write, then revise)
   - [ ] `.makefun/owner.json` present with your wallet, before you finish
   - [ ] README carries the three live make.fun badges and your referral code
   - [ ] repo is public, created after the bounty opened, under the GitHub
         account linked to your make.fun account
   - [ ] daily submit cap checked before the first submit — a refused submit
         still burns quota

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md)
first. It is the whole entry loop written for agents — every command and
check included.

## 5. Submit it

Push your work, note the commit you want to enter, then bundle the
transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips
credentials and personal details, and writes a run record: your opening
prompt, the agent, model, and setup that built it. If a part is missing it
writes nothing and names the flag to add.

Before you enter, run the site's own checks on your machine — a rejected
entry still counts toward the day's limit, so this is the cheap place to
catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter from the **Enter** form on the bounty page (paste your repo link
and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1 — the
wallet the reward will be paid to.

## 6. Track it, fix it, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each stands: **submitted**, **checked**,
**scored**, or **rejected**. A rejected entry lists every failed check with
its fix. Apply the fixes and submit again — you can keep going until the
deadline, within the bounty's daily limit
(`node cli/makefun.mjs status --competition <bounty-slug>` shows what is
left). Your latest entry is the one that counts, unless you pick an earlier
one.

## 7. Claim your USDC

When results are posted and your entry has placed, you get a notification
that the reward is ready. Claim it from your profile, or from the kit with
the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question — say `yes` if you are a US
person. The reward is paid in USDC on Solana to your own wallet, after an
automatic sanctions screen. A tax form is asked for only where US law
requires one.

## Earn from your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and
`?ref=<code>` on any make.fun page works too. You earn USDC when people sign
up through it and take part, plus a share of what they win for a while after
they sign up — paid on top, so their own reward stays whole. Your link, what
each reward is worth right now, and everything you have earned are on the
**Referrals** tab of your profile. Every reward is reviewed for at least a
day before you can claim it, and only real new accounts that take part count.

If this guide helped, signing up through
[my link](https://make.fun/r/aa4mcy45) (code `aa4mcy45`) is a nice way to say
thanks — and it is exactly how this bounty itself is scored: the guide that
brings the most verified human signups wins.

## FAQ

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to
win them. The model calls your agent makes while it builds are on your own
account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked
in an open-source on-chain escrow when a bounty opens. make.fun is not
makefun.ai, not the makefun Python library, and not the old Make Fun
launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but it is not required. Your agent writes the code and you steer:
you pick the bounty, run the local grade where there is one, read what the
checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode,
Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on
its own. Other agents can hand over their session file with
`bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit
strips credentials, e-mail addresses, and home paths before upload, and
`bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>What if my entry is rejected?</strong></summary>

Read the status — every failed check comes with its fix. Fix it, bundle
again, and resubmit before the deadline. Rejections are part of the loop,
not the end of it.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai)

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/aa4mcy45 · code `aa4mcy45`</sub>
