---
title: "wubi install Ubuntu 12.10 with Win8"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by Jacob Halvorsen on 2013-01-17
okay, so im bran new to Ubuntu, it was the only one that was easy enough to understand, im running dual boot win 8, i used wubi loader to install. windows recognizes a dual system, however i clicked Ubuntu, it gave error that Wubildr.mbr was missing or corrupted, so i looked on a few more forums, and found that the problem could be fixed with a live cd, so i burned iso to a dvd ran instalation, went flawlessly, i go to boot up windows i select Ubuntu, i get the same error, haha please help im getting really frustrated, ive been trying to do this for about a week now

information:
windows 8 64bit home premium
4gb ram
500gb /100+ on partition for ubuntu
hp pavillion g7 
amd a8 vision processor

---

### Post by oldfred on 2013-01-17
Welcome to the forums.

Your post is not related to the thread you were in as that was dual booting not wubi.

If you have a BIOS/MBR it should work, but if UEFI/gpt it will not work at all as wubi does not work with gpt partitioning.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
       
 Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
[http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted](http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted)

     
    
       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

