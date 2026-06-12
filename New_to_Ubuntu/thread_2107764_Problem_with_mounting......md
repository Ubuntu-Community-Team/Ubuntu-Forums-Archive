---
title: "Problem with mounting....."
date: 2013-01-22
forum: New to Ubuntu
---

### Post by frenchian on 2013-01-22
...partitions on an external HD

I decided to reformat an external HD, attached by USB. I used GParted, and set it up with four primary partitions. The first is NTFS and will be used for an image of my W7 dual boot. The other three are EXT4 and are for use with Kubuntu, which is set to automount all removable devices.

When I boot up, I get an error message saying "an error occurred while trying to mount /media/SDB3 - press S to skip....". So I do that. Once it boots, I look at /root/media. There is an anomoly - two of the partitions are called USB0 and USB1, the third is called SDB3 (the physical partition number). I don't know if this matters....

So, SDB3 isn't mounted - the other two (USB0 and USB1) are. Somewhere (I can't find where) I get an option to mount SDB3, but when I try, I get another error message

"error mounting: mount exited with error code 1: helper failed with mount: wrong FS type, bad option, bad superblock on /dev/SDB3, missing code........."

Any help to get four working partitions will be much appreciated

Thanks

UPDATE #1

If I open KDE Partition Manager, I can mount SDB3 there, and it seems to work
If I boot into recovery mode, I get an error message about SDB3, something along the lines of "Unsupported Optional Features (240)". Some discussion suggests this is a result of chosing EXT4?? I could easily go back to EXT3, if that helped...

UPDATE #2

I have
A. disconnected the external HD,
B. I have deleted all mention of the external partitions from system settings -> removable devices -> automatic mounting at start-up or attach,
C. I have deleted the entry /root/media/sdb3,

and STILL it stops at boot-up with the error message "an error occured while trying to mount sdb3, press S to skip".

I'm stuck. A clean re-install is beckoning.......

Any ideas before that?

Thanks

---

### Post by frenchian on 2013-01-23
OK, seems like I fixed it. Fingers crossed.

I found a thread that indicated there could be a corrupted entry in /etc/fstab. I had a look and, yes, there was one line referring to sdb3 (which no longer existed). As advised, I added a "#" to the front of the line and re-booted.

Success! No error message!

So, re-attached the external HD, created the four new partitions (EXT3 this time, just in case) and ....

Success! It all works!

No re-install this time! Phew!

Cheers

---

### Post by cepal on 2013-01-23
I'd do last instance search "everywhere":
grep -Ri sdb3 /etc/
grep -Ri sdb3 /root/

I'm quite surprised you have /root/media/ ; first, I wouldn't recommend using "root" as primary account, second, I'd rather expect ubuntu to have /media/{username} removable media mount path, weird...

---

