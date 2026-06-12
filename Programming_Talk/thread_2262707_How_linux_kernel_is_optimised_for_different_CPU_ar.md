---
title: "How linux kernel is optimised for different CPU architectures?"
date: 2015-01-26
forum: Programming Talk
---

### Post by pavelexpertov on 2015-01-26
Hello, I was reading about brief list of features that each processor family had in an intel manual book for IA-32 and 64-BIT. It got me wondering how programmers, who volunteer their time to make and send patches (if I understand correctly) to development kernel version, which will eventually becomes final version, to be able to optimise the kernel so it can work on different architectures and still use main features of processors. SO I have the following questions:
So the main kernel is optimised in a way so that it uses main functions and features within different CPUs so it can be portable? So if I wanted to use extra features within a processor, would I have to make a custom kernel?
In a case of Intel, it provides additional drivers (or its linux installer from their opensource website). Do the drivers tend to fix problems or make the processor work better and efficiently compared to the main kernel?
Are linux patches written in pure C or C++ so they can work for different CPUs structures?
Thank you!!!!!

---

### Post by 3246251196 on 2015-01-26
Hi, all patches are made in C (or assembly .S) as that is what the Kernel is written in - low level. 

As for how the kernel handles different archs - the directory tree of the 2.6 kernel's arch (architecture directory) looks like this:

arch/
&#9500;&#9472;&#9472; alpha
&#9500;&#9472;&#9472; arm
&#9500;&#9472;&#9472; arm26
&#9500;&#9472;&#9472; cris
&#9500;&#9472;&#9472; frv
&#9500;&#9472;&#9472; h8300
&#9500;&#9472;&#9472; **i386**
&#9500;&#9472;&#9472; ia64
&#9500;&#9472;&#9472; m32r
&#9500;&#9472;&#9472; m68k
&#9500;&#9472;&#9472; m68knommu
&#9500;&#9472;&#9472; mips
&#9500;&#9472;&#9472; parisc
&#9500;&#9472;&#9472; ppc
&#9500;&#9472;&#9472; ppc64
&#9500;&#9472;&#9472; s390
&#9500;&#9472;&#9472; sh
&#9500;&#9472;&#9472; sh64
&#9500;&#9472;&#9472; sparc
&#9500;&#9472;&#9472; sparc64
&#9500;&#9472;&#9472; um
&#9500;&#9472;&#9472; v850
&#9492;&#9472;&#9472; **x86_64**

The kernel has all the necessary modules in it when you download it. You compile it targeted for what you want - using menuconfig (for example) where you can choose to include the modules (drivers) you actually want and whether you want them to be static in the kernel etc.

So this is the good thing about Linux in that it has a lot of (potential) drivers already there for you without the need to go out and download drivers like you need to for Windows. Of course you need to compile module and ***modprobe*** it in if you haven't statically included it or already compiled it, but at least the drivers are self contained (for the most part). And, if you do need to download a module for linux - at least it is using a repo that is monitored by people before allowing it to be released. How many times I have tried to install a drivers on Windows and went to a "dodgy" site I cannot count. There are third party repo's out there of course and ideally you would check them closely.

This is just an attempt at answering some of what you ask!

---

### Post by pavelexpertov on 2015-01-26
Thank you for your reply, the kernel's arch tree is amazing :). However, since you mentioned that I have to compile modules, what does it mean to make the modules *static?* Does it mean these modules will be run at a start up and then choose one of them so they can run on a certain architecture? And how about compiling module and modprobe it in?
This is because I remember I installed Lubuntu on my pentium 4 machine and then I moved the harddrive to another old machine with Intel 2 duo core. And it worked. So due to information about modules and compiling make the OS portable between computers?

---

### Post by 3246251196 on 2015-01-26
So I can configure a kernel using the kernel configuration tool and select a video camera driver to be static (this is just an example). It means that the code for it is part of the monolithic structure of the kernel: i.e. it cannot be changed and it is there. Instead, I could have selected the video camera driver to be a module: one of the things that distinguishes the linux kernel. I can dynamically install or uninstall the module at run time. So maybe I have realised I want to use the video camera I can run modprobe (which is just a smarter version of insmod - because modprobe does what insmode does BUT also pulls in dependencies; for example, when you install a debian package... you can install just that one package but this is not as smart as installing that package and ALSO installing all the things that it depends on - otherwise it does not work) and then use the camera.

I actually run a core 2 duo too and its still a rock solid system about 8 years old for me. But I think in your case the instruction sets were the same between your Pent4 and Core2Duo. - x86_64. I doubt you could have booted up the kernel had you went from a Pent4 to - for example - some ARM7 chip. But I would like someone else to confirm this.

---

### Post by pavelexpertov on 2015-01-26
Thanks again and now it makes tonnes of sense. Yeah you are right about the instructions sets, it's probably because I was lucky. However, since it possible to install and uninstall a module at runtime, would an OS (or in this case init/systemd I believe) be responsible in selecting different architecture modules? Because either 32/64 bit versions of OS must be compatible with AMD and INTEL out of the box. Furthermore, I read one of youtube videos about 10 reasons why linux rocks and one of the reasons was that you can actually take a hard drive to a different computer and load it without problems.

---

### Post by tgalati4 on 2015-01-27
In my mind, the ultimate kernel is one that uses so little resources so that I have the maximum number of CPU cycles to run MY applications and code.  You generally want the kernel to get the heck out of the way so you can do your work.  An operating system that eats 12% of CPU cycles, all the time, is not an optimized one.

The fact that the kernel runs on several different architectures and still gets out of the way for user programs is amazing.  Are there features in some CPU's that are not supported?  Yes, probably.  Can you compile a custom kernel to enable those features?  Generally yes.  Can you improve the task scheduling over the default settings?  Yes probably, for specific workloads.  

As you dig into the kernel details and spend some time with the kernel configuration, you appreciate the work and the elegance of the whole system.  Can you eliminate stuff from the kernel that you don't need?  Yes.  Can you get a faster, slimmer kernel, even real-time performance?  Yes.  Can you modify the kernel to support undervolting?  Yes.  Can you modify the kernel to support more than 256 processors?  Yes.  Not long ago, the hard-coded limit was 16 processors, then 64 processors.

As far as modules, the more static modules you have, the fatter the kernel.  Dynamic loading of modules allows for a smaller kernel with only the modules loaded for hardware that is detected.  This is why you can pull a hard drive from one computer and generally get it to boot on another machine.  The modules get dynamically loaded during boot so the system can adapt to new hardware, or broken/missing hardware.  This adaptability is one of the reasons that linux can boot and run off of a CD, DVD, or USB drive.  Try doing that with another operating system.

---

### Post by 3246251196 on 2015-01-27
Hi, thanks tg. I have swapped a hdd to a different machine at work before and it worked flawlessly - the only thing I needed to change was the MAC address in a file to update it to the new address for networking. But, this was done from one machine of one architecture to another machine of the same architecture.

I would still like to know what happens if you remove a HDD from an x86_64 to an ARM platform. I know that ARM is supported, but the modules etc - all the kernel code is compiled for x86_64 instructions. I cannot see how plugging in an "ARM module" would work (not suggesting you even suggested that). I feel like you would need to recompile the kernel. I would like to get clarification on this myself.

---

### Post by tgalati4 on 2015-01-27
Because ARM motherboards tend to be SoC (System-on-a-Chip), they do behave differently than traditional CPU/motherboard architectures.  You can take a 32-bit Intel (i686) kernel and run it on a 64-bit machine (AMD64) because the 64-bit can natively handle 32-bit Intel instructions.  You can't do the reverse because the 32-bit CPU doesn't have 64-bit data buses or handle memory pages above 4 GB.

I doubt you can simply add an ARM module to the base Intel-compiled kernel to get it to run on an ARM computer.  I'm pretty sure you need an ARM-compiled kernel to boot properly.  Normally this is done by building a cross-compiler environment. Otherwise, the file system (perhaps Ext4) can still be read from one system to the other. 

Is there a Use Case for what you have proposed?  Sure.  Develop an OS on an Intel box and put it on an ARM phone.  I don't see how this can be done without going through a cross-compile step (compiling the kernel with the ARM architecture switch on an Intel machine).

---

### Post by 3246251196 on 2015-01-27
Yup, that clears things up. Cheers.

---

### Post by pavelexpertov on 2015-01-27
[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=241895") 				 				 					 						 	[**[COLOR=#000000]tgalati4  &[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895") [ 						 							 						 					]("http://ubuntuforums.org/member.php?u=1258334") 				 				 					 						 	[**[COLOR=#000000]3246251196[/COLOR]**]("http://ubuntuforums.org/member.php?u=1258334"), thanks for your replies, because it gives me a big picture of the kernel's portability and it's well interesting!!!!! hopefully I will get to customise a kernel one day!!!!

---

