---
title: "Trying to recover files from failed hard drive using ubuntu"
date: 2015-02-10
forum: New to Ubuntu
---

### Post by terry33 on 2015-02-10
HP Pavillion laptop refuses to boot, had a code 301 so assume hard drive has either failed or is about to. Desperately need to recover photos stored on this device (I know - backup backup backup). Have tried using Ubuntu live CD to recover and followed the tutorials but no joy. New user so not confident I've done everything right, or even if drive is recoverable at all.
Does the following ring any bells and if so could anyone give me an idiots guide as to what I should be trying?

[I]Unable to access 978GB Volume
Error mounting /dev/sda4 at /media/Ubuntu/088C64C78C64B13C: command-line `mount -t "ntfs" - 0
" uhelper+udisks 2, nodev, nosvid, vid+999, gid+999, dmask+0077, fmask=0177""/dev/sda4""/media/Ubuntu/088C64C78C64B13C" exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 3).
Failed to mount`/dev/sda4: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. 

Thanks[/I]

---

### Post by carl4926 on 2015-02-10
Use dd with ionice to make an image of your HD

It might be like this for example
```
ionice -c3 ddrescue /dev/sda /media/sdc1/laptop.iso
```

where sda would be your hd
/media/sdc1 would be your target for the backup

Parted magic might work better
[https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso](https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso)

---

### Post by Mark Phelps on 2015-02-11
Since the drive was formatted NTFS, you might have better results using Windows data recovery apps.  To do that, you would have to be able to connect the drive to a Windows PC, download and install "recuva" and see if it finds anything on the drive.

Sorry, but the combination of the I/O error message and the reference to hardware fault implies that your drive has failed -- and if that's the case, only rebuilding it using a disk repair service will work and those start out at $1000 USD.

---

### Post by DavidSr on 2015-02-12
Here is an idea not involving any OS.  Google *[SIZE=3]SeaTools[/SIZE]* for DOS.   This download from the Seagate hard drive company will create a Boot CD that will allow you to test and possibly recover and/or bypass bad sectors to able to access data.

---

