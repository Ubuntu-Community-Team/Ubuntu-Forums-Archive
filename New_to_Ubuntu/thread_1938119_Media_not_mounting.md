---
title: "Media not mounting"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by stdare on 2012-03-09
Hello all,
I have recently added an additional hard drive to my system running Ubuntu 10.10.
On boot, I get a message saying that media failed to mount.
When I choose the Skip option Ubuntu starts up okay.
The odd thing is that the drive is available and working when I log in. :confused:

Any suggestions on how to fix this annoying message at boot?

Thanks

---

### Post by Jon Monreal on 2012-03-09
Is it an internal or external (USB, etc.) drive?

---

### Post by androssofer on 2012-03-09
> **stdare said:**
> Hello all,
I have recently added an additional hard drive to my system running Ubuntu 10.4.
On boot, I get a message saying that media failed to mount.
When I choose the Skip option Ubuntu starts up okay.
The odd thing is that the drive is available and working when I log in. :confused:

Any suggestions on how to fix this annoying message at boot?

Thanks

also is it encrypted?

---

### Post by stdare on 2012-03-09
The drive is an internal SATA HDD. No, it is not encrypted.
Thanks.

---

### Post by NikTh on 2012-03-09
Hi ,
Can you give the results of those three commands ? 
```
sudo fdisk -l 
cat /etc/fstab 
sudo blkid
```

and what type is file system ? ntfs ? ext4 ?

---

### Post by stdare on 2012-03-09
> **NikTh said:**
> Hi ,
Can you give the results of those three commands ? 
```
sudo fdisk -l 
cat /etc/fstab 
sudo blkid
```and what type is file system ? ntfs ? ext4 ?

The filesystem is ntfs.
I'll give the terminal commands a whirl now, but warning: I am still pretty new to this...

---

### Post by stdare on 2012-03-09
> **NikTh said:**
> Hi ,
Can you give the results of those three commands ? 
```
sudo fdisk -l 
cat /etc/fstab 
sudo blkid
```

and what type is file system ? ntfs ? ext4 ?
The blkid may have given me a clue, as I seem to have an extra ext4 partition that I don't see in the user mount tool.
Is it possible that I have conflicting file system settings somehow?

OT: A hint on how to do screenshots in Ubuntu would also be of use.  Would be nice to post up a screenshot....

---

### Post by NikTh on 2012-03-10
The results of commands you can do a copy-paste in here. But put the results in code tag. Select the text and hit # 
You can hit Atl + printscreen keys for a screenshot of current window , or printscreen alone for a screenshot of all desktop.

---

### Post by stdare on 2012-03-10
Thanks for the suggestions, but I have a new problem now.  Mucking around in the media mounting GUI, I think I must have done something stupid as the machine won't boot now.
Getting the GRUB (i think it was) recovery window on startup.  Its not the drive in question, as I removed that and tried a boot with the same result.  :-(

Thanks for your help.

---

