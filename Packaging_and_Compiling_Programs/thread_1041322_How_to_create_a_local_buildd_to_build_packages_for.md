---
title: "How to create a local buildd to build packages for other architectures ?"
date: 2009-01-16
forum: Packaging and Compiling Programs
---

### Post by kalon33 on 2009-01-16
Hello all,

I read this how-to from debian : [http://www.debian.org/devel/buildd/setting-up](http://www.debian.org/devel/buildd/setting-up)

But got at the end something not functionnal at all.

Could you describe me a way to set up a buildd in Ubuntu (automated if possible, I have hardy, intrepid and jaunty (for testing) on my computer) which could automatically build sources (the same that I dput to my ppa in Launchpad) into debs for my arch and other ones ? I have some packages I can't redistribute to build (i.e. ffmpeg with some extra codec options) and others packages I want to try without spamming my ppa or waiting for the queue.


Thanks for your help.

--kalon33.

---

### Post by Vorian on 2009-01-18
> **kalon33 said:**
> Hello all,

I read this how-to from debian : [http://www.debian.org/devel/buildd/setting-up](http://www.debian.org/devel/buildd/setting-up)

But got at the end something not functionnal at all.

Could you describe me a way to set up a buildd in Ubuntu (automated if possible, I have hardy, intrepid and jaunty (for testing) on my computer) which could automatically build sources (the same that I dput to my ppa in Launchpad) into debs for my arch and other ones ? I have some packages I can't redistribute to build (i.e. ffmpeg with some extra codec options) and others packages I want to try without spamming my ppa or waiting for the queue.


Thanks for your help.

--kalon33.

The example you link to is showing a couple of things.  It is a function of [sbuild]("https://help.ubuntu.com/community/SbuildLVMHowto"), which requires LVM.

[pbuilder]("https://wiki.ubuntu.com/PbuilderHowto"), for example, will allow you to create build environments for amd64 and i386 (as long as you have an amd64 proc and kernel)

---

