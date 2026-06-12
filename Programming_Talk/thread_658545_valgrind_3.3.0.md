---
title: "valgrind 3.3.0"
date: 2008-01-04
forum: Programming Talk
---

### Post by faginbagin on 2008-01-04
I'm trying to debug a mutex deadlock in mythtv's mythvideo plugin. I'm new to mythtv's source, so I'm getting lost navigating the code. I thought things might go faster if I used valgrind's helgrind to help me track down thread issues. Unfortunately, the version of valgrind that is available for gutsy doesn't support helgrind. However, the latest version of valgrind, 3.3.0, released Dec 11, 2007, does. I found this version in merges.ubuntu.com, seems that automatic merging of debian and ubuntu patches to the previous version didn't work. So I'm wondering which way to go:

1) Understand how to use what's available from merges.ubuntu.com, sorting through which patches to use or not use.

2) Get the source package from debian.org and build that on ubuntu gutsy.

3) get the source from valgrind.org and build that.

I'm leaning toward option 2 because I believe I'll get something useable faster. So my question is, does it make sense to compile a source package downloaded from debian on ubuntu?

TIA

---

### Post by Tuna-Fish on 2008-01-04
Usually, yes. If it fails, however, don't bother troubleshooting it, just get it from valgrind directly.

---

### Post by faginbagin on 2008-01-04
Thanks, I'll give the debian source a go. I was about to do it anyway, but it's nice to have some positive feedback. If it won't compile, I'll do as you suggest and get the source from valgrind.org

---

