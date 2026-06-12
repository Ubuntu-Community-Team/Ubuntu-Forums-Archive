---
title: "Using dieharder test suite to test a PRNG"
date: 2011-02-28
forum: Programming Talk
---

### Post by R33D3M33R on 2011-02-28
I'm trying to test a pseudo random number generator with dieharder. I generate 10 mio lines with the generator save them to file rand.txt with this header:

```
#==================================================================
# generator lcg  seed = 9350
#==================================================================
type: d
count: 10000000
numbit: 32
```Then I try to run it with:

```
dieharder -f rand.txt -a
```But it doesn't appear to be working, because the test header says:

```
#                        Run Details
# Random number generator tested: mt19937
# Samples per test pvalue = 100000 (test default is 100000)
# P-values in final KS test = 100 (test default is 100)
```

It tests mt19937 instead of the file. What could be wrong?

---

### Post by R33D3M33R on 2011-02-28
I have found the solution. You **must** use the **-g 202** flag to allow file input.

---

