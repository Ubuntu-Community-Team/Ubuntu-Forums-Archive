---
title: "permanently bind folders"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by LinuxVirgin2000 on 2014-03-14
Hi, I am trying to bind a folder on a shared partition between windows and ubuntu to a folder in my home folder.

the folders are: /media/SharedPartition/Shared     and       /home/deepak/Shared


I found an anwer on these forums that suggeted I should add:

/media/SharedPartition/Shared /home/deepak/Shared auto bind

to the fstab, so I did, but I don't really understand fstab properly and I think I've added it wrong, all I did was add the line above to the very end of the fstab file and saved it, but when I boot a message comes up saying something like "there was an error when mounting /home/deepak/Shared press S to skip or M to manually..."

what have I done wrong?

P.S I have already set the "sharedPartition (SDa6) to mount automatically at boot using "storage device manager"

Thanks in advance

---

### Post by matt_symes on 2014-03-14
Hi

Try adding this to your fstab file

```
/media/SharedPartition/Shared /home/deepak/Shared none bind 0 0
```

I bind a number of extX and other directories in my fstab but i don't bind any NTFS or FAT32 partitions so i'll be interested to see if the above works.

If it does not  work, we'll find the correct solution for you.

Kind regards

---

### Post by LinuxVirgin2000 on 2014-03-15
Hi, thanks for you reply

I tried adding your suggestion to the fstab but I still have the same message come up at boot saying it could not mount

does it matter where you add the line in fstab? I just stuck it on a new line at the end of the file?

---

### Post by LinuxVirgin2000 on 2014-03-15
Hi I managed to solve the problem,

since I installed "storage device manager" to auto mount "SharedPartition" at boot it somehow automatically changed the pathway to get to the drive (not sure if that is the correct teminology) so basically Instead of :

[COLOR=#000000]/media/SharedPartition/Shared /home/deepak/Shared auto bind

I actually need to type:
[/COLOR]
/media/SDa6/Shared /home/deepak/Shared auto bind

I added this to the fstab now and it works perfecly so yes I can confirm that auto bind does work btween ntfs and ext4

Thanks for your help.

---

