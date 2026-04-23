# Evaluation Setup

This file is outside the editable surface. It defines how results are judged. Agents cannot modify the evaluator or the scoring logic — the evaluation is the trust boundary.

Consider defining more than one evaluation criterion. Optimizing for a single number makes it easy to overfit and silently break other things. A secondary metric or sanity check helps keep the process honest.

eval_cores: 1
eval_memory_gb: 1.0
prereq_command:

## Setup

Install dependencies and prepare the evaluation environment.

```bash
npm install
```

This project is a pure JavaScript project with no build step required. The benchmark measures parsing performance of front-matter extraction from strings.

## Run command

```bash
node benchmark-simple.js
```

## Output format

The benchmark must print `METRIC=<number>` to stdout.

## Metric parsing

The CLI looks for `METRIC=<number>` or `ops_per_sec=<number>` in the output.

## Ground truth

The baseline metric represents operations per second for parsing front-matter from a set of test fixtures. The benchmark parses 6 different fixtures (including simple YAML, complex nested structures, and files without front-matter) for 100,000 iterations and reports the total operations per second. Higher numbers indicate better performance.
