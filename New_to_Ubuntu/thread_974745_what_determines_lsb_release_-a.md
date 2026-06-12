---
title: "what determines lsb_release -a ?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by jdrodrig on 2008-11-07
Curious question. What determines the answer to lsb_release -a?

I upgraded to 8.10 but if I boot into the previous, 8.04 kernel (from the boot grub) and code lsb_release -a, I get:

jdrodrig@trino-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
jdrodrig@trino-ubuntu:~$ 

why?

I would have thought the kernel determines the "Release" version.

---

### Post by drs305 on 2008-11-07
I just rebooted back into 8.04 and got what you would expect:
```

~: lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

```

You could confirm the one you are using by checking the kernel:
```
uname -r
```
Hardy is kernel 24
Intrepid is kernel 27

---

### Post by jdrodrig on 2008-11-08
That was precisely the source of my confusion. I get:

jdrodrig@trino-ubuntu:~$ uname -r
2.6.24-19-generic

jdrodrig@trino-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
jdrodrig@trino-ubuntu:~$ 

So the kernel is 8.04's but the release is labeled 8.10. Any ideas why?

---

### Post by drs305 on 2008-11-08
> **jdrodrig said:**
> So the kernel is 8.04's but the release is labeled 8.10. Any ideas why?

The only thing I can add is that on my system I do not share any partitions between the two versions - I don't have a separate home partition shared by both versions.

---

### Post by ad_267 on 2008-11-08
It uses the /etc/lsb-release file to get this information. That won't change whatever kernel you're using.

---

### Post by jdrodrig on 2008-11-08
Thanks! that solves it!

---

### Post by Kellemora on 2008-11-08
Hi AD

Although your answer IS correct (as always!)

I don't know if it clarifies some of the other comments.

Either that, or I'm even more confused now than before.

Although the Kernel is changed to include things for the new release, it's still just the Kernel and technically don't have anything to do with the Version Release.

For example, one may have to upgrade from msDOS 6 to msDOS 7 in order to upgrade WinDOZE 3.0 to 3.11, because the older DOX 6 didn't have the instruction sets required for the WinDoze upgrade.

Nonetheless, DOS was DOS and Winders is Winders, a program runnin on DOS.

Isn't 8.04 running ON Kernels 24-19 or the latest crashed kernel 24-21?
And if you want to use 8.10 you will need to upgrade the Kernel to 27 so it can see the features of 8.10 that 24 couldn't see?

Just curious myself about this is all!

I thought the Kernel WAS the OS and the Distro WAS the Programs that ran on it.  

EG:  Running Winders 3.11 on msDOS 7.(current Mickey$oft release)
OR Running Ubuntu 8.04 ON Linux 2.6.24-(current Debian release)
Exception:  Winders is both the OS & GUI rolled into one, but it still runs on msDOS.  Whereas Ubuntu has a choice of GUI's or even none at all.

Am I seeing that ALL WRONG as usual?????

TTUL
Gary

---

### Post by cariboo on 2008-11-08
THe operating system is Linux, the distribution is the kernel and the rest of the files. The kernel number doesn't have anything to do with the distribution version number. Yours seesm to be broken if you are still running the 2.6.19 kernel, instead of the 2.6.27 kernel. Some of the new features will not work, like the new video drivers.

Jim

---

### Post by Kellemora on 2008-11-08
Hi Cariboo

I rolled back to 19 last night because the new 21 kernel upgrade caused an area wide network crash, brought down all 8 computers here.
I was up all night and spent most of today trying to get things up and running again for the Monday morning workday.  I only moved back up to 21 about an hour ago to see if I could get it stable enough to trust.
So instead of spending my weekend relaxing, I'm in the office doing work to see if it will hold up.  Probably be here half a day tomorrow too.
I learned the hard way, HOLD all upgrades until Friday night after we close the doors.

I'm using the Hardy 8.04 LTS Distro, probably won't even look at 8.10 and wait for the next LTS Distro to be released.
Our LAN is hardwired, more secure and a whole lot less problems.

Are you sure about the Distro being the Kernel?????
I thought Linux Torvalds developed the Unix like Kernel just so a PC could act like Unix.  If the Distro is the Kernel, then there is not much of Linux left in it anymore.  Isn't it the Kernel that interfaces with the CPU?????

I studied it not to long ago, but I don't retain that technical stuff too long in my olde age, hi hi.

TTUL
Gary

---

### Post by ad_267 on 2008-11-08
The kernel is how applications interface with the computer hardware and controls all the computer resources. Ubuntu 8.10 comes with the 2.6.27 kernel and like cariboo907 said, some of the other packages such as video drivers depend on features in the new kernel.

The distribution is really the set of packages that come installed and the packages and versions available from the repositories, including the kernel. The operating system isn't just the kernel, it's also all the other things like the gui, package management and applications. Different Linux distributions use different versions of the linux kernel configured in different ways.

---

### Post by jdrodrig on 2008-11-09
Background: I upgraded to 8.10 but to check some issues, I re-booted and picked 8.04 from the grub menu.

To make it a tiny bit more confusing; after a couple of hours to be running 8.04 (selected from the grub menu) the auto-update showed me that severals updates were available, including kernel 27...I said yes and after a few minutes, everything seemed ok, I rebooted but if I type uname -r I am still under the kernel 19

why is this? what drives the auto-update feature? the distro version (lsb_release)? for instance, in this case did the system though I was running 8.10 and realizing I was under kernel 19 sent the update to 27, even tought the 27 was already installed in my system? can I run kernel 27 and still be labeled 8.04?

---

### Post by Kellemora on 2008-11-09
Hi AD

I'll cut this real short, since it appears I've hijacked anothers thread in the process.

I think we are saying the same thing, just using different terminology to do so.  A lot of the terminology has changed over the years also.  A COMPLETE device assembled to make a monitor was often called a CRT, yet the CRT is just ONE COMPONENT in the whole assembly that makes up a Monitor.  CRT stands for Cathode Ray Tube (The picture tube itself).  One could have just as easily called a monitor a Flyback or a Width Coil and it could have taken hold, even though it was the wrong terminology for the completed Device.

We always used CPU (which is the processor only) for the entire PC box.  But as people became more refined, using the wrong terminology suddenly reared it's ugly head, so to speak.
When somebody TODAY asks what CPU you have, you don't say Oh, I have a Compaq, HP or Dell, you NAME the CPU as Intel or AMD.

But, I don't think we have moved along for enough to distinguish the software yet and still call the ENTIRETY of the software either OS or installed programs.  Although some of it is broken down into Drivers and Programs.

A computer is actually what?
The internal hardware, the motherboard carrying the CPU and the BIOS which handle the Boot devices and first stage memory.

Next you have the Kernel and Shell (user interface)
The Kernel is what actually handles all the system hardware, both internal and external, the pointers and memory blocks.
It deals directly with the Processor and handles memory, filesystem and drivers, the sockets.  In other words, it's the IO part of the computers operational software.
It just hangs around looking for an an executable to be tossed it's way, then like a traffic cop, virtually handles everything in the form of IO calls.

It is the Operating System of the computer!  In this case LINUX.

Of course a computer is useless without having something to do!
So programs are written to give the computer something to do.

Programs are the Executables the Kernel is looking for!

But something needs to control all these programs and make them all work together and be moderately easy to use.  For most of us, this comes in the form of a GUI.   Such as the X-window system and it's adornments, eg Gnome.
Certain basic programming tools are included along with the user interface, such as word processing, audio players, video players, etc.  
Together those components are also termed as being the OS or Operating System.
Technically, since Linux is the Operating System, the user interface should be called by something else.

I think Mickey$oft is who got started out on the wrong foot here by calling their "Disk Operating System" DOS as the Operating System of the computer, and it's stuck ever since and was carried on through Windows.  Which should have been called something other than Operating System!

Then to finish off, we have the PROGRAMS that we as users run on the computer.  Nonetheless, everything from the Kernel to the user installed Program is Software, each designed to do something different.

If Ubuntu is the OS, then where does that leave Debian and LINUX?????

TTUL
Gary

---

### Post by ad_267 on 2008-11-09
Kellemora, most of what you say makes sense and it does get confusing with the way different terms can be used. Linux itself isn't an operating system though, it is only the operating system kernel. Most Linux distributions also use a lot of software from the GNU project to create an operating system, such as the GNU C library and the GNU core utilities. That's why many people call an operating system GNU/Linux rather than just Linux. I would say Ubuntu is the operating system, Debian is another operating system that Ubuntu is based on, and Linux is the kernel used by Ubuntu. Yes it is a bit different when you look at Windows, because Windows doesn't come packaged with so many different applications like Ubuntu does, so it's harder to draw the line as to which parts you call the operating system. You could say that everything that comes on the live CD is part of the Ubuntu operating system. If you only don't include all the extra software, then just Linux + GNU would be the operating system.

jdrodrig, if you upgraded to 8.10 you might still have the old 2.6.24 kernel used by Hardy as an option, but all of the other packages should be upgraded and you are using the Intrepid repositories. So even though you're running an older kernel the package manager knows you are running 8.10 based on what's in your /etc/apt/sources.list file. This tells the package manager where to look for updates. It would have looked at the latest kernel you had installed, not the one you were currently running, so it wouldn't download a kernel you already had.

---

