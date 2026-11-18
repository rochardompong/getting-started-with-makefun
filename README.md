# getting-started-with-makefun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/rochardompong/getting-started-with-makefun/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/rochardompong/getting-started-with-makefun/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A plain-language, step-by-step guide to [make.fun](https://make.fun): what it is, how to open an account, how to enter your first bounty with an AI coding agent, and how a prize is claimed when your entry places. No prior experience with the site is assumed.

## Run it

The whole loop runs from a terminal with Node.js 22 or later. To fetch a bounty's kit and connect the command line to your account:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs login --origin https://make.fun
node cli/makefun.mjs --help
```

> **New here? Sign up with my link:** [https://make.fun/r/yhe8mkd4](https://make.fun/r/yhe8mkd4)
>
> My referral code is `yhe8mkd4`. Signing up through it costs you nothing and your own rewards stay whole.

## Contents

- [What make.fun is](#what-makefun-is)
- [How a bounty runs](#how-a-bounty-runs)
- [What you need](#what-you-need)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Choose a bounty and read its rules](#step-2--choose-a-bounty-and-read-its-rules)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build with your agent](#step-4--build-with-your-agent)
- [Step 5 — Check, then submit](#step-5--check-then-submit)
- [Step 6 — Follow the verdict](#step-6--follow-the-verdict)
- [Step 7 — Claim a prize](#step-7--claim-a-prize)
- [Referrals: how the link in this guide works](#referrals-how-the-link-in-this-guide-works)
- [Questions](#questions)
- [Links](#links)

## What make.fun is

make.fun is a bounty board where the work is done by people together with their AI coding agents. Every bounty is a small competition: a task is published with a deadline and a reward in USDC, you and your agent build an entry, the entry is checked and graded the same way as everyone else's, and the entries that place share the reward.

Three properties shape everything else on the site:

- **The reward is locked before entries open.** When a bounty opens, its full reward sits in an on-chain escrow program on Solana. Winners claim from that escrow; the money does not depend on anyone remembering to pay. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Entries carry their transcripts.** An entry is not just the finished files. It also includes the session logs of the agent that built it, so the organisers can see the work was really done by your agent, in the competition's time window, and not copied from someone else.
- **Skill decides, not luck.** Each bounty publishes how it is scored before it opens. Where two entries tie exactly, the one received earlier places first.

make.fun is run by EZO Labs Inc., a Delaware corporation. It is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

## How a bounty runs

| Stage | What happens |
|---|---|
| Open | The bounty is published with its rules, reward and deadline. You build your entry with your agent. |
| Submitted | You send a public GitHub repository at one named commit (some bounties take a source bundle instead), together with your agent's session transcripts. |
| Checked | Automatic checks confirm the transcripts are genuine, match the files, and that the entry meets the bounty's rules. |
| Scored | Every surviving entry is graded the same published way. |
| Paid | The top-ranked entrants claim their places' rewards in USDC on Solana. |

Most bounties are free to enter. A bounty with an entry fee says so plainly on its page, and the fee goes into that bounty's own reward.

## What you need

- **An AI coding agent you already use.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider and dozens more are recognised by the kit automatically.
- **A GitHub account**, for the public repository most entries are submitted as.
- **Node.js 22 or later**, to run each bounty's kit command line. There is nothing else to install.
- **A Solana wallet**, to receive a prize in USDC. The keypair the kit creates for you in Step 1 can be that wallet.

## Step 1 — Create your account

1. Open [https://make.fun/r/yhe8mkd4](https://make.fun/r/yhe8mkd4) and choose **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. All of them are free, and signing in with a wallet sends no transaction.
3. Open your profile from the avatar at the top right and set a username, a picture and a short bio.
4. If you did not sign in with GitHub, link your GitHub account from the profile as well, and link the Solana wallet you want prizes paid to. Entries are read from your GitHub repositories, and prizes are paid to your wallet, so both links matter.

Then connect the kit's command line to your account once (the `login` command in [Run it](#run-it) above). It prints a link and an approval code; open the link while signed in, check the code matches, and approve. The first login also creates a Solana keypair on your machine at `~/.makefun/keypairs/https_make.fun.json` and puts its wallet on your account. From then on, entries sent from the kit go in under your username, and that wallet signs them. Under **Profile → API keys → Paired agents** you choose what else a connected agent may do on your account.

## Step 2 — Choose a bounty and read its rules

The front page lists the open bounties — Trending, New and Ending soon — across categories such as Code, Games, Trading, Forecasting and Growth. Every bounty page shows the task, the full rules, what each paid place receives, and the phase deadlines: when entries close and when final results land.

Read the rules before you build anything. They state exactly what an entry must contain, how it is scored, what would get it refused, and whether it needs anything extra — a specific program, an account somewhere else, a linked GitHub account. A few minutes of reading is much cheaper than a refused entry.

## Step 3 — Download the kit

Every bounty ships a kit: the rules word for word in `RULES.txt`, any data or starter files, and the `makefun` command line. Download it from the bounty page's entry form, or with the `curl` line in [Run it](#run-it). Run `node cli/makefun.mjs --help` inside the kit folder to see everything the command line can do.

Where a bounty can be graded on your own machine, its `RULES.txt` has a **Grade locally** section with the exact command, so you can measure a practice score before you ever submit. Where it cannot, the rules say grading is the server's alone — the local checks in Step 5 are then your pre-flight.

## Step 4 — Build with your agent

1. **Wait for the opening, then start a fresh session.** Entries are built in agent sessions that begin at or after the bounty's opening time; a session that started earlier cannot be entered, even if the work continued afterwards.
2. **Create a new public repository** under your linked GitHub account, clone it next to the kit folder, and open your agent's session in it.
3. **Add an OSI-approved license** (MIT is the common choice). An entry without one is refused.
4. **Start from the kit's `starter/`** when it has one, and have your agent make it your own. A starter is a working entry that meets the rules — it is not a winner, and submitting it unchanged fails, because none of its lines are your agent's.
5. **Let the agent write the files in that session.** The checks match the transcripts against the files, so work that appears from nowhere counts against you. Writing some of it by hand is allowed; it simply counts less as your agent's work.
6. **Add whatever the rules ask for** — many bounties name a README template, a screenshot, or a specific entrypoint file. The rules are the checklist.

One tip that saves real time: have your agent read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, commands and checks included.

## Step 5 — Check, then submit

From the kit folder, bundle the transcripts of the sessions that built the entry:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

The bundle collects every session that worked on the repository, strips credentials and personal details, and adds a run record: your opening prompt word for word, the harness, model and setup that did the work, and the MCP servers used. If part of the record is missing, `bundle` writes nothing and names the flag that supplies it.

Then run the site's own pre-submit checks locally, on the exact commit and bundle you are about to send:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Fix everything it flags. A refused entry still counts toward the bounty's daily submission limit, so this local pass is the cheap place to catch a mistake.

When the check is clean, submit from the kit (or from the **Enter** form on the bounty page):

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The keypair signs the entry message; the wallet it belongs to is the wallet a prize for this entry will be claimed to.

## Step 6 — Follow the verdict

```sh
node cli/makefun.mjs status
```

shows your entries and their stages: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with the fix for it. Apply the fixes and submit again — you can resubmit until the deadline, within the bounty's daily and total limits. Know that your most recent submission with a receipt is the one that counts as your final entry, so resubmit to fix a problem, not on a whim.

## Step 7 — Claim a prize

When the final results are posted and your entry has placed, the prize becomes claimable from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person` honestly; a false answer disqualifies. Claims pass an automatic sanctions screen. For an escrowed bounty the prize is claimed from the escrow to the wallet that signed the winning entry, and a first claim pays the small Solana network fee and account rent (about 0.0025 SOL). A tax form is asked for only where the law requires one — for prizes paid from make.fun's reward wallet, only once a winner's prizes in a calendar year reach the tax reporting threshold.

## Practical tips from the entry loop

- **Budget your submissions.** Every bounty caps submissions per day and in total, and a refused entry still spends one. Run the local `check` until it is clean before you spend a submission on it.
- **Start the session after the opening, not before.** This is the easiest refusal to earn and the hardest to fix afterwards: no edit can move a session's start time. If your agent has been chatting about the bounty since yesterday, open a fresh session to build in.
- **Keep the build in one place.** Sessions that worked on the entry are collected from the machine that ran them. Build on one machine, in one repository clone, and bundle from that same machine.
- **Read a refusal literally.** Each failed check names its own fix, and the fix is usually small — a missing license file, a README in the wrong case, a session that began too early. Fix the named cause rather than rebuilding everything.
- **Mind the final re-check.** For repository entries the organisers read the repository again at the end: it must still be public, still yours, and its default branch must still carry whatever the rules required (for a guide like this one, the referral code). Do not rename, move or gut the repository after submitting.
- **Ties go to the earlier entry.** When you are choosing between submitting a clean entry now and polishing it for another day, remember that an exact tie is broken by the earlier receipt.

## Referrals: how the link in this guide works

Every account has a referral link, `https://make.fun/r/<code>`; adding `?ref=<code>` to any make.fun link carries the same code. This guide's link is mine: [https://make.fun/r/yhe8mkd4](https://make.fun/r/yhe8mkd4), code `yhe8mkd4`.

The mechanics are simple and worth understanding before you share your own:

- A referral binds to the first code a visitor's browser saw, and that first touch holds for 60 days; a later link does not replace it.
- When a new account signs up while your code is bound to it, you are credited, and make.fun pays referral rewards on top — the new account's own rewards are never reduced to pay yours.
- Only real, new accounts that actually take part count. Your own account, signups that share your person or network, clusters from one address, idle accounts and bots are all filtered out by the same checks that pay the referral rewards.
- Every reward is held for review (a day from binding) before it can be claimed.

Your own link, what each reward is currently worth, and everything you have earned are on the **Referrals** tab of your profile.

## Questions

<details>
<summary><strong>Does it cost anything to enter?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. A bounty with an entry fee says so on its page before you start. The model calls your agent makes while building are on your own agent account, as usual.
</details>

<details>
<summary><strong>Is make.fun legitimate?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation, and a bounty's reward is locked in a public, open-source on-chain escrow program on Solana when the bounty opens — before anyone builds anything. Winners claim from that escrow.
</details>

<details>
<summary><strong>Do I need to be a programmer?</strong></summary>

It helps, but your agent does the typing. Your part is steering: choosing a bounty you understand, reading its rules, checking the local grade and the pre-submit checks, and deciding when the entry is ready.
</details>

<details>
<summary><strong>Which agents can I use?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider and dozens more are found by the kit on its own. If your tool keeps its sessions somewhere unusual, `bundle --session <file>` points the kit at the file.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

They are read to verify that your own agent built your entry — that is the fairness mechanism of the whole site. Before upload, the kit strips credentials, e-mail addresses and home paths, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>What if my entry is refused?</strong></summary>

A refusal is not the end of the entry. The status names each failed check and its fix; correct the cause and submit again before the deadline, within the bounty's submission limits.
</details>

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — questions and other builders

---

<sub>Entered on [make.fun](https://make.fun/?ref=yhe8mkd4&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
