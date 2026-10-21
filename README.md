# Repolex Knowledge Graph of bokeh/bokehrs

RDF knowledge graph data for [bokeh/bokehrs](https://github.com/bokeh/bokehrs), parsed by [repolex](https://repolex.ai).

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
rlex download bokeh/bokehrs
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 7771574ca220470182b21db4b4e788682c85789e
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 7771574ca220470182b21db4b4e788682c85789e
│           └── chunk-001.nq.gz
├── blob
│   ├── 218d9db2294081f94313e7de4367102d3977be69.nq.gz
│   ├── 2adfe1e030dc69d7cd9e3cc172f8eb32ef6df70d.nq.gz
│   ├── 2c790f1923c9cda3a7efdd616e2df563c19bc399.nq.gz
│   ├── 4a4d1dda29912a4e216839c62ed8bb94d150b499.nq.gz
│   ├── 5a0b914cfa7db2c102d09ff37d0040bcd54be474.nq.gz
│   ├── 6171cafdcd73c6a03c16b69199e60e0134984a3e.nq.gz
│   ├── 6cbbf6c69532baa709e2a8a41a9a4417bd46a8a6.nq.gz
│   ├── 85bc68dbe62af0fc99753c849f10e79321ffaf99.nq.gz
│   ├── c41f0a241e7053f4a201ec9e46c7ff7c71ce3f78.nq.gz
│   ├── cac82f213eaa64b729ba6a670c22fbc66553d1f9.nq.gz
│   ├── d31255f480628654ccbffa83fa75716c9652f2dd.nq.gz
│   ├── e40c58200544cb891b9150c6b4766c47ee4459c7.nq.gz
│   ├── ee6d4a3febc1f91e6480bd3f615a8f0ea476f34c.nq.gz
│   └── f8a1234d0b2b01363b698a23f790f700191798c4.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 7771574ca220470182b21db4b4e788682c85789e.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 20 files
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

[bokeh/bokehrs](https://github.com/bokeh/bokehrs)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
