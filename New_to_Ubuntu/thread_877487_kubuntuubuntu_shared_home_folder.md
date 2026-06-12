---
title: "kubuntu/ubuntu shared home folder"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by noland on 2008-08-01
hi!  

I installed Ubuntu Hardy with a separate /home partition, then installed KUbuntu on a new partition with the same username/password everything.  Is it possible to use the same /home partition for both installations? i guess it is but i just now cant figure it out... any help apreciated!

Phil

---

### Post by noland on 2008-08-01
or any other place i should be redirected??  heeeeeeeeellp hehehehehe

---

### Post by LowSky on 2008-08-01
when you installed you should have used manual partition the hard drive. You can then choose what partitions can be what and therefor share a /home patition

---

### Post by eightmillion on 2008-08-01
You should just be able to create a symbolic link from one to the other. This is a rough example. You copy all the contents of one of them to the other. Then rm -rf that one. Then you would do something like 'ln -s /media/disk/home/user /home/'

---

### Post by noland on 2008-08-01
when i first installed ubuntu, i did use the manual partitioning of 2 15Go partitions, which on one went the original install.. also did a 50 Go partition for the /home and another 2Go for the SWAP.  Now, secondly i installed Kubuntu on the second... you say i should have again chosen manual partitioning to "reformat" the future /home partition?? i thought the first time should have been the right one, but then again what do i know :)

---

### Post by JillSwift on 2008-08-01
All you'd have to do when installing Kubuntu is to use "manual" and POINT /home to your home partition. You don't have to repartition anything or format anything but the new install.

***but***:
Why are you installing a whole Kubuntu installation when KDE and Gnome can easily co-exist in the same installation?

```
sudo apt-get install kubuntu-desktop
```to get Kubuntu all settled in. You can then select Gnome or KDE from the login screen menu.

---

### Post by noland on 2008-08-01
i heard that KDE and GNOME did not coexist very well, maybe im wrong.. actually i also want to keep that second partition in case i ever want to try other distros... i will reinstall KUbuntu tomorrow with the "point to" thingy tomorrow, cuz now im dead beat hehehehe thanks all, ill keep you posted!

---

