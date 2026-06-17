# Trust Is the Next Bottleneck — References & Evidence

**Confidential Computing Summit 2026 · Pawan Khandavilli**
Every load-bearing claim in the talk, with its primary source. Organized by slide.

Live deck: https://pkhandavilli.github.io/ccs2026-trust-bottleneck/
Attestation handshake PR: https://github.com/pkhandavilli/agent-governance-toolkit/pull/1

---

## Slide 2 — The cold open (five numbers)

| Claim | Source |
|---|---|
| **770,000 agents** exposed in a single night (Moltbook) | Wiz disclosure — https://www.wiz.io/blog/exposed-moltbook-database-reveals-millions-of-api-keys · incident brief — https://www.prplbx.com/blog/moltbook-breach-incident-brief |
| **195 million** citizen records exfiltrated with Claude Code + GPT-4.1 (Mexico, 9 agencies) | https://socradar.io/blog/mexican-government-breach-claude-chatgpt/ |
| **150M+ downloads, 10 CVEs**, 9/11 registries poisoned (MCP supply chain) | OX Security — https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ |
| **1 character** Host-header auth bypass (BadHost, CVE-2026-48710, Starlette/FastAPI) | X41 D-Sec — https://x41-dsec.de/lab/advisories/x41-2026-002-starlette/ · InfoQ — https://www.infoq.com/news/2026/06/badhost-ai-systems-vulnerability/ · scanner — https://badhost.org |
| **€0.01** transfer memo hijacks a banking AI agent (Blue41 / Bunq) | https://blue41.com/blog/how-we-helped-bunq-secure-their-financial-ai-assistant/ |

---

## Slides 3–5 — Payments is building agent trust right now

| Claim | Source |
|---|---|
| **Visa connected its payment network to ChatGPT** (Jun 11); top Reddit reaction "first person to trick the chatbot is about to make bank" (4,503 upvotes) | https://www.reddit.com/r/nottheonion/comments/1u33ymj/visa_plugs_its_payment_network_into_chatgpt/ |
| **Visa Trusted Agent Protocol** — signed agent-identity headers at the network layer (with Cloudflare; 100+ partners) | https://corporate.visa.com/en/products/trusted-agent-protocol.html |
| **Mastercard Agent Pay** — tokenized agent identities via MDES | https://www.mastercard.com/news/ |
| **Google AP2** — W3C Verifiable Credentials, signed Intent/Cart/Payment mandates; contributed to FIDO | https://ap2-protocol.org |
| **FIDO Agentic Authentication TWG** chartered (Apr 27–28, 2026) | https://www.businesswire.com/ (FIDO Alliance, Apr 27 2026) |
| "Who signs off on the machine?" — liability question in financial services | PYMNTS — https://www.pymnts.com/news/banking/2026/agentic-ai-and-banks-who-signs-off-on-the-machine/ |
| **The delegation problem** (token reused = overprivileged, or absent = untracked across hops) | O'Reilly Radar, Sunil Prakash, May 26 — https://www.oreilly.com/radar/who-authorized-that-the-delegation-problem-in-multi-agent-ai/ |
| **Blue41 / Bunq €0.01 attack** (context-as-attack-vector example) | https://blue41.com/blog/how-we-helped-bunq-secure-their-financial-ai-assistant/ |

---

## Slide 6 — The NSA got MCP right, and missed the deeper problem

| Claim | Source |
|---|---|
| **NSA AI Security Center** published its first MCP threat model (May 2026); recommends crypto identity and verifiable logs but stops short of hardware attestation | NSA CSI "MCP: Security Design Considerations" — https://www.nsa.gov/Portals/75/documents/Cybersecurity/CSI_MCP_SECURITY.pdf |
| **"MCP Is Dead?"** — tool definitions consume 10.5% of Claude's context window; architecture insufficient (HN 400 pts) | Quandri — https://www.quandri.io/engineering-blog/mcp-is-dead |
| Layering response: "the fix is layering, not replacement" | https://medium.com/@reactjsbd/mcp-isnt-dead-the-critique-is-right-the-fix-is-layering-not-replacement-26f2c076c0be |

---

## Slide 7 — The evidence cascade

| Row | Source |
|---|---|
| OX Security (Apr 15) — 10 CVEs, 150M+ downloads, registries poisoned | https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ |
| BadHost (May 27) — 1-char Host-header auth bypass | https://x41-dsec.de/lab/advisories/x41-2026-002-starlette/ |
| Mexico government (Dec–Feb) — 195M records | https://socradar.io/blog/mexican-government-breach-claude-chatgpt/ |
| O'Reilly Radar (May 26) — delegation problem | https://www.oreilly.com/radar/who-authorized-that-the-delegation-problem-in-multi-agent-ai/ |
| Mitiga / Claude Code (Jun) — MCP config hijack proxies OAuth tokens | https://www.esecurityplanet.com/threats/claude-code-mcp-attack-enables-persistent-token-theft/ |
| Blue41 / Bunq (Jun 10) — €0.01 memo hijack | https://blue41.com/blog/how-we-helped-bunq-secure-their-financial-ai-assistant/ |

Community-sentiment signals (same window):
- AI agent bankrupted its operator scanning DN42 (HN 1,451 pts) — https://lantian.pub/en/article/fun/ai-agent-bankrupted-their-operator-scan-dn42lantian.lantian/
- AI agent runs amok in Fedora (HN 549 pts) — https://lwn.net/SubscriberLink/1077035/c7e7c14fbd60fae9/
- "Continue? Y/N" permission-fatigue game (HN 386 pts) — https://llmgame.scalex.dev

---

## Slides 8–10 — Necessary, not sufficient; four gaps

| Claim | Source |
|---|---|
| Established frameworks (OWASP Agentic Top 10, NIST, ISO, CSA, Microsoft AGT) are real progress but stop at software trust | OWASP — https://www.infosecurity-magazine.com/news/owasp-agentic-ai-security-maturity/ |
| **AWS Bedrock AgentCore Identity** roots agent identity in OAuth/JWT tokens, not a hardware measurement (counter-example) | https://aws.amazon.com/blogs/machine-learning/introducing-amazon-bedrock-agentcore-identity-securing-agentic-ai-at-scale/ |
| **IETF WIMSE** is drafting how to carry remote-attestation evidence inside a workload-identity token | https://datatracker.ietf.org/wg/wimse/documents/ |
| RFC 8693 (OAuth 2.0 Token Exchange) — per-hop delegation | https://datatracker.ietf.org/doc/html/rfc8693 |

---

## Slide 11 — Three teams, same week, same architecture

| Team | Source |
|---|---|
| **Uber** — agent identity (SPIFFE/SPIRE workload identity, per-hop RFC 8693 token exchange, provenance chain), May 21 | https://www.uber.com/us/en/blog/solving-the-agent-identity-crisis/ |
| **attestable-mcp-server** (kontext-security) — enclaved mode, deny-without-attestation, working code; arXiv:2605.24248, May 22 | https://github.com/kontext-security/attestable-mcp-server · https://arxiv.org/abs/2605.24248 |
| **1Password** (credential management for AI agents) and **Keycard** (runtime attestation via SPIFFE, ephemeral per-task credentials) — two separate vendors, May 2026 | 1Password — https://blog.1password.com · Keycard — https://keycard.com |
| **WorkOS auth.md** — agent registration protocol (May 25) | https://workos.com |

---

## Slides 12–13 — The 6-layer stack & end-to-end payments on Confidential ACI

| Claim | Source |
|---|---|
| **Azure Confidential Container Instances** runs AMD SEV-SNP; per-container TEE boundary, MAA attestation | https://learn.microsoft.com/azure/container-instances/container-instances-confidential-overview |
| Layer 5 policy enforcement example — Microsoft **Agent Governance Toolkit** (OSS), missing piece is hardware anchoring | https://github.com/pkhandavilli/agent-governance-toolkit/pull/1 |
| Sweden **IMY** ruled TEEs + remote attestation (RFC 9334) satisfy GDPR Article 32 ("from promises to verifiable proof"), report IMY-2026-5444 | CCC blog — https://confidentialcomputing.io/2026/05/25/swedens-data-protection-authority-issues-landmark-gdpr-guidance-on-trusted-execution-environments/ |

---

## Slide 14 — Hardware is the foundation, not the silver bullet

| Claim | Source |
|---|---|
| **Hades** malware embeds prompt injection so AI scanners classify it as safe (software trust fails silently) | InfoWorld — https://www.infoworld.com/article/4182692/meet-hades-the-malware-that-lies-to-ai-security-agents.html |
| TEE side-channels are real and mitigated through patch + re-attestation (honest accounting) | TEE.Fail / prior CC side-channel research (Spectre, Foreshadow, ZenBleed, CacheWarp) |
| **OWASP:** 83% of enterprises plan agentic AI; only 29% feel ready to secure it | https://www.infosecurity-magazine.com/news/owasp-agentic-ai-security-maturity/ |
| EU AI Act high-risk obligations enforceable **Aug 2, 2026** (technology-neutral) | https://artificialintelligenceact.eu |
| Sweden IMY GDPR Article 32 precedent | https://confidentialcomputing.io/2026/05/25/swedens-data-protection-authority-issues-landmark-gdpr-guidance-on-trusted-execution-environments/ |
| Gap in EU AI Act for high-risk agentic systems | WatersTechnology — https://www.waterstechnology.com/emerging-technologies/7953095/mcp-is-dead-long-live-mcp |

---

## Slides 15–17 — The market is moving; what to build; close

| Claim | Source |
|---|---|
| **$236B** agentic AI market by 2034 ("if we ensure they are trustworthy") | WEF, Jan 2026 — https://www.weforum.org/stories/2026/01/ai-agents-trust/ |
| **75% of enterprises** adopting confidential computing (IDC 2025: 18% production, 57% pilot) | Survey, Forough et al., arXiv:2605.03213 — https://arxiv.org/abs/2605.03213 |
| **Apple Private Cloud Compute** shipped on Google Cloud (Intel TDX + NVIDIA confidential GPUs + Titan RoT); first PCC outside Apple data centers | Apple Security — https://security.apple.com/blog/expanding-pcc/ · https://www.helpnetsecurity.com/2026/06/10/apple-private-cloud-compute-google-cloud-expansion/ |
| WorkOS / Uber / 1Password shipping on attested identity, waiting for the hardware layer | (see slide 11 sources) |
| Building in public — provider-neutral attestation handshake PR | https://github.com/pkhandavilli/agent-governance-toolkit/pull/1 |

---

## Context & further reading

- "Confidential Computing for Agents" — Grokipedia (xAI knowledge base, ~60 references): https://grokipedia.com/page/Confidential_Computing_for_Agents
- "Agentic AI security is moving fast — here's where to start" — Confidential Computing Consortium, Jun 11 2026: https://confidentialcomputing.io/2026/06/11/agentic-ai-security-is-moving-fast-heres-where-to-start/
- "When Agents Handle Secrets: A Survey of Confidential Computing for Agentic AI" — arXiv:2605.03213: https://arxiv.org/abs/2605.03213

---

*Compiled for audience Q&A. Dates and attributions verified against primary sources where available; a few vendor links point to the company's main page where the exact post URL was not stable. Corrections welcome via the repo.*
