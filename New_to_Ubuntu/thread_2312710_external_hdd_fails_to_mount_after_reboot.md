---
title: "external hdd fails to mount after reboot"
date: 2016-02-06
forum: New to Ubuntu
---

### Post by cafeledavid on 2016-02-06
anyone know why everytime I reboot my PC, I always have to run chkdsk in my windows vmware to get it to work again? after I do this, it's fine until the next reboot, it says its failing but I only have this issue when it's connected to ubuntu 14.04

thanks

Error mounting /dev/sdf1 at /media/david/0ABA3EF1BA3ED8C1: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdf1" "/media/david/0ABA3EF1BA3ED8C1"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
 (udisks-error-quark, 0)

---

### Post by cariboo on 2016-02-06
You need to do what the error message says, attach the external drive to a system running windows, run chkdsk /f on it.

---

### Post by cafeledavid on 2016-02-06
yeah.. already said that I do that and then its fine again but this only happens in ubunutu, if i connect it to my windows pc its fine - this only happens when i reboot my ubuntu pc

---

### Post by sandyd on 2016-02-06
chkdsk /f only checks for disk errors, but not anything else.

Maybe try running:
```

chkdsk /R
```

Have you also checked the drive's SMART status?

---

### Post by cafeledavid on 2016-02-06
i find it amazing you still need Windows to use linux... right now I am about to smash my damn PC into the wall because VLC player sucks! all i want to do is add a song to my playlist and it wont let me unless i make a brand new playlist... 1 month of using linux and i am about to donate money to bill gates to smash this OS to hell!

---

### Post by QIII on 2016-02-06
What makes you think you still need Windows to use Linux?

Are you accessing the external disk from Windows in VMWare at any time when you are running the Windows VM in Linux?  Could it be that Windows is leaving the disk in an inconsistent state?

---

### Post by Vladlenin5000 on 2016-02-06
You still need Windows to correct logical errors in partitions formated with the [**Microsoft's proprietary NTFS**]("https://en.wikipedia.org/wiki/NTFS"). Not only that, > the NTFS code is a purple opium-fueled Victorian horror novel that uses global recursive locks and SEH for flow control as described by one of the company's devs, quoted [URL="http://blog.zorinaq.com/?e=74"]here.
[/URL]

---

### Post by cafeledavid on 2016-02-07
apology, so much frustration with so many issues on linux made me so angry when i posted last night

No i never connect the ext hdd to my vmware os unless i have to run chkdsk /f on it and that only happens after i reboot my ubuntu 14.04 system/PC, after running chkdsk /f i can use it perfectly fine..until i reboot again

thank you

---

### Post by Vladlenin5000 on 2016-02-07
What you need to run, in Windows, was mentioned in post #4. That's what will finally correct the logical errors (and mark as unusable and bad sectors).

---

### Post by cafeledavid on 2016-02-11
after 2 days of it running chkdsk /r

it worked

thank you sandy

> **sandyd said:**
> chkdsk /f only checks for disk errors, but not anything else.

Maybe try running:
```

chkdsk /R
```

Have you also checked the drive's SMART status?

---

### Post by cafeledavid on 2016-02-14
actually nevermind, rebooting a second time it stopped auto mounting, maybe its going i dunno...

---

