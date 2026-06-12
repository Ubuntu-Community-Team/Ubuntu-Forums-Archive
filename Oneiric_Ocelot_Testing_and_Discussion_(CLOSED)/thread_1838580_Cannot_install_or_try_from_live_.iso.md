---
title: "Cannot install or try from live .iso"
date: 2011-09-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Derek Karpinski on 2011-09-03
I'm using the daily Sept 3 iso.  The md5sums match.  I've tried from a USB stick using the startup disk creator, the dd command, and tried installing in Virtualbox.  In all cases, I get the same result.  An install window that won't let me 'Try Ubuntu' or 'Intstall Ubuntu'.

I can get to the console from this screen.  It isn't locked up, I just can't continue.

Any help?

---

### Post by lucazade on 2011-09-04
Try to use beta1 iso, probably ubiquity installer was broken in that daily image.

---

### Post by jerrylamos on 2011-09-04
> **lucazade said:**
> Try to use beta1 iso, probably ubiquity installer was broken in that daily image.

Beta 1 is way way way downlevel.  First thing after doing a Beta 1 install is boot in recovery mode and do "fix broken packages" after enabling internet with root prompt "dhclient".  Lots of updates.

As is Beta 1 invariably has some crashes which Apport can't report complaining about tons of downlevel packages.

I've done a couple installs from Sept 02 O.K.

My last install was Lubuntu Oneiric. Ubiquity crashed and crashed and crashed, I selected "ignore" and install went fine.

Jerry

---

### Post by kansasnoob on 2011-09-04
Did you check the integrity of the CD?

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Note: you must press a key as soon as the CD starts to boot in order to see the full menu. You have a bout 3 seconds to press a key.

---

### Post by jerrylamos on 2011-09-04
I've had various problems with "isohybrid" and "startup disk creator" (what a mess, it keeps losing the .iso and then complains about the USB format etc.  Hassle.)   and of course Alpha images don't fit on a CD.

My solution is to format a USB stick to ext3

I use zsync to update the .iso's 

I usually do sudo chmod 666 *.iso since the image downloads with just root permissions.

Simply copy the Oneiric.iso onto the USB. 

I always have other Ubuntu partitions running so I do:

df to make sure what /dev/sdx the USB is, in this example sdc1 as hd3,1

sudo gedit /etc/grub.d/40_custom then add this to the file:

menuentry "Ocelot sdc1 USB" {
set isofile="/oneiric-desktop-i386.iso"
loopback loop (hd3,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

sudo update-grub

If necessary do
sudo grub-install /dev/sda

then reboot and choose the new Grub2 entry.

Try running the Live, if you wish, do an install.  

Since putting the .iao onto the USB is a simple copy, updating to the next day's .iso is just a copy to the USB no messy isohybrid or startup disk creator

Cheers good luck,

Jerry

p.s. Used to be I could put the .iso onto a hard drive, example to a folder on sda1, however Oneiric Alpha & Beta have been pretty erratic on booting but did allow some Live testing.  Install is then problematical unless you have a 2nd hard drive.

---

### Post by mc4man on 2011-09-04
Today's daily (04/09) may boot to a blank welcome screen. If so then closing the installer window should then allow the live session to load - may take 20 sec's or so.
(just did so here & was able to use live session

---

### Post by sammiev on 2011-09-04
> **mc4man said:**
> Today's daily (04/09) may boot to a blank welcome screen. If so then closing the installer window should then allow the live session to load - may take 20 sec's or so.
(just did so here & was able to use live session

Had the same thing happen on Friday and the above worked for me then. :)

---

