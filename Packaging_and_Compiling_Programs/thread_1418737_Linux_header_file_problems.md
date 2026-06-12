---
title: "Linux header file problems"
date: 2010-02-28
forum: Packaging and Compiling Programs
---

### Post by bourne-sc2 on 2010-02-28
Hello,

I've been doing research with a professor, and have been playing around with building my own Linux module.  I have Ubuntu Linux (9.04) on my laptop, and have always been able to run simple C programs such as hello world without issue.

However, when I do a make, it says it cannot find 3 header files I am using : linux/config.h, sys/syscall.h, and stdio.h.  The last one makes almost no sense to me, since I can run a hello world c program from the same directory with no issues.  Furthermore, I am also using linux/module.h, linux/kernel.h, linux/sched.h, and linux/string.h.  It does not complain about those at all.

I've followed a few how-tos about making my own kernel modules, and here is where I have a problem...

Running apt-get install kernel-headers-$(uname -r) gives me:
Couldn't find package kernel-headers-2.6.28-18-generic

Is there something I'm doing wrong? I can't figure what's wrong or what I'm doing wrong.

Let me know if you do need to see code, however it wont even compile so I didn't think that would be of any use.

Thanks

---

### Post by gmargo on 2010-03-01
Try **linux**-headers.... instead of **kernel**-headers.....

---

### Post by bourne-sc2 on 2010-03-01
I tried that, and it tells me that I have the newest version already.

---

### Post by bourne-sc2 on 2010-03-04
*bump* anyone?  It's really holding me up.  Does anyone happen to have a reliable website that explains how to build/compile kernel modules?  Obviously the one I used did not work.

---

### Post by Bachstelze on 2010-03-04
[font=monospace]linux/config.h[/font] was removed in the 2.6.19 version of the kernel.

All other headers are in the [font=monospace]libc6-dev[/font] package, which is the first thing to install when you want to do C programming in Ubuntu. See the stickies at the top of this section.

---

### Post by bourne-sc2 on 2010-03-04
Bach,

Thank you for the response.  I do already have the libc6-dev installed.  It is nice to know that the linux/config.h header is no longer alive.

I'm not sure why it can't find stdio.h when invoking the make file to build my module, but since linux.config.h is obsolete, I'll need to consult another how-to concerning my program

Thanks

---

