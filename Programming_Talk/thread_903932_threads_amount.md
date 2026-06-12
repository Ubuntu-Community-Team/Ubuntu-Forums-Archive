---
title: "threads amount?"
date: 2008-08-28
forum: Programming Talk
---

### Post by StOoZ on 2008-08-28
does the amount of simultaneously working threads , in an application (lets assume its a C++ application) , can vary from one API/lib to another? or its an OS dependent stuff?

I mean , just as an example , can a I simultaneously use more wxThreads , than boost::thread threads?

---

### Post by dribeas on 2008-08-29
> **StOoZ said:**
> does the amount of simultaneously working threads , in an application (lets assume its a C++ application) , can vary from one API/lib to another? or its an OS dependent stuff?

I mean , just as an example , can a I simultaneously use more wxThreads , than boost::thread threads?

I don't know how wxThreads are implemented, but boost threads are a uniform wrapper around pthreads, so you can use as many boost::threads as pthreads. I would assume that wxThreads internally use pthreads in linux, so that the three should be the same. Browse wxThread docs when running in linux.

   David

---

