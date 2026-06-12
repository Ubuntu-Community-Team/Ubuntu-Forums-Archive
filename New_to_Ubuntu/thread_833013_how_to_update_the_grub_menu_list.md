---
title: "how to update the grub menu list"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by littletinman on 2008-06-18
Ok here,s the deal. I recently installed XP on a seperate partition on my laptop. I had to delete my test partition of ubuntu to do so because i had tooo many primary partitions. Everything went well except now i can only boot into my XP  partition (sda 0,0), and my 32 bit ubuntu partition (sda 0,1), from the grub list. the other partitions listed there don't boot into my 64 bit ubuntu (sda 0,2 or 3, i can't remember which). I need to be able to boot into the 64 bit ubuntu. So how do i update grub so that it automatically deletes the dead links and detects the real ones?


 Well, i eargerly await your help.

---

### Post by rraj.be on 2008-06-18
I hope just this will do what you needed.

```
Boot into live cd
```

Open terminal and type 
```

sudo grub

find /boot/grub/stage1
```

if it returned like ```
(hdx,y)
```

type 

```
root (hdx,y)

setup (hdx)

quit

sudo reboot
```

---

### Post by Chr0mis on 2008-06-18
There are two options to edit the grub menu, one is temporary, the other one is permanent. 

Temp: before grub boots into the 32bit ubuntu or the win xp, just move to the entry you want to boot, for example the not-working linewhich boots into ubuntu 64b (but fails). type "e" for edit, and just enter towards the line that specifies the hard disk and partition. Just backspace the wrong entry and fill in the correct harddisk and partition. You can use tab completion if you'd like. Then just press enter and "b" to boot. 

The permanent one: manually edit grub.lst: 
```
 sudo nano /boot/grub/menu.lst
```
Scroll to the line which boots into ubuntu 64b (but fails) and enter the correct hard disk and partition. You can comment out the not-working entries by putting "#" in front of them.

---

### Post by kpkeerthi on 2008-06-18
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by littletinman on 2008-06-18
I already did what the first guys said. Now i'll try what the second guy said.

---

### Post by littletinman on 2008-06-18
Does sda4 mean (sda 0,4)

---

### Post by kpkeerthi on 2008-06-18
> **littletinman said:**
> Does sda4 mean (sda 0,4)

It would be (hd0,3)

---

### Post by ruffEdgz on 2008-06-18
Well, I was reading everyone's response and they are all right but are you editing the /boot/grub/menu.lst without mounting the ubuntu partition?

If you aren't, it won't help because you will be changing what's on the Live CD. What you need to do is mount your ubuntu partition to the live CD and then go from there.

```

sudo mkdir /mnt/ubuntu
sudo mout -t ext3 /dev/sdb1 /mnt/ubuntu
df -h

```

After you mount the ubuntu partition, then you can go into /mnt/ubuntu/boot/grub/ to go edit the menu.lst file. Do what Chr0mis said which is:

> 
Scroll to the line which boots into ubuntu 64b (but fails) and enter the correct hard disk and partition. You can comment out the not-working entries by putting "#" in front of them.


Hope that helps!

---

