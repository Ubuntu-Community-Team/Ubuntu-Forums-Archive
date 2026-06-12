---
title: "Unable to delete partition in disk utility"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by mmohithster on 2011-12-08
I am using ubuntu11.10 .I have done two partitions in the disk utility to the free space after installing ubuntu.NEW VOLUME D and NEW VOLUME E....am not able to delete the NEW VLOUME E.the only difference beteween the two partition as in the page is the partition type......but am not able to change the partition type from empty(0*00) to NTFS...also in the HOME folder NEW VOLUME D comes under devices and NEW VLOUME E comes under computer. and if i try to unmount it from the HOME this is the message that i get.....*[I]umount: /media/New Volume E is not in the fstab (and you are not root)*[/I]

What should i do to get both the partitions under DEVICES...???

---

### Post by fdrake on 2011-12-08
do in the terminal:
```

sudo umount -a

```
#now exit disk-utility and restart again and try to delete the partition or follow my commands to do the same thing with gparted.
```

sudo apt-get install gksudo gparted
gksudo gparted

```
hilihgt your partition and delete it

---

### Post by mmohithster on 2011-12-09
its not working with above method
please help....

---

### Post by mmohithster on 2011-12-09
The main problem is everytime i shut down and start my system.......the NEW VOLUME E is not visible ...it will be visible only if i go to the disk utility and mount it.....

---

