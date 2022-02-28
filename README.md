<p align="center">
  <a href="https://docs.capter.io">
    <img src="/media/icon.png" alt="Capter logo" width="128" height="128">
  </a>
</p>

# Capter CLI

![test-build](https://github.com/capterqa/cli/workflows/test-build/badge.svg)
[![codecov](https://codecov.io/gh/capterqa/cli/branch/alpha/graph/badge.svg?token=DAUCAH1MWW)](https://codecov.io/gh/capterqa/cli)
[![npm](https://img.shields.io/npm/v/@capterqa/cli)](https://www.npmjs.com/package/@capterqa/cli)

Capter is a lightweight **end-to-end** testing tool for APIs. It's language agnostic and can test APIs written in any language (Node.js, Go etc).

- 🧑‍💻 Write tests in YAML
- 🔎 Run the same tests locally, in CI, or as a cron job to monitor your live APIs
- 🏃‍♂️ Takes **less than a minute** to get started

## How it works:

Create a workflow file in a `.capter` folder:

```yaml
# .capter/products.yml

name: products
steps:
  - name: fetch all products
    id: products
    url: ${{ env.URL }}/api/products
    assertions:
      - !expect status to_equal 200
      - !expect body to_be_array

  - name: fetch first product
    url: ${{ env.URL }}/api/posts/${{ products.response.body.0.id }}
    assertions:
      - !expect body.id to_equal ${{ products.response.body.0.id }}
```

Then run the CLI:

```sh
URL=http://localhost:3000 capter test
```

## Demo

![CLI](/media/demo.gif)

## Getting started

Follow the instructions in the documentation to get started:

- [Installation](https://docs.capter.io/cli/guide/installation)
- [Getting started](https://docs.capter.io/cli/guide/getting-started)

## API

- [CLI reference](https://docs.capter.io/cli/reference/cli)
- [Workflow reference](https://docs.capter.io/cli/reference/workflow)

# License

The Capter CLI is provided under the [MIT License](http://http//opensource.org/licenses/mit-license.php). See LICENSE for details.


# 修改

- [ ] 控制台日志输出简化、详细日志写入 error.log
- [ ] 支持执行单个文件或者 API
