---
title: "Daily live copying to usb?"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-08-24
Hi all not sure where i read it, but is it not possible just to extract an 11.10 iso onto a usb stick and have it boot from it now?

---

### Post by fjgaude on 2011-08-24
Yes just dd the image to your USB, in this case was /dev/sdd. Change the /sdd to whatever yours might be.

```
sudo dd if=oneiric-desktop-amd64.iso of=/dev/sdd
```

Let us know how you do.

---

### Post by coffeecat on 2011-08-24
```
sudo dd if=/path/to/oneiric.iso of=/dev/sdX
```

Change sdX to whatever your usb stick is. Change oneiric.iso to correct ISO filename. You don't even have to reformat, erase, or do anything to the USB stick before you run the dd command.

---

### Post by VinDSL on 2011-08-25
Here's a mini HOWTO that I made, a while back:  [http://ubuntuforums.org/showpost.php?p=10945413&postcount=1](http://ubuntuforums.org/showpost.php?p=10945413&postcount=1)

---

### Post by ELD on 2011-08-25
It doesn't seem to recognise the command "if" ?

---

### Post by meborc on 2011-08-25
> **ELD said:**
> It doesn't seem to recognise the command "if" ?

```
if
``` is not the command... ```
dd
``` is the command, if is just an operator

check ```
man dd
```

---

### Post by ELD on 2011-08-25
Okay so i used the wrong terminology, the point still stands that it didn't recognise it.

Figured it out anyway, for the =

Doing it this way is a little unfriendly though, there is no progress notification, the terminal doesn't update like it would on say apt downloads saying % or anything. Could that be implemented?

---

### Post by coffeecat on 2011-08-25
> **ELD said:**
> Okay so i used the wrong terminology, the point still stands that it didn't recognise it.

If you left out the "dd" command the bash terminal would have interpreted a leading "if" as an if command in bash syntax and simply returned you to the prompt waiting for a "then" command.

> **ELD said:**
> Doing it this way is a little unfriendly though, there is no progress notification, the terminal doesn't update like it would on say apt downloads saying % or anything. Could that be implemented?

Talk to the upstream dd developers about it. People have been complaining about the lack of a verbose option in dd for years. Google for "dd verbose" and you'll find some workarounds - not very user-friendly though.

If you want a more friendly way of preparing a bootable USB stick from an Ubuntu ISO, use startup disk creator. It comes in the tin.

---

### Post by ELD on 2011-08-25
Well it didn't seem to work, sat for 10 minutes on a black screen, will try the usb creator.

---

### Post by meborc on 2011-08-25
you can always try unetbootin

that is what i use

---

### Post by cecilpierce on 2011-08-25
Have you tried 'unetbootin'?
It has a gui and always works for me when others failed.

In a terminal type:
sudo apt-get install unetbootin
then type: unetbootin

You don't have to use it, but take a look.

@meborc, you beat me to it !!!

---

### Post by ELD on 2011-08-25
Startup disk creator works fine for me first time, just did it and it's now booting, i will probably continue to use it until any hybrid issues are sorted :)

Edit > Saying that it's gone to a black screen again so maybe duff download or yesterdays daily wasn't working properly.

---

### Post by meborc on 2011-08-25
> **ELD said:**
> Edit > Saying that it's gone to a black screen again so maybe duff download or yesterdays daily wasn't working properly.

if you have an ATI card, you might need to add radeon.nomodeset=1 in your grub boot line

---

### Post by jerrylamos on 2011-08-25
> **meborc said:**
> if you have an ATI card, you might need to add radeon.nomodeset=1 in your grub boot line

My ati radeon xpress 200 on my fastest pc has all sorts of troubles with Oneiric especially but not limited to Unity-3D and Compiz.  Unity-2D a little better.  

On that pc I do an update, maybe a couple times if xorg died during the update, then run for a little while and report whatever bug showed up.

On this pc runs with uisuial flock of alpha bugs and lockups.  

ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI

Don't need any modeset commands.  Your results mayu vary...

Jerry

---

### Post by jerrylamos on 2011-08-25
On topic, I've tried "startup disk creator" and "unetbootin" and the hybrid boot dd thing.  Pretty cranky.

I just bring up gparted format the first partition of the USB at least 800 mb with ext3 (or ext2).  Do note if the USB is sdb or sdc or whatever.  Important.

Copy your .iso onto that partition.

Then on my running linux I have an entry like so.  Adjust the hd1,1 for sdb or hd2,1 for sdc.  Adjust the folder for the set isofile for wherever you coopied the .iso into.  Could just be /oneiric-desktop-i386.iso if it's in the root folder of the USB partition.

```

sudo gedit /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Ocelot sdb1 USB" {
set isofile="/boot/iso/oneiric-desktop-i386.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

```
then
```

save
exit
sudo update-grub

```

Then reboot you have a choice of booting your regular linux or the USB.

Do note, the above works on a hard drive as well, make a folder like /boot/iso copy the .iso into it.

Used to be, before Alpha 3, I could use any hard disk partition;  As of Alpha 3 it absolutely has to be on partition 1.

Now booted off the USB you can run live, if you like it, then install.  If you booted off a .iso on a hard drive, you can install but to a different hard drive or even a USB hard drive.

Good luck.  I'm having fun and learning linux.

Jerry

---

