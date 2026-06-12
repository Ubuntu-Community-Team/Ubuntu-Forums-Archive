---
title: "Ubuntu freezing for periods every so often?"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by ian49 on 2014-07-13
It's a little hard to describe the problem I'm struggling to solve and not sure where to start in terms of trying to identify the likely cause but I'm hoping someone might be able to offer some suggestions.

Basically, I had previously run Ubuntu 10.04 as wubi on my laptop without any problems whatsoever for a number of years. I recently got a new HD for my laptop and thought this would be a good time to install the latest version of Ubuntu (14.04) and get rid of Windows altogether.

Anyway, I've successfully installed 14.04 and implemented gnome flashback and docky in order to avoid Unity.

Everything appears to be running OK except... after a certain period of time whatever software I'm using becomes unresponsive for a period of time.. hard to say how long for as it appears to vary but sometimes it's maybe in excess of 30 seconds, others maybe just a few seconds. For example, I could be entering some values in Calc and then I'm locked out and can't input anything until the block clears. Other times I might click Places and select the Documents folder and then again nothing happens for about 20 seconds. Sometimes the active window greys out but not always. Since I use my laptop for business purposes for several hours at a stretch this is making my life very difficult indeed.

I've no idea what to do in order to diagnose what the problem might be... I should also mention that the laptop has 2GB of RAM and a dual processor and at the times these lock-outs or freezes occur both memory and processor activity seem fine. So, all in all I'm totally baffled. Can anyone help?

---

### Post by mooreted on 2014-07-13
If the mouse cursor still moves when the application freezes, then it is related to graphics. Probably a problem with compositing (compiz).

From a command prompt look at the output of the command "dmesg". There may be a clue in there.

If you have AMD or Nvidia make sure you install the proprietary video driver for your system.

When the computer freezes do the following:

1. CTRL+ALT+F1
2.Login as user.
3. sudo pkill compiz-decorator
4. pkill -9 compiz

And see if that unfreezes it.

---

### Post by ian49 on 2014-07-13
> **mooreted said:**
> If the mouse cursor still moves when the application freezes, then it is related to graphics. Probably a problem with compositing (compiz).

From a command prompt look at the output of the command "dmesg". There may be a clue in there.

If you have AMD or Nvidia make sure you install the proprietary video driver for your system.

When the computer freezes do the following:

1. CTRL+ALT+F1
2.Login as user.
3. sudo pkill compiz-decorator
4. pkill -9 compiz

And see if that unfreezes it.

Thanks for responding.

 It looks like both CPU and graphics are Intel. The mouse moves just fine during the periods when I'm unable to type anything.

Assuming that the problem is with compiz is there anything I can do to fix it?

I also ran dmesg as suggested but wasn't sure what output to expect... I got a whole mass of info, much of which looked similar to:

[138590.694421] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[138641.893573] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled


EDIT:  I've switched compositing on for Metacity and going to try that for a while to see if that gets rid of the problem.

---

### Post by mooreted on 2014-07-13
Well, there is no special driver for Intel graphics. It could be that your laptop doesn't have the power to run compositing desktops like Gnome, Unity and KDE. You might have to switch to something like Xfce. Fortunately it's really easy to do.

Please post the output of the command: lspci

---

### Post by ian49 on 2014-07-13
> **mooreted said:**
> Well, there is no special driver for Intel graphics. It could be that your laptop doesn't have the power to run compositing desktops like Gnome, Unity and KDE. You might have to switch to something like Xfce. Fortunately it's really easy to do.

Please post the output of the command: lspci

It might be too early to say but so far the problem hasn't reappeared while running Metacity so I'm keeping my fingers crossed.

Here is the output from lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)

---

### Post by mooreted on 2014-07-13
I found a post about Intel graphics and a few suggestions about installing the Intel graphics drivers that may help:

[http://askubuntu.com/questions/454623/should-i-install-intel-graphics-installer-for-intel-mobile-gm965-gl960](http://askubuntu.com/questions/454623/should-i-install-intel-graphics-installer-for-intel-mobile-gm965-gl960)

---

### Post by ian49 on 2014-07-13
> **mooreted said:**
> I found a post about Intel graphics and a few suggestions about installing the Intel graphics drivers that may help:

[http://askubuntu.com/questions/454623/should-i-install-intel-graphics-installer-for-intel-mobile-gm965-gl960](http://askubuntu.com/questions/454623/should-i-install-intel-graphics-installer-for-intel-mobile-gm965-gl960)

Thanks for that.

---

### Post by vasa1 on 2014-07-13
Are this question and the question [you asked about LibreOffice]("http://ubuntuforums.org/showthread.php?t=2233312") related? BTW, you haven't responded to posts in that thread.

---

### Post by ian49 on 2014-07-14
> **vasa1 said:**
> Are this question and the question [you asked about LibreOffice]("http://ubuntuforums.org/showthread.php?t=2233312") related? BTW, you haven't responded to posts in that thread.

Well, initially I only noticed the problem when I was using LibreOffice but that turned out to be because I spend most of my time using it. Today, I realised that the problem was a general one and that's when I posted the new thread here. It does seem, as suggested earlier in the thread, that compiz was the source of the problem. I switched to metacity a short while ago and at the moment it does look like the problem is fixed as I've yet to have any lock ups. Will go take a look at the other thread now.

---

### Post by mooreted on 2014-07-14
That is awesome, next time someone has a Compiz problem, I will suggest that. Good job.

---

### Post by didier5 on 2014-09-29
Any news on this subject ?

I'm using Lubuntu 14.04.1 - AMD Athlon(tm) 64 Processor 3200+ - 1Go Ram.

Calc sheet is by far my main tool. Unfortunately, the slowest application.
And I can't swith like that to Gnumeric.

A good test to reproduce this problem.  On a small LibreOffice file, select all cells,
then slowness starts. Xorg takes all the CPU ressource.

Anti alias, selected or not,  has no effect on performance.

---

