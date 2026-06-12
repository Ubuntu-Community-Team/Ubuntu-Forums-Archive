---
title: "Ubuntu Linux Kernel - understanding version numbers"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by D0natell0 on 2013-04-15
Hi,
Here are some (probably dumb) questions:

Does kernel 2.6.32-46 include kernel 2.6.37 (i.e. everything between x.x.32 and x.x.46)?
What is the a difference between kernel 2.6.32-46 and 2.6.37?

Just trying to get something to work (see [https://01.org/linuxgraphics/downloads/2012/intel-2010q4-graphics-stack-release](https://01.org/linuxgraphics/downloads/2012/intel-2010q4-graphics-stack-release))
Thanks in advance.

---

### Post by Paqman on 2013-04-15
It's a newer version of the same code yes. There will be new stuff in the newer version and bugfixes. They may also have removed some code, but that would only happen for really ancient stuff that they're sure nobody uses any more.

---

### Post by ibjsb4 on 2013-04-15
Have you looked at the changelog?

[http://kernelnewbies.org/LinuxVersions](http://kernelnewbies.org/LinuxVersions)

---

### Post by philinux on 2013-04-15
> **D0natell0 said:**
> Hi,
Here are some (probably dumb) questions:

Does kernel 2.6.32-46 include kernel 2.6.37 (i.e. everything between x.x.32 and x.x.46)?
What is the a difference between kernel 2.6.32-46 and 2.6.37?

Just trying to get something to work (see [https://01.org/linuxgraphics/downloads/2012/intel-2010q4-graphics-stack-release](https://01.org/linuxgraphics/downloads/2012/intel-2010q4-graphics-stack-release))
Thanks in advance.

[http://en.wikipedia.org/wiki/Linux_kernel#Version_numbering](http://en.wikipedia.org/wiki/Linux_kernel#Version_numbering)
This explain it.

---

### Post by grahammechanical on 2013-04-15
The numbers that you should focus on are the first three sets of numbers. They are the revision numbers set by the Linux organisation. The number after the dash ( - ) is a revision number provided by the Ubuntu developers to track the modifications that may make.

So, kernel 2.6.32 is older than kernel 2.6.37. These a revised kernels from Linux organisation. To give you an example. The other day I installed Raring Ringtail. It came with kernel 3.8.0-17.27 and has been ungraded at least twice over the last few days. So, I also have 3.8.0-18.28 and 3.8.0-18.34

They are all Linux 3.8.0 kernels but -17.27; -18.28 & -18.34 reference modifications made by Ubuntu developers to fix bugs, such as Nvidia drivers breaking Compiz. Which is what happened a few days ago. The developers cannot mess with the proprietary drivers but they can access the Linux kernel code and they put those packaging markers their so that if their changes produce their own bugs they can identify which package causes the problem.

Anyway, the answer to your first question is, NO.

The Linux developers have not always been systematic in their use of revision numbers. But this old post might explain things a bit better.

[http://www.linfo.org/kernel_version_numbering.html](http://www.linfo.org/kernel_version_numbering.html)

Regards

---

