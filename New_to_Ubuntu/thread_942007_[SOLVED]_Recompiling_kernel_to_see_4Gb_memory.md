---
title: "[SOLVED] Recompiling kernel to see 4Gb memory"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by akelsall on 2008-10-08
Hello, I'm now running into a problem others seem to have come across. I just upgraded from 3Gb to 4Gb of RAM, but Ubuntu is only seeing 3.3Gb. I read through the forums and one suggestion was recompile the kernel with PAE enabled. 

I have never recompiled a kernel before, but I'm willing to give it a shot (I just loaded Ubuntu 8.04 today on a new hard drive, so no biggie if things get jacked up). 

Can someone explain to me, in simple terms, how to go about doing this? I'm very comfortable with computers, loading software, installing hardware, etc., but I've never ran Linux and have never recompiled a kernel, so this will be a "learning opportunity" for me :biggrin:

Thanks,

Andy

---

### Post by blakjesus on 2008-10-08
Just checking but...
Do you have 32-bit Ubuntu installed or 64-bit? Because no 32-bit OS can read 4GB of memory. :popcorn:

---

### Post by knix on 2008-10-08
1) Install the linux-image-server package. this supports high RAM on 32-bit systems.

2)If you want to compile a kernel yourself, kernelcheck is very easy to use. You'll want to enable highmem (or himem, I forget how it's spelled) when you configure the kernel.
Do this whan you have time - it takes me ~ 1hr. on a C2D @1.4 GHz.

---

### Post by akelsall on 2008-10-08
Hello blakjesus, thanks for getting back to me. I'm kinda caught in the middle now, as you indicated 32-bit OS can't read 4Gb, while other forum members say you can. You mind if I ask where you got this info from? I'm just trying to get a definitive answer on this, as another post to my question says it can be done. 

Thanks,
Andy

---

### Post by akelsall on 2008-10-08
Forgot to mention I'm running the 32-bit version:

sudo lshw | grep width
    width: 32 bits        

 uname -a
Linux hikerguy 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

---

### Post by knix on 2008-10-08
Normally, a 32-bit system CANNOT access 4GB of memory. However, the Linux kernel has some features, which, when enabled, allow this. linux-image-server has them. If you want to run 64-bit, you'll have to install a 64-bit ubuntu (from a 64-bit CD or other installation media)
Edit: oops, just realized your hardware was 32-bit too.

---

### Post by akelsall on 2008-10-08
Hello Knix, is there any downside to installing the server package? Right now, I'm just running Ubuntu on a desktop, although I do plan on tinkering with setting up a mail server and finding out what Apache is all about. If that's my plan, does it make sense to go ahead and install the server package?

Also, I have a few questions about compiling the kernel (bear with me here, as this is uncharted territory for me):

1. When I compile a kernel, what exactly am I doing? Am I modifying my existing kernel, then compiling it into a new version, or am I compiling a new version of the kernel (say, a release candidate)?


2. Do I run any risk of losing data that I may copy over from my old HD to my new HD (or even lose the partitions I've set) if I try booting to the new kernel? I did set up a separate /home partition if that matters. 

Thanks,

Andy

---

### Post by crispy_420 on 2008-10-09
There are ways to allow a 32-bit linux system with 4GB(or beyond) to use it all. Can't remember off the top off my head but essentially it works by chopping the RAM in half with some dedicated to only the kernel and the rest for the functional system.

Hope that gets you looking in the right direction.

---

### Post by akelsall on 2008-10-10
Not actually resolved, but marking as solved since no new responses have been poste in some time. Will continue to research this, as there are still lingering questions.  Thanks to all who replied.

---

### Post by WWSmith36 on 2008-10-10
I am pretty sure you can do this without recompiling you kernel

Just install the following packages and reboot

```
sudo apt-get install linux-restricted-modules-server
sudo apt-get install linux-headers-server
sudo apt-get install linux-image-server linux-server
```

**Source:** 
[http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)

---

