---
title: "Parallel Algorithms"
date: 2008-01-31
forum: Programming Talk
---

### Post by Royall on 2008-01-31
I'm starting my senior seminar and I'd like to do something with parallel processing, but I don't really know anything about the topic. I'd like to use Nvidia's CUDA to do the implementation, but those details don't really matter at this point. What's a simple algorithm I should try to implement to get me rolling in this direction?

---

### Post by rufius on 2008-01-31
MapReduce is always a good start. Probably the easiest way to process things in parallel.

[MapReduce paper](http://labs.google.com/papers/mapreduce.html) <-- Read that and have some fun implementing it :-D

---

### Post by hod139 on 2008-01-31
Real time ray tracing on a GPU is a possible idea. For some other ideas see: [http://gamma.cs.unc.edu/hardware/](http://gamma.cs.unc.edu/hardware/)

---

### Post by pjkoczan on 2008-01-31
It depends on what sort of thing you're looking for.

If you're looking to study easily parallelized algorithms, matrix operations, merge-sort, image manipulations, or any other divide-and-conquer algorithm should work well.

But if you're looking to do something a little more original, maybe look into trying to parallelize something you wouldn't normally think of parallelizing. Maybe compiler optimization, or finding a way to nicely parallelize something that could have contention like database updates.

I went to a seminar recently that examined some of the possibilities of multicore programming, and some of the limitations that need to be overcome.  One of the suggestions was to write parallel versions of algorithms from Knuth's book "The Art of Computer Programming".

---

### Post by Anthon berg on 2008-02-14
Image filters are a good candidate for this. You could take basically any filter from ImageMagick or Gimp and parallelize it - one on-GPU hardware thread per pixel, wham: ~40x speedup.

---

### Post by Shin_Gouki2501 on 2008-02-14
Maybe u should look a abit into functional programming!

---

