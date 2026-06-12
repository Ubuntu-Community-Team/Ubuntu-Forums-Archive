---
title: "No such file or directory"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by ALWAYZBLESS on 2012-06-06
Hey all, Ive just gotten a mele a1000 and im beggining to fool around with it a bit and earlier I had downloaded a melea1000 ubuntu img file that is approx 4gb in size. The problem is that I am unable to write this image to microsd.. anytime I enter in the command sudo dd if=~/home/username/Downloads/ubuntu.img of=/dev/sdb I get an error saying no such file or directory exists.. I have formated the microsd, logged in as root, and tried this command mounted and unmount to no avail... Ive also have changed the permissions for my download folder and the img file itself but I still cant get this thing to write to microsd and I am looking for help at this point lol, has anyone else ever experienced anything like this or perhaps I am missing something here? Thx in advance guys!

---

### Post by steeldriver on 2012-06-06
> **ALWAYZBLESS said:**
> 
```
sudo dd if=~/home/username/Downloads/ubuntu.img of=/dev/sdb
```

the ~ character expands to /home/username... so you have effectively written

```
sudo dd if=/home/username/home/username/Downloads/ubuntu.img of=/dev/sdb

```

---

### Post by ALWAYZBLESS on 2012-06-06
LMAO... damn you linux, thx for the feedback will test this right now and post back

---

### Post by ALWAYZBLESS on 2012-06-06
Still not working.. ive changed it to sudo dd if=~/Downloads/ubuntu.img of=/dev/sdb

UPDATE: it seems "sudo dd if=~/username/Downloads/ubuntu.img of=/dev/sdb" worked for me

so is it correct to assume that the tilde only expands to root/home?

---

