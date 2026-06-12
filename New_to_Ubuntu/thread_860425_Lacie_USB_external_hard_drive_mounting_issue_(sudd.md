---
title: "Lacie USB external hard drive mounting issue (suddently!)"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-15
All this while I can read/write this external hard drive after first manually mount it with "sudo mount /dev/sdb1". Somebody told me it was not auto-mount because I did not disconnect it properly in XP which I think might be true in my case. So, I fired up XP in VirtualBox, plug in this external HD, and disconnect it properly upon detection. However, when I try to use it in Hardy Heron, weird thing happened. I still need to manually mount it as before but instead of read/write capability as before, I get folder permission warning when I try moving a movie inside it. Last time, I can see all my folder in this HD, but now only My Music, Doc, and My Movie are visible. Other (like 7-8 folders) are totally vanished, un-hide do not yield anything either. 

This is my fstab entry for this HD:
/dev/sdb1 /media/sdb1 vfat rw,user,noauto,umask=0 0 0   

When I check /media/sdb1, the permission is limited to root! I did change (chown [username][/media/sdb1], but after reboot, it revert back to root. Please help me:(

---

### Post by wariskampar on 2008-07-16
Can anyone share the fstab entry for USB external HD for me

---

### Post by bumanie on 2008-07-16
Do you get an error message when the drive doesn't mount? If so, please post that. I suspect mounting and unmounting the drive in virtualbox will not have the same effect as doing so on an actual hard drive. I'd try 'safely remove device' off a xp hard drive installation.

---

### Post by wariskampar on 2008-07-16
The drive can be manually mounted in hardy Heron and was safely disconnected in XP (VirtualBox) w/o any error message. However, I'll try disconnect it once again using my wife XP. Anyway, do you mind sharing your fstab entry. Just want to compare with mine, just in case that might be a problem

---

### Post by nothingspecial on 2008-07-16
Don`t know if this will help but if the hard drive is ntfs and you unmounted  it incorrectly it may have written something to the hds log that is causing problems. This  can clear the log without mounting it.

```
sudo apt-get install ntfsprogs
```

Then

```
sudo ntfsfix /dev/sdb1
```

---

### Post by timcredible on 2008-07-16
if it's fat32, use ```
dosfsck -a
``` to fix the errors

---

### Post by wariskampar on 2008-07-16
Today is even worst. I can not see any folder in the HD after manually mounting it. Hope the problem is temporary otherwise my wife gonna be very mad because all our photo of about 2 years past are all in there. Right now I'm running dosfsck code as suggested. Will keep posted  for any development

---

### Post by pbg on 2008-12-12
ok so after trying the things here, elswhere and not succeding, I disconnected the LaCie from my intrepid ibex beta and plugged it into my mac. I unmounted the device properly. I then re connected the LaCie to my ubuntu desktop computer and I had write access. The problem was resolved similarly to the post about unmounting it correctly in WinDoz. I feel lucky that the fix was so simple, after everything else. so try this dumb fix if you are stumped. It might solve your problem quickly.

---

### Post by johnkaiman on 2008-12-16
I have the same issue.

I was able to use the lacie disk before. I just plugged it into xubuntu with no problems, but ubuntu laptop won't recognise it! What is going on? I've tried properly unmounting it on windows computers, and on the xubuntu desktop I've got. Help!

---

