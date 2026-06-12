---
title: "CIFS/SMBFS not mounting windows share"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by drewciferpike on 2012-08-27
This is confusing. I set up a directory to be shared on my win7 machine. I'd like to mount it on a linux box, not just connect through the network (can't upload pics from a network drive...).

when adding lines to fstab, 
" //Drew-pc/d /home/drew/pc cifs uid=drew,user=drew,password=_password_ " 
will get me an icon labeled "pc" in the devices area, but when I click on it all I get is "mount: only root can mount //Drew-pc/d on /home/drew/pc"

using SMBFS in fstab wouldn't even get the "pc" device to show up, so I figure that's a lost cause.

I've been googling like a mofo, but I haven't seen anything about mounting as root. What the heck am I missing, here?

---

### Post by androssofer on 2012-08-31
> **drewciferpike said:**
> This is confusing. I set up a directory to be shared on my win7 machine. I'd like to mount it on a linux box, not just connect through the network (can't upload pics from a network drive...).

when adding lines to fstab, 
" //Drew-pc/d /home/drew/pc cifs uid=drew,user=drew,password=_password_ " 
will get me an icon labeled "pc" in the devices area, but when I click on it all I get is "mount: only root can mount //Drew-pc/d on /home/drew/pc"

using SMBFS in fstab wouldn't even get the "pc" device to show up, so I figure that's a lost cause.

I've been googling like a mofo, but I haven't seen anything about mounting as root. What the heck am I missing, here?

can you not just use the mount command?

```
sudo mount <server>:/dir /local/dir
```

---

### Post by Jacobonbuntu on 2012-08-31
> **drewciferpike said:**
> This is confusing. I set up a directory to be shared on my win7 machine. I'd like to mount it on a linux box, not just connect through the network (can't upload pics from a network drive...).

when adding lines to fstab, 
" //Drew-pc/d /home/drew/pc cifs uid=drew,user=drew,password=_password_ " 
will get me an icon labeled "pc" in the devices area, but when I click on it all I get is "mount: only root can mount //Drew-pc/d on /home/drew/pc"

using SMBFS in fstab wouldn't even get the "pc" device to show up, so I figure that's a lost cause.

I've been googling like a mofo, but I haven't seen anything about mounting as root. What the heck am I missing, here?

... you need a separate .cifscredentials file for username and password, there is a pretty good manual [here]("http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/")

---

### Post by bootedguy on 2012-08-31
Have you installed smbfs? It is not installed as default, but is required for a fstab mount.

---

