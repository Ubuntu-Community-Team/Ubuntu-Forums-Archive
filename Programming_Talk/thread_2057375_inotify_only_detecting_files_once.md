---
title: "inotify only detecting files once"
date: 2012-09-13
forum: Programming Talk
---

### Post by firkinfedup on 2012-09-13
Hi there,

I'm trying to use the inotify API's in Ubuntu. Firstly I'm monitoring a folder, then when files are detected I then process them and move them to another folder, once processed sometimes I want to move them back.

They get detected fine the first time, but not after that. It seems to remember the filename and refuse to do anything with it after that.

Any ideas how I can avoid this?  I'm using the following as reference...

[http://man7.org/tlpi/code/online/dist/inotify/demo_inotify.c.html](http://man7.org/tlpi/code/online/dist/inotify/demo_inotify.c.html)

Just to add to this, if I have let's say 10 files, and I feed them in 1 at a time they get detected, second time round, not detected.  So the continuous loop appears to be working fine.

I've also tried deleting the file from the folder rather than moving it and copying its contents manually to where I process it, thinking that it might maintain some kind of link to the moved file; but this has exactly the same effect.

Nick.

---

