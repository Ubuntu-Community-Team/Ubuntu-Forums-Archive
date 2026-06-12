---
title: "[SOLVED] Adding a 2nd HDD"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by thomand52 on 2008-05-26
I'm new to Linux and want to install another HDD to my box. I'm unsure where to start.
I've installed the drive in my system but when I attempt to access it it tells me the drive can't be mounted.I've tried creating a new folder on this drive in terminal but without much luck. 
Any help or direction would be much appreciated.

---

### Post by philinux on 2008-05-26
Install gparted from synaptic.

You'll have to use System>prefs> Main menu to enable the menu option in Admin.

You can then use gparted on your new drive to create a partition.

---

### Post by iansane on 2008-05-26
Brand new harddrive? is it formated?

Have you tried accessing it with gparted?
gparted is in synaptic and if installed is under System>Administration>Partition Editor

Type ```
 sudo fdisk -l 
```
in terminal and see if it shows up in the list of drives.

---

### Post by thomand52 on 2008-05-26
Thanks , I didn't know about gparted. Once I found it everything worked well.

---

