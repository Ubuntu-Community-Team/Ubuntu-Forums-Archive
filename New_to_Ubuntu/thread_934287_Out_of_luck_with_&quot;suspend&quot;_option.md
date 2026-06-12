---
title: "Out of luck with &quot;suspend&quot; option ?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by faron45 on 2008-09-30
Does anyone out there know how I can get my pc to suspend ? I've installed both programs from synaptic package manager titled tuxonice-userui & suspend2-userui & neither seem to have worked for my suspend button.Am I just out of luck with the suspend option on my machine or ?? helllllllllppppp !!

---

### Post by uberdonkey5 on 2008-09-30
hate to say this, but on many laptops Ubuntu just has a major problem with suspend (including my own). I've tried many fixes without any luck also. I know this isn't a real solution, but I just use my power settings creatively (dimming monitor etc), or tuen off the computer.

---

### Post by faron45 on 2008-09-30
Uber....okay,one thing-I'm not using a laptop.And,the way I figure this is if Xubuntu installs a suspend key along with shutdown  etc shouldn't there be a way to make it work ?

---

### Post by KIAaze on 2008-09-30
I also never got suspend to work. :(
Hibernate works for me.
Didn't know about the packages you mentioned. Installing them now.

["Fix suspend and hibernate"]("http://brainstorm.ubuntu.com/idea/94/") is the most popular idea on ubuntu brainstorm...

_Here are some links to try to fix it:_
[http://devresources.linux-foundation.org/dev/robustmutexes/src/fusyn.hg/Documentation/power/video.txt](http://devresources.linux-foundation.org/dev/robustmutexes/src/fusyn.hg/Documentation/power/video.txt)

[http://linux.conf.au/programme/detail?TalkID=139](http://linux.conf.au/programme/detail?TalkID=139)
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

(I haven't tried everything yet, mostly because making changes / suspending / force shutdown /reboot is not a very fun activity...)

The comment by amitk (an Ubuntu dev) on brainstorm is also interesting:
> Thanks for all your comments. We strive to improve Ubuntu with every release and this feedback is important to us. Here are a few thoughts in getting suspend and hibernate to work:

1. It is very complex to get working because it depends on every peripheral driver on the system behaving correctly. And sometimes there are just buggy drivers.
2. The single biggest culprit preventing suspend/hibernate is the video driver.
3. With binary drivers (mainly ATI and Nvidia), we do not have _any_ control over making these drivers behave - so users are left to choose between better 3D support or hibernate.
4. Suspend2 suffers from lack of support upstream (Linus') tree. Coupled with the fact that the patch is very intrusive, it makes maintenance of the patch harder for Ubuntu.
5. As has been shown recently on LKML and various talks [1], both the swsusp and suspend2 (tuxonice) suffer from significant design drawbacks, so that they may never work correctly. There is new work ongoing on using a kexec-based approach that is being currently seen as the successor to the current design.
6. Using open drivers has a better chance of success. If that doesn't work, I urge you to file bugs on launchpad.net so that we might try to fix those.
7. References [2] and [3] are pointers to further debugging your suspend/hibernate issues. Help us in fixing your machines.

Regards,
Amit

[1] [http://linux.conf.au/programme/detail?TalkID=139](http://linux.conf.au/programme/detail?TalkID=139)
[2] [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
[3] [https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

---

### Post by KIAaze on 2008-09-30
...and just in case somebody has the same PC as you and got suspend to work, you should also post your PC specs (including graphics card).

Unlikely, but you never know. ;)

---

### Post by faron45 on 2008-09-30
KIAaze-If could you tell me just exactly how to go about finding & posting those pc specs your talking about,I will do so .And thanks VERY much for all the above info.I'll take a good hard look at all that in a bit.Right now I'm watching Predator 2 with my woman.Heh,heh.

---

### Post by phidia on 2008-09-30
You can get your computer specs by searching your make and model or open a terminal and enter > sudo lshw

BTW even though I prefer ubuntu opensuse is easier to get suspend working in on my HP Pavilion dv6707us. No matter what I've tried with Ubuntu-and I've tried a lot-resume from suspend will not work correctly.

---

### Post by KIAaze on 2008-09-30
Well, I just meant something like this (my specs):
Compaq Presario 2500 (written on PC)
ATI Radeon IGP 345M with 64 MB shared video memory
448 MB RAM (512-64)
Intel(R) Pentium(R) 4 CPU 2.40GHz

_To get the video card name:_
```
lspci | grep VGA

```

_To get the video card RAM:_
```
grep -i ram /var/log/Xorg.0.log; grep -i mem /var/log/Xorg.0.log

```

_To get the RAM size:_
```
grep MemTotal /proc/meminfo
free
dmesg | grep Memory

```
(The last one shows the real RAM size, while the others show the (RAM size) - (space used by kernel).)

_To get the CPU info:_
```
grep 'model name' /proc/cpuinfo
```

_To get the full system info:_
```
lshal
sudo lshw
lspci -vvnn

```
(some info may be redundant and I'm not sure what info lshal gives, but it looks like hardware related stuff)

There are also some great graphical apps giving system info:
```
sudo apt-get install hardinfo
```
It allows you to generate an HTML page with your system info.

Here's another one:
[http://taufanlubis.wordpress.com/2007/10/09/check-your-hardware-information-using-hwinfo-in-ubuntu/](http://taufanlubis.wordpress.com/2007/10/09/check-your-hardware-information-using-hwinfo-in-ubuntu/)

The standard Ubuntu way:
[http://linuxtnt.wordpress.com/2007/08/18/ubuntu-hardware-information/](http://linuxtnt.wordpress.com/2007/08/18/ubuntu-hardware-information/)

---

### Post by faron45 on 2008-09-30
phidia-thanks.

KIAaze-00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)

(==) intel(0): Depth 16, (==) framebuffer bpp 16
(--) intel(0): Linear framebuffer at 0xE8000000
(==) intel(0): Will alloc AGP framebuffer: 24576 kByte
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): [drm] framebuffer handle = 0xe8000000
(II) Initializing built-in extension XINERAMA
(II) Bus 0 non-prefetchable memory range:
(II) Bus 0 prefetchable memory range:
(II) Bus 1 non-prefetchable memory range:
(II) Bus 1 prefetchable memory range:
(--) PCI:*(0:1:0) Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller rev 3, Mem @ 0xe8000000/26, 0xeff80000/19
(II) intel(0): VESA VBE Total Mem: 1024 kB
(II) intel(0): I810CheckAvailableMemory: 206844k available
(II) intel(0): [agp] GART: no dcache memory found
(II) intel(0): [agp] Bound backbuffer memory
(II) intel(0): [agp] Bound depthbuffer memory
(II) intel(0): [agp] Bound System Texture Memory
(II) intel(0): Allocated Scratch Memory

MemTotal:       254592 kB
bobby@cybertek:~$ free
             total       used       free     shared    buffers     cached
Mem:        254592     239924      14668          0       2852      63032
-/+ buffers/cache:     174040      80552
Swap:       738948      72100     666848


This enough info ??
And,thanks.
This post will probably come in handy for me at a later time .

---

