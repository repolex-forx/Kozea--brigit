# Repolex Knowledge Graph of Kozea/brigit

RDF knowledge graph data for [Kozea/brigit](https://github.com/Kozea/brigit), parsed by [repolex](https://repolex.ai).

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
rlex download Kozea/brigit
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 247482e49eb7ad562555ac7a3f654f2cdace619f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 247482e49eb7ad562555ac7a3f654f2cdace619f
│           └── chunk-001.nq.gz
├── blob
│   ├── 23ac759785f69752e5f10319beedb4f99496e3a0.nq.gz
│   ├── 3dce25081549f9f8aa6c2ee5b0a354a8ac673f84.nq.gz
│   ├── 62b631a76b5a5b1c22b9ebe0c2b2ac084711d249.nq.gz
│   ├── 62f138bc3c50e3cfba60f4f65a1f966f1c221f31.nq.gz
│   ├── 665f62d2b3e9df7dc99ba294c8e2d2c4cf381128.nq.gz
│   ├── b7e478982ccf9ab1963c74e1084dfccb6e42c583.nq.gz
│   ├── d059f72c3b345cf637065538104808a3f9ec039b.nq.gz
│   ├── d2b5a98ae4095f1aef32008ec60c5d0129e570d7.nq.gz
│   ├── dbe6ce96b5975510dc7f349f22399becc95492ca.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 247482e49eb7ad562555ac7a3f654f2cdace619f.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
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

[Kozea/brigit](https://github.com/Kozea/brigit)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
