---
title: "Mounting volume help"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by lolumadclan on 2008-06-25
Hi, I started using Ubuntu Linux a week ago and I was able to open my Hard Drive so I could view Window Files and now I cannot It says "cannot mount volume" How should i go about mounting the hard drive?

---

### Post by bumanie on 2008-06-25
Easiest way is to install ntfs-3g (gives read/write ability to ntfs) and ntfsconfig. In terminal > sudo apt-get install ntfs-3g then > sudo apt-get install ntfsconfig The go to Applications --> System Tools and open ntfsconfig Fill in the box and your ntfs drive will be automatically added to /etc/fstab and will automount at boot.

---

### Post by lolumadclan on 2008-06-25
> E: Couldn't find package ntfsconfig


i got an error.

---

### Post by andrewbrown22 on 2008-06-25
> **lolumadclan said:**
> i got an error.

Try 
```
 sudo apt-get install ntfs-config
```
instead.

---

### Post by logos34 on 2008-06-25
typo

ntfs-config

---

### Post by joe bocan on 2008-06-25
hi i'm bringing and other question


i accidently mounted 2 partion at the same mount point
how to unmount manually?

---

### Post by lolumadclan on 2008-06-25
alright so it installed but now it says to <click here to set a mount point> Where should I set it?

---

### Post by lolumadclan on 2008-06-25
nvm lol dumb question
'

---

### Post by lolumadclan on 2008-06-25
okay so i have another problem with mounting it..now it says that "You are not privileged to mount this volume."

---

