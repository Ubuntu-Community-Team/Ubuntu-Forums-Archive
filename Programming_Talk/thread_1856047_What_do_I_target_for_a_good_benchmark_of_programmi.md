---
title: "What do I target for a good benchmark of programming languages?"
date: 2011-10-07
forum: Programming Talk
---

### Post by s3a on 2011-10-07
Firstly, I've asked similar (but not identical) questions here, but given that the topics are not exactly the same, don't be angry at me. I know how to use high-resolution timers but I'm not quite sure what to test to have a plausible set of data to make an argument with for a paper. (As I wrote this forum post, I started to figure some stuff out but I'm still not too certain if I am on the right path - basically, I need some words of wisdom, confirmation or disapproval).

I'm guessing I need to test:
[LIST=1]
[*]32-bit integer arithmetic
[*]64-bit long integer arithmetic
[*]64-bit double arithmetic
[*]Algorithm speed comparisons
[*]Various operating systems, hardware
[*]Data structures (like ArrayList, LinkedList in Java)
[/LIST]

But, what do I do exactly? Do I just try different algorithms like bubble sorts, etc between two programming languages, measure them to the nanosecond range, do each thing 1000 times and average the results? Is that most of what a benchmark consists of? I'm trying to do as detailed a benchmark as possible but I have yet to cover any computer science in university so I can't do something super complex (but please suggest a complex idea anyways if you have one and if I cannot do it - I will try a simplified version of it).

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by karlson on 2011-10-07
> **s3a said:**
> 
I'm guessing I need to test:
[LIST=1]
[*]32-bit integer arithmetic
[*]64-bit long integer arithmetic
[*]64-bit double arithmetic
[*]Algorithm speed comparisons
[*]Various operating systems, hardware
[*]Data structures (like ArrayList, LinkedList in Java)
[/LIST]

But, what do I do exactly? Do I just try different algorithms like bubble sorts, etc between two programming languages, measure them to the nanosecond range, do each thing 1000 times and average the results?

That depends on what you are trying to benchmark and what your premise is.  In general I'd start with some standardized benchmarks to get a general idea, but if you are looking to compare one language to another you would have to find.

I might start with the list here:
[http://en.wikipedia.org/wiki/Benchmark_(computing)](http://en.wikipedia.org/wiki/Benchmark_(computing))
add [Bonnie](http://www.coker.com.au/bonnie++/) to it and go from there.

In general the benchmark is would be dependent on the statistical method you are using.  More commonly a mean or a median of a large set of observations

---

### Post by ofnuts on 2011-10-07
> **karlson said:**
> That depends on what you are trying to benchmark and what your premise is.  In general I'd start with some standardized benchmarks to get a general idea, but if you are looking to compare one language to another you would have to find.

I might start with the list here:
[http://en.wikipedia.org/wiki/Benchmark_(computing)]("http://en.wikipedia.org/wiki/Benchmark_%28computing%29")
add [Bonnie]("http://www.coker.com.au/bonnie++/") to it and go from there.

In general the benchmark is would be dependent on the statistical method you are using.  More commonly a mean or a median of a large set of observations
Comparing languages in terms of speed on the final result doesn't make much sense, I would not expect fully compiled languages (C, C++, Fortran, Cobol...) to give very different results everything else being equal.

And comparing speeds on complex built-in data structures won't tell you more than the speed of a specific library implementation...  

Even for a given language,  differences you find among compliers may have more to do with technical compromises than with the actual "speed quality" of the compiler: check for debug information or arithmetic behavior flags. You have to become an  expert with both compilers to produce meaningful results.

---

