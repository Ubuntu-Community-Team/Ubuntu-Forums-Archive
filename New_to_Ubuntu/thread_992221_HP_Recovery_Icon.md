---
title: "HP Recovery Icon"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by dmalpack89 on 2008-11-24
I've been customizing my new 8.10 install and I've been learning quite a bit. However, my HP_RECOVERY drive is constantly showing up on my desktop every time I boot ubuntu. I don't want it there, but the only option I've seen is to unmount it. I learned how to take root control in terminal and everything just fine, but it still shows up everytime. It would be a pain to have to unmount it everytime I booted. Any ideas?

I'm running AMD x 64, dual booting with Windows Vista Home Premium on an HP Pavillion dv6000 series. Thanks!

---

### Post by phidia on 2008-11-24
Look at your /etc/fstab file. That partition should show up there.
Just put a "#" in front of the entry for the partition. It won't auto mount after that.

---

### Post by dmalpack89 on 2008-11-24
> **phidia said:**
> Look at your /etc/fstab file. That partition should show up there.
Just put a "#" in front of the entry for the partition. It won't auto mount after that.

It says I don't have permissions necessary to save file after I edit it. It also says please check that you have typed the location correctly and try again.

Never mind, I was able to figure it out with gedit in terminal. Thanks!

---

### Post by MJWitter on 2008-11-24
open up a terminal and type:
> sudo gedit /etc/fstab
That will allow you to edit the file as root.
Just be careful what you do in that file as it is very NB for your system.

---

### Post by SunnyRabbiera on 2008-11-24
Those recovery partitions can be a pain indeed, but they come in handy with a windows system.

---

