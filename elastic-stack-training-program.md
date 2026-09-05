# Elastic (ELK) Stack Engineering Training Program
### Complete Beginner → Production-Ready, Certification-Grade Elastic Engineer

**Audience:** Complete beginners to Elastic (basic Linux/command-line comfort assumed, zero prior Elastic/Kibana knowledge).
**Stack versions covered:** Elastic Stack 8.x (current widely-deployed) and 9.x (latest). Version-specific differences are flagged inline with a **[8.x/9.x DIFF]** tag wherever they matter.
**Certification alignment:** Phase 2 is built directly against the official **Elastic Certified Engineer (ECE)** exam objectives — and goes deeper than the exam requires in several places, per design intent. Note: Elastic updated the ECE exam from targeting Elastic 8.15 to targeting **9.3** effective September 1, 2026 — this program's Phase 2 projects are written to work on either version, with **[8.x/9.x DIFF]** flags anywhere the exam-relevant behavior changed.
**Format:** Five phases, each building on the last. Time estimates assume a beginner working through material carefully (including reading docs, hitting errors, and fixing them) — not just following steps blindly.

---

## PREREQUISITES

**Required — must have before starting:**
- Comfort with a command-line terminal: navigating directories, running commands, editing a file with nano/vim/VS Code
- Basic JSON literacy — able to read and hand-write nested JSON objects and arrays
- Basic understanding of REST APIs and HTTP methods (GET/POST/PUT/DELETE, status codes)
- A computer capable of running Docker and a local Kubernetes cluster (`kind`/`minikube`) — 16GB RAM recommended; 8GB is workable but tight once multiple projects run at once
- Ability to create free-tier accounts: an **Elastic Cloud** trial account, and an **AWS** account (used for EC2/S3 in later projects)

**Strongly recommended — helpful, but taught along the way if missing:**
- Basic Linux fundamentals: users/permissions, systemd services, package managers (apt/yum) — essential for Phase 4's manual on-prem build
- Basic networking concepts: IP addressing, ports, firewalls/security groups, DNS — needed for cluster discovery, TLS, and especially the Cross-Cluster Search/Replication projects
- Basic scripting ability in Python or Bash — several projects (benchmarking, threat-feed ingestion, Terraform automation) involve writing or adapting small scripts
- Basic Git/version-control familiarity — used throughout the Infrastructure-as-Code project and for keeping stack configuration under version control
- Basic Docker concepts (images, containers, volumes) — Phase 0.5 teaches this from scratch, but prior exposure speeds things up
- Basic Kubernetes concepts (pods, services, YAML manifests) — Phase 0.4 teaches this from scratch, but prior exposure helps

**Not required:**
- Any prior Elasticsearch, Kibana, or Elastic Stack experience — this program assumes zero prior exposure and builds every concept from first principles
- Any prior data engineering, search, or observability background

**A note on pacing:** because this program targets complete beginners, Phase 0 and the early Phase 1 projects deliberately over-explain concepts that experienced infrastructure engineers might find slow. Students with a strong existing Linux/cloud background can expect to move faster than the stated estimates; the estimates are calibrated for a true beginner working carefully through each concept, not skimming it.

---

## PROGRAM TIME SUMMARY

| Phase | Focus | Estimated Time |
|---|---|---|
| Phase 0 — Architecture & Provisioning Foundations | Concepts + 3 provisioning methods | ~24 hours |
| Phase 1 — Core Standard Projects | Full production skillset (16 projects) | ~107 hours |
| Phase 2 — Elastic Certified Engineer (ECE) Deep-Dive | Certification-grade mastery incl. CCS & CCR (12 projects) | ~79 hours |
| Phase 3 — Bonus Track: Security/SIEM | Optional specialization (3 projects) | ~18 hours |
| Phase 4 — Capstone: Self-Managed On-Prem | Final integrated deployment | ~22 hours |
| **Core Program Total (Phases 0, 1, 2, 4)** | | **~232 hours (~16–23 weeks part-time at 10–15 hrs/week)** |
| **Full Program incl. Bonus Track** | | **~250 hours (~17–25 weeks part-time)** |

A full-time bootcamp pace (~30 hrs/week) completes the core program in **~7–8 weeks**, or the full program including the bonus track in **~8–9 weeks**.

---

## FULL EXERCISE LIST (Quick Reference)

**Phase 0 — Foundations**
- 0.1 Elastic Stack Architecture Deep Dive — *4 hrs*
- 0.2 Node Roles & Cluster Topology Lab — *5 hrs*
- 0.3 Provisioning Method 1: Elastic Cloud Hosted (ECH) — *3 hrs*
- 0.4 Provisioning Method 2: Elastic Cloud on Kubernetes (ECK) — *6 hrs*
- 0.5 Provisioning Method 3: Docker / Docker Compose — *4 hrs*
- 0.6 Provisioning Trade-Off Comparison Exercise — *2 hrs*

**Phase 1 — Core Standard Projects**
1. Ingestion with Beats (Filebeat) — *5 hrs*
2. Ingestion with Logstash — *6 hrs*
3. Ingestion with Elastic Agent & Fleet — *6 hrs*
4. Data Modeling: Mappings, Templates & Data Streams — *6 hrs*
5. Index Lifecycle Management & Data Tiers — *8 hrs*
6. Kibana Visualization, Lens & Dashboards — *6 hrs*
7. Querying: DSL, ES|QL & EQL — *6 hrs*
8. Security Fundamentals: TLS, RBAC, API Keys, SSO — *8 hrs*
9. Alerting with Kibana Alert Rules — *5 hrs*
10. Observability: Application Performance Monitoring (APM) — *8 hrs*
11. Observability: Synthetic Monitoring — *5 hrs*
12. Observability Capstone: Unified Monitoring of a Real Application — *10 hrs*
13. Snapshot, Restore & Disaster Recovery — *6 hrs*
14. Performance Tuning, Scaling & Benchmarking (Rally) — *8 hrs*
15. Rolling Upgrades & Capacity Planning — *6 hrs*
16. Infrastructure as Code: Terraform for Elastic Cloud/ECK — *8 hrs*

**Phase 2 — Elastic Certified Engineer (ECE) Deep-Dive**
1. Custom Analysis & Text Analysis Engineering — *8 hrs*
2. Nested & Object Relationships in Mappings — *5 hrs*
3. Document CRUD, Reindex API & Update By Query Mastery — *6 hrs*
4. Advanced Ingest Pipelines with Painless Scripting — *8 hrs*
5. Advanced Query DSL: Fuzzy Matching, Highlighting, Sorting, Pagination & Search Templates — *7 hrs*
6. Aggregations Deep-Dive: Bucket, Metric, Pipeline & Sub-Aggregations — *8 hrs*
7. Runtime Fields & Asynchronous Search — *5 hrs*
8. Shard Allocation Diagnostics & Cluster Health Repair — *6 hrs*
9. Hot/Warm/Cold Architecture with Node Attributes & Shard Allocation Awareness — *6 hrs*
10. Cross-Cluster Search (CCS): Full Setup & Querying — *7 hrs*
11. Cross-Cluster Replication (CCR): Leader/Follower Setup — *7 hrs*
12. Searchable Snapshots & Full Backup/Restore Mastery — *6 hrs*

**Phase 3 — Bonus Track: Elastic Security/SIEM**
- B1. Detection Engineering Fundamentals — *6 hrs*
- B2. Building SIEM Dashboards — *5 hrs*
- B3. Threat-Intel Enrichment Project — *7 hrs*

**Phase 4 — Capstone**
- C1. Self-Managed On-Prem Production Deployment — *22 hrs*

---
---

# PHASE 0 — ARCHITECTURE & PROVISIONING FOUNDATIONS
*(~24 hours)*

## 0.1 Elastic Stack Architecture Deep Dive — *4 hrs*

**Objective:** Understand what each component does and how they fit together before touching a keyboard for real work.

**Cover:**
- **Elasticsearch** — the distributed search/analytics engine; documents, indices, the inverted index concept (why search is fast)
- **Kibana** — the UI/visualization and management layer
- **Logstash** — the heavyweight ingest/transform pipeline tool
- **Beats** — lightweight single-purpose shippers (Filebeat, Metricbeat, Packetbeat, etc.)
- **Elastic Agent + Fleet** — the modern, unified replacement/wrapper for Beats, managed centrally via Fleet Server, using "integrations" (pre-built data collection + parsing bundles)
- **[8.x/9.x DIFF]** Elastic Agent/Fleet has matured significantly between 8.x and 9.x — in 9.x, Agent-based collection is the clearly recommended default over standalone Beats for new deployments; standalone Beats remain fully supported but are positioned as the "legacy/lightweight" option.

**Exercise:** Draw (by hand or in a tool like Excalidraw/diagrams.net) the full data flow: source → shipper/agent → (optional Logstash) → Elasticsearch → Kibana. Label every component. This diagram becomes the reference students annotate throughout the program.

**Deliverable:** An architecture diagram + a one-page written explanation of what problem each component solves.

---

## 0.2 Node Roles & Cluster Topology Lab — *5 hrs*

**Objective:** Understand cluster anatomy well enough to make real topology decisions later.

**Cover:**
- **Master-eligible nodes** — cluster state management, why you need an odd number for quorum (split-brain avoidance)
- **Data nodes** and the **hot/warm/cold/frozen** tier model — where data lives as it ages, and why (cost vs. query speed trade-off)
- **Ingest nodes** — running ingest pipelines close to the write path
- **Machine learning (ml) nodes** — anomaly detection workloads
- **Transform nodes** — continuous/batch data transforms (pivoting/rolling up data)
- **Coordinating-only nodes** — pure request routing/fan-out, no data storage
- Shards and replicas — primary vs. replica, why shard count is a decision you can't easily undo later
- Cluster state, discovery, and quorum-based master election

**Exercise:** Stand up a single-node Elasticsearch instance locally (via the simple `.tar.gz`/`.deb` install — this is the one moment in the whole program where a single-node "quick start" is appropriate, purely to inspect internals). Run:
- `GET _cat/nodes?v` and `GET _cat/health?v`
- `GET _nodes` and identify which roles the node has
- Create an index with `number_of_shards: 3` and `number_of_replicas: 1`, then run `GET _cat/shards` and explain why replica shards show unassigned on a single node.

**Deliverable:** A written explanation (with `_cat` API output as evidence) of shard/replica behavior and why topology choices in production aren't arbitrary.

---

## 0.3 Provisioning Method 1: Elastic Cloud Hosted (ECH) — *3 hrs*

**Objective:** Provision a real multi-node deployment the way most companies who don't want to run their own infrastructure actually do it.

**Step-by-step:**
1. Create an Elastic Cloud trial account (Elastic offers a free trial — no local install needed for this method).
2. Create a new deployment: choose a cloud provider/region, and select a **hardware profile** (e.g., "Storage Optimized" vs. "General Purpose") — explain what each profile is tuned for.
3. Configure the deployment topology in the UI: hot data tier size, whether to enable a dedicated master tier, Kibana instance size.
4. Once deployed, connect via the Cloud ID and an API key (not username/password) from a local script, confirming connectivity with `GET /`.
5. Explore what ECH manages *for you* automatically: TLS certificates, backups (snapshots to cloud storage), version upgrades, scaling.
6. Resize the deployment (add a data node / increase RAM) live and observe zero-downtime scaling.

**Deliverable:** A live ECH deployment + a short write-up: "What did Elastic manage for me that I would otherwise have to do myself?"

---

## 0.4 Provisioning Method 2: Elastic Cloud on Kubernetes (ECK) — *6 hrs*

**Objective:** Provision the same kind of cluster, but as a Kubernetes-native, IaC-friendly deployment — the pattern most platform/infra teams use when they want Elastic running inside their own Kubernetes estate.

**Step-by-step:**
1. Stand up a local Kubernetes cluster (`kind` or `minikube` — free, no cloud cost).
2. Install the **ECK operator** via its official manifests (`kubectl apply -f https://download.elastic.co/downloads/eck/<version>/crds.yaml` and the operator manifest).
3. Define an `Elasticsearch` custom resource (YAML) specifying node sets (e.g., a 3-node master+data set), and apply it — watch ECK provision pods, TLS certs, and a Kubernetes Service automatically.
4. Define a `Kibana` custom resource pointing at the Elasticsearch resource, and connect them.
5. Scale the Elasticsearch node set by editing the YAML's replica count and re-applying — observe ECK handle the rolling change safely.
6. Inspect what ECK auto-generated: the TLS CA secret, the elastic user's auto-generated password secret, internal Service DNS names.
7. **[8.x/9.x DIFF]** Note any CRD schema/field changes between the ECK operator versions compatible with 8.x vs. 9.x Elasticsearch — check the ECK compatibility matrix before choosing versions.

**Deliverable:** A working ECK-provisioned cluster inside `kind`/`minikube` + the YAML manifests used, with comments explaining each field.

---

## 0.5 Provisioning Method 3: Docker / Docker Compose — *4 hrs*

**Objective:** Understand the fully manual, container-based approach — the fastest way to spin up a realistic multi-node cluster on a single laptop for development/testing.

**Step-by-step:**
1. Write a `docker-compose.yml` defining 3 Elasticsearch containers (forming a real multi-node cluster via Docker's internal networking) and 1 Kibana container.
2. Configure environment variables per node: `node.roles`, `discovery.seed_hosts` (using Docker service names), `cluster.initial_master_nodes`.
3. Enable security (`xpack.security.enabled=true`) and generate/mount TLS certificates using `elasticsearch-certutil` inside a helper container step — don't skip security "for convenience," even in a local Docker setup, since the whole point is production-realistic habits.
4. Bring the stack up with `docker compose up -d` and verify with `GET _cluster/health` through the exposed port.
5. Connect Kibana to the cluster using the auto-generated enrollment token or manually-configured credentials.
6. Tear down and bring back up with a named Docker volume, and confirm data persisted across restarts (a common beginner mistake is losing data because volumes weren't mounted).

**Deliverable:** A working `docker-compose.yml` (with security enabled) that any student can `docker compose up` to reproduce a 3-node secured cluster from scratch.

---

## 0.6 Provisioning Trade-Off Comparison Exercise — *2 hrs*

**Objective:** Cement the judgment, not just the mechanics.

**Exercise:** Write a short comparison document answering, for each of ECH, ECK, and Docker:
- Who manages upgrades, backups, and scaling?
- What's the cost model (managed service billing vs. your own infra billing vs. free/local)?
- When would a real company choose this method? (e.g., ECH for teams with no dedicated infra function; ECK for platform teams already standardized on Kubernetes; Docker/Compose for local dev, CI test environments, or small self-hosted setups)
- What does each method hide from you that Phase 4's on-prem build will force you to do manually?

**Deliverable:** A one-to-two-page comparison table + narrative — this is the document a student could genuinely bring to a "why did you choose X" interview question.

---
---

# PHASE 1 — CORE STANDARD PROJECTS
*(~107 hours)*

## Project 1 — Ingestion with Beats (Filebeat) — *5 hrs*

**Objective:** Learn the lightweight, single-purpose shipper model.

**Data source:** The public **NASA-HTTP access log dataset** (real 1995 Apache-format web server logs, widely mirrored — search "NASA HTTP access log dataset"), or generate live traffic with **`flog`** (github.com/mingrammer/flog), a synthetic Apache/Nginx/JSON log generator.

**Step-by-step:**
1. Install Filebeat on a VM/container pointed at the log file (or `flog`'s live output).
2. Enable the built-in **Apache module** (`filebeat modules enable apache`) and compare its pre-built parsing to writing your own custom input + ingest pipeline from scratch.
3. Configure the Elasticsearch output with an API key (least-privilege, not the superuser).
4. Verify data lands correctly in the default Filebeat data stream, and inspect the ECS (Elastic Common Schema) fields it auto-populated.
5. Build a simple Kibana Discover view and a Lens visualization confirming ingestion.

**Deliverable:** Working Filebeat pipeline + a short note comparing the module's auto-parsing vs. hand-built parsing effort.

---

## Project 2 — Ingestion with Logstash — *6 hrs*

**Objective:** Learn heavyweight transform-in-flight ingestion, and debug the classic real-world failure modes.

**Data source:** Same NASA/`flog` log source as Project 1 (reuse it to highlight the architectural difference vs. Beats-only ingestion).

**Step-by-step:**
1. Install Logstash; build a pipeline: `input { beats {} }` → `filter { grok, date, geoip }` → `output { elasticsearch {} }`.
2. Feed a log line containing a raw unicode null byte and watch Elasticsearch reject/mangle the document; fix with a `mutate { gsub }` step.
3. Feed a non-default timestamp format, observe `_dateparsefailure` tags, and fix the `date` filter's match patterns.
4. Trigger a mapping conflict with a dotted field name (e.g., `user.name` sent as a flat string key) and fix it with the **dot-expander** ingest processor.
5. Compare this Logstash-based pipeline to Project 1's direct-to-Elasticsearch Beats pipeline — when would you actually need Logstash in the path?

**Deliverable:** Documented Logstash pipeline config + a "bugs I hit and fixed" write-up.

---

## Project 3 — Ingestion with Elastic Agent & Fleet — *6 hrs*

**Objective:** Learn the modern, centrally-managed ingestion model that's replacing standalone Beats in new deployments.

**Step-by-step:**
1. Set up **Fleet Server** (either via ECH's built-in Fleet-managed option from Phase 0.3, or self-hosted).
2. Enroll a new Elastic Agent from a host/VM into Fleet using an enrollment token.
3. Assign a **System integration** and an **Apache/Nginx integration** to the agent's policy from the Fleet UI — no manual config file editing required — and watch data start flowing.
4. Compare this centrally-managed experience to Project 1's manually-configured Filebeat: what changed operationally (policy-based management, central upgrade control, unified agent for logs+metrics+more)?
5. Add a custom log input to the agent policy for a source not covered by a pre-built integration, and build a custom ingest pipeline for it in Fleet's "Advanced" settings.
6. **[8.x/9.x DIFF]** Note UI/workflow differences in Fleet's integration policy editor between 8.x and 9.x if present at the time of teaching.

**Deliverable:** A Fleet-managed agent policy + data flowing from at least one pre-built integration and one custom input.

---

## Project 4 — Data Modeling: Mappings, Templates & Data Streams — *6 hrs*

**Objective:** Move beyond "let Elasticsearch guess the mapping" to deliberate schema design — the single biggest gap between hobbyist and production usage.

**Step-by-step:**
1. Ingest a JSON dataset (Kibana's built-in **sample eCommerce or web logs dataset** is a good fit) using dynamic mapping, and inspect the auto-generated mapping with `GET <index>/_mapping`.
2. Identify mapping mistakes dynamic mapping made (e.g., a numeric-looking field mapped as `text` instead of `keyword`, dates not recognized).
3. Design an explicit **index template** with a **component template** for common fields, correct field types (`keyword` vs. `text`, `date` formats, `geo_point`), and appropriate `analyzer` choices.
4. Convert the ingestion target from a plain index to a proper **data stream**, understanding the backing-index/rollover relationship.
5. Re-ingest the same data through the new template and confirm mapping correctness.

**Deliverable:** A component + index template pair (JSON) + a before/after mapping comparison document.

---

## Project 5 — Index Lifecycle Management & Data Tiers — *8 hrs*

**Objective:** Manage data cost and performance over time — a core "keeps the lights on" production skill.

**Step-by-step:**
1. On your Phase 0 cluster (ECK or Docker, since this needs multiple data tiers), configure nodes with `data_hot`, `data_warm`, `data_cold`, and (optionally) `data_frozen` roles.
2. Build an **ILM policy**: rollover on size/age, move to warm after N days (with `shrink` and `forcemerge` actions), move to cold after N more days, and delete after a retention period.
3. Attach the ILM policy to your Project 4 data stream via the index template.
4. Force a rollover manually and observe a new backing index created, and the old one begin its lifecycle journey through `_ilm/explain`.
5. Configure a **searchable snapshot** as the frozen-tier storage mechanism, and explain the cost/performance trade-off it represents (cheap object storage, slightly slower first query). *(This gets a full dedicated deep-dive later in Phase 2.12 — here, the goal is just to see it work end-to-end inside an ILM policy.)*
6. Simulate the passage of time by setting artificially short ILM phase durations for testing, and watch data actually migrate tiers within the lab session.

**Deliverable:** A working ILM policy moving data through at least 3 tiers, with `_ilm/explain` output as evidence, plus a written explanation of the cost/performance trade-off at each tier.

---

## Project 6 — Kibana Visualization, Lens & Dashboards — *6 hrs*

**Objective:** Build dashboards the way a professional does — not just "click a chart," but designed for an audience and a decision.

**Step-by-step:**
1. Using your Project 1–4 ingested data, build a **Data View** with proper field formatting.
2. Build 4–5 visualizations in **Lens**: a time-series line chart, a top-N bar chart, a data table with conditional formatting, and a geo map (using the `geoip` fields from Project 2).
3. Compose them into a single dashboard with filters and a global time picker, designed around a specific audience question (e.g., "Is our web traffic healthy right now?" — not just "here are some charts").
4. Add a **drilldown** (click a bar → filter another panel or navigate to Discover with context preserved).
5. Share the dashboard via a shareable link and as a scheduled PDF/PNG report.

**Deliverable:** A published dashboard + a one-paragraph "audience and purpose" statement justifying each panel's inclusion.

---

## Project 7 — Querying: DSL, ES|QL & EQL — *6 hrs*

**Objective:** Be fluent in all three major query approaches, and know when to reach for each. *(Phase 2.5 goes much deeper into DSL-specific query features — this project is about breadth across languages, not exhaustive DSL mastery.)*

**Step-by-step:**
1. Write the same analytical question (e.g., "top 10 URLs by request count in the last 24 hours, excluding bots") three ways:
   - **Query DSL** (`GET <index>/_search` with `aggs`)
   - **ES|QL** (`FROM <index> | WHERE ... | STATS ... | SORT ... | LIMIT 10`)
   - Compare readability and iteration speed between the two.
2. Learn **EQL** (Event Query Language) with a sequence-based query (e.g., "process A started, then within 5 minutes process B started") against sample process/event data — this previews the Security bonus track.
3. Use the ES|QL console in Kibana (Discover's ES|QL mode) to interactively explore data without writing JSON.
4. Build one Kibana Lens visualization powered directly by an ES|QL query instead of the classic aggregation editor.
5. **[8.x/9.x DIFF]** ES|QL has expanded significantly in capability (e.g., joins, more functions) moving from 8.x into 9.x — flag which functions used in this exercise are version-gated.

**Deliverable:** A short reference sheet, written by the student, comparing DSL vs. ES|QL vs. EQL syntax for the same three example questions.

---

## Project 8 — Security Fundamentals: TLS, RBAC, API Keys, SSO — *8 hrs*

**Objective:** Build the access-control layer a production cluster cannot ship without.

**Step-by-step:**
1. On your Docker or ECK cluster, generate a CA and node certificates with `elasticsearch-certutil`, and enable transport + HTTP TLS end-to-end (mTLS between nodes).
2. Create **custom roles** with least-privilege index/cluster privileges (e.g., a read-only "dashboard viewer" role scoped to one index pattern, a "log writer" role that can only index, not read/delete).
3. Create users assigned to those roles and verify enforcement by attempting (and being denied) an out-of-scope action.
4. Create **API keys** scoped down further than the issuing user's own privileges, and use one in a Beats/Agent config instead of a username/password.
5. Configure a basic **SSO** integration concept using SAML or OIDC against a free identity provider test tenant (e.g., a free Okta developer account), understanding the role-mapping concept even if full production SSO setup is simplified for the lab.
6. Document a full access-control matrix: which role can do what, on which indices.

**Deliverable:** A working TLS+RBAC+API-key configuration, plus a written access-control matrix.

---

## Project 9 — Alerting with Kibana Alert Rules — *5 hrs*

**Objective:** Build real detection logic on top of the data you've already ingested.

**Step-by-step:**
1. Using Project 1/2's web log data, author an **Elasticsearch Query rule** (Kibana Alert Rule) that fires when error-response-code volume exceeds a threshold in a rolling window.
2. Author a second rule using an **ES|QL rule type**, replicating the same detection logic, and compare authoring experience to the DSL-based rule.
3. Configure a **connector/action** (email, Slack, or a webhook to a simple local receiver) so the rule notifies somewhere real.
4. Test the rule's recovery behavior (does it notify when the condition clears, not just when it fires?).
5. Tune the rule to avoid alert fatigue (appropriate check interval, grouping, and suppression).

**Deliverable:** A working, tested alert rule with a documented "what does this alert mean and what should the on-call engineer do" runbook note.

---

## Project 10 — Observability: Application Performance Monitoring (APM) — *8 hrs*

**Objective:** Instrument a real application and understand distributed tracing.

**Step-by-step:**
1. Deploy a small sample application (Elastic publishes an official **APM sample "opbeans" demo app** for exactly this purpose, in multiple languages) or instrument your own simple app.
2. Install the **APM integration** via Elastic Agent/Fleet (Project 3 skills reused) and point the app's APM agent at it.
3. Generate traffic against the app and explore the resulting **service map**, transaction traces, and span waterfalls in Kibana APM.
4. Introduce an artificial slow database call or an error in the sample app, redeploy, and confirm APM surfaces it as a latency spike / error rate increase.
5. Correlate an APM trace with the underlying logs from the same request (log/trace correlation via shared identifiers) — a core "real production debugging" skill.

**Deliverable:** A working APM setup with a captured trace of a deliberately-introduced performance problem, plus the log correlation showing the same incident from both angles.

---

## Project 11 — Observability: Synthetic Monitoring — *5 hrs*

**Objective:** Monitor availability proactively, from the outside in.

**Step-by-step:**
1. Using Elastic **Synthetics** (via Fleet/Elastic Agent or the standalone `@elastic/synthetics` CLI), write a lightweight monitor that checks an HTTP endpoint (your Project 10 sample app, or any public URL) on an interval.
2. Write a second, **browser-based journey** monitor (Playwright-backed) that simulates a real user flow (load a page, click something, assert content appears).
3. Deliberately break the monitored endpoint/flow and confirm the synthetic monitor correctly reports the failure with a screenshot/trace.
4. Wire a Kibana Alert Rule to the synthetic monitor's results so a failed check pages someone (reusing Project 9 skills).

**Deliverable:** A working synthetic monitor (uptime + one browser journey) with a captured failure screenshot from the deliberately-broken test.

---

## Project 12 — Observability Capstone: Unified Monitoring of a Real Application — *10 hrs*

**Objective:** Combine Projects 3, 9, 10, and 11 into one coherent observability solution for a single application — this is what "world-class production observability" actually looks like end-to-end.

**Step-by-step:**
1. Take the Project 10 sample application and instrument it fully: logs (via Agent), metrics (via Agent's System/Docker integration), APM traces, and a synthetic uptime + journey check.
2. Build a single **"Service Health" dashboard** combining all four signal types for this one application.
3. Simulate a realistic incident (e.g., inject latency, then a full outage) and walk through diagnosing it using each signal type in turn — document which signal you'd check first in a real on-call scenario and why.
4. Set up alert rules across at least two signal types (e.g., an error-rate APM alert and a synthetic-monitor-down alert) with different urgency/routing.

**Deliverable:** A single unified dashboard + a written incident-response narrative for the simulated outage, showing how logs, metrics, traces, and synthetics each contributed to the diagnosis.

---

## Project 13 — Snapshot, Restore & Disaster Recovery — *6 hrs*

**Objective:** Prove you can recover a cluster, not just build one. *(This is the foundation-level version — Phase 2.12 later adds searchable-snapshot depth and full mastery-level scenarios.)*

**Step-by-step:**
1. Register a snapshot repository (local filesystem for lab purposes, or actual S3/cloud storage if available).
2. Configure an **SLM (Snapshot Lifecycle Management)** policy for automated, scheduled snapshots.
3. Take a manual snapshot, then deliberately delete an index (simulating an incident) and **restore** it from the snapshot, verifying document counts match.
4. Simulate a full cluster loss scenario: stand up a brand-new empty cluster and restore data into it from the snapshot repository — this is the real DR test, not just "restore into the same cluster."
5. Document a Recovery Point Objective (RPO) and Recovery Time Objective (RTO) for your setup based on snapshot frequency and observed restore time.

**Deliverable:** A documented, tested DR runbook with actual measured restore time, and stated RPO/RTO.

---

## Project 14 — Performance Tuning, Scaling & Benchmarking — *8 hrs*

**Objective:** Learn to measure before you optimize — and how to prove an optimization actually worked.

**Step-by-step:**
1. Install **esrally** (Elastic's official benchmarking tool) and run a baseline benchmark against your cluster using one of Rally's standard tracks (e.g., `http_logs`).
2. Record baseline indexing throughput and query latency.
3. Deliberately misconfigure something for a controlled comparison (e.g., too many shards for the data volume, or an inefficient mapping with excessive `text` fields), re-run the benchmark, and observe the regression.
4. Fix the misconfiguration and re-run to confirm recovery, producing a clean before/after/fixed three-point comparison.
5. Tune at least one real setting with measurable impact (e.g., refresh interval, bulk request size, replica count during a bulk load) and quantify the improvement.

**Deliverable:** A benchmark report (Rally output + your own summary table) showing a measured before/after performance change from a real tuning decision.

---

## Project 15 — Rolling Upgrades & Capacity Planning — *6 hrs*

**Objective:** Learn to change a live production cluster without an outage, and to plan ahead instead of reacting.

**Step-by-step:**
1. On a multi-node cluster (Docker or ECK), perform a **rolling upgrade** to a newer minor version: disable shard allocation, stop one node, upgrade its binaries, restart, re-enable allocation, wait for green, repeat per node.
2. Confirm zero query downtime was experienced by running a continuous background query loop throughout the upgrade.
3. **[8.x/9.x DIFF]** Attempt (in a disposable lab cluster only) a major-version upgrade path (8.x → 9.x) and document the specific pre-upgrade compatibility checks Elastic requires (deprecation warnings, the Upgrade Assistant in Kibana) versus a routine minor-version rolling upgrade.
4. Build a simple capacity-planning worksheet: given a projected daily ingest volume and retention period, calculate required storage, and back into a shard/node count recommendation using the sizing heuristics learned in Phase 0.

**Deliverable:** A documented, executed rolling upgrade with zero-downtime evidence, plus a capacity-planning worksheet for a hypothetical future growth scenario.

---

## Project 16 — Infrastructure as Code: Terraform for Elastic Cloud/ECK — *8 hrs*

**Objective:** Stop clicking buttons in the console — manage your Elastic infrastructure the way a real platform team does.

**Step-by-step:**
1. Use the official **Elastic Cloud Terraform provider** to define an ECH deployment (topology, version, region) as code, `terraform apply` it, then modify the config (e.g., resize) and `terraform apply` again to see a controlled, reviewable change.
2. Destroy and recreate the same deployment from the Terraform config alone, proving the environment is fully reproducible.
3. For the ECK path, express the `Elasticsearch`/`Kibana` custom resources (from Phase 0.4) as Terraform-managed Kubernetes manifests (via the Kubernetes/Helm Terraform providers), so the whole stack — cluster and Elastic resources — is defined in one version-controlled place.
4. Store index templates, ILM policies, and alert rules as version-controlled JSON/YAML files, and write a small script that applies them via the Elasticsearch/Kibana APIs on deploy — treating "stack configuration," not just "infrastructure," as code.

**Deliverable:** A Terraform configuration that can fully recreate your Elastic deployment from scratch, plus version-controlled stack-configuration files (templates/policies/rules) applied via script.

---
---

# PHASE 2 — ELASTIC CERTIFIED ENGINEER (ECE) CERTIFICATION DEEP-DIVE
*(~79 hours)*

Phase 1 gave students a working professional skillset. Phase 2 now goes back through the data-modeling, querying, and cluster-administration surface area with the specific rigor the official **Elastic Certified Engineer** exam demands — and, per design intent, pushes past exam depth in several places (e.g., the CCS and CCR projects go further than a single exam task would require, into full failure-mode testing). Nothing here duplicates Phase 1; each project either covers a concept Phase 1 didn't touch, or takes a Phase 1 concept (analyzers, snapshots) to certification-grade depth.

**Exam objective category → project mapping** (based on Elastic's official published objectives):

| ECE Exam Objective Category | Covered By |
|---|---|
| Data Management (mappings, templates, analyzers, nested objects) | Projects 2.1, 2.2 (+ Phase 1 Project 4) |
| Searching Data (queries, highlighting, sorting, pagination, CCS, runtime fields) | Projects 2.5, 2.7, 2.10 (+ Phase 1 Project 7) |
| Data Processing (CRUD, reindex, update-by-query, ingest pipelines/Painless) | Projects 2.3, 2.4 |
| Data Analysis (aggregations) | Project 2.6 |
| Cluster Management (shard diagnostics, snapshots, CCS, CCR, hot/warm) | Projects 2.8, 2.9, 2.10, 2.11, 2.12 (+ Phase 1 Project 13) |
| Installation & Configuration / Security (deploy, node config, RBAC) | Phase 0 + Phase 1 Project 8 |

**[8.x/9.x DIFF — exam version note]** As of September 1, 2026, Elastic updated the live ECE exam to target Elastic Stack **9.3** (previously 8.15). All Phase 2 projects are written to work on both versions, but students specifically preparing to *sit the current exam* should do a final pass of these projects on a 9.3 cluster and pay attention to the version-diff callouts below.

---

## 2.1 Custom Analysis & Text Analysis Engineering — *8 hrs*

**Objective:** Understand exactly how text becomes searchable — the concept most self-taught Elastic users skip, and the exam tests directly.

**Step-by-step:**
1. Use the `_analyze` API to see how the built-in `standard` analyzer tokenizes a sentence, then do the same with `simple`, `whitespace`, and `english` analyzers, and explain the differences (stemming, stop words, lowercasing).
2. Build a **custom analyzer** from components: pick a `tokenizer` (e.g., `standard`), and stack `char_filter`s (e.g., `html_strip`) and `filter`s (e.g., `lowercase`, `asciifolding`, a custom `stop` filter, a `synonym` filter) — test it against real messy text (HTML-embedded product descriptions work well).
3. Build a **custom normalizer** for `keyword` fields (e.g., lowercase + trim, so `"USA"` and `"usa "` match on exact-match fields).
4. Define **multi-fields**: map a single field (e.g., `product_name`) as both `text` (for full-text search) and `keyword` (for exact match/aggregation) and as a second `text` field using a different language analyzer.
5. Build a **dynamic template** that automatically maps any field ending in `_code` as `keyword` regardless of what value first arrives, and any string field over a certain length as `text` — test by indexing documents with fields matching and not matching the pattern.
6. Write a short reference doc explaining when you'd reach for a custom analyzer vs. a normalizer vs. a dynamic template.

**Deliverable:** A component template containing at least one custom analyzer, one normalizer, and one dynamic template, tested against real sample data with `_analyze` output as evidence.

---

## 2.2 Nested & Object Relationships in Mappings — *5 hrs*

**Objective:** Understand the single most commonly-missed mapping concept: how Elasticsearch actually stores arrays of objects internally, and why it silently breaks naive queries.

**Step-by-step:**
1. Index a document with a plain `object`-mapped array field (e.g., an order with multiple line items, each having a `product` and `quantity`), then run a query that should match "an item where product=X AND quantity=Y" — but which actually matches incorrectly by mixing fields *across* different array elements (the classic "flattening" bug).
2. Explain, with the `_mapping` and query evidence, *why* this happened (object arrays are flattened internally — Elasticsearch loses the per-element association).
3. Remap the same field as `nested`, reindex the data, and rewrite the query as a `nested` query — confirm it now correctly respects per-element relationships.
4. Explore the trade-off: nested fields are stored as separate hidden documents internally, which affects both query complexity (`nested`/`inner_hits`) and performance at scale (many nested docs per parent = more overhead) — benchmark a bulk index of documents with a large nested array vs. the same data flattened.
5. Cover the alternative — `join` fields (parent/child relationships) — briefly, and explain when you'd reach for `join` instead of `nested` (parent/child data that changes independently and frequently vs. array data indexed once with its parent).

**Deliverable:** A documented before/after (object → nested) example showing the exact incorrect-match bug and its fix, plus a short note on the performance trade-off you observed.

---

## 2.3 Document CRUD, Reindex API & Update By Query Mastery — *6 hrs*

**Objective:** Be fluent in every document-level operation the exam tests, including the two most commonly under-practiced APIs.

**Step-by-step:**
1. Perform full CRUD via the REST API: `PUT`/`POST` to index a document (with and without an explicit `_id`), `GET` to retrieve it, partial `_update` (both a field-merge update and a Painless-script update), and `DELETE`.
2. Use `_bulk` to perform mixed index/update/delete operations in a single request, and correctly interpret a bulk response containing partial failures.
3. Use the **Update By Query API** to apply a change across every document matching a query (e.g., add a `processed: true` field to all documents older than a date) without reindexing.
4. Use the **Reindex API** to copy data from one index to another while transforming it in-flight with a Painless `script` block (e.g., renaming a field, or combining two fields into one) — and reindex from a **remote cluster** (`remote.host`) as a separate exercise, since this is explicitly exam-tested and easy to overlook.
5. Compare `_update_by_query` vs. `_reindex` vs. a `Reindex API with a script`: when is each the right tool?

**Deliverable:** A worked example of each API (CRUD, bulk, update-by-query, reindex-with-script, remote reindex) with before/after document counts or content as evidence.

---

## 2.4 Advanced Ingest Pipelines with Painless Scripting — *8 hrs*

**Objective:** Go beyond Phase 1's basic ingest-pipeline debugging into building non-trivial pipelines with real conditional logic and scripting.

**Step-by-step:**
1. Build a multi-stage ingest pipeline chaining at least five processors: `grok` or `dissect` (parse), `date` (timestamp), `set` (add a computed field), `rename`, `remove`, and a conditional processor guarded by an `if` condition (e.g., only run `lowercase` if a field exists and matches a pattern).
2. Write a **Painless script processor** that performs logic no built-in processor covers (e.g., compute a custom risk score from three numeric fields, or conditionally categorize a value into a bucket label).
3. Build an **enrich processor** end-to-end: create an enrich policy against a lookup index (e.g., a small IP-to-department mapping), execute the policy, and use it in a pipeline to enrich incoming documents.
4. Configure a pipeline's `on_failure` handling so a processor failure routes the document to a dead-letter index instead of silently dropping or blocking ingestion — then deliberately trigger a failure and confirm the routing works.
5. Simulate the whole pipeline using the `_ingest/pipeline/_simulate` API before ever touching live data — build the habit of simulating first.

**Deliverable:** A production-style ingest pipeline (5+ processors, one Painless script, one enrich lookup, one failure-handling path) with `_simulate` output as evidence.

---

## 2.5 Advanced Query DSL: Fuzzy Matching, Highlighting, Sorting, Pagination & Search Templates — *7 hrs*

**Objective:** Master every query-shaping feature the exam tests individually.

**Step-by-step:**
1. Write queries covering the full match family: `match`, `match_phrase`, `multi_match` (with `best_fields` and `most_fields` type), and a `bool` query combining `must`/`should`/`must_not`/`filter` correctly (and explain why `filter` doesn't affect score while `must` does).
2. Apply **fuzzy matching** (`fuzziness: AUTO`) to tolerate typos, and test it against deliberately misspelled search terms.
3. Add **highlighting** to a query response so matched terms are wrapped in `<em>` tags, and tune the highlighter's fragment size.
4. Implement **sorting** by multiple fields (including a `_script`-based sort for a computed value) and **pagination** two ways: classic `from`/`size` (and explain its deep-pagination limitation) and `search_after` for efficient deep pagination.
5. Define and use a **search template** (a parameterized, reusable query stored server-side) and execute it via `_search/template` with different parameter values.
6. Write an **asynchronous search** (`_async_search`) against a large dataset, poll for partial results, and retrieve the final result — and explain when async search is the right tool (long-running queries over huge datasets where you don't want to hold a client connection open).

**Deliverable:** One consolidated Dev Tools console script exercising every feature above against a shared dataset, with comments explaining each query's purpose.

---

## 2.6 Aggregations Deep-Dive: Bucket, Metric, Pipeline & Sub-Aggregations — *8 hrs*

**Objective:** Full fluency in Elasticsearch's analytics engine, not just "terms agg + a chart."

**Step-by-step:**
1. Write **metric aggregations**: `avg`, `sum`, `min`/`max`, `cardinality` (approximate unique count), and `percentiles`.
2. Write **bucket aggregations**: `terms`, `date_histogram`, `range`, and `filters` (multiple named filter buckets in one request).
3. Nest a metric aggregation inside a bucket aggregation as a **sub-aggregation** (e.g., average order value per product category), then nest a second level (e.g., further split by region) to build a genuinely multi-dimensional analysis.
4. Write a **pipeline aggregation** that operates on the output of another aggregation (e.g., `derivative` or `moving_fn` on a `date_histogram`'s bucket counts, or `bucket_script` to compute a ratio between two sibling metrics).
5. Combine a **runtime field** (defined at query time, not indexed) into an aggregation — e.g., aggregate on a computed "price bucket" that doesn't exist as a stored field — and discuss the performance trade-off of computing at query time vs. indexing the field.
6. Build one real multi-level report entirely in aggregations (no Kibana Lens) — e.g., "average response time per URL per hour, with week-over-week percentage change" — combining bucket, sub-aggregation, and pipeline aggregation concepts together.

**Deliverable:** The final multi-level aggregation query plus its raw JSON response, with a written explanation of each nesting level's purpose.

---

## 2.7 Runtime Fields & Asynchronous Search — *5 hrs*

**Objective:** Understand schema-on-read as a deliberate design tool, not just a query-time hack. *(Runtime fields also appear inside Project 2.6's aggregation work — this project is where they're taught properly, end to end.)*

**Step-by-step:**
1. Define a **runtime field** in an index mapping using a Painless script (e.g., derive a `full_name` field from `first_name` + `last_name`, or bucket a numeric field into labeled ranges) and query/aggregate on it without ever indexing it.
2. Define the same logic as a **query-time runtime field** (in the `_search` request body itself, not the mapping) for a one-off exploratory need, and compare the two approaches' use cases.
3. Benchmark a query using a runtime field against the same query with the field properly indexed, at a meaningful document count, and document the latency difference — runtime fields trade indexing cost for query-time cost, and the exam expects you to understand that trade-off, not just the syntax.
4. Revisit **asynchronous search** in this context: run an async search using a query that includes a runtime field over a large index, demonstrating why async search and runtime fields are often used together for ad hoc, exploratory analysis over data you don't want to permanently reshape.

**Deliverable:** A runtime field defined both ways (mapping-level and query-level), plus a benchmark table comparing runtime-field query latency to an equivalent indexed-field query.

---

## 2.8 Shard Allocation Diagnostics & Cluster Health Repair — *6 hrs*

**Objective:** Be able to walk into a red or yellow cluster and fix it — one of the most heavily-tested, hands-on exam skills.

**Step-by-step:**
1. Deliberately break your cluster's health in at least three distinct ways and diagnose/fix each:
   - **Unassigned replica shards** on a single-node setup — diagnose with `GET _cluster/allocation/explain`, understand why it's expected here, and fix by setting `number_of_replicas: 0` where appropriate.
   - **Disk watermark breach** — fill a node's disk (or lower the watermark thresholds to trigger it artificially) and watch shards fail to allocate; diagnose via `_cluster/allocation/explain` showing the disk threshold decider, and fix by freeing space or adjusting `cluster.routing.allocation.disk.watermark.*` settings appropriately.
   - **Shard allocation filtering conflict** — set an `index.routing.allocation.require` attribute that no node satisfies, watch the index go unassigned, and fix it.
2. Use `GET _cat/shards?v`, `GET _cat/allocation?v`, and `GET _cluster/health?level=indices` together as your standard triage sequence, and write up that sequence as a checklist.
3. Practice manually rerouting a shard with the `_cluster/reroute` API (with `retry_failed: true` after fixing an underlying issue).

**Deliverable:** Three documented incident diagnoses (symptom → API evidence → root cause → fix) plus your personal triage checklist.

---

## 2.9 Hot/Warm/Cold Architecture with Node Attributes & Shard Allocation Awareness — *6 hrs*

**Objective:** Build a hot/warm architecture the exam-tested, manual way — using node attributes and allocation filtering directly — which is more foundational than (and a prerequisite for understanding) the ILM-managed version from Phase 1 Project 5.

**Step-by-step:**
1. Tag nodes with a custom attribute in `elasticsearch.yml` (e.g., `node.attr.box_type: hot` on some nodes, `warm` on others) — do this across your Docker or ECK multi-node cluster.
2. Create an index with `index.routing.allocation.require.box_type: hot`, confirm (via `_cat/shards`) it only allocates to hot-tagged nodes.
3. Manually "age" the index by updating its allocation requirement to `warm`, and watch Elasticsearch relocate its shards live to the warm-tagged nodes — this is exactly what ILM automates, but doing it by hand here builds the underlying mental model.
4. Configure **shard allocation awareness** (`cluster.routing.allocation.awareness.attributes`, e.g., by rack/zone) so replica shards are deliberately spread across failure domains, and prove it by inspecting shard placement.
5. Connect this back to Phase 1 Project 5: re-read your ILM policy from that project and identify exactly which of these manual steps ILM was automating on your behalf.

**Deliverable:** A manually-tiered cluster with a live shard relocation demonstrated, plus a short note connecting each manual step to its ILM-automated equivalent.

---

## 2.10 Cross-Cluster Search (CCS): Full Setup & Querying — *7 hrs*

**Objective:** Configure and query across multiple independent Elasticsearch clusters — a distinct exam objective, and a genuinely common enterprise pattern (e.g., querying regional clusters without centralizing all data into one).

**Step-by-step:**
1. Stand up **two separate clusters** (reuse two of your Phase 0 environments, e.g., one Docker Compose cluster and one ECK cluster, so the exercise is realistic rather than two nodes of the same cluster).
2. On "Cluster A," register "Cluster B" as a **remote cluster** via `PUT _cluster/settings` (or Kibana's Stack Management → Remote Clusters UI), using the **sniff mode** (`cluster.remote.<alias>.seeds`) first — the classic node-discovery-based approach.
3. Rebuild the same connection using **proxy mode** (`cluster.remote.<alias>.mode: proxy`, `proxy_address`) instead, and explain when proxy mode is preferred (e.g., when only a single well-known entry point is reachable, such as through a load balancer, rather than direct node-to-node connectivity).
4. Secure the remote connection using the modern **API-key-based cross-cluster security model**: generate a **cross-cluster API key** on Cluster B scoped to specific indices/privileges (`POST _security/cross_cluster/api_key`), and configure Cluster A's remote settings with `security_mode: api_key` — then explain how this differs from (and is more granular than) the older mutual-TLS/certificate-trust model.
5. Run cross-cluster searches: a query against a single remote index (`GET clusterB:my-index/_search`), a query spanning **multiple** remote clusters and a local index in one request (`GET local-index,clusterB:my-index/_search`), and a wildcard query against all configured remotes (`GET *:my-index/_search`).
6. Configure `skip_unavailable: true` on the remote cluster setting, then simulate Cluster B being unreachable (stop it) and confirm the CCS query against both clusters still returns local results gracefully instead of failing outright — then flip it to `false` and observe the difference.
7. Build one Kibana **cross-cluster data view** (spanning `clusterB:my-index*`) and confirm a dashboard can visualize federated data without ever copying it into Cluster A.

**Deliverable:** A working two-cluster CCS setup demonstrated under both connection modes and both security models, plus a documented test of `skip_unavailable` behavior during a simulated remote-cluster outage.

---

## 2.11 Cross-Cluster Replication (CCR): Leader/Follower Setup — *7 hrs*

**Objective:** Set up real leader/follower index replication between two clusters — used for disaster recovery and geo-distributed read replicas, and explicitly exam-tested as a distinct skill from CCS (CCS federates queries without copying data; CCR actually copies and continuously syncs data).

**Note:** CCR requires an active trial or paid Elastic subscription (Platinum/Enterprise tier) on self-managed clusters — activate a 30-day self-managed trial license on your lab clusters for this project (ECH deployments have it available by default at the appropriate subscription level).

**Step-by-step:**
1. Using two clusters (reuse your Project 2.10 setup, or bring up two fresh ones), register Cluster A as a remote on Cluster B (the follower registers a remote pointing at the leader) — CCR direction is the reverse of how you might intuitively set it up, so get this right first.
2. On Cluster A (**leader**), create and populate an index with sample data.
3. On Cluster B (**follower**), start replication with `PUT /follower_index/_ccr/follow` referencing the remote cluster alias and leader index name.
4. Write new documents to the leader index and confirm they appear on the follower within moments — measure and document the replication lag.
5. Configure an **auto-follow pattern** so any *new* index on the leader matching a pattern (e.g., daily rollover indices like `logs-2026.*`) is automatically picked up and replicated without manual intervention — create a new matching index on the leader and confirm it's auto-followed.
6. Test **pause/resume** of a follower index (`_ccr/pause_follow` / `_ccr/resume_follow`).
7. Run a **failover drill**: simulate the leader cluster becoming unavailable, and **unfollow** the follower index (`POST /follower_index/_ccr/unfollow`) to promote it into a normal, independently-writable index — write new data directly to the (formerly-follower) index to prove promotion succeeded, then discuss what a real failover runbook would need to cover (DNS/application cutover, re-establishing replication in the reverse direction once the original leader recovers).

**Deliverable:** A working leader/follower pair with measured replication lag, a demonstrated auto-follow pattern, and a completed failover drill with a written runbook.

---

## 2.12 Searchable Snapshots & Full Backup/Restore Mastery — *6 hrs*

**Objective:** Take Phase 1 Project 13's basic snapshot/restore skill to certification depth, with the exam's specific focus on **configuring a snapshot to be searchable**.

**Step-by-step:**
1. Revisit your Project 13 snapshot repository, and this time take a snapshot of an index you intend to move to the frozen tier.
2. **Mount the snapshot as a searchable snapshot** (`POST /_snapshot/<repo>/<snapshot>/_mount`), choosing between the `full_copy` and `shared_cache` storage options, and explain the trade-off (local disk cache for performance vs. minimal local storage relying on the object-store cache).
3. Query the mounted searchable-snapshot index directly and confirm it behaves like a normal (if slightly slower on cold cache) index, without ever running a traditional restore.
4. Compare this to a traditional `_restore` of the same snapshot into a fully-provisioned index, and measure the difference in both restore time and steady-state storage cost.
5. Combine this with Phase 2.9's tiering work: mount a searchable snapshot directly into a `data_frozen`-tagged node, completing the full hot→warm→cold→frozen data journey using both ILM-style and manual approaches.
6. Restore a **specific subset** of indices from a snapshot containing many indices (using an index pattern in the restore request), and separately practice restoring the **global cluster state** (index templates, ILM policies, etc.) from a snapshot that included it — a commonly-overlooked restore scenario.

**Deliverable:** A searchable-snapshot-backed frozen index serving live queries, plus a documented comparison table (searchable snapshot vs. traditional restore) covering time-to-availability and storage cost.

---
---

# PHASE 3 — BONUS TRACK: ELASTIC SECURITY / SIEM
*(Optional specialization — ~18 hours)*

## B1. Detection Engineering Fundamentals — *6 hrs*

**Data source:** Elastic's own public **detection-rules repository** (`github.com/elastic/detection-rules`) — real, production-grade detection logic to study and adapt.

**Step-by-step:**
1. Enable **Elastic Security** on your cluster and ingest a sample security dataset (Elastic Security's built-in demo data, or your own host's System integration data from Phase 1 Project 3).
2. Study 2–3 existing rules from the public detection-rules repo, understanding their EQL/KQL logic.
3. Write one original detection rule against your own ingested data (e.g., flag unusual process execution or repeated failed logins) using EQL.
4. Tune the rule to reduce false positives using exception lists.

**Deliverable:** One working, original detection rule with documented tuning decisions.

---

## B2. Building SIEM Dashboards — *5 hrs*

**Step-by-step:**
1. Explore Elastic Security's built-in dashboards (Overview, Detections, Host/User views).
2. Build a custom SIEM-oriented dashboard surfacing your Project B1 detection's alerts alongside relevant host context.
3. Configure case management: turn a triggered detection into a **Case** and document a mock investigation.

**Deliverable:** A custom SIEM dashboard + one documented mock case.

---

## B3. Threat-Intel Enrichment Project — *7 hrs*

**Data source:** The public **CISA Known Exploited Vulnerabilities (KEV) Catalog** (cisa.gov/known-exploited-vulnerabilities-catalog) — a real, actively-updated feed.

**Step-by-step:**
1. Ingest the CISA KEV feed into its own index (a simple scheduled script pulling the public JSON/CSV feed).
2. Build an enrichment step (ingest pipeline `enrich` processor — reusing the deeper enrich skills from Phase 2.4) that checks any CVE-referencing data in your other indices against the KEV feed, tagging matches as "known exploited in the wild."
3. Build a rule/dashboard panel highlighting any activity in your environment referencing a KEV-listed CVE — a genuinely realistic SOC enrichment pattern.

**Deliverable:** A working enrichment pipeline plus one dashboard panel surfacing KEV-matched activity.

---
---

# PHASE 4 — CAPSTONE: SELF-MANAGED ON-PREM PRODUCTION DEPLOYMENT
*(~22 hours)*

## C1. Self-Managed On-Prem Production Deployment

**Objective:** With ECH, ECK, and Docker all learned — and certification-grade cluster administration mastered in Phase 2 — do it the fully manual way, on local VMs or cloud VMs (e.g., AWS EC2), with none of the automation those methods provided. This is deliberately the hardest, most time-consuming project in the program, because it's meant to expose everything the earlier methods were quietly handling.

**Step-by-step:**
1. **Provision infrastructure** — 3–5 VMs, either locally (VirtualBox/Multipass/UTM) or on cloud VMs (AWS EC2 free-tier-eligible instances), with proper network security groups/firewall rules restricting Elasticsearch's transport and HTTP ports to only the intended hosts.
2. **Install Elasticsearch manually** from the `.deb`/`.rpm`/tarball package on each node — no container, no operator. Hand-configure `elasticsearch.yml` for node roles, discovery, and cluster formation.
3. **Manually generate and distribute TLS certificates** with `elasticsearch-certutil`, copying certs to each node yourself and configuring both transport and HTTP TLS — no ECK/ECH auto-generation this time.
4. **Manually configure RBAC and API keys** for the services that will write to this cluster, reusing Phase 1's least-privilege design principles.
5. **Set up ingestion** — install Elastic Agent (or Filebeat/Metricbeat) on the VMs themselves to monitor their own OS-level logs/metrics, proving the cluster can observe its own host infrastructure.
6. **Install Kibana manually** on a separate node/VM and connect it to the cluster with a manually-generated service token.
7. **Set up your own backup strategy** — configure a snapshot repository against either a local NFS-style shared path or real cloud object storage (e.g., an S3 bucket from an EC2-based build), and schedule SLM policies exactly as in Phase 1 Project 13, applying the searchable-snapshot skills from Phase 2.12 if you configure a frozen tier here too.
8. **Set up your own monitoring** of this cluster (Stack Monitoring via Metricbeat/Agent) so you'd actually know if it were unhealthy — nobody is doing this for you anymore.
9. **Apply ILM, index templates, and at least one alert rule** from Phase 1's work to this new environment, proving your stack-configuration-as-code approach from Project 16 is portable across deployment methods.
10. **Write the full production runbook**: how to start/stop the cluster safely, how to add a node, how to rotate certificates before they expire, and how to restore from backup — the kind of document a real team would leave for the next engineer.

**Optional extension — full-circle integration:** Register this on-prem cluster as a remote cluster against your Phase 0.3 ECH deployment and run a live **Cross-Cluster Search** across your fully manual environment and your fully managed one — and/or set up **Cross-Cluster Replication** to continuously replicate an index from ECH down into this on-prem cluster as a DR/read-replica exercise, directly reusing Phase 2.10 and 2.11's skills in a genuinely mixed managed/self-managed topology.

**Deliverable:** A fully self-managed, secured, monitored, backed-up Elasticsearch + Kibana deployment on VMs (local or EC2), with a written production runbook — the final proof that the student understands not just how to use Elastic, but how to run it.

---

## Program Completion Checklist

By the end of the **core program** (Phases 0, 1, 2, 4), a student should be able to, unaided:
- Explain and justify a cluster topology for a given workload
- Provision Elastic three different ways and articulate the operational trade-offs of each
- Build a complete, secure ingestion-to-visualization pipeline using modern (Agent/Fleet) and classic (Beats/Logstash) methods
- Design production-grade mappings — including custom analyzers, normalizers, dynamic templates, and correct nested-vs-object modeling — and build ILM-driven and manually-tiered hot/warm/cold/frozen architectures
- Query fluently across DSL (including fuzzy matching, highlighting, sorting, pagination, search templates, and async search), ES|QL, and EQL, and build multi-level bucket/metric/pipeline aggregations from scratch
- Perform every core document-level operation, including reindex-with-script and update-by-query, and build multi-stage ingest pipelines with Painless scripting and enrich lookups
- Diagnose and repair real cluster health incidents (unassigned shards, disk watermarks, allocation filtering conflicts) using the same APIs the exam tests
- Configure and operate **Cross-Cluster Search** and **Cross-Cluster Replication** between independent clusters, including secure API-key-based remote connections and failover drills
- Implement least-privilege security end-to-end, including TLS and SSO concepts
- Build real observability (logs + metrics + APM + synthetics) for an application, and diagnose an incident using it
- Perform disaster recovery (including searchable snapshots), benchmarking, rolling upgrades, and capacity planning
- Manage Elastic infrastructure and configuration as code
- Deploy and fully operate a self-managed, on-prem production cluster from nothing
- Sit the **Elastic Certified Engineer** exam with hands-on depth meeting or exceeding its published objectives

Completing the **bonus track** additionally qualifies them to speak credibly to detection engineering and SIEM work in a security-focused interview or role.
