---
title: "OpenMP, Anyone?"
date: 2006-04-07
forum: Programming Talk
---

### Post by Lightmywifire on 2006-04-07
Anyone here have any experience using OpenMP?

---

### Post by GoldBuggie on 2006-04-08
yup...used it for some numerical methods assignments in school

---

### Post by maubp on 2006-09-05
An old thread, but seemed better than starting a new one.

Are there any OpenMP capable compilers on Ubuntu yet?

I know that GCC 4.2 includes this feature (project GOMP), and according to [this post](https://www.redhat.com/archives/fedora-devel-list/2006-July/msg00508.html) RedHat have backported GOMP to their branch of GCC 4.1

(**Update** - I've logged a support request on launchpad about getting [OpenMP support in gcc 4.1 on Edgy](https://launchpad.net/distros/ubuntu/+ticket/1709))

I've tried and failed to install a snapshot of 4.2 on my machine ([thread here](http://www.ubuntuforums.org/showthread.php?t=250071)).

Does anyone know if Ubuntu will/has backported GOMP/OpenMP support into available versions of GCC?

---

### Post by GoldBuggie on 2006-09-05
maybe not in the repositories but a open source openmp compiler project is here.

[http://fenixforge.com/](http://fenixforge.com/)

Haven't tried latest gcc so I can't help you there.

---

### Post by maubp on 2006-09-05
Thanks for that link to FenixForge.com and OdinM/Balder **GoldBuggie** - have you tried it?

I've stuck a few queries on their website forum, like does it work on 64bit Linux:
[https://fenixforge.com/forum/forum.php?forum_id=19](https://fenixforge.com/forum/forum.php?forum_id=19)

However, the site looks rather unloved, with no updates since June 2005, and no forum postings at all this year (until mine).

I think for my project a recent GCC would be ideal, as my non-parallel code already compiles fine on GCC 4.0 with no warnings.  It just looks like a pain to get an OpenMP / GOMP version of GCC at the moment.

:(

---

### Post by maubp on 2006-09-08
The Intel Compiler is free as in beer (for personal non-commericial use with restrictions).

Version 9.0 has a few problems with linking to GCC 4.0  libraries (e.g. the power functions in cmath), but using -cxxlib-icc seems to work. It supports OpenMP 2.0

Version 9.1 seems to work on a system with GCC 4.0 installed, and supports OpenMP 2.5

According to Intel's website, on Linux they use pthreads for their OpenMP implementation... anyone know what GCC uses?

---

### Post by jespdj on 2006-09-12
> **maubp said:**
> According to Intel's website, on Linux they use pthreads for their OpenMP implementation... anyone know what GCC uses?
I have compiled GCC 4.1.1 on Cygwin (Windows) recently. One of the configuration options is what threading support GCC should use (see the [GCC config page](http://gcc.gnu.org/install/configure.html)).

You should be able to see which threading support your GCC is compiled with using the following command:

gcc -v

---

