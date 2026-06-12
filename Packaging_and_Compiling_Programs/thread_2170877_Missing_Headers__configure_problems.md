---
title: "Missing Headers / configure problems"
date: 2013-08-28
forum: Packaging and Compiling Programs
---

### Post by gfine on 2013-08-28
First I got an error when running a ./configure saying :

checking for kernel linux/version.h ... no
The file /include/INCLUDE_VERSION_H does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/3.8.0-19-generic/build).

Then reading some forum posts where they hit the same problem it was suggested doing a make in the kernel's head dir. I did so 

But then that produced another error when I did the **make**:

*** No rule to make target `/usr/src/linux-headers-3.8.0-19-generic/arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h'.  Stop.

Checking the directory shows that syscall_32.tbl is indeed missing.  I have done **apt-get install linux-headers-$(uname -r)**, and previous to that **apt-get update**.  

Anyone have an idea of what I am not doing properly? I have had this happen in 12.04 LTS and 13.04 LTS.

G

---

### Post by gfine on 2013-08-29
Noticed one thing. The kernel verison is wrong. Whether booting the live CD or doing a uname -r it comes back as 3.8.0-29-generic, which is beyond 13.04 LTS (3.8.0-19),  12.04 LTS is (from the best I can tell) supposed to be at 3.2.0.52

Anyone have any idea how this could have happened?  Any ideas?  

Presently it has me at an impasse. I downloaded the proper headers which from the best I can tell is 3.2.0.52, but resetting the kernel version is not something I have experienced.  

G

---

### Post by tgalati4 on 2013-08-29
What is it that you are trying to do?  Although not hard, compiling the kernel is a 2-3 hour exercise that requires many, many [steps]("https://help.ubuntu.com/community/Kernel/Compile").

The kernel version differences are minor and happen when you perform updates.  So unless you have a specific reason to compile the initial install kernel, your sources will come from the latest version of the kernel for your distro.  If you have not performed all of your updates, then there will be a (slight) mismatch.  Whether this mismatch causes a problem with your system, only you will be able to tell us.

---

### Post by gfine on 2013-08-30
Well, my reason is compiling a specialized ALSA driver which is then installed into the kernel.  Thanks for the link, but there is nothing on Precise Pangolin (12.04).  Some of it is very old (Hardy). I have been doing kernel configuring/building, and writing device drivers since 2005, and have suffered through bad builds, migrating to 2.6.x from 2.4.x, and so on.  

Initially (with 12.04.2) I had no problem. The driver built and installed without problem.  Then I allowed an update to happen which I assume brought my system to the 12.04.3 level, and then the kernel version (and missing headers) problem appeared.  I downloaded and reinstalled on a different partition, and ran into the same problem.  I then downloaded 12.10 and it reports its kernel version as 3.5.0-17 (Which I expect is correct).  I still run into the missing syscall_32.tbl file. but the kernel version is not jacked up as it is on 12.04.3. 

As I said in my 2nd post, the wrong version (3.8.0-29) appears on the 12.04.3 Live CD. 

I'd feel a lot better that it was me if someone would load the 12.04.3 Live CD and open a terminal and type "uname -r", and report to us the version number it comes back with.  This would verify it is me, and that somehow I squirreled the build on my system. But, as I said, I see it on an independent load, and on the live CD.  So something is amiss.  If I felt it was only in my kernel build tree I wouldn't mention it.  But if this is in 12.04.3 it has a potential of affecting the entire community that is running 12.04.2 LTS, does an update, and then pulls down the kernel headers, and can not compile their kernel (and drivers) anymore. 

I am hoping it is just me, and is not a pervasive bug. 

tgalati4, Thanks for the link but I have been there.  As I said I am no stranger to doing kernel builds. 

For info sake my system: AMD FX-8150 (running at 3.6ghz per core), ASUS Sabertooth 990fx motherboard, 16 GB RAM, twin 1 TB Sata-6 drives, NVidia 520 GT video. 

G

---

### Post by steeldriver on 2013-08-30
I wonder if it's related to this? --> [http://ubuntuforums.org/showthread.php?t=2169404](http://ubuntuforums.org/showthread.php?t=2169404)

I'm not sure exactly what the resolution was - perhaps PM Bashing-Om for details?

---

### Post by SevenMachines on 2013-08-31
Newer kernels have moved version.h from include/linux. You can link it,
```
sudo ln -s /usr/src/linux-headers-`uname -r`/include/generated/uapi/linux/version.h /usr/src/linux-headers-`uname -r`/include/linux/version.h
```


Might solve the original issue, it crops up a bit with compiling some external modules against newer kernels

---

### Post by gfine on 2013-08-31
Steel. Seems that Bashing-Om ran into the same problem but is not experienceing the build break I am. His version is jacked as mine is.  SevenMachines, Done that. But then again I need the right header to match the kernel version.  When I did this on other verions it resolved not finding the version.h during a ./configure, but not the syscall_32.tbl missing.  Sigh.  Guess I have to pull the files down one by one after I find out why it is missing in the first place.  Note to all, this happens on x86-64 so YMMV on seeing this.  I put Raring on another parititon and ran into the same compile problem. so I figure I'll spend this weekend unraveling what 'define' or disintegrate is causing the compile error.  

But the again the version mismatch is a different rabbit. 

Anyone know what the correct version for 12.04.3 is supposed to be?

---

### Post by gfine on 2013-09-11
Been crawling all over the web on this problem.  Each time the response is install the kernel headers. They are installed !!!  syscall_32.tbl is missing. Do I just download it from a previous vesion or what?  I am getting to wits end on this.

---

