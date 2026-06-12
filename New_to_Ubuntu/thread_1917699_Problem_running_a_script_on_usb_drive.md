---
title: "Problem running a script on usb drive"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2012-01-30
I am trying to install slax on my pendive. I have extracted slax.tar file on pendrive and last step required to complete setup is run bootinst.sh file inside the pendrive. But I am not able to make the script executable no matter if I try it as root or how. I am trying command

```
chmod a+x /media/New/boot/bootinst.sh
```What is solution?
Thanks in advance.

---

### Post by drmrgd on 2012-01-30
The problem is likely due to the formatting of your flash drive.  Is it formatted as FAT32 by chance?  If so, then the problem is that it won't accept linux permissions.  There are a few workarounds:

1. Format the drive using a linux format so that you can change the permissions as you need.

2. Copy the file from the drive to linux, change the permissions there.

3. Change the mount entry of your flash drive by adding a 'exec' option to the mount point (not recommended as this will make every file on the drive executable, which is a security risk and not desirable).

---

### Post by sujitrjadhav on 2012-01-30
> **drmrgd said:**
> The problem is likely due to the formatting of your flash drive.  Is it formatted as FAT32 by chance?  If so, then the problem is that it won't accept linux permissions.  There are a few workarounds:

1. Format the drive using a linux format so that you can change the permissions as you need.

2. Copy the file from the drive to linux, change the permissions there.

3. Change the mount entry of your flash drive by adding a 'exec' option to the mount point (not recommended as this will make every file on the drive executable, which is a security risk and not desirable).

1. Formatting drive with linux format is of no use because as per installation documentation at [http://www.slax.org/documentation_install_slax.php](http://www.slax.org/documentation_install_slax.php) syslinux works  with FAT only

2. Running the script inside pendrive is necessary as the script makes bootable the drive inside which it is run.

3. I am a newbie and do not not how to use the third option suggested by you. I mean can you please give me exact command that I should type to mount /media/New partition with exec option.

---

### Post by sujitrjadhav on 2012-01-30
Found how to do that

sudo mount /dev/sdb1 /media/New -o exec,rw

worked.
Thanks Very much

---

