---
title: "iPod format question"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by tech-quilla on 2008-05-19
Good day all.

Very new to Linux but so far Ubuntu has actually been easier to work with than I expected. Recently my Mac iBook died, So my main computer has become a Toshiba Satellite 105 running Ubuntu 8.05. Happily I seem to be able to do most anything I was able to do on my Mac... Except...

I have a iPod question.  

Question. In order to sync my iPod using either Rythembox or gtkpod, does my first gen Nano need to be formated as a Windows unit? Right now it is in Mac format. If possible I would like to keep it as it is since there is music loaded on it and without a Mac I have now way of loading iTumes Music store purchases. I would like to be able to load and remove podcasts from the Nano.

With both application the iPod does mount and I can see every thing on it. Using Rythembox I can start to play music or podcasts but after a bit both applications just quit.
When I try to transfer a podcast in Rythembox I get a dialog"

[INDENT]Could not open file "/media/Fud's iPod/iPod_Control/Music/f33/TWiT0143H.mp3" for writing[/INDENT] 

Using gtkpod the dialog reads"

[INDENT]Transfer of 'TWiT 142: I Like Big Pockets' failed. Error opening '/media/Fud’s iPod/iPod_Control/Music/F46/gtkpod817820.mp3' for writing (Read-only file system).[/INDENT]

Thanks In Advance

---

### Post by GCoffee on 2008-05-19
I belive, though not certain, that the ipod has a linux format does it not?

Hope that helps,
GCoffee.

---

### Post by twright on 2008-05-19
if you search synaptic for hfs you might be able to find the packages needed

---

### Post by rockerphil on 2008-05-19
i know this sounds odd, but the way i got my iPod to work for me was to connect it through the USB port and then rebooting, afterwards it mounts as a writable part of your file system. hope this helps

---

### Post by tech-quilla on 2008-05-22
From what I'm seeing with the dialogs it looks like the iPod does not have write permissions enabled. It will mount to the desktop and also shows up in Rythembox. But if I try and drag a non DRM'd podcast onto it or use Rythembox or gtkpod i'm being told it's read only acccess.:confused: 

 Makes sense since it was tied to iTunes on my Mac. 

So does anyone know how to set permissions on an iPod with out re formatting it?

---

### Post by naknak987 on 2008-10-22
Ipods set up on a mac are formated different then windows. I can't remember how macs format them but windows will format the Ipod as fat. From What I've heard, linux will only sync to a fat Ipod.
My Ipods Fatter then yours. :lolflag:

---

### Post by o.besner on 2008-10-22
Songs that you purchase on iTunes store can only be used in iTunes. Nothing that is not Apple will not work. So yep, you'd better not format that iPod for a while. I don't know if you can re-download a song you've already purchased ? Never used Apple store...

When you say "Mac formatted", what you're looking for is called HFS. Try installing the two packages hfsplus and hfsutils. You can find them with Synaptic Package Manager. Or just open a console and type :

*sudo apt-get install hfsplus hfsutils*

Then maybe it'll work. I know no one that is using a Mac, so can't help ya. What would you do on Windows ? Maybe I can work from there.

---

### Post by No-Neck on 2008-10-22
This thread is pretty old now but it is certainly possible to use HFS+ iPods on Linux, do as o.besner said and then remount the iPod from the command line, making sure your user has privilidges over the mount point. :)

---

### Post by NickD-NLUG on 2008-11-07
> **No-Neck said:**
> This thread is pretty old now but it is certainly possible to use HFS+ iPods on Linux, do as o.besner said and then remount the iPod from the command line, making sure your user has privilidges over the mount point. :)

I've got a similar issue, except mounting my iPod from the command line, as root, still results in a "read only" file system.

Any ideas on how I can begin to troubleshoot this?  I've tried rebooting my system with the iPod plugged in, but without success.  Fdisk doesn't recognise any of the partitions on the system, but if I manually mount the third I can see the files on there... I just can't write any more to it.

Any ideas welcome.

---

