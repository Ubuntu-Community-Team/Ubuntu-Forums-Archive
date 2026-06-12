---
title: "Automatic mount of internal media"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by RokyFromGoky on 2008-06-15
My hard drive is divided in two parts (29.6 GB Media and 62.2 GB Media). Is it possible that they become automatically available, so that any shortcuts will actual work? Now I have to mount it first.   Or is it possible to change to owner to myself instead of root?

Thanks!!

---

### Post by Eisenwinter on 2008-06-15
You will have to edit fstab. 

What is the name for the device you want to automatically mount? It will usually be either /dev/sda or /dev/hda.

---

### Post by Joeb454 on 2008-06-15
Is it NTFS or ext3 etc.

The type of filesystem depends on how you need to mount it :)

---

### Post by Victormd on 2008-06-15
> **RokyFromGoky said:**
> My hard drive is divided in two parts (29.6 GB Media and 62.2 GB Media). Is it possible that they become automatically available, so that any shortcuts will actual work? Now I have to mount it first.   Or is it possible to change to owner to myself instead of root?

Thanks!!

Check the [HOW TO]("http://ubuntuforums.org/showthread.php?t=802699") on my signature...

---

### Post by Najmudin on 2008-06-15
I'm not sure if that will help but If it's ntfs you can go to applications > add/remove search for "NTFS configuration tool" click apply , after finishing the installation you'll find it on application>system tools and it should do the job.

---

### Post by Joeb454 on 2008-06-15
See the link at the bottom of my sig for that - It's a HowTo using that method (I provided screenshots where I could :))

---

