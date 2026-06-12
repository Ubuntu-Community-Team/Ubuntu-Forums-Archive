---
title: "Difference in MPI and OpenMP?"
date: 2009-10-29
forum: Programming Talk
---

### Post by helstreak on 2009-10-29
I've been looking at MPI and OpenMP lately and I'm wondering the differences.

Is one better for multicore and the other for multiple nodes?

If I have a multicore processor and I have 4 of these computer strung together would there be a performance difference depending on which library I used?  Would I use OpenMP for the code operating on each node and use MPI for the code that is talking between nodes?

Thanks for your incite :)

---

### Post by slavik on 2009-10-30
the difference? tremendous!!!

OpenMP is for shared memory systems, where all CPUs have access to all memory. Won't work on any other type of system. It's nice in that it easily parallelizes loops which is where we mostly need parallelization.

MPI on the other hand works with multiple nodes (but still sucks).

And what you said: "Would I use OpenMP for the code operating on each node and use MPI for the code that is talking between nodes?" Yeap, exactly that.

Please note, OpenMP is not "better" at multicore, with just enough boiler plate pthread code, you write your own OpenMP. OpenMP is mostly just that. (which is still nice and useful, it's just not item 9).

---

