---
title: "An issue with GRUB and my Ubuntu installation"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by gettin sombrero on 2008-04-26
A week ago I installed Ubuntu 8.04 beta through the wubi installer and it worked fantastically. So a short time after that I decided to give the OS its own install so I resized a partition and used the guided installation to install it.

At first installation, it didn't install grub so I did some research and found that it can happen so I used the super grub disc and on the second go 'round it installed grub. This is where my problems begin.

When I start up, it goes through the normal process of loading grub 1.5 and I see Ubuntu there but when I select it it says that the partition does not exist when I'm sure it does. I've checked with Partition Magic and the official Hardy release CD and I've found not only does the partition exist but the files are installed on that partition (however I'm not sure if its a working installation). 

So, I'm a little stuck and would like some suggestions on how to get GRUB to recognize my installation of Hardy. If thats not possible I guess I'll just fix my MBR and give it a go with the non-beta release in hope that this problem has been fixed.

---

### Post by MDSmith2 on 2008-04-26
Does it say anything else or say that differently?
Did you md5sum the disk and burn it at a slow speed?
I myself think getting the new release be better because it could be some bug in the beta.

---

### Post by gettin sombrero on 2008-04-26
> **MDSmith2 said:**
> Does it say anything else or say that differently?
Did you md5sum the disk and burn it at a slow speed?
I myself think getting the new release be better because it could be some bug in the beta.

I don't recall what it says verbatim, but I do recall 22 and "the partition does not exist".

I didn't md5sum the disk but I did burn it at 2 speed.

I'll take your advise and use the official release after I fix my mbr.

Still hoping for some help though.

---

### Post by MDSmith2 on 2008-04-26
Read though this and you might find something:[http://ubuntuforums.org/showthread.php?t=378322](http://ubuntuforums.org/showthread.php?t=378322)
what you said might seem like when you installed grub, grub didn't know were the Ubuntu partition was.

---

### Post by gettin sombrero on 2008-04-26
> **MDSmith2 said:**
> Read though this and you might find something:[http://ubuntuforums.org/showthread.php?t=378322](http://ubuntuforums.org/showthread.php?t=378322)
what you said might seem like when you installed grub, grub didn't know were the Ubuntu partition was.

This thread saved my linux installation. Thanks for this :)

---

### Post by MDSmith2 on 2008-04-26
Congrats!
hope you enjoy Ubuntu!


(When your done could you mark this thread as "Solved" using the thread tools above the first post. Thank you)

---

