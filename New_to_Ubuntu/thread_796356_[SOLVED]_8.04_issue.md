---
title: "[SOLVED] 8.04 issue"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by jazzz337 on 2008-05-16
Tring to upgrade to 8.04 and I get this message 

The upgrade aborts now. The upgrade needs a total of 887m free space on disk "/var". Please free at least an additional 260m of disk on "/var" Empty trash and remove temporary packages of former installations using "sudo apt-get clean"

I have done all this still need space not sure what is needed and what is not needed on the /var any help is greatly appreciated.

---

### Post by kirios on 2008-05-16
Do you have /var on the / partition or a separate partition? Can you post the output of **sudo fdisk -l** here?

> **jazzz337 said:**
> Tring to upgrade to 8.04 and I get this message 

The upgrade aborts now. The upgrade needs a total of 887m free space on disk "/var". Please free at least an additional 260m of disk on "/var" Empty trash and remove temporary packages of former installations using "sudo apt-get clean"

I have done all this still need space not sure what is needed and what is not needed on the /var any help is greatly appreciated.

---

### Post by Oldsoldier2003 on 2008-05-16
> **jazzz337 said:**
> Tring to upgrade to 8.04 and I get this message 

The upgrade aborts now. The upgrade needs a total of 887m free space on disk "/var". Please free at least an additional 260m of disk on "/var" Empty trash and remove temporary packages of former installations using "sudo apt-get clean"

I have done all this still need space not sure what is needed and what is not needed on the /var any help is greatly appreciated.

```
sudo rm /var/log/*.gz
```will removed your archived logs

any particular reason you are running a separate /var ?(if you are not running a separate var try running sudo apt-get autoremove && sudo apt-get clean)

---

### Post by Paqman on 2008-05-16
Try clearing out anything else you don't need on /

[HOWTO: Cleaning up all those unnecessary junk files...](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by jazzz337 on 2008-05-16
Thank you to all of you for your help I solved the issue with Gpart I made the /var bigger had the room

---

