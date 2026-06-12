---
title: "cant dual boot with xp"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by bunaras on 2008-05-17
First of all i want to say, that im totally new at ubuntu and linux. Now i have a bit of a problem. Ill ty to explain. Before installing ubuntu i had xp and vista on my pc. I had 3 partitions: one for xp, one for vista, and one for keeping data. What i did before installing ubuntu is I formatted the drive with vista, and installed ubuntu in that partition. Ubuntu is working perfect. BUT i cant get back into my xp. What scares me that i can only see my data drive from ubuntu. And the GRUB is somehow showing vista/longhorn os as the alternate os to ubuntu. Maybe there is some trick to see the options for GRUB or to set it right (i need some stuff from my xp badly)??

---

### Post by shadow-of-sin on 2008-05-17
Please post the output of this command in the terminal:
```
sudo fdisk -l
```

---

### Post by meierfra. on 2008-05-18
After you posted "sudo fdisk -l" check out this link:

[http://support.microsoft.com/?kbid=922809&sd=RMVP]("http://support.microsoft.com/?kbid=922809&sd=RMVP")

---

### Post by tjwoosta on 2008-05-18
you should be able to just alter your /boot/grub/menu.lst so it points to your xp partition rather than vista

---

