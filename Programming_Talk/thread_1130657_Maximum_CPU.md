---
title: "Maximum CPU"
date: 2009-04-20
forum: Programming Talk
---

### Post by Lekshmi on 2009-04-20
In order to know how many processors are in the system,what function have to be used? Is there any data structure which keep maximum number of CPU?

---

### Post by asbuntu on 2009-05-25
I found this in "The How-To-Geek" (google:number of processors)

cat /proc/cpuinfo | grep processor | wc -l

Its not a callable function, per se, but you might be able to wrap it up in something.

---

