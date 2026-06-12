---
title: "POLL: Broadcom Wifi in Hardy Heron 8.04"
date: 2008-07-20
forum: Recurring Discussions
---

### Post by zoubidoo on 2008-07-20
I still don't have my Broadcom card working in Hardy although it worked fine in Feisty.

What are your experiences with Broadcom Wifi cards?

 - is it working?
 - is it working well?
 - is it painless to get going?

---

### Post by JagDragon on 2008-07-20
I have a Linksys WPC54G v1.2, using the Broadcom 4306 card. In the past I have used ndiswrapper, but I prefer to not use it so I hunted for other drivers, and finally found one. The b43. Homepage: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Here is a tutorial on getting your wireless card working on 8.04. All (or most) of the following will be done in a terminal, so have one open!

**Identify your card**
```
lspci | grep Network
```
Which should print out something along the lines of
```
Network controller: Broadcom Corporation BCM4306
```
Look for that number (in this case 4306) and go to the [supported hardware]("http://linuxwireless.org/en/users/Drivers/b43#supported") section of the driver page and see if your chipset is there. If it is, continue. If not, find out how to use ndiswrapper.

**Download the Firmware**
Next, you need to install b43-fwcutter and the firmware for the driver. The b43 module is actually already in the kernel, it just requires the firmware.

**For those with a working internet connection**
```
sudo apt-get install b43-fwcutter
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
```
Select "No" when it asks you to automatically download the firmware. This has never worked for me.

**For those without a working internet connection**
You will need to get the files from another computer and transfer them onto your computer. Files needed:
- [b43-fwcutter.deb]("http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb")
- [broadcom-wl-4.80.53.0.tar.bz2]("http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2")

After they are downloaded, transfer them onto your computer via CD or USB drive. To install b43-fwcutter:
```
sudo dpkg -i b43-fwcutter.deb
```
Select "No" when it asks you to automatically download the firmware. You have no connection to the internet.

**Finish the install**
Now that you have b43-fwcutter installed, and have broadcom-wl-4.80.53.0.tar.bz2 in your current directory, we can finish the install.
```

tar -xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo b43-fwcutter -w /lib/firmware wl_apsta.o

```
And that is it! Close the terminal, reboot your system, and enjoy using your Broadcom card!

I'm willing to troubleshoot if anyone has any questions/problems.

---

### Post by zoubidoo on 2008-07-20
@JagDragon

Thanks for the tutorial JagDragon.  I'm glad it was painless for you.  

Perhaps we could start a new thread for each card and keep this thread on the overall experience.

Cheers,
Z.

---

### Post by Kevbert on 2008-07-20
I was surprised how well it worked for me after having problems in Gutsy.  A new install of Hardy Ubuntu and my Broadcom BCM4306 installed with no problems.  Kubuntu Hardy did give minor problems.  In both cases I had a wired LAN connected during install.

---

### Post by Sef on 2008-07-20
Moved to recurring discussions.

---

### Post by natrone on 2008-08-13
I wish this would work for me.  What if your card requires b43legacy.  I repeated your instructions verbatim with absolutely no result.

---

### Post by Ozor Mox on 2008-08-13
It works fine with no effort required on my part, but I'm 95% sure that it is the cause of the occasional random total lockup of my laptop. That is, it locks up so hard that the clock stops moving, Ctrl+Alt+Backspace or Ctrl+Alt+F1 do nothing, Alt+SysRq+REISUB does nothing, and I can't even switch Caps Lock or Num Lock on and off! The last entry in the syslog seems to be related to the wireless card, something like "PHY transmission error". Anyone else have this trouble?

---

### Post by willca on 2008-08-14
Got the same problem. Wireless works flawlessly and then all of a sudden a hard lockup. No way out but to press the power button and reboot.

my lspci output is this.

02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

Most of the times I notice the lockup when I am downloading huge files via firefox. For a while I thought it was the browser or even powernowd (coz it seem to be always happening when I am not in AC in my old dell laptop). But did see the same b43-phy0 message prior to the lockup in kern.log.

So now I am trying to update my kernel as suggested by this link otherwise if things still go south i am back to using ndiswrapper which btw have worked wonderfully in passed ubuntu versions I used.

[http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966)

---

### Post by willca on 2008-08-15
Ended using ndiswrapper. Getting 54mbs and good signal like with firmware via fwcutter. But its not locking up things though.

---

### Post by Bigwookie on 2008-09-26
Hi

I'm new to Linux so please keep any answers simple :), also noticed this thread is a little old so grateful for any help.

I've followed all the steps in the tutorial and I'm still not able to get my wireless working.

I've checked and I have a linksys card with a Broadcom BCM 4306 rev 03 chip

I've also run sudo lshw -C network and the output includes the line 
configuration: driver=b43-pci-bridge latency=32 module=ssb

I thought this indicated that the driver and firmware were installed, although I would welcome someone to correct me on this.

I have restarted the computer, but the Netwotrk Manager still doesn't seem able to connect, even when I disconnect the wired ethernet.

I can have a wired network connection if needed to install or download any software.

Thanks in advance for any help.

---

