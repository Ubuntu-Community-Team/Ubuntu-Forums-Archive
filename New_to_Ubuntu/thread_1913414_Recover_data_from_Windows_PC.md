---
title: "Recover data from Windows PC"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by andreasd70 on 2012-01-22
Absolute Beginner with Ubuntu!
My Windows 7 PC doesn't boot anymore, tried boot repair in several was without success. So I'm trying to save my data before re-installing Windows 7. Created Ubuntu 11.10 CD and it loaded Ubuntu through CD without installing it (yet). Wokrs just fine and under the home folder I see 3 devices:
System_drv
Lenovo_recovery
Windows7_OS
I can access system dev and lenovo, but my files aren't there, so I assume they are under windows7.
when I try to access the windows7_os I get the following error message:
Error mounting: mount exited with exit code 13:ntfs_attr_prread_i: ntfs_pread failed: input/output error
failed to read nyfs$bitmap:input/output error
NTFS either inconsistent, or there is a hardware fault, or it's a soft raid/fakeraid hardware. In the first case run chkdsk /f on windows then reboot windows twice.
If the device is a softraid/fakeraid then first activate it and mount a different device under the /dev/mapper/ directory.

I ran chkdsk /f getting the following message:
The type of the file system is NTFS
Cannot lock current drive
Windows cannot run disk checking on this volume because it is write protected.

And now what? Any help would be much appreciated!

---

### Post by yeats on 2012-01-22
You won't be able to run chkdsk from the Ubuntu live CD.  If you have your Win7 install/repair disk that should have come with your computer, you can use that to run chkdsk to repair the drive, then you can use Ubuntu to recover your files before installing.

---

### Post by CharlesA on 2012-01-22
> **yeats said:**
> You won't be able to run chkdsk from the Ubuntu live CD.  If you have your Win7 install/repair disk that should have come with your computer, you can use that to run chkdsk to repair the drive, then you can use Ubuntu to recover your files before installing.
Yep. You will have to run chkdsk on the partition before it can be mounted in Linux.

I think you can also force the mount, but I do not recommend that at all.

---

### Post by andreasd70 on 2012-01-22
Thanks for the quick response.

I ran chkdsk /f through windows using the recovery disk, but I'm still getting this error

---

### Post by yeats on 2012-01-22
Maybe this would help?

[http://forums.whirlpool.net.au/archive/1229012](http://forums.whirlpool.net.au/archive/1229012)

In any case, this looks like a Windows support issue.

---

### Post by CharlesA on 2012-01-22
If you've got another windows box around, I would stick the hard drive in it and see if you can access the files there.

Otherwise you could force the mount on *nix, but like I said earlier, I don't recommend it.

---

### Post by andreasd70 on 2012-01-22
unfortunately it's a laptop, so switching the hard drive is not an option. how would I go about force mounting it?

---

### Post by CharlesA on 2012-01-22
[http://blog.arvixe.com/how-to-force-mount-unclean-shutdowned-windows-ntfs-or-fat32-drive-in-linux/](http://blog.arvixe.com/how-to-force-mount-unclean-shutdowned-windows-ntfs-or-fat32-drive-in-linux/)

It might make the problem worse, but if it is still getting the same error even after running chkdsk, then there might be something else wrong with the drive.

---

### Post by matt_symes on 2012-01-22
Hi

If you have a spare usb hard drive kicking about, might i suggest making a backup using ddrescuse first from a LiveCD. 

You can the work on the hard drive to your hearts content knowing you have a backup.

I have had to do this today.

Kind regards

---

### Post by CharlesA on 2012-01-22
Huge +1 to having a backup.

---

