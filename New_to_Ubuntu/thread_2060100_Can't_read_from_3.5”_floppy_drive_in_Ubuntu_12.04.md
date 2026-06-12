---
title: "Can't read from 3.5” floppy drive in Ubuntu 12.04"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by foberle on 2012-09-19
I have a dual boot machine (Windows and recently installed Ubuntu 12.04). “Floppy Drive” shows up under Devices in left side panel of Nautilus, but I am unable to read any disk that I insert in the drive.
 

 In the /etc/fstab, the following line was created on installation (from a Live-CD):
 

```
/dev/fd0   /media/floppy0    auto    rw,user,noauto,exec,utf8    0  0 
```
 When I insert a 3.5” floppy in the drive, however, it's as if the drive isn't even recognized – no head noise when I attempt to read it, etc. I should mention that the drive functions just fine under Windows.
 

 Thinking that perhaps the “utf8” designator might be an issue (I couldn't find any reference to that as an option in any fstab documentation I located on the web), I removed that and restarted, but that made no difference whatever.
 

 One thing I did notice by accident, though, is that when I started up Gparted with a disk in the drive, the light came on, although this made no difference to the operation of the drive and it wasn't shown in Gparted's drive listings.

---

### Post by stevem531 on 2012-09-20
From what I can gather (I am quite new to Ubuntu) there have been issues relating to the support for internal 3.5" floppy disks going back a couple of years or so to earlier releases of Ubuntu as discussed for example in this thread :-

[http://ubuntuforums.org/archive/index.php/t-1599639.html](http://ubuntuforums.org/archive/index.php/t-1599639.html)

I have no idea whether the same methods that were suggested then to fix the problem would still work but they might be worth a try depending on how keen you are to get the drive working.

I have an external 3.5" USB floppy drive and that seemed to be working OK when I tried it with my 12.04.1 installation, but USB drives are handled differently. I only mention this as a possible solution if you have no success getting the internal drive to work.

Regards

Stephen

---

### Post by Mark Phelps on 2012-09-20
My floppy drive working in 12.04 just fine.

Line from the fstab file is as follows:

> /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

... which appears to match yours...

Also, the drive shows up as an icon when I click the Home button on the upper left.

---

### Post by foberle on 2012-09-20
Steve and Mark:

Thanks for your replies. As suggested in the reference Steve provided, I used the command:
```
udisks --mount /dev/fd0

```
which indeed sounded like it had mounted the drive, although when I attempted to click on the Floppy Drive icon listed under Devices in Nautilus, it looked like nothing had worked.

Then I spotted a new icon for "floppy0" under Computer and it was there. I was able to see the files on the disk, although I haven't attempted to see if I can write to it yet.

Now the issue would be how to make that persistent. Since Mark's line in fstab looks just like mine, I would have to assume that there is some other file he has somewhere that takes care of this, but I have no idea where to look.

This will get me going, so the pointers are much appreciated, but I'm not certain the Ubuntu experience will be all that enjoyable if I have to actively mount the thing every time I want to use it. Is there some setting that can trigger the mount command when Ubuntu detects that a floppy has been inserted?

Again, thanks.

---

