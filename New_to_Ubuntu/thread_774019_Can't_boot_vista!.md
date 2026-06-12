---
title: "Can't boot vista!"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Niklas93 on 2008-04-29
I've posted this thread before, but I simply can't find it anywhere so now I'm posting it again. A week ago i decided to install ubuntu 7.10 in dual boot with vista on my computer. I resized the vista partition and created a new ex3 and swap partition for ubuntu using the partition tool that is build into the ubuntu installer. The installation went fine and without problems. But then when i restarted and open grub I couldn't see vista on the grub menu? So now I'm totally lost and I don't know how to set vista active again. I've tried gksudo gedir /boot/grub/menu.lst and in there i couldn't see anything for vista eighter. I tried creating it (writing title vista makeactive chainloader + 1) but it obsouisly didn't work (I don't know anything about it), and now gksudo gedir /boot/grub/meun.lst is broken too. When I write my password in there it just doesn't start. So to be short please help me

---

### Post by hermes0710 on 2008-04-29
> **Niklas93 said:**
> I've posted this thread before, but I simply can't find it anywhere so now I'm posting it again. A week ago i decided to install ubuntu 7.10 in dual boot with vista on my computer. I resized the vista partition and created a new ex3 and swap partition for ubuntu using the partition tool that is build into the ubuntu installer. The installation went fine and without problems. But then when i restarted and open grub I couldn't see vista on the grub menu? So now I'm totally lost and I don't know how to set vista active again. I've tried gksudo gedir /boot/grub/menu.lst and in there i couldn't see anything for vista eighter. I tried creating it (writing title vista makeactive chainloader + 1) but it obsouisly didn't work (I don't know anything about it), and now gksudo gedir /boot/grub/meun.lst is broken too. When I write my password in there it just doesn't start. So to be short please help me

Can you post the contents of menu.lst?
Also post the structure of your hard drive containing vista, i mean how many partitions does it have and in which one is vista hosted.

---

### Post by Alldan on 2008-04-29
it's not a very good ideea to resize vista partition from ubuntu installer. 
You must use Vista utility to resize vista partition , then use ubuntu installer to create required ext3 and swap using the free space. this is a safe solution.
In your case you can try to repair vista using vista dvd then reinstall ubuntu or bootloader only

---

### Post by morjava on 2008-04-29
how is this a problem?

---

### Post by Alldan on 2008-04-29
look here: [http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

---

