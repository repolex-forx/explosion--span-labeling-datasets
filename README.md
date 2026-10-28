# Repolex Knowledge Graph of explosion/span-labeling-datasets

RDF knowledge graph data for [explosion/span-labeling-datasets](https://github.com/explosion/span-labeling-datasets), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/span-labeling-datasets
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a35c3948d04892e53465bb9b874298a6de609743
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── a35c3948d04892e53465bb9b874298a6de609743
│           └── chunk-001.nq.gz
├── blob
│   ├── 03e5a613b8b328ee51dd35e0c0c01fc73d467c96.nq.gz
│   ├── 233b6c171dbb47023d763390e6403d40ed59f835.nq.gz
│   ├── 24fecedf81457d68e37c44f86d06aea13080f231.nq.gz
│   ├── 29a70728d3208eef0f98fee318351a88ff63f0c3.nq.gz
│   ├── 594328618c7810c4cc9f05a725b95a0e2d9d5882.nq.gz
│   ├── 7452f3bc5d3ed59d7206632bfd69b29d2cbb1461.nq.gz
│   ├── 8c2ac52268ab12046a5ed76d18f4176fc5d3dcdd.nq.gz
│   ├── 9d8e5d288d82c94ab8b8487aa24eb570eb3296c8.nq.gz
│   ├── af57c1c87683a25b1d825746295ddeed47e602d4.nq.gz
│   ├── b2978f77bd279b2f97de89878b2aca84a80deda3.nq.gz
│   ├── b3b7d73e884957ac924b9926f79b0a698c7fd337.nq.gz
│   ├── d7f48acce88356d229a98c3289c510160db37051.nq.gz
│   ├── e18dd3d818276cbb8ebd8ad6b8871b19ba6486d2.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e886213b96a5cf15317d4635013a222e3264c035.nq.gz
│   ├── ef7d4b5f4321e676d0cea89df4314e956bad1cb2.nq.gz
│   └── f37e194aee4a617e368759412b8f9f695cfcc3ba.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── a35c3948d04892e53465bb9b874298a6de609743.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 24 files
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

[explosion/span-labeling-datasets](https://github.com/explosion/span-labeling-datasets)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
