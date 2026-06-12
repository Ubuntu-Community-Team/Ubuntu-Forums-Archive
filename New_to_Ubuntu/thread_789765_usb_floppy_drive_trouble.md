---
title: "usb floppy drive trouble"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by marsdv on 2008-05-10
i have a freecom floppydisk drive on loan for the weekend and want to put a few files on disks for my synthesizer.
but it's not working. i get the error "can't mount disk" (translated from dutch) when i double click on the floppydrive icon under computer.
does this mean this floopydrive is not compatible with linux? or does it mean my disks aren't compatible (DD disks) or are they not formatted correctly (don't see a way to format them while not beeing able to mount), or is there a way to fix this?
thanks for any help / suggestions!

btw i'm running ubuntu hardy

---

### Post by marsdv on 2008-05-11
nobody any idea what is the cause?

---

### Post by annda on 2008-05-11
take a look at this thread, it might be related, especially the last posts:
[http://ubuntuforums.org/showthread.php?t=789406](http://ubuntuforums.org/showthread.php?t=789406)

if not, tell us more.

---

### Post by marsdv on 2008-05-12
The person in that post can manually mount, I can't.
I've done pmount /dev/fd0
pmount /dev/floppy/0
sudo mkdir /media/floppy
sudo mount /dev/fd0 /media/floppy
sudo mount /dev/floppy/0 /media/floppy
and all don't work
then i checked in the dev folder and i don't have either /dev/fd0 or /dev/floppy/
I have no clue as to what to try or do.

---

### Post by marsdv on 2008-05-12
btw when i put in the usb cable when a floppy is in the drive it does not give me an icon under Computer
when i put in the usb cable when there is no floppy in the drive i do get an icon under Computer. but it is usually an icon called floppydrive (translated from dutch, but once it gave me the icon name scsi drive.

---

