# Repolex Knowledge Graph of samuelcolvin/githubproxy

RDF knowledge graph data for [samuelcolvin/githubproxy](https://github.com/samuelcolvin/githubproxy), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download samuelcolvin/githubproxy
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 0679cb7f6082a761679b355d97d4bc4aff5e6a8b
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 0679cb7f6082a761679b355d97d4bc4aff5e6a8b
│           └── chunk-001.nq.gz
├── blob
│   ├── 0aefc5d0b5b91a62b60a564b949b3146a8d3b457.nq.gz
│   ├── 183d7fcea9343fc870421eb0326091e0e3b980ca.nq.gz
│   ├── 1b1ad6243f6204cde96bbfdbbe53203746bbea3c.nq.gz
│   ├── 1e9386623e054deaf380f4e85150ad47dcec1fbb.nq.gz
│   ├── 49e4fcbd351c4e22fede0ac8386e916bcc119cff.nq.gz
│   ├── 930b10b4adbba6b591fad214c2d2bd55ff9b20f6.nq.gz
│   ├── 998516d016aea65fcef8f7262636f179077fb5a1.nq.gz
│   ├── b7afb4df36db04da370229f1c6cafd006cdd6ca9.nq.gz
│   ├── d413880789829e147a4edd44c41535755ffdd7ea.nq.gz
│   └── d9c4a897d75c04387a87593c1d999fbaa7b47bd0.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 0679cb7f6082a761679b355d97d4bc4aff5e6a8b.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 16 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[samuelcolvin/githubproxy](https://github.com/samuelcolvin/githubproxy)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
