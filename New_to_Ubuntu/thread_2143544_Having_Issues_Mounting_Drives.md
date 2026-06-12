---
title: "Having Issues Mounting Drives"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by hugh1846 on 2013-05-09
I recently installed Ubuntu on a computer I built to use as a small home server, and I am attempting to set everything up so I can share my drives with other computers on my network. I have partitioned my drive using Gparted, and now I am trying to mount my partitions so that they are automatically mounted on system start up.

Most of the forums I have searced pointed me to Storage Device Manager, but when I search for it in Ubuntu Software Center, I can't seem to find it. Is Storage Device Manager still available, and if so, any ideas why I can't find it? I'm also not opposed to using the terminal to mount the drives, but the forum posts that I have looked at were a bit confusing.

Any information would be greatly appreciated, and if you need anyadditional information let me know. Thanks!

---

### Post by dino99 on 2013-05-09
when an ubuntu system boot, it load the required device(s) to work with; then the "mountall" package load "on demand" the others. Gnome-disk-utility can be set as you like/need; and System Settings Sharing can also be set.

---

### Post by DuckHook on 2013-05-09
As dino99 says, based on your description, these partitions should be automatically sensed and mounted, so this is quite odd. Please post output of:```
sudo blkid
``````
df -m
``````
cat /etc/fstab
```The fstab file is the one that tells Ubuntu what partitions to mount at startup. You may have to manually configure it, but let's see what it says first.

Also, please provide full description of your system. i.e. is it desktop, make, model, cpu, memory, etc, as much as you can. The above commands will tell us about your disks.

---

### Post by DuckHook on 2013-05-09
After reading your post more carefully (something I should have done before asking for all that info) it seems that you are really just asking how to share partitions across a network. I take it that you are already able to see the partitions on your own box. If so, then you really just have to make a decision about how you want these partitions shared. If the other boxes on your network are Windows machines, then you want to install Samba. This will make your partitions look like Windows shares to Windows machines. If your other boxes are all Linux, then you have a choice between Samba and NFS. I use NFS for my own network, but Samba is perfectly acceptable.

Instructions for setting up Samba are [here]("https://help.ubuntu.com/community/Samba/SambaServerGuide"). Instructions for NFS are [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

---

