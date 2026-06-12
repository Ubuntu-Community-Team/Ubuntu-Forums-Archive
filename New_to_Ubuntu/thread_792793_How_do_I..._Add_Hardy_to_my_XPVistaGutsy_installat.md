---
title: "How do I... Add Hardy to my XP/Vista/Gutsy installations?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by RichTJ99 on 2008-05-13
Hi,

I currently have a XP/Vista + Gutsy setup on my Dell 1210 laptop.  I would like to try out Hardy.  I have three partitions right now, one for XP, one for vista, and one for Gutsy.  Gutsy has a 30gb partition (it is a single ext3 partition I think).  

How can I install Hardy as a stand alone using say 10gb of the gutsy partition?  

Thanks,
Rich

---

### Post by pedro_orange on 2008-05-13
Resize the 30GB you've assigned to Gutsy using the Hardy installation disk I reckon.

Shouldn't take too long.

---

### Post by RichTJ99 on 2008-05-13
Where in the Hardy installation does it let me resize?  I have always used the "use the most continuous free space" in my installations for Ubuntu.

---

### Post by JC Cheloven on 2008-05-13
Also you can use gparted within a live cd session to shrink the gutsy partition by 10 Gb, leaving that space as 'free'. I prefer that way, as the (later) installation in the free space is a bit more straightforward. Anyway you will got it easily ;.)

---

### Post by JC Cheloven on 2008-05-13
> **RichTJ99 said:**
> Where in the Hardy installation does it let me resize?  I have always used the "use the most continuous free space" in my installations for Ubuntu.

Yes, use that option in combination with the (previous) space freeing. That'h what I meant.

---

