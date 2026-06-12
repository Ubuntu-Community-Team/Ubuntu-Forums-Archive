---
title: "Error mounting filesystem"
date: 2014-12-10
forum: New to Ubuntu
---

### Post by jakkamgirish on 2014-12-10
I am getting the following errors 
"\\   Error mounting /dev/sda1 at /media/ubuntu/E2A493F1A493C707: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda1" "/media/ubuntu/E2A493F1A493C707"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
 (udisks-error-quark, 0)  //"


i have tried the following code
sudo mount -t ntfs/dev/sda/mnt/sda1

but no pleasure, nothing is happening its just goes to the nest line and waits and the mounting doesnt happen.

i even tried the disk utility
it says "Disk is OK, 5 bad sectors"

i have tried the following code and its output was

ubuntu@ubuntu:~$  sudo mount -t ntfs /dev/sda1  /media/SW_Preload -o force
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by gregory10 on 2014-12-10
Linux seems to need a mount point to be able to mount the disk
I'm thinking you didn't put a mount point (or whatever they are called sorry new to this also) when you formatted the disk(s)
That is the only thing I can think of that would cause what you hare experiencing to happen. 
You should get this confirmed by somebody else but am thinking that is it.

If it is true then you would likely need to reformat the disk(s) and make sure you put the mount point in. Start again
as I am not so sure it would be able to do it any other way but from the formatting stage. I mean of course the partitioning needs to be redone.
I would get that confirmed first though if I was you. there are lots of tools available for those sorts of jobs.

---

### Post by nerdtron on 2014-12-10
This is an NTFS drive. Better to use windows own check disk utility to scan and fix it.
Reasons for this type of error could be the hibernation you used in windows (if this is a windows OS drive) or that this drive is properly/safely removed in windows.

---

### Post by gregory10 on 2014-12-10
It may be as easy as making an image of the widows system as is
then reformatting the drive using a Linux tool set and putting the mount point on the ntfs drive at the beggining of the disk
then installing from the iso image....

I'm still thinking it is about having a mount point on the drive to be able to mount it.
Sorry I can't be sure about this but you need some feedback so there it is...

I know it's a steep learning curve but when you get there it's worth the climb 
I have had a few issues resolved through this forum and learned a lot along the way. 
all the best
G

---

