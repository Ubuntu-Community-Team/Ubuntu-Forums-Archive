---
title: "Will Broadcom drivers be fixed for 11.10?"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MasterNetra on 2011-08-26
I was wondering if the broadcom drivers will be fixed for 11.10 sense they're broke in natty... at least for bcm4312. And does anyone know if the drivers broadcom Open-sourced support/can be used for bcm4312?

---

### Post by pferraro on 2011-08-26
> **MasterNetra said:**
> I was wondering if the broadcom drivers will be fixed for 11.10 sense they're broke in natty... at least for bcm4312. And does anyone know if the drivers broadcom Open-sourced support/can be used for bcm4312?

Do you have the right driver installed?  For the bcm4312, you need to use the special low-power version of the b43 driver.  Do this:
1. Remove any existing proprietary drivers.  This include the STA driver and any b43-based drivers.  Use the "Additional Drivers" tool to remove them.
2. Install the "firmware-b43-lpphy-installer" package.  If you're using Software Center, search for "b43" and install the package containing LP-PHY in the description.
3. Reboot.
4. Enjoy your wireless.

---

### Post by cariboo on 2011-08-26
There are so many different versions of the bcm4312 chipset, that you have to try all of them. My netbook with bcm4312 works well with the wl driver.

---

### Post by MasterNetra on 2011-08-26
> **pferraro said:**
> Do you have the right driver installed?  For the bcm4312, you need to use the special low-power version of the b43 driver.  Do this:
1. Remove any existing proprietary drivers.  This include the STA driver and any b43-based drivers.  Use the "Additional Drivers" tool to remove them.
2. Install the "firmware-b43-lpphy-installer" package.  If you're using Software Center, search for "b43" and install the package containing LP-PHY in the description.
3. Reboot.
4. Enjoy your wireless.

I'll try that if/when I try 11.04 again. While wireless takes some effort to get running its not the show stopper for me, the instability of Unity in 11.04 is. Random crashes, and logouts, and glitches in general added up to a unusable release for me. The mint linux version of it works fine, a occasional random crash/logout occurs but its a uncommon occurrence there.

But for now I'm using old reliable 10.10 . At for me its very stable and nearly glitchless. I suppose your mileage will very pending system of course.

> **cariboo907 said:**
> There are so many different versions of the bcm4312 chipset, that you have to try all of them. My netbook with bcm4312 works well with the wl driver.

I wish my bcm4312 version would work out of the box for Ubuntu...heres to someday hoping or to getting the funds for a new machine...

---

### Post by cariboo on 2011-08-26
> **MasterNetra said:**
> I'll try that if/when I try 11.04 again. While wireless takes some effort to get running its not the show stopper for me, the instability of Unity in 11.04 is. Random crashes, and logouts, and glitches in general added up to a unusable release for me. The mint linux version of it works fine, a occasional random crash/logout occurs but its a uncommon occurrence there.

But for now I'm using old reliable 10.10 . At for me its very stable and nearly glitchless. I suppose your mileage will very pending system of course.



I wish my bcm4312 version would work out of the box for Ubuntu...heres to someday hoping or to getting the funds for a new machine...

I'd suggest that if you are suffering crashes in both mint and natty, that you may have a hardware problem. I have natty on my media center pc, Atom 230, 1GiB ram,  Nvidia 6250LE, with XBMC running on top of it, and haven't had a crash since installation.

---

### Post by walt.smith1960 on 2011-08-26
> **cariboo907 said:**
> I'd suggest that if you are suffering crashes in both mint and natty, that you may have a hardware problem. I have natty on my media center pc, Atom 230, 1GiB ram,  Nvidia 6250LE, with XBMC running on top of it, and haven't had a crash since installation.
  I'll second what cariboo said.  My 11.04 install had some minor issues when first released and updates were many.   The last couple months at least it has been quite stable though I run it with Gnome Classic.

---

### Post by 3rdalbum on 2011-08-27
Ubuntu doesn't just happen through osmosis - if there's an issue that you've encountered, you need to let them know.

Download the 11.10 daily build and run it as a live CD. Check if your Broadcom chip works properly. If it doesn't, submit a bug report using the 'ubuntu-bug' command.

If you can't get today's daily build then get the absolute latest version you can.

If at all possible, install Ubuntu 11.10 in alpha (it's reasonably stable for now, it won't eat your cat) and keep it up-to-date so you can provide information to developers about whether any updates have fixed the driver for you.

---

### Post by MasterNetra on 2011-08-27
> **cariboo907 said:**
> I'd suggest that if you are suffering crashes in both mint and natty, that you may have a hardware problem. I have natty on my media center pc, Atom 230, 1GiB ram,  Nvidia 6250LE, with XBMC running on top of it, and haven't had a crash since installation.

No, no hardware problem, works perfectly fine Ubuntu 10.10 and windows.

---

### Post by cariboo on 2011-08-28
Just because Ubuntu works well running one version, doesn't mean a hardware problem won't show itself when running another version or OS. As an example, before I quit using ATI/AMD video cards, I had a 9200 that worked as well as it should running a Linux variant, but it would start acting up on Windows after only about 15 minutes of usage, eventually it stopped working completely no matter what OS I used.

---

### Post by MasterNetra on 2011-08-28
> **cariboo907 said:**
> Just because Ubuntu works well running one version, doesn't mean a hardware problem won't show itself when running another version or OS. As an example, before I quit using ATI/AMD video cards, I had a 9200 that worked as well as it should running a Linux variant, but it would start acting up on Windows after only about 15 minutes of usage, eventually it stopped working completely no matter what OS I used.

Well thats just it though it works fine in Windows XP, WIndows 7, Ubuntu 10.10 (and previous versions), even fedora, and opensuse. I find it unlikely it is a issue from the actual hardware end. Unity itself is clearly unstable in 11.04 in general. Mint Linux has it removed in its version and its a heck of a lot more stable then vanilla Ubuntu Natty, if it works fine for you great, but my hardware setup is among the many in which it is unstable on.

---

### Post by cariboo on 2011-08-28
This starting to get way off topic, but to prove to yourself whether it is Unity that is a problem on your hardware, why not install one of the other desktop environments, like LXDE or XCFE on top of Natty and see if the problems persist.

---

### Post by MasterNetra on 2011-08-28
> **cariboo907 said:**
> This starting to get way off topic, but to prove to yourself whether it is Unity that is a problem on your hardware, why not install one of the other desktop environments, like LXDE or XCFE on top of Natty and see if the problems persist.

Because Mint Linux 11 is Natty without Unity and trying it without Unity entirely demonstrates this far more effectively sense their is nothing of Unity still on the system to possible corrupt the test. The few crashes I had on Mint Linux 11 where when I was on the internet and I suspect it was from the bcmwl-kernal-source or dkms as both were 10.10's version, otherwise Mint Linux 11 is stable as a rock for me, with the exception of a few freezes with the laptop closed, which were, after some testing, come to find out occur when the system turns off the screen while the laptop is closed. There is no question for me that it is Unity and not my hardware.

---

### Post by MasterNetra on 2011-08-28
> **pferraro said:**
> Do you have the right driver installed?  For the bcm4312, you need to use the special low-power version of the b43 driver.  Do this:
1. Remove any existing proprietary drivers.  This include the STA driver and any b43-based drivers.  Use the "Additional Drivers" tool to remove them.
2. Install the "firmware-b43-lpphy-installer" package.  If you're using Software Center, search for "b43" and install the package containing LP-PHY in the description.
3. Reboot.
4. Enjoy your wireless.
Little update, tried installing that package "firmware-b43-lpphy-installer" for Linux Mint 11 got a error.

*Update*: Tried the original firmware-b43-installer, and to my surprise it worked and just about instantly too..maybe I forgot to remove one of the other packages when I tried it last time. *Shrugs* Oh well. Have had network stability issues with b43 in the past though, but maybe it will be fine. Guess I will see as time progresses.

```

Selecting previously deselected package b43-fwcutter.
(Reading database ... 140133 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Selecting previously deselected package firmware-b43-lpphy-installer.
Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_4.174.64.19-5_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:1673
14e4:4312)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:1673
14e4:4312)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer

```

---

### Post by lucazade on 2011-08-28
> **MasterNetra said:**
> ```

Not supported card here (PCI id 14e4:1673
14e4:4312)!

```

your card is not supported by this driver/module

check your pciid with:
```
lspci -n
```

it will likely be: 
14e4: xxxx

---

### Post by MasterNetra on 2011-08-28
> **lucazade said:**
> your card is not supported by this driver/module

check your pciid with:
```
lspci -n
```

it will likely be: 
14e4: xxxx

As mentioned in the update I edited in the post the firmware-b43-installer worked this time. Apparently my card just can't use that other one.

Results:

```

00:00.0 0600: 8086:2a00 (rev 0c)
00:02.0 0300: 8086:2a02 (rev 0c)
00:02.1 0380: 8086:2a03 (rev 0c)
00:1a.0 0c03: 8086:2834 (rev 02)
00:1a.1 0c03: 8086:2835 (rev 02)
00:1a.7 0c03: 8086:283a (rev 02)
00:1b.0 0403: 8086:284b (rev 02)
00:1c.0 0604: 8086:283f (rev 02)
00:1c.1 0604: 8086:2841 (rev 02)
00:1c.5 0604: 8086:2849 (rev 02)
00:1d.0 0c03: 8086:2830 (rev 02)
00:1d.1 0c03: 8086:2831 (rev 02)
00:1d.2 0c03: 8086:2832 (rev 02)
00:1d.7 0c03: 8086:2836 (rev 02)
00:1e.0 0604: 8086:2448 (rev f2)
00:1f.0 0601: 8086:2815 (rev 02)
00:1f.1 0101: 8086:2850 (rev 02)
00:1f.2 0101: 8086:2828 (rev 02)
00:1f.3 0c05: 8086:283e (rev 02)
03:01.0 0607: 1217:7135 (rev 21)
03:01.4 0c00: 1217:00f7 (rev 02)
[B]09:00.0 0200: 14e4:1673 (rev 02)
0c:00.0 0280: 14e4:4312 (rev 01)[/B]

```

---

