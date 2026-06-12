---
title: "format a HD on a VERY old machine"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-11-03
Hi Community:

I have an old P4 and I want to format its hard disk.

That old P4 has a CD reader.... not a DVD reader.

I thought I could use a live CD of ubuntu, load it, and do the formating...

However, all new (and even 10.14) ISOs are larger than will fit on a 700Mb CD.

How can I format that hard disk??

Thanks!
Old Jimma from the soon to be sequestered financial cliff country

---

### Post by grahammechanical on 2012-11-03
Put the hard disk into the machine that is running 12.04.

---

### Post by The Cog on 2012-11-03
xubuntu 12.04 fitted on a CD.
It's probably worth keeping a copy of SystemRescue CD [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage) in your toolbox - that could format your disk too.

---

### Post by newb85 on 2012-11-03
All standard Ubuntu .isos prior to 12.10 [s]fit onto[/s] [color=blue]are burnable to[/color] a standard 700MB CD.

There is no such thing as Ubuntu 10.14 (nor could there be, as there are only twelve months in a year ;)).

---

### Post by GreatDanton on 2012-11-03
If you have an option I would go with live Usb.

---

### Post by dwb814 on 2012-11-03
> **Old Jimma said:**
> Hi Community:

I have an old P4 and I want to format its hard disk.

That old P4 has a CD reader.... not a DVD reader.

I thought I could use a live CD of ubuntu, load it, and do the formating...

However, all new (and even 10.14) ISOs are larger than will fit on a 700Mb CD.

How can I format that hard disk??

Thanks!
Old Jimma from the soon to be sequestered financial cliff country

If it has windows on it, and A floppy drive. You can download a self-extracting .exe to a floppy from [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm) then reboot and format from there.

---

### Post by mwl128340 on 2012-11-03
gparted also has an iso that is very useful for formatting and does fit onto a cd and loads quicker than a full version of ubuntu.

---

### Post by mwl128340 on 2012-11-03
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by HermanAB on 2012-11-03
You could use Knoppix.

---

### Post by newb85 on 2012-11-03
Okay, to recapitulate, the OP has been given several suggestions:

[list=1]
[*]Hook the HDD up to a machine with Ubuntu already installed.
[*]Create a Xubuntu Live CD.
[*]Create a SystemRescue CD.
[*]Create an Ubuntu Live CD older than 12.10.
[*]Create an Ubuntu Live USB.
[*]Create a bootable floppy disk.
[*]Create a Gparted Live CD.
[*]Create a Knoppix CD.
[/list]

All of these methods should work.  (Well, I can't vouch for the floppy method, as I haven't sat at a machine with a floppy drive in over three years.)  And we could create pages of more suggestions, but at this point, that's not really helpful.  The OP just needs to pick one and try it.

---

### Post by crispy_420 on 2012-11-04
I guess why do you want to format the disc, or what is your goal? 

Do you just want it wiped or you planning on an install?

---

### Post by black veils on 2012-11-04
ubuntu mini.iso [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by newb85 on 2012-11-04
> **black veils said:**
> ubuntu mini.iso [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Does mini.iso allow a Live session?  The OP wants to format the HDD, but never said anything about installing Ubuntu.

---

### Post by squakie on 2012-11-05
It would help to know how old "VERY old" is - we could be talking all the way back to rfm (?)- and that would probably mean a utility from the disk manufacturer to actually do the low-level format before you can do the rest.   It's been a LONG time, but we used to have to do that YEARS ago, and that usually meant a floppy, so you would need a floppy drive as well.  Supposedly the disks that came after rfm(?) did not require a low level format.   Don't know what you've got, so hard to give exact instructions.

---

### Post by newb85 on 2012-11-05
> **squakie said:**
> It would help to know how old "VERY old" is - we could be talking all the way back to rfm (?)- and that would probably mean a utility from the disk manufacturer to actually do the low-level format before you can do the rest.   It's been a LONG time, but we used to have to do that YEARS ago, and that usually meant a floppy, so you would need a floppy drive as well.  Supposedly the disks that came after rfm(?) did not require a low level format.   Don't know what you've got, so hard to give exact instructions.

Notwithstanding, the OP should still be able to boot from a Live media, at which point
```
sudo lshw -C disk
```
would give us the details about the issue you raised.

---

### Post by squakie on 2012-11-06
Not necessarily - the systems old enough to have a drive like that normally did not support booting from anything but floppy or hard disk - they wouldn't boot from a CD or USB.  I can't imagine someone having a  system that old, but it is a possibility.  Depending on your age, some of this may have been before your time - if so, you're lucky!  At the time, coming from a systems programming background and tech support on big iron, those little boxes we all have on our desktops were just a novelty, and we didn't mind the work you had to go through on them.  Thank goodness things have changed!  

Have a good one! ;)

---

