---
title: "Partimage Problem"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-01
I backed up my windows partition using partimage.

Every thing worked fine and at last after the end of backup i cant find where my backup image file is stored.

please help me.

---

### Post by Maestro23 on 2008-06-01
PartImage FAQ: [http://www.partimage.org/Partimage-FAQ#Where_does_partimaged_save_images.3F](http://www.partimage.org/Partimage-FAQ#Where_does_partimaged_save_images.3F)

---

### Post by bumanie on 2008-06-02
Partimage asks for a partition to send the output file to, therefore you should know where you sent it. Partimage asks for you to nominate the input partition (ie which drive/partition you wish to copy and the next thing is to nominate where the output file goes to). It is really a gui for dd commands where one would dd if=/dev/sda1 of=/dev/sdb2 where /dev/sda1 is what you are copying and /dev/sdb2 is the partition you send the output to. Unless you copied it to the same partition you were copying from, it will be where you sent it or has in fact not worked even though it seemed as though it did. You could try and track down your output image by looking at the disk usage analyzer. Applications --> Accessories --> Disk Usage Analyzer. Also if you made a zipped output, it will be a .gz package

---

### Post by rraj.be on 2008-06-02
I havent mentioned any name in that field because it dosnt display its place to enter destination location.

it just displayed "Enter your description here"

now i found my back up in my root folder.

Thanks a lot.

---

