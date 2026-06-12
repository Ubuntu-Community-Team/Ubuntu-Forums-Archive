---
title: "Auto load Windows XP"
date: 2005-10-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Astronaut on 2005-10-08
Hello there, I'm new to this forum, newbie but very entusiast about the wonders of linux. I installed my Ubuntu 5.04 successfully along with Windows XP. I also loaded successfully Windows XP into Grub so I have no problems using any of the Operating systems in my pc. My problem is that I don't know how to set Windows boot by default, since I'm not the only user in the house and the rest of my family uses Windows. Thanks a lot...

---

### Post by Zelut on 2005-10-08
This would simply be a matter of editing the grub config file.  I don't have my linux box with me so I can't remember the path/filename offhand but you can change the default OS in that file.  (I'm assuming since you mentioned you editing to include XP that you can find it again... sorry I can't remember the filename)

---

### Post by Astronaut on 2005-10-08
[QUOTE=kuyaedz]This would simply be a matter of editing the grub config file.  I don't have my linux box with me so I can't remember the path/filename offhand but you can change the default OS in that file.  (I'm assuming since you mentioned you editing to include XP that you can find it again... sorry I can't remember the filename)[/QUOTE]

Thanks for answering, are you refering to grub.conf?

---

### Post by Zelut on 2005-10-08
yeah, thats the one :)

---

### Post by aysiu on 2005-10-08
```
sudo nano /boot/grub/menu.lst
```

*default 0* means "make the first entry the default one."
*default 1* means "make the second entry the default one."

And so on. Find out which entry Windows XP is (fourth, fifth, whatever), minus one and make that the default.

---

### Post by Astronaut on 2005-10-08
It was number 3, thanks a lot!

---

