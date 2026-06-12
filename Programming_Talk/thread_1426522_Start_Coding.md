---
title: "Start Coding"
date: 2010-03-10
forum: Programming Talk
---

### Post by kernelnewbie1 on 2010-03-10
"Hello linux world!"
  I am new to linux programming , but i have learnt C/C++, assembly, also had a course on Operating Systems and Unix
 I think this must be enough to form basics for a kernel programmer

I wish to learn how to modify Kernel and check the results , there by i can implement my new ideas into kernel

I mainly wish to learn how do i go about fixing a bug once i notice it,
like ... When i installed ati driver to my kubuntu box , the cursor got disappeared  , i did not know where to start to fix such a bug ............

Now the great community of LINUX please help me in learning all these

---

### Post by Zugzwang on 2010-03-10
Linux kernel modifications is not quite simple. You should seriously consider reading some books on Linux kernel modification first (like "Linux device drivers" by J.Corbet et al. or "Linux kernel development"
by R.Love). Your university library might help you here.

---

### Post by unmole on 2010-03-10
Download the Linux kernel source from kernel.org
Extract it to /usr/src and checkout the Documentation/kernel-docs.txt
That should help you get started.

Best of luck and may the source be with you!

---

### Post by hyperAura on 2010-03-10
well modifying the kernel and recompiling the whole thing is something ive never done before but i guess its not an easy job.. good luck to you, hopefully u will solve many bugs.. :)

---

### Post by rahul_bhise on 2010-03-24
this site may be a help
[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")
Linux From Scratch (LFS) is a project that provides you with step-by-step instructions for building your own custom Linux system, entirely from source code.

---

### Post by dargaud on 2010-03-24
I find it easier to fiddle with the kernel when doing embedded programming than on a full PC. You get 'all at once' tools like buildroot, you can minimize your kernel to only a few drivers, you can minimize the entire OS to no more than 5 files (yes!), you can get rid of all security measures (no users, no init levels, etc), you get boot times of 2 seconds (yes!) for when you screw things up... In other words you can grok the whole system in your head. 

And best of all, you don't have to use an embedded device, as you can run it fine on an old x86 PC !

---

### Post by Xyro on 2010-03-24
+1 for "Linux kernel development" by R.Love. Reading through it at the moment and it is fantastic.

---

### Post by kernelnewbie1 on 2010-03-25
Thanks all , Linux kernel development by R.Love is a great book :D

---

