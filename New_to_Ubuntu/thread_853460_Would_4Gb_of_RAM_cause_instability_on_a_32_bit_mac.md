---
title: "Would 4Gb of RAM cause instability on a 32 bit machine?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by muteXe on 2008-07-08
Hello,
My new laptop is a ubuntu-vista dual boot.  I've only had less than 2 weeks.  Now when i boot into vista, it bluescreens after being on for about 10 minutes.  I have been posting on vista forums but they dont seem to be technically "with it" as linux people.
Thankfully when i boot into linux i dont get any crashing or anything like that.  My question is:  should I be prepared for an eventual major crash when I boot into linux because it may have problems coping with 4Gb of RAM on my 32 bit machine? (like crappy vista seems to be).

Thanks in advance,

mute

---

### Post by tamoneya on 2008-07-08
dont worry.  Thats just vista being vista.  The only problem with running 32 bit on a 4GB+ RAM system is that you are wasting money.  No kernel panics or BSODs.

---

### Post by phidia on 2008-07-08
A 32 bit OS won't recognize more than 3Gb of ram. I'm not a booster of Vista but the behavior you have described isn't normal so while it's under warranty (hopefully) you might want to let the computer maker know you are having a problem-if this is a hardware issue you want them to fix or replace the laptop.
Out of curiousity what make and model laptop is this?

---

### Post by descendency on 2008-07-08
> **phidia said:**
> A 32 bit OS won't recognize more than 3Gb of ram.

Because of the memory addressing of the graphics card and CPU.

---

### Post by Inxsible on 2008-07-08
Since you have 4GB of RAM, why not use a 64 bit Ubuntu to fully utilize your system capabilities?

As for Vista, it probably is a problem with Vista and nothing to do with you having 4GB of RAM.

---

### Post by damis648 on 2008-07-08
Actually, a 32-bit OS can recognize up to a total of 4GB combined memory. This includes your actual RAM and graphics memory, (as well as swap??). So, on my machine with 4GB ram and a 256MB graphics card, free -m tells me:
```
             total       used       free     shared    buffers     cached
Mem:          3545        899       2646          0         22        430

```
where 3545 is my total available RAM, which was 4GB minus kernel, root access, swap, and graphics memory.

---

### Post by sdennie on 2008-07-08
You can use all 4G of memory on a 32bit machine by using a kernel with PAE support.  This allows the kernel to address up to 36bits of RAM (64G) while still having your machine behave like a 32bit machine.  The Ubuntu -server kernel has support for this but, it's not well suited for desktop use so, if you don't go 64bit, you'd have to compile a 32bit kernel with PAE support to see all 4G of RAM.  

I've been running a custom kernel with PAE and 4G of RAM for several months now and have not had a single stability problem.

---

### Post by Paul Weaver on 2008-07-08
> **Inxsible said:**
> Since you have 4GB of RAM, why not use a 64 bit Ubuntu to fully utilize your system capabilities?


Is Flash available for 64bit linux yet? Or Java?

I've noticed PAE options in the kernel before, which seemed to allow > 4GB of total memory space on 32bit?

> 
As for Vista, it probably is a problem with Vista and nothing to do with you having 4GB of RAM.

Vista isn't that bad, especially out of the box. Could be dodgy memory -- Vista will use more than Ubuntu initially. You'd need to talk to Microsoft support (I assume as you pay for vista you get a support contract) with the numbers on the blue screen -- I understand it's the equivalent of a kernel panic.

You could run memtest86 overnight too.

---

### Post by tamoneya on 2008-07-08
> **damis648 said:**
> Actually, a 32-bit OS can recognize up to a total of 4GB combined memory. This includes your actual RAM and graphics memory, (as well as swap??). So, on my machine with 4GB ram and a 256MB graphics card, free -m tells me:
```
             total       used       free     shared    buffers     cached
Mem:          3545        899       2646          0         22        430

```
where 3545 is my total available RAM, which was 4GB minus kernel, root access, swap, and graphics memory.

the 32 bit limit does not include swap although like you said it does include graphics memory.  Swap is just a harddrive partition.

---

### Post by sdennie on 2008-07-08
> **damis648 said:**
> Actually, a 32-bit OS can recognize up to a total of 4GB combined memory. This includes your actual RAM and graphics memory, (as well as swap??). So, on my machine with 4GB ram and a 256MB graphics card, free -m tells me:
```
             total       used       free     shared    buffers     cached
Mem:          3545        899       2646          0         22        430

```
where 3545 is my total available RAM, which was 4GB minus kernel, root access, swap, and graphics memory.

> **tamoneya said:**
> the 32 bit limit does not include swap although like you said it does include graphics memory.  Swap is just a harddrive partition.

As tamoneya said, you aren't seeing 4G of RAM.  As a comparison, here is the output of my XPS m1330 (similarly configured to your XPS m1530) with PAE enabled:

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          4049       3890        159          0        217       2179
-/+ buffers/cache:       1493       2556
Swap:         4000          0       4000
$ uname -a
Linux zorba 2.6.24.7-pae #1 SMP PREEMPT Sun Jun 22 17:18:06 MDT 2008 **i686** GNU/Linux

```

With the default 32bit kernels, my reported RAM is closer to yours (about 3.5G).

---

### Post by pofigster on 2008-07-08
Theoretically a 32-bit system can recognize up to exactly 4 Gigs of RAM (2^32 = 4 gigs).

---

### Post by sdennie on 2008-07-08
> **pofigster said:**
> Theoretically a 32-bit system can recognize up to exactly 4 Gigs of RAM (2^32 = 4 gigs).

Yes but in practice, that is never the case.  The reason is that various devices on your computer need large chunks of the memory address space to work properly and so the system maps them into the higest parts of memory.  When that happens on a machine with 4G of RAM and a 32 bit kernel without PAE, it limits the amount addressable physical RAM.

---

### Post by bodhi.zazen on 2008-07-08
> **tamoneya said:**
> dont worry.  Thats just vista being vista.  The only problem with running 32 bit on a 4GB+ RAM system is that you are wasting money.  No kernel panics or BSODs.

> **phidia said:**
> A 32 bit OS won't recognize more than 3Gb of ram. I'm not a booster of Vista but the behavior you have described isn't normal so while it's under warranty (hopefully) you might want to let the computer maker know you are having a problem-if this is a hardware issue you want them to fix or replace the laptop.
Out of curiousity what make and model laptop is this?

> **descendency said:**
> Because of the memory addressing of the graphics card and CPU.

Where do you people get your information ?

> For **32-bit systems** the Server Edition is configured to use **PAE** which **allows addressing up to 64GB of memory** while the Desktop Edition is configured for 4GB.[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

---

### Post by muteXe on 2008-07-08
it's a dell xps M1330.
i'm not as concerned with the fact i may not be using my full 4Gb of RAM, just if it's stable in a 32 bit environment.

Thanks for all your replies by the way :)

mute

---

### Post by Inxsible on 2008-07-08
> **Paul Weaver said:**
> Is Flash available for 64bit linux yet? Or Java?

I've noticed PAE options in the kernel before, which seemed to allow > 4GB of total memory space on 32bit?Flash and java are just as easy to install on a 64 bit machine as they are on 32 bit machines.

---

### Post by k3lt01 on 2008-07-08
> **muteXe said:**
> Hello,
My new laptop is a ubuntu-vista dual boot.  I've only had less than 2 weeks.Who made the machine dual-boot? You, someone else, or did it come from the factory like it?

> **muteXe said:**
>  Now when i boot into vista, it bluescreens after being on for about 10 minutes.  I have been posting on vista forums but they dont seem to be technically "with it" as linux people.
Thankfully when i boot into linux i dont get any crashing or anything like that.  My question is:  should I be prepared for an eventual major crash when I boot into linux because it may have problems coping with 4Gb of RAM on my 32 bit machine? (like crappy vista seems to be).

Thanks in advance,

muteIf you dual-boot any OS you are going to have to clean up the OS that was installed natively. So say for example you have Vista on a 200GB HDD, you make it dual boot Vista and Ubuntu, there are going to be parts of Vista that have been moved. This can, and from my experience will, cause some problems even if they are just minor until the Vista install is checked out. Do a Scan Disk, Defrag, etc. and see how it goes. You may have to use System Recovery if that doesn't work to get Vista back on track.

---

### Post by Xerp on 2008-07-08
> **muteXe said:**
> it's a dell xps M1330.
i'm not as concerned with the fact i may not be using my full 4Gb of RAM, just if it's stable in a 32 bit environment.

Thanks for all your replies by the way :)

mute

The RAM will not cause instability.

---

### Post by phidia on 2008-07-08
nevermind

---

### Post by bodhi.zazen on 2008-07-08
> **phidia said:**
> nevermind

LOL, I saw that ninja edit :lolflag:

You can either install the server or openvz kernel on your desktop install or compile your own kernel.

:popcorn:

---

### Post by descendency on 2008-07-08
> **bodhi.zazen said:**
> Where do you people get your information ?

[http://www.dansdata.com/askdan00015.htm](http://www.dansdata.com/askdan00015.htm)

---

### Post by sdennie on 2008-07-08
> **descendency said:**
> [http://www.dansdata.com/askdan00015.htm](http://www.dansdata.com/askdan00015.htm)

I only read the first paragraph or two before concluding that Dan is wrong.

---

### Post by bodhi.zazen on 2008-07-09
> **descendency said:**
> [http://www.dansdata.com/askdan00015.htm](http://www.dansdata.com/askdan00015.htm)

Shh ... Don't tell dan ...


[http://technet.microsoft.com/en-us/windowsserver/bb430827.aspx](http://technet.microsoft.com/en-us/windowsserver/bb430827.aspx)

> 128 MB of RAM minimum required; 256 MB or more recommended; 64 GB maximum for x86-based computers

[http://kerneltrap.org/node/2450](http://kerneltrap.org/node/2450)

> <clip> ... PAE addresses the 4 GB physical memory limitation ... </clip>

Now I do not know about you, but I find technet.microsoft and kerneltrap to be very reliable sources of information.

:popcorn:

---

### Post by bodhi.zazen on 2008-07-09
> **vor said:**
> I only read the first paragraph or two before concluding that Dan is wrong.

LOL, you only need to read the title:

> Last modified  										01-Apr-2008.

---

### Post by sdennie on 2008-07-09
Just to prevent bodhi.zazen from getting the last post, I will post the output from the 32bit PAE enabled machine I'm currently on:

```

sdennie@zorba:~$ uname -a
Linux zorba 2.6.24.7-pae #1 SMP PREEMPT Sun Jun 22 17:18:06 MDT 2008 [COLOR="Red"]i686[/COLOR] GNU/Linux
sdennie@zorba:~$ grep X86_32 /boot/config-`uname -r`
[COLOR="Red"]CONFIG_X86_32=y[/COLOR]
sdennie@zorba:~$ grep CONFIG_HIGHMEM /boot/config-`uname -r`
# CONFIG_HIGHMEM4G is not set
[COLOR="Red"]CONFIG_HIGHMEM64G=y[/COLOR]
CONFIG_HIGHMEM=y
sdennie@zorba:~$ file /lib/libc-2.7.so 
/lib/libc-2.7.so: ELF [COLOR="Red"]32-bit[/COLOR] LSB shared object, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, stripped
sdennie@zorba:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          [COLOR="Red"]4049[/COLOR]       3889        160          0        311       2606
-/+ buffers/cache:        970       3078
Swap:         4000          0       4000

```

---

### Post by damis648 on 2008-07-09
> **vor said:**
> Just to prevent bodhi.zazen from getting the last post, I will post the output from the 32bit PAE enabled machine I'm currently on:

```

sdennie@zorba:~$ uname -a
Linux zorba 2.6.24.7-pae #1 SMP PREEMPT Sun Jun 22 17:18:06 MDT 2008 [COLOR="Red"]i686[/COLOR] GNU/Linux
sdennie@zorba:~$ grep X86_32 /boot/config-`uname -r`
[COLOR="Red"]CONFIG_X86_32=y[/COLOR]
sdennie@zorba:~$ grep CONFIG_HIGHMEM /boot/config-`uname -r`
# CONFIG_HIGHMEM4G is not set
[COLOR="Red"]CONFIG_HIGHMEM64G=y[/COLOR]
CONFIG_HIGHMEM=y
sdennie@zorba:~$ file /lib/libc-2.7.so 
/lib/libc-2.7.so: ELF [COLOR="Red"]32-bit[/COLOR] LSB shared object, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, stripped
sdennie@zorba:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          [COLOR="Red"]4049[/COLOR]       3889        160          0        311       2606
-/+ buffers/cache:        970       3078
Swap:         4000          0       4000

```

Now... to go about enabling PAE (CONFIG_HIGHMEM64G), would I have to recompile the kernel? Or could I just set it in this configuration file? (/boot/config-2.6.24-19-generic)?

---

### Post by meindian523 on 2008-07-09
As an aside,my motherboard supports a max of 2GB of RAM,and I already have one 512MB module in the 1st slot.Suppose I bought a 2GB module and plugged it into the second slot,would Linux still see the entire 2.5GB of RAM and use it,or would it be limited by motherboard capabilities?

---

### Post by muteXe on 2008-07-09
> **k3lt01 said:**
> Who made the machine dual-boot? You, someone else, or did it come from the factory like it?

If you dual-boot any OS you are going to have to clean up the OS that was installed natively. So say for example you have Vista on a 200GB HDD, you make it dual boot Vista and Ubuntu, there are going to be parts of Vista that have been moved. This can, and from my experience will, cause some problems even if they are just minor until the Vista install is checked out. Do a Scan Disk, Defrag, etc. and see how it goes. You may have to use System Recovery if that doesn't work to get Vista back on track.


I made it dual-boot.  I shall try these things you've suggested.  Thank you.  I was also thinking that it didn't blue-screen at all until i installed SP1 on vista.  I might try uninstalling this as well.  Failing that I will get rid of vista altogether I think.

Thanks again,

mute

p.s. these forums are good.

---

### Post by muteXe on 2008-07-09
How do you enable PAE support on a 32bit machine to show the 4Gb in a desktop distro of Ubuntu?
Thanks again,

mute

---

### Post by damis648 on 2008-07-09
> **muteXe said:**
> How do you enable PAE support on a 32bit machine to show the 4Gb in a desktop distro of Ubuntu?
Thanks again,

mute

Check this: [http://www.howtoforge.com/forums/showthread.php?t=21](http://www.howtoforge.com/forums/showthread.php?t=21)
And just replace the kernel version(s) with your output of
```
uname -r
```

EDIT: I forgot mentioning including PAE... check here: [http://www.howtoforge.com/forums/showthread.php?t=1373#5](http://www.howtoforge.com/forums/showthread.php?t=1373#5)

What you might want to do is update your kernel at the same time. If you are doing that (I am right now), check kernel.org for maybe 2.6.25-10. I am compiling this one with PAE.

---

### Post by muteXe on 2008-07-09
Looks horribly complicated for a n00b like myself.
I think i'll be happy with it only using 3Gb :)

---

### Post by sdennie on 2008-07-09
> **damis648 said:**
> Now... to go about enabling PAE (CONFIG_HIGHMEM64G), would I have to recompile the kernel? Or could I just set it in this configuration file? (/boot/config-2.6.24-19-generic)?

You would have to recompile the kernel or, as bodhi.zazen said, install and use the -server kernel.  That should be as simple as:

```

sudo apt-get install linux-image-server linux-headers-server linux-restricted-modules-server

```

After that, when you restart you'll have the option to use the server kernel in grub.  Depending on how you use your machine, you may not notice any difference between the -server and -generic kernels (except that the -server will show up to about 64G of RAM).

---

### Post by damis648 on 2008-07-09
> **vor said:**
> You would have to recompile the kernel or, as bodhi.zazen said, install and use the -server kernel.  That should be as simple as:

```

sudo apt-get install linux-image-server linux-headers-server linux-restricted-modules-server

```

After that, when you restart you'll have the option to use the server kernel in grub.  Depending on how you use your machine, you may not notice any difference between the -server and -generic kernels (except that the -server will show up to about 64G of RAM).

Thank you... T discovered this. I attempted to recompile the kernel... I had a kernel panic in the middle so I just won't bother with it. Thanks anyway!

---

### Post by bodhi.zazen on 2008-07-09
> **damis648 said:**
> Thank you... T discovered this. I attempted to recompile the kernel... I had a kernel panic in the middle so I just won't bother with it. Thanks anyway!

FYI: Installing the server kernel via synaptic or apt-get is both easy and safe ;)

---

