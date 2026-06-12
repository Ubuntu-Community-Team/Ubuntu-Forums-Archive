---
title: "Notebook is always accessing CD-ROM"
date: 2009-03-10
forum: Philippine Team
---

### Post by randytan on 2009-03-10
Hi All!

May napansin ako sa notebook ko.

It accesses the CD-ROM even if there is no disc there. Do you guys know why this happens?

I think this contributes to eating the battery's life.

Sometimes when it accesses the hard drive, it also accesses the CD-ROM.

Is there a way to fix this?

All assistance, as always, will be greatly appreciated.

Thanks.

---

### Post by loell on 2009-03-10
may we know the content of your fstab?

```
cat /etc/fstab
```

---

### Post by randytan on 2009-03-11
Upon typing the command above, here is what I got:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=304b5767-7b68-4ccd-a193-4e19da7cab35 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9231306b-a96e-4175-8004-09393c4f16aa /home           ext3    relatime        0       2
# /dev/sda5
UUID=db965eaf-d9e3-4a73-bbc5-ffb345bc1c30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by loell on 2009-03-11
seems fstab is fine, could you check your software sources?

System menu --> Administration --> Sofware sources

then look at "Third-party" tab , try to uncheck the cdrom source.

---

### Post by randytan on 2009-03-12
Hi loell,

Upon doing what you suggested, I found the following unchecked:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner (Source Code)

The repositories for OpenOffice and Skype are checked.

Under the Ubuntu Software tab, everything but the "Source Code" check box is checked. (Should this be checked by the way?)

The item in the installable from D-ROM/DVD is not checked.

Hope this helps.

---

### Post by randytan on 2009-03-16
Hi All!

Any ideas? :D

---

### Post by Samhain13 on 2009-03-18
Maybe your notebook just wants to listen to music or watch a movie? :D

---

### Post by guitar_man on 2009-03-18
**Samhain13**::lolflag:
sir sa ibang os ba ok yung cd rom mo?

---

### Post by jeffimperial on 2009-03-18
> **randytan said:**
> Hi All!

Any ideas? :D
Nag-install ka ba ng kahit anong program na maaring isa sa mga resources nya ay manggagaling dapat sa optical drive mo?

Say, you inserted an Audio CD into the drive and played it with Amarok. Then, you created a playlist from the tracks in that audio CD. If, by any chance the playlist remains even after ejecting that CD, syemps mag-a-attempt 'yung Amarok na hanapin ang files sa original source (i.e. Audio CD). Same goes with any other program that could in any probability need to get files that should have been available to the computer through your optical drive.

IMHO :-)

---

### Post by randytan on 2009-03-19
Hi All!

Samhain13: :lolflag:

guitar_man:
when the unit was still running windows xp, it wasn't accessing the CD-ROM continuously like it is now.

jeffimperial:
I haven't done anything like you described. I haven't even transferred my music to the unit yet. The only discs that I have used the ROM drive with is the installation CD when I installed Ubuntu and some of the archive discs made on my office unit that didn't get read for some reason even if the ROM can read DVDs.

Any other ideas guys? :?: ](*,) :confused:

---

### Post by guitar_man on 2009-03-19
sir try mo yung sinabi ni sir loell;)

---

### Post by kilosan on 2009-03-22
Coincidentally, maybe your CD drive is dying out?

---

### Post by randytan on 2009-03-22
guitar_man:
I already tried loell's suggestion and couldn't even find that option in the selection. If you note in one of the posts above, I noted the items found there, what items were checked, and what items were not checked.

kilosan:
That's a possibility. I've been toying with the idea of ditching it and replacing it with an extended battery pack as it's actually a modular bay. I was also thinking of replacing it with a slim external drive instead.

Keep 'em coming. ;)

---

