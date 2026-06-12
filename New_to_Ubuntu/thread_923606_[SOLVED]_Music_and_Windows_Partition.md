---
title: "[SOLVED] Music and Windows Partition"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by rdiggs on 2008-09-18
Still pretty new to Ubuntu and I was wondering if there was any way I could play music off of my Windows partition in Ubuntu without transferring everything over. Help with Songbird specifically would be much appreciated.

---

### Post by Elfy on 2008-09-18
Not sure about songbird, but when I started I had my music on a ntfs drive - you should have read rights (assuming that you use a recent version of ubuntu) - so all you should need to do is get the drive to mount when you boot. Can you open aterminal (Accessories) and paste these commands in and then post the outputs you get please.

```
sudo blkid
sudo fdisk -l
cat /etc/fstab
```

If you have not done so as yet - sudo will require your normal password - it will not show at all when you type it, that is normal.

Edit - I would assume that songbird will allow you to point to a music library, once the drive is mounted it should be available.

---

### Post by MegaJim on 2008-09-18
If ubuntu detected your windows disk during install, it should be located at /media/disk-name

If not, you may have to set it up using ntfs-config, read this wiki entry: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

As regards using songbird, its not in the repositories so you'll have to download it from their website, or you can use the deb file for ubuntu here: [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

---

### Post by rdiggs on 2008-09-19
It turned out that I couldn't access my Windows partition because it wanted to do a disk check. I booted in Windows, took forever, and after it did the disk check I booted in Ubuntu and was able to access my music. Songbird is also able to create a file path to it quite easily. I should really just get rid of Windows, but not until I'm confident that Songbird can give me what I need in terms of my iPod.

---

