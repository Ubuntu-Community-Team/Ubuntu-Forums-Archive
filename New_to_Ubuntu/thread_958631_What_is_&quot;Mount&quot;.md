---
title: "What is &quot;Mount?&quot;"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by CapnChkn on 2008-10-25
Like the title asks, "What exactly is Mount, and what does it do?"

---

### Post by tompickles on 2008-10-25
mount. It is what you do to allow access to all drives on your computer. You mount CDs, DVDs, USB sticks. Your hdd is mounted automatically. It allows you to access the stuff on your disk basically. They are mounted to usually /media/cdrom or /mnt/name depending on if you manually mount it in terminal or if ubuntu mounts it for you.

Edit:

try man mount in terminal

---

### Post by OutOfReach on 2008-10-25
Mount allows you to access storage devices connected to your computer. Without mounting a drive, you will not be able to access it

---

### Post by CapnChkn on 2008-10-25
I see.  I've never had any problems with actually mounting any device.  I just plug it in and then I use it.

Thank you.

---

### Post by SunnyRabbiera on 2008-10-25
All operating systems mount hard drives,just in different ways.
Windows mounts hard drives like "typical" devices, the CD player in the computer works and ejects the media like the one you might have in that stereo system you have, or that DVD player you might have too.
Linux also mounts but it treats devices more cautiously in my opinion, it actually encourages people to safely remove media from the computer so that the drive doesnt get messed up.
I have had windows kill many drives, linux has only killed 1 to my record.

---

### Post by mdsmedia on 2008-10-25
> **SunnyRabbiera said:**
> All operating systems mount hard drives,just in different ways.
Windows mounts hard drives like "typical" devices, the CD player in the computer works and ejects the media like the one you might have in that stereo system you have, or that DVD player you might have too.
Linux also mounts but it treats devices more cautiously in my opinion, it actually encourages people to safely remove media from the computer so that the drive doesnt get messed up.
I have had windows kill many drives, linux has only killed 1 to my record.All in the name of "ease of use" lol.

---

### Post by GuitarRocker2562 on 2008-10-25
You shouldn't really need it, when you plug-in a device it should mount automatically. However, if you want to mount a partition that isn't normally mounted, you would then use the mount command.

---

### Post by CapnChkn on 2008-10-25
Sheepishly I admit I've used various forms of Microsoft all the way back to DOS 1.  Though I am that old, I haven't been using computers that long, just picked up old systems.

I've borked a few USB flash drives, but never destroyed any.  A full format always seemed to get them up and running again.

Thank you Guitar.  I'm still a little mystified, but this gets me closer.

---

