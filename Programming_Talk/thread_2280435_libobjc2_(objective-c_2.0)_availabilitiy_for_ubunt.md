---
title: "libobjc2 (objective-c 2.0) availabilitiy for ubuntu 14.04"
date: 2015-05-30
forum: Programming Talk
---

### Post by mark allyn on 2015-05-30
Hello everyone,

I have been unable to compile, link, and run objective-c 2.0 programs using GNUstep on my 14.04 box.  A week ago Steeldriver kindly shared bash scripts with me that should, I thought, have done the job.  This involved downloading libobjc2-1.7, the GNUstep core libraries, and libdispatch.  Unfortunately, libobjc2 must (apparently) be compiled from source if it is to be installed on 14.04.  This is where the problem originates:  cmake (2.8.12.2)  is unable to make the source and GNU makefile won't run because it has been deprecated.  Despite a ton of research I can't figure out what's the matter with cmake.

So, my question:  Does anyone know of plans to make libobjc2 available as a .deb package.  AFAIK, it is not available for 14.04, but is available --and runs--on 12.04?

Mark Allyn

---

