---
title: "Entire system crashes when transferring files via USB"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by b1001421 on 2013-10-26
I had a data scare recently so I started pulling all the files off of my external drive and onto a desktop folder in my Xubuntu 13.10 installation. I didn't think anything off it and figured out it was a simple corrupted file in a directory causing problems. I managed to delete that file using a terminal command and everything was fine. I formatted my external drive and error checked it and didn't have any issues so I started copying the files back over onto the external drive and the system crashes completely after a minute or so. I pull the USB cord out of the external drive and hold the power button down on my computer.

I thought it was just a random freeze and don't see any corrupted data in the folder that was being copied so I do it again but with a single folder instead of all at once...and it crashes again. I do the same thing except I plug in my USB flash drive and start copying files over and again, it crashes.


Can anyone help me with this? I need to copy the files back up so I have two backups. I was going to try and copy the files over through a LIVE CD but I don't want it to crash while writing again. I am trying to transfer about 50GB of assorted media. I transferred about 5GB through USB about three weeks ago on the previous Xubuntu version. There is no problem transferring data off a drive.

Is it possible to tell if it is a problem with the USB on my system and not just a software problem?

---

### Post by b1001421 on 2013-10-27
I just realized that every time it froze I had two or three thunar windows opened...I tried transferring files without any windows open and the system did not hard freeze.

---

### Post by b1001421 on 2013-10-29
I solved the problem by just formatting my external drive to EXT4...Copied the files over without a single issue. I am guessing it is just a bug. I ran fsck on the drive and everything is in order.

---

### Post by tgalati4 on 2013-10-29
In the future, open a terminal:

```
dmesg | tail -40
```

That will display any errors which would be helpful to troubleshoot.  It's possible that the disk drive is starting to fail.  Unfortunately, you have to put the drive on a ribbon cable or SATA cable, because you can't read the SMART parameters over USB.

---

