---
title: "unionfs shares need manual mounting every boot"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by benfindlay on 2008-04-29
Hi,

I'm using unionfs to share 2 external USB harddrives as one folder. The hard drives mount at boot fine (I used the diskmounter script to write my fstab and then added the unionfs stuff after), but I have to manually mount the unionfs mount point every time I reboot with the command ```
sudo mount /home/user/share
```
Is there anyway that I can automate this to happen during boot at all?

Thanks in advance
Ben

---

