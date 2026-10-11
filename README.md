# Repolex Knowledge Graph of tox-dev/velodex-data

RDF knowledge graph data for [tox-dev/velodex-data](https://github.com/tox-dev/velodex-data), parsed by [repolex](https://repolex.ai).

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
rlex download tox-dev/velodex-data
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9a3a52f8ec0d34e3fc55364aa337add1730c2404
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9a3a52f8ec0d34e3fc55364aa337add1730c2404
│           └── chunk-001.nq.gz
├── blob
│   ├── 1e8f52b099c14f49388c45373d0270a847dc25df.nq.gz
│   ├── 359ea0c5d10e319e3d89e13d58423f5b2f18938e.nq.gz
│   ├── 37464c3f4f85fc42e75096333d3d680679d94a18.nq.gz
│   ├── 42928c6ac324f6156e25d7e92a3d236f2dbc07ef.nq.gz
│   ├── 4775f56a41a0de1d5b9ec9a095c5dfc56f749e93.nq.gz
│   ├── 4a3d04f2d6da356c2659ce870b7d484061772089.nq.gz
│   ├── 5046d779c56d2860a70740532e02e2917567fe95.nq.gz
│   ├── 5fa6404308612356a07a5437eb800c384d624ab0.nq.gz
│   ├── 62dd87bd2a694646bec030081e855ed78dd7f36f.nq.gz
│   ├── 6f47eba7b2d0ed013eaa049d2d5950d86ff1de06.nq.gz
│   ├── 7c60a475734b98d76f33ee03f87fdc60fcd0e5e7.nq.gz
│   ├── 91f46246e1eac0f3612aa1fa6a2586b9d752d14d.nq.gz
│   ├── 939387f6cc8ae8f72eda7509422d1b94fbcf2cf9.nq.gz
│   ├── 9d8623c9aef83d5bc5eaeef3bb42591edb8e2cfb.nq.gz
│   ├── aaeffdb30360160bf4038f2cceacdb3420231474.nq.gz
│   ├── db759d1a60fdcf16453886c5aaac6ff8a16eb184.nq.gz
│   └── e7681097d73b7ed2ec6dfc0082a1662de499e204.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9a3a52f8ec0d34e3fc55364aa337add1730c2404.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 23 files
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

[tox-dev/velodex-data](https://github.com/tox-dev/velodex-data)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
