---
title: "Suspend/Hibernate doesn't work in Hardy"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by urvaksh on 2008-05-01
Upgraded to Hardy. The suspend/hibernate does not work on my laptop. Didn't work with Gutsy either.
Is there a workaround or do I have to live without it.

---

### Post by nofrendo on 2008-05-01
There are some problems with hibernation, but sometimes making your swap file larger helps. Try making it about double the size of your RAM

---

### Post by urvaksh on 2008-05-01
How do i increase my swap file. In simple english please. i'm a noob:)
Thanks

---

### Post by excogitation on 2008-05-02
Install gparted using Synaptic
(or sudo apt-get update
sudo apt-get install gparted),

and then resize the partition with
System -> Administration -> Partition Editor.

You might have to activate the partition
if $ free shows Swap: 0 0 0
using sudo swapon /dev/"swap partition"
(you can see which partition it is e.g.
with gparted)

To permanently activate the swap partition
you have to edit fstab accordingly.

---

### Post by urvaksh on 2008-05-02
Thanks

---

