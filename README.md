# Repolex Knowledge Graph of klen/Flask-Collect

RDF knowledge graph data for [klen/Flask-Collect](https://github.com/klen/Flask-Collect), parsed by [repolex](https://repolex.ai).

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
rlex download klen/Flask-Collect
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 2297e78a798ed701572de15747060b73c21817da
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 2297e78a798ed701572de15747060b73c21817da
│           └── chunk-001.nq.gz
├── blob
│   ├── 0043c3bd95c653a9e652b72f00d1789e8639f3df.nq.gz
│   ├── 08bca9c83e671f9085fef98efeb7617022c3cb88.nq.gz
│   ├── 0a719f5dcec758a7a8e8231de8f1c5103efbfb99.nq.gz
│   ├── 0f15ce18bbb1f099f5988672aefcc4661c072d98.nq.gz
│   ├── 1c12c2bb5c4ea10350782212ac6a90da9c9c29d2.nq.gz
│   ├── 1e69e51aefeaab2b9a14cd585b6ff47d0716af9d.nq.gz
│   ├── 23fe0c1e4ad878f1953a6da942ea315cdf9b46aa.nq.gz
│   ├── 3027220c1dbceab649fd4bc793409f068d4ad1d7.nq.gz
│   ├── 392f751d74467dc556e612899f7bee3db8e5d765.nq.gz
│   ├── 44f3ab7086d2e7db65c79f12446197bdf03eb7d2.nq.gz
│   ├── 4f6b1f7dea16c833f19b1c26d8d4576d5bbc7f25.nq.gz
│   ├── 5f4e47ab11002fa7ff29e7f7ae5024b4093ac440.nq.gz
│   ├── 75be3f80a27687726cfe443069e8bf08019472b9.nq.gz
│   ├── 7614dc7c3231c5738905a36d6216a1c628372454.nq.gz
│   ├── 7d1693ba1aa2d56e4bdaaf60df4454c0f6d8d74d.nq.gz
│   ├── 8314a143f5a9fbebc17611a96d6c63f8c2471159.nq.gz
│   ├── 842fd07dacebe39f19352e15788ee81542a9c1f2.nq.gz
│   ├── 8932e69e5829095ca391dd9e55c850861df23ad6.nq.gz
│   ├── 897c27642f074b7b8d99f0e91611ddfc53de5f2b.nq.gz
│   ├── 8d577467ffd82c8406a8c9c26f8c88316006eb09.nq.gz
│   ├── 991912d894b345372b278ec2b8c67eeaa237cf65.nq.gz
│   ├── 9a3e9817cc207be06ffa358d0b651e09dbf27776.nq.gz
│   ├── 9d6d0f2f9b4067f5d64549b06b2f6b293fd2bd59.nq.gz
│   ├── a27a99345052d20201a9d50a2a247cc515393acd.nq.gz
│   ├── ae39df4b6037874771037d24ef7eeb30f42b75e8.nq.gz
│   ├── c968c2f0ca79d61b6635c240bc9e355ef2aea2ef.nq.gz
│   ├── d40c7c6243f6a14d333172572c45b7e77da1aeec.nq.gz
│   ├── e15cc3d44d4d11bfc48ea2fe63139d7023e6740d.nq.gz
│   ├── e32ece578f93fcca8ddc4ac7a677ecf251252adc.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e82817eb527ff92b296d54f609a4f4bde1602a3b.nq.gz
│   ├── ede5c15d359445e66e1230246428606bc9eb847e.nq.gz
│   ├── f14affdcbcb75a0624df8c0433ad3a2d536cc6ee.nq.gz
│   ├── f53ddf0235fc7dc401c289cbbe03dd843d9fdf71.nq.gz
│   ├── f62f76ef44354d08b0a49b4387e5df1bd7be2bcd.nq.gz
│   ├── fc725f2b1194d6361e5df099bb495d635fc981b7.nq.gz
│   └── ff7ec4cfa849ea3ed8bb69fea40025ef2b0dd742.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 2297e78a798ed701572de15747060b73c21817da.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 45 files
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

[klen/Flask-Collect](https://github.com/klen/Flask-Collect)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
