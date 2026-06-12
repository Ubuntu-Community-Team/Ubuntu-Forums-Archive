---
title: "Saving Hard Drive data using Ubuntu live CD"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by anything really on 2013-01-25
Due to some overheating issue, my Windows crashed and is not booting. To save the hard drive data, I used an Ubuntu live CD to access my hard drive through Ubuntu and save it elsewhere. Usually the hard drive can't be mounted due to errors while closing, so these commands were supposed to help access the hard drive:

sudo /bin/bash
mkdir /media/disk
mount -t ntfs-3g /dev/sda1 /media/disk -o force

I basically followed these instructions: [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

But I get this message in the Terminal and am still unable to access the drive:

Error mounting /dev/sda2 at /media/ubuntu/56C468F7C468DB2F: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda2" "/media/ubuntu/56C468F7C468DB2F"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Any help please? I have no experience with or knowledge of Ubuntu.

Thanks a lot!

---

### Post by furything on 2013-01-25
Hi Your output shows this.
> In the first case run chkdsk /f on Windows
then reboot into Windows twice. 
I suggest doing just that. Get your old windows install/recovery disk. Get it to boot into console recovery mode and run the check disk.

Another option if you have a second pc is move the faulty drive across to it and use the gui to check disk and disk the thorough test and auto repair. It sounds like the ntfs partition table is damaged. This tells the os what is on the drive and where it is located.

---

### Post by sudodus on 2013-01-25
+1

Repair with ```
chkdsk /f
``` from Windows or from a Windows preinstallation environment if you have no computer available with a working Windows OS.

- Bart PE
- Windows PE
- or newer Windows 7 PE

You find information on the internet how make such a preinstallation environment.

---

