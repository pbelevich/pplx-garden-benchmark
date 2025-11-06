# PPLX Garden Benchmark

```bash
git clone https://github.com/perplexityai/pplx-garden.git
```

```bash
docker build -t pplx-garden-dev - < ./pplx-garden/docker/dev.Dockerfile && docker build -t pplx-garden -f pplx-garden.Dockerfile .
```

```bash
enroot import -o pplx-garden.sqsh dockerd://pplx-garden
```

```bash
sbatch pplx-garden.sbatch
```

# All-to-All Performance Results

Decode (128 tokens) Dispatch and Combine Median Latency:

|       | My pplx-EFA | pplx-EFA | pplx-CX7 | DeepEP-CX7 | x | My pplx-EFA | pplx-EFA | pplx-CX7 | DeepEP-CX7 |
|-------|------------:|---------:|---------:|-----------:|---|------------:|---------:|---------:|-----------:|
| EP128 |    424.5 μs |          |          |            | x |    588.5 μs |       μs |       μs |         μs |
| EP64  |    268.6 μs | 266.7 μs | 187.5 μs |   177.9 μs | x |    393.6 μs | 391.2 μs | 309.1 μs |   325.0 μs |
| EP32  |    230.9 μs | 229.1 μs | 153.9 μs |   159.1 μs | x |    336.9 μs | 335.0 μs | 266.3 μs |   285.0 μs |
| EP16  |    218.0 μs | 214.8 μs | 110.2 μs |   123.9 μs | x |    244.6 μs | 241.5 μs | 185.5 μs |   203.0 μs |
| EP8   |     50.6 μs |  49.7 μs |  50.5 μs |    42.6 μs | x |     64.1 μs |  64.2 μs |  65.3 μs |    72.0 μs |


Prefill (4096 tokens) Dispatch and Combine Median Latency:

| x     | My pplx-EFA |  pplx-EFA |  pplx-CX7 | DeepEP-CX7 | x | My pplx-EFA |  pplx-EFA |  pplx-CX7 | DeepEP-CX7 |
|-------|------------:|----------:|----------:|-----------:|---|------------:|----------:|----------:|-----------:|
| EP128 |   5883.4 μs |           |           |            | x |  10785.1 μs |           |           |            |
| EP64  |   5395.6 μs | 5334.3 μs | 4665.2 μs |  5071.6 μs | x |   9854.9 μs | 9779.3 μs | 8771.1 μs |  5922.7 μs |
| EP32  |   4605.2 μs | 4619.0 μs | 4011.8 μs |  3680.2 μs | x |   8286.3 μs | 8271.5 μs | 7526.8 μs |  3565.4 μs |
| EP16  |          μs | 3196.7 μs | 2734.8 μs |  2481.9 μs | x |          μs | 5379.1 μs | 1062.2 μs |  1863.9 μs |
| EP8   |          μs | 1052.4 μs | 5071.1 μs |  1810.3 μs | x |          μs | 1396.7 μs | 1405.1 μs |   962.9 μs |
