---
title: "Partition Problem using GParted."
date: 2014-04-20
forum: New to Ubuntu
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-20
hello i am muhammad ahmad mujtaba
i am using Ubuntu 14.04LTS Trusty Tahr right now and wants to do something with hard drive partitions.

[IMG]http://i57.tinypic.com/24pffoi.jpg[/IMG]

as you can see , i have /dev/sda4 == 100GB Useless [empty] and /dev/sda5 contains Ubuntu which is only 50GB.
I want to merge both in 150GB as a whole!

How can i achieve this using Gparted. Please be step by step and precise, i have very bad past at hard partitioning xD.
P.S. I am new to GPARTED.

---

### Post by carl4926 on 2014-04-20
You need to work from a Live cd/dvd/usb not from the installed system

If you delete sda4 it will cause mapping issues, so for now, I'd say shrink it to a few GB
That should leave free space so you can resize sda5 to take up that free space

FYI: What you have a poorly contrived layout. 

Always backup your files before doing work like this

*As you can see, currently some partitions are locked because they are in use. Hence the need to use a Live version.

This [https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso](https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso)
Is a cd of Parted Magic which  is very useful
Try it

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-20
Thanks for the link and i'll do as you told!

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-05-10
yep ! it worked. . . .[thanks and sorry for replying so late :D ]

---

