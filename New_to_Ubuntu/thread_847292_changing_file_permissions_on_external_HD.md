---
title: "changing file permissions on external HD"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by gerben1 on 2008-07-02
Can anybody give me some hints on why I am not able to change the file permissions on this external hard disk? The chmod command seesmt to be executed without error, but the permisions do not change.

```

gerben@CC1184274-A:/media/disk/Fotos/Volkstuin/slideshows$ ls -l testfile
-rwxrwxrwx 1 root root 0 2008-07-02 17:38 testfile
gerben@CC1184274-A:/media/disk/Fotos/Volkstuin/slideshows$ sudo chmod 666 testfile
gerben@CC1184274-A:/media/disk/Fotos/Volkstuin/slideshows$ ls -l testfile
-rwxrwxrwx 1 root root 0 2008-07-02 17:38 testfile
  

```

---

### Post by russbook on 2008-07-02
I am having a similar issue: [http://ubuntuforums.org/showthread.php?t=847294]("http://ubuntuforums.org/showthread.php?t=847294")

I have read that you can not chmod on a fat32 partition - not sure if this is true but may be partly to blame?

---

### Post by prshah on 2008-07-02
> **gerben1 said:**
> C
I am not able to change the file permissions on this external hard disk? The chmod command seesmt to be executed without error, but the permisions do not change.


> **russbook said:**
> I am having a similar issue: [http://ubuntuforums.org/showthread.php?t=847294]("http://ubuntuforums.org/showthread.php?t=847294")




You cannot "chmod" on non linux/unix filesystems; ntfs, vfat and fat32 do not support users, groups, permissions, links, etc. To change permissions, use either the "umask" modifier when mounting, or change the umask setting in your fstab if the device is automounting. Note that in this case, the permission changes are global across the device.

---

### Post by Sydius on 2008-07-02
Yes, it isn't possible to chmod on NTFS/FAT32 (Windows) file-systems because it requires underlying support in the file system to enforce the permissions--basically, there is nowhere to store the permissions.

You can, however, set it up so that an entire drive has specific permissions/owner/group information, though.  I did this for a USB drive that I didn't want other users (who connected via network) to have access to (even though they could walk into my room and take if they really wanted).  You know, gotta' protect my... collections... :biggrin:

I did this via fstab, which you can find more information at:

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

---

### Post by gerben1 on 2008-07-02
Okay thanks, that's why it did not work in my case then. It contains an NTFS file system. 

It does not "seem" to be handled by fstab in Ubuntu 8.04 though, as in my /etc/fstab there are only 4 rules, one for the root partition, one for the swap partition, one for proc and one for the cd/dvd-drive. Yet the external HD gets auto-mounted as soon as I plug it in.

---

### Post by prshah on 2008-07-02
> **gerben1 said:**
> 
It does not "seem" to be handled by fstab in Ubuntu 8.04 though,


Yes, now mounting devices in userspace doesn't require fstab revision; do ```
sudo apt-get install pmount
man pmount
``` for more information.

---

