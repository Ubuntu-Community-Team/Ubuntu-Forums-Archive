---
title: "Unable to mount Hard Disk Drive"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by ash.ashwin.s on 2013-11-26
When I try accessing my Hard Disk after plugging it in, the following pop up comes up :-

Error mounting /dev/sdd1 at /media/ashwin/Ashwin: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdd1" "/media/ashwin/Ashwin"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdd1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Please help, thanks in advance

---

### Post by Bucky Ball on 2013-11-26
Welcome.

Does this mount point exist:
```

/media/ashwin/Ashwin
```

... and have you set it up to mount it there? If you are running Windows, this could possibly be the result of a bad shutdown and the disk was not closed properly. Try looking at it in Windows and going through the right click procedure to eject the drive then try again in Ubuntu.

Also, please use [code] tags. Thanks. ;)

---

### Post by ash.ashwin.s on 2013-11-29
Hi,
 I have used my external HDD on ubuntu lot of times(I don't have windows :D), I encountered this problem when I was copying data to my external HDD from laptop running on ubuntu. The copy was interrupted as the data cord of the HDD was unplugged accidentally.

[COLOR=#000000]Code:
/media/ashwin/Ashwin[/COLOR]
[COLOR=#000000]Ashwin is the name of my HDD, I have not made any configurations/settings for using my HDD, just using the defaults(plug and play). 

[/COLOR][COLOR=#000000]Code:
/media/ashwin/[/COLOR]
[COLOR=#000000]The above folder is present and empty as no external HDD is connected (or) error mounting my HDD[/COLOR][COLOR=#000000]
[/COLOR]
I'll try to check if it's getting mounted fine on windows and also do everything as suggested in the error text in my 1st post

Thanks :)

---

### Post by Bucky Ball on 2013-11-29
Yep, sounds like the disk wasn't closed properly. Boot it in Windows, eject safely, unplug. Boot to Ubuntu and try again.

---

