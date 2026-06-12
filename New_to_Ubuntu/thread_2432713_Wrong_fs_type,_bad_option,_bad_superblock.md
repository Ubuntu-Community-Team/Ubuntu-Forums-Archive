---
title: "Wrong fs type, bad option, bad superblock"
date: 2019-12-07
forum: New to Ubuntu
---

### Post by antee on 2019-12-07
Hello,

I am trying to mount an encrypted home partition on external hdd with Ubuntu 16.04. I have Ubuntu 19.10. Here is a good explanation of how to do it.
[www.techrepublic.com/article/how-to-mount-an-encrypted-linux-home-directory-to-salvage-data/]("http://www.techrepublic.com/article/how-to-mount-an-encrypted-linux-home-directory-to-salvage-data/")

But after i run
sudo ecryptfs-recover-private /media/UUID/home/.ecryptfs/USERNAME/.Private

i end up with
mount: /tmp/ecryptfs.8jkY3rvY: wrong fs type, bad option, bad superblock on /tmp/ecryptfs.I0n0vlBS/.ecryptfs/USER/.Private, missing codepage or helper program, or other error.
ERROR: Failed to mount private data at [/tmp/ecryptfs.8jkY3rvY].

I cannot boot from this hdd either. Is there any way to solve it. Hopefully not too complicated.

There is an option to repair filesystem in Disks app. Can i start with it.

Thank you

---

### Post by oldfred on 2019-12-07
I think these are similar instructions.
       Includes chroot. /home encryption:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/) 
    
The most common and often only alternative with encrypted data is reinstall & restore from backup. The entire purpose of encryptions is to prevent access. And if any sort of data corruption that possibly could be repaired with standard data, often cannot be done as repairing/moving broken data sector does not work.

---

### Post by Autodave on 2019-12-07
I have no experience with encryption, but when I see "bad superblock", that tells me that I need a new hard drive.

---

### Post by antee on 2019-12-07
Thank you

---

