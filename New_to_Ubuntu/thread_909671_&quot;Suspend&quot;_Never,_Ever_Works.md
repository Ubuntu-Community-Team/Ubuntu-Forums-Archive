---
title: "&quot;Suspend&quot; Never, Ever Works"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by E.T.Smith on 2008-09-03
The halfway step for powering down the machine without shutting down entirely. This has *never* worked right for me across multiple editions of Ubuntu. Waking up the machine after suspension always results in a breakdown of desktop visual elements. In ub' 7, it was windows leaving traces after they closed or moved until the desktop was illegible. Now in Ub' 8, the problem manifests as a flicker in open pages of increasing frequency (and, when I restart, a kaleidoscope of colored typographical symbols that I haven't seen since the days of MS-DOS). Clearly, something about the Suspend process screws up either Ubuntu's or Gnome's ability to render graphics, but I have no idea what or how. Is this an uncommon problem?

---

### Post by tuxxy on 2008-09-03
I had issues too, disabling all power saving fixed it for me :lolflag:

---

### Post by mrsteveman1 on 2008-09-03
In the past, some of the graphics drivers required special settings and tricks to come back from suspend correctly.

For instance back last year it was still necessary to mess with the video bios and some other random things to get a 945gm chip to come back after suspend, otherwise it would just stay black.

Hard to say what would fix it tho. Whats the graphics chip?

---

### Post by werries on 2008-09-03
Major problems with linux support:
suspend/hibernate
wireless
some sound problems (damnit ALSA!)

We be working on it. =/
For now, workarounds must suffice.

---

### Post by solaceinsilence9 on 2008-09-03
ESPECIALLY when it comes to notebooks. Just curious, what kind of computer are you using? PC or notebook? Brand? Model?

---

### Post by Gannon8 on 2008-09-03
Both my Desktop and my laptop do not come out of suspend mode. The monitor "turns on" but does not show anything. I think most Linux people are experiencing this.

---

### Post by solaceinsilence9 on 2008-09-03
...the trade off for having a great OS! :D

---

### Post by Locutus_of_Borg on 2008-09-03
i can hibernate just fine

i used to be able to suspend and resume, but about thirty minutes after resuming from a suspend the desktop would lock up, the mouse would still move, but nothing else would work and i would have to resort to using the sysrq sequence to reboot, now i can suspend, resume, and immediately freeze, so i just hibernate.  boot/reboot times for hibernation from full working desktop to off is about 30 seconds, then from off to full working desktop is about 20 seconds.  the extra 10 seconds saved from suspend over hibernate is not really worth it to me

---

### Post by KableKiB on 2008-09-03
Seems to be working fine on my old piece of crap Compaq Presario X1000. I do get the flaky graphics, and it does take about 5 seconds to get out of suspend mode but it works fine once it does.

---

### Post by anewguy on 2008-09-04
Okay, let's start with some basic things first.

(1) laptop or desktop?

(2) how much main memory?

(3) when you installed Ubuntu, did you note what size it was making the swap partition?

(4) again, do lspci in a terminal window and post back here.

We'll try to go from there.  

Dave :)

---

### Post by cro.smiley on 2008-09-04
Hi, I have hp nx6110 and suspend is stuck with blank screen and blinking cursor in top left corner. I use ndiswrapper for broadcom wireless card so it could be a problem, but it worked well before a week or so.

Some basic things:
laptop, 1,5gb main memory, installed it yesterday and downloaded all updates, swap 2gb

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

free:
```

Mem:       1547300     575812     971488          0      33380     263108
-/+ buffers/cache:     279324    1267976
Swap:      2048248          0    2048248

```

---

### Post by anewguy on 2008-09-04
There are debates on this all over the net and these forums, but I will give you "safe" guidelines:

Disk space is cheap - so make your swap partition at least 2 times the size of your physical memory.  If you have 1 gig of memory, make swap at least 2 gig (there is additional overhead, so in reality 2.5 gig would be better).  I'm not sure exactly what suspend actually does internally, but I know if you try to hibernate it copies physical memory to swap before cycling down.  There is always overhead associated with it, but if your memory isn't full then 2 times should work for swap - 2.5 times would be better and more than enough.

For everyone reading this - remember this is for hibernate, not just normal usage.  Swap files normally would not need to be anywhere near that amount, but for hibernate it is best.

Also, search these forums for problems with wake from suspend and wake from hibernate - there are MANY posts.  Sometimes there is some tweaking involved with some files and settings to make it work.  Sometimes I don't think it ever does work.  Also, do a search on Yahoo! or Google for Linux wake from suspend problem or linux wake from hibernate problems.  There will be a LOT of returns, and no, a lot won't refer specifically to Ubuntu.  However, read the posts any way as sometimes you can find hints and clues as to what is going on and only need post here to ask the specifics for adapting that solution to your PC and Ubuntu.

Dave :)

---

