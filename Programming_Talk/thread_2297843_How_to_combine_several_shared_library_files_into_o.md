---
title: "How to combine several shared library files into one?"
date: 2015-10-07
forum: Programming Talk
---

### Post by venkat28vk on 2015-10-07
Hi,

I have a created a few .so files. I would like to know how to combine them into single shared library objects using gcc?

---

### Post by Rocket2DMn on 2015-10-08
I believe you would need to create a project that links to static versions of your shared libraries (.a instead of .so), then produces its single shared object.  This would have all the code from the existing libraries that it linked in statically.  AFAIK, you can't statically link to a shared object library.

---

