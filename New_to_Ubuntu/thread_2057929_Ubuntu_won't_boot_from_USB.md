---
title: "Ubuntu won't boot from USB"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by Ryanicholls on 2012-09-14
Okay, so I'm using a Vaio notebook(PCG-21313M), Windows 7, with no CD drive. I've put Ubuntu 12.04.1 onto a usb stick using pendrivelinux.com, and tried to follow instructions on that site to boot Ubuntu from the usb, but when I cycle to 'External HDD' when rebooting it just flashes 'Operating System missing' and all I can do from this point is power off. I'm very new to this and have no clue how to go about correcting this.

---

### Post by critin on 2012-09-14
> **Ryanicholls said:**
> Okay, so I'm using a Vaio notebook(PCG-21313M), Windows 7, with no CD drive. I've put Ubuntu 12.04.1 onto a usb stick using pendrivelinux.com, and tried to follow instructions on that site to boot Ubuntu from the usb, but when I cycle to 'External HDD' when rebooting it just flashes 'Operating System missing' and all I can do from this point is power off. I'm very new to this and have no clue how to go about correcting this.

When the bio screen screen opens, can you see words:  BOOT (key #) SETUP (key#)?
You have to push the boot key when bio comes up.  If you have to enter BIOs, set usb to boot first.

Mine doesn't say 'external drive', it says usb or flash, but computers are different, so you may have to research yours.

How did you put the iso image onto the stick?

---

### Post by black veils on 2012-09-14
yes make sure your usb flash drive is set to boot first in the bios, or instead use another key to access the boot device menu to choose there and then, which key varies from computer to computer. its usually F keys, like F2, F12, F10, F8, Esc.

try making the usb flash drive again, using [this tool]("http://unetbootin.sourceforge.net/")

---

### Post by steveeobleve on 2012-09-14
Open BIOS by hitting F2 (or possibly Del or F3 depending on the Sony model) as soon as the Sony/VIAO logo appears. Go to boot options and make sure it's booting from the USB before it boots from the hard drive.

---

### Post by Ryanicholls on 2012-09-15
Tried putting 'external' as the priority boot, but keep getting the same 'os missing' screen, Only have the three options, Hdd external or network..

---

### Post by black veils on 2012-09-15
if you select hdd, are there any options which appear?

did you redo the usb flash drive using unetbootin, like i linked? you should do that.

---

### Post by Ryanicholls on 2012-09-15
Yeah I tried the link, and no options when you click hdd, or external device it just reboots to whichever you pick

---

### Post by black veils on 2012-09-15
seems silly but try the "best answer" from here:

[http://answers.yahoo.com/question/index?qid=20080803205828AAdcYBc](http://answers.yahoo.com/question/index?qid=20080803205828AAdcYBc)


but obviously you will be using a ubuntu flash drive, not a windows disc.

i am also wondering though, how old is the machine, does it have a floppy drive?


someone else also said "My SZ has a dedicated BIOS option that says 'enable external drive boot' - check if you have something like that."

---

### Post by Ryanicholls on 2012-09-15
F11 does cycle boot options on mine, but each time i press it to cycle to external device i just get the same missing OS message, I have enabled external drive boot, and it's a reasonably new machine, only USB ports or an SD slot, but i don't have an SD large enough to try yet.

---

### Post by black veils on 2012-09-15
things i would try..

- test the bootable flash drive in another computer, in case it is a bad stick.

- format the usb flash drive, either using gparted in linux or the ms.windows format option from properties. format it, then do the unetbootin thing again.

- the ubuntu **[alternate installer]("http://mirror.bytemark.co.uk/ubuntu-releases/precise/")**

- putting plop boot manager on an sd card to see if it will boot, to subsequently allow booting from the usb flash drive.

---

