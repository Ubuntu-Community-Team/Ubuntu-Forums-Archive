---
title: "New kernel for Ubuntu 20.04 LTS"
date: 2020-11-01
forum: New to Ubuntu
---

### Post by lillebowski on 2020-11-01
Hi, I'm wondering if there will be a kernel upgrade for Ubuntu 20.04 LTS as there is a new Ubuntu kernel in 20.10. Or could I get a new official version for 20.04 with long term support (not the mainline kernel)?

Additional info: My hardware is not fully supported by 20.04 but in Opensuse Tumbleweed everything works fine. I suspect that it's the new kernel but really want a long term support system and I know Ubuntu well and like it.

Thanks!!!

---

### Post by ActionParsnip on 2020-11-01
You could use the mainline kernel PPA

---

### Post by CatKiller on 2020-11-01
Kernels get backported to LTS releases through the Hardware Enablement (HWE) mechanism. After the interim releases have been out a while to test them, the LTS HWE stack will be upgraded to that version.

---

### Post by deadflowr on 2020-11-01
> Additional info: My hardware is not fully supported by 20.04 
What parts aren't supported?

---

### Post by lillebowski on 2020-11-01
Well I thought about it but everbody says it's very risky. I mentioned it at the end of the question. Thanks anyway.

---

### Post by grahammechanical on 2020-11-01
Ubuntu 20.04 is a Long Term support release and it will get newer Linux kernels during the support period. Ubuntu 20.04 may get the Linux 5.8 kernel of Ubuntu 20.10 but not for about six months. Ubuntu has what are called point releases every six months. Ubuntu 20.04 is now at its first point release Ubuntu 20.04.1. It is with these point releases releases that Long Term Support (LTS) versions get newer kernels.

You could run a Ubuntu 20.10 live session to see if it recognizes all the hardware. Interim versions like 20.10 are supported for 9 months. After which you will need to upgrade to 21.04 and then 21.10 and finally 22.04 to have the Long Term Support version that you desire. In the meantime, Ubuntu 20.04 will have received the 20.10 kernel and later kernels.

It might be better to seek assistance in fixing the hardware issues which might be related to missing drivers.

Regards

P.S. The difference between Opensuse and Ubuntu is that Opensuse is on a rolling release version. Whereas Ubuntu has a periodic release distribution method.

---

### Post by lillebowski on 2020-11-01
@ CatKiller: Alright, cool. Do you have any idea when that could be? How long does it take normally?

My previous answer was for ActionParsnip. Sorry, my first time here;)

---

### Post by lillebowski on 2020-11-01
@deadflowr: Apparently my AMD Ryzen5 4500U. No HDMI signal, no brightness control, I tried everything but in Opensuse everything works right from the start.

---

### Post by grahammechanical on 2020-11-01
If you want to experiment you could put in another install of 20.04 and install the mainline kernel on that. It is not wise to experiment with the main/working use installation.

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

Regards

---

### Post by lillebowski on 2020-11-01
@grahammechanical: Ha Thanks! You really know what you're talking about! Yeah I'll check the live version 20.10 then. Should be just what I want with upgrades. If the kernel fixes my problems, of course. There are a lot of people struggling with the new AMD Ryzens, and I tried many solutions but nothing worked. A few of them installed the mainline kernel and it fixed the problems, but like I said it seems too risky. Thanks again.

---

### Post by CatKiller on 2020-11-01
> **lillebowski said:**
> @ CatKiller: Alright, cool. Do you have any idea when that could be? How long does take normally?

I don't know for sure when it will happen. Previous LTSes have updated the HWE stack with the second point release, so 20.04.2 in this case.

As already mentioned (including by you) you can use the mainline repository if you want to try a newer kernel before then. There are also PPAs for newer versions of Mesa.

---

### Post by ajgreeny on 2020-11-01
There is already a 5.8.0- series of hwe kernels in the repos so you could try ```
sudo apt install linux-generic-hwe-20.04-edge
``` which will bring with it all the dependencies, which on my Xubuntu 20.04 would be installing the following.

linux-headers-generic-hwe-20.04-edge
linux-image-5.8.0-25-generic
linux-modules-extra-5.8.0-25-generic
linux-image-generic-hwe-20.04-edge
linux-generic-hwe-20.04-edge
linux-headers-5.8.0-25-generic
linux-hwe-5.8-headers-5.8.0-25
linux-modules-5.8.0-25-generic

However, if you have other problems they really should be overcome first, as **grahammechanical** says, or you may be chasing an answer that is simply not possible.

Did you install Ubuntu 20.04 from the original iso or did you wait until 20.04.1?  If users wait until 20.04.2 point version the system will automatically upgrade to the further hwe kernel versions as they are released; I do not think that happens automatically if you install 20.04.1 but I'm not totally certain about that.
If you manually install a linux-image-hwe with all the related packages I believe that will also be automatically upgraded as new versions become available but again I am not completely sure about that.

See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for some more details; a litttle outdated but still will give you more of a clue.

---

### Post by lillebowski on 2020-11-01
@ajgreeny: Nice! Thanks, I'll try to find more information about the long term support of these hwe packages, that's very new to me. I have the 20.04.1 version but Im not sure if I installed that version or if there was an update. But I learned a lot, I'm glad that I asked.

---

### Post by lillebowski on 2020-11-01
@CatKiller:Thanks. I didn't know what 'Mesa' is so I had to search first. Could be an easy fix... now I have to decide what to try first. :)

---

### Post by CatKiller on 2020-11-01
Essentially, when drawing things, applications will talk to Mesa, Mesa will talk with the kernel, and the kernel will talk with the hardware.

For the symptoms you're describing - ports not working - it's probably hardware enablement through the kernel that you need. For other symptoms - bugs or performance issues - newer versions of Mesa may have fixes.

If you install a newer kernel you'll still have the old one if the new one doesn't work: you can choose which kernel you want to boot into from the Grub menu.

---

### Post by CatKiller on 2020-11-01
> **lillebowski said:**
> Thanks, I'll try to find more information about the long term support of these hwe packages, that's very new to me.

The HWE stack gets full support over the lifetime of the LTS release. Which kernel is the HWE kernel will change with each point release; both the initial release kernel and the latest in the HWE stack are fully supported with backported bugfixes and security updates.

---

### Post by lillebowski on 2020-11-01
IT WORKS! I decided to use the command from ajgreeny (sudo apt install linux-generic-hwe-20.04-edge), it took around 1 minute to install. I did a reboot and now the HDMI-Port works and I can control the brightness. Everything else works as well, as fast as before. Big thanks to everyone, and thanks Catkiller for clarifying about the ports and for confirming that there will be a real support! You're awesome!


Edit: Two days later it's still all running well, no problems at all. My new kernel is version 5.8.0-25. I searched around and found out that this 'edge'-hwe-kernel is meant as a preview and might be a bit buggy. Just a little warning. Here is a quote from [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack:](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack:) 
[SIZE=2][FONT=arial]
"hwe-16.04-edge[/FONT][/SIZE][SIZE=2][FONT=arial]
This  represents the path that provides users early access to the upcoming HWE  Stack that is to be released next for the Ubuntu 16.04 LTS.  The aim is  to provide this early preview in order to allow users to test the  upcoming HWE Stack prior to the automatic upgrade taking place. (...) As mentioned, the kernel version provided by the  hwe-16.04-edge path will provide early access to the newer kernel  version up to ~6mo prior to the hwe-16.04 path receiving the same."[/FONT][/SIZE]

---

