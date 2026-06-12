---
title: "incapable of mounting iso Please help."
date: 2012-06-17
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2012-06-17
I have never been able to successfully mount an iso file, whether on windows or Ubuntu. I have gmountiso and every time I try it says the location "seems to be mounted read-only" I would prefer to put it to a flash drive but I have blank CDs available also.  Please help.

---

### Post by DarrenMR415 on 2012-06-17
And items always end up inside the location.

---

### Post by Paqman on 2012-06-17
What are you trying to do, get at the files inside an ISO, or burn it to a disk? If you just want to mount it to read the contents you can just double click it.

---

### Post by DarrenMR415 on 2012-06-17
I want to burn it to a disk so I can boot from it.

---

### Post by Cheesemill on 2012-06-17
If you want to burn it to a CD just right-click on the .iso file and select 'Write to Disk'.

To create a bootable USB you can use [unetbootin]("apt://unetbootin").

---

### Post by Mopar1973Man on 2012-06-17
... or if you want you could burn it with K3B if you used to doing like windows...

---

### Post by LawM on 2012-06-17
how about...

mount -o loop file.iso /mnt/

Choose the files you want, copy to where you like...

---

