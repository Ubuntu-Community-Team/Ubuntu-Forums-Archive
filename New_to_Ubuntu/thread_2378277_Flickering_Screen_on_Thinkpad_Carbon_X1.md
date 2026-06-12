---
title: "Flickering Screen on Thinkpad Carbon X1"
date: 2017-11-21
forum: New to Ubuntu
---

### Post by heaheahea on 2017-11-21
Hello folks, I am fresh to Linux and overwhelmed at some of the issues I'm encountering, namely, needing to zoom all text (I'm not THAT OLD!) and most recently, a flickering screen issue. BUT I'M NOT GIVING UP! I'm breaking up with Mac and Windows can eat a brick! 

I found an [old thread]("https://ubuntuforums.org/showthread.php?t=2061180") where the flickering issue was resolved for someone after providing the command results for specs and whatnot. It appears the graphics card needed configuration? Here are my results, can you help me? If you can link me to a particularly useful thread re: the small fonts that would also be wonderful, there are a lot of results out there, talking about add-ons and extensions and whatall...

Thank you kindly!
hea

   hea@hea-ThinkPad-X1-Carbon-4th:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"
hea@hea-ThinkPad-X1-Carbon-4th:~$ uname -a
Linux hea-ThinkPad-X1-Carbon-4th 4.13.0-17-generic #20-Ubuntu SMP Mon Nov 6 10:04:08 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
hea@hea-ThinkPad-X1-Carbon-4th:~$ lspci -nnk | grep -ia2 vga
    Subsystem: Lenovo Skylake Host Bridge/DRAM Registers [17aa:2238]
    Kernel driver in use: skl_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 520 [8086:1916] (rev 07)
    Subsystem: Lenovo HD Graphics 520 [17aa:2238]
    Kernel driver in use: i915
--
00:08.0 System peripheral [0880]: Intel Corporation Skylake Gaussian Mixture Model [8086:1911]
    Subsystem: Lenovo Skylake Gaussian Mixture Model [17aa:2238]
00:13.0 Non-VGA unclassified device [0000]: Intel Corporation Device [8086:9d35] (rev 21)
    Subsystem: Lenovo Device [17aa:2238]
    Kernel driver in use: intel_ish_ipc
hea@hea-ThinkPad-X1-Carbon-4th:~$ env | grep DESK
DESKTOP_AUTOSTART_ID=10bdeb664d16a10eda151130337117897500000010580008
DESKTOP_SESSION=ubuntu
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=ubuntu:GNOME
GNOME_DESKTOP_SESSION_ID=this-is-deprecated

---

### Post by mörgæs on 2017-11-28
Hi, welcome to the fora.

The thread to which you link deals with Nvidia graphics. It won't help your Intel gear.

First I suggest that you try some alternative distros in a live boot to narrow down the problem. Does, say Xubuntu 17.04 behave differently?

---

