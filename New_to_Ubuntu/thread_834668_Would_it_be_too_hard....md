---
title: "Would it be too hard..."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by ubuntnewb on 2008-06-19
To have a simply utility you could type to get a list of drives and what linux has labeled them? I have a machine with a cdrom on the primary PATA controller and my hard disk is on the first sata port, but I'll be darned if they're labeled hda and sda!@#$@%@#$%@$^%$#@ :mad:

---

### Post by sdennie on 2008-06-19
You could try:

```

df

```

---

### Post by bumanie on 2008-06-19
To get hard drive names and UUID numbers > sudo blkid You can also > cat /etc/fstab and your cd-rom(s) should be listed there as will your automounting hard drives and floppy (if you have one). You can do > sudo lshw which gives you  along list of all the devices attached to the computer, this will give you the model of your cd-rom as well as its device name - this is called 'logical name' in this list. Hope this helps.

---

