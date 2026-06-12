---
title: "How To Make LimeWire save files in a partition."
date: 2008-05-07
forum: New to Ubuntu
---

### Post by gkrules on 2008-05-07
I am dual booting windows vista and ubuntu. im forced to keep vista for schoolwork because there arent any linux versions of it.
but anyways,
my hdd is set up like this
sda1 - vista [ntfs]
sda2 - swap [swap]
sda3 - ubuntu hardy heron [ext3]
sda4 - data [ntfs]


how do i set up limewire so it will save all of my downloads onto the data partition of my harddrive?

---

### Post by damis648 on 2008-05-07
i do beleive in preferences you can change the directory to save downloaded files.

---

### Post by gkrules on 2008-05-07
> **damis648 said:**
> i do beleive in preferences you can change the directory to save downloaded files.

yea i know that but i cant change it the data partition
there is no option for it...the only option is stuff in the root [/] drive

---

### Post by crjackson on 2008-05-07
you have to mount the ntfs data drive before running limewire.  I would install ntfs-config and tell it to automount the partition on boot.

---

### Post by gkrules on 2008-05-07
> **crjackson said:**
> you have to mount the ntfs data drive before running limewire.  I would install ntfs-config and tell it to automount the partition on boot.

how would i do that?

and why did it create a new topic when i edited this one?

---

### Post by crjackson on 2008-05-07
```
sudo apt-get install ntfs-config
```

open up a terminal session and paste in this code...  then once it's installed go to your applications menu and launch the program.

---

### Post by gkrules on 2008-05-07
that does make sense

thanks i got it now

---

### Post by Bakon Jarser on 2008-05-07
> **crjackson said:**
> ```
sudo apt-get install ntfs-config
```

open up a terminal session and paste in this code...  then once it's installed go to your applications menu and launch the program.

This tool seems to only be for enabling write support for ntfs and does not have an option for auto mounting ntfs drives.

**Edit:**  Your drives must not be mounted when you launch the program in order for you to set them to automount

---

### Post by gkrules on 2008-05-07
yea i manually set it to automount
and if they are not unmounted when u start it...they wont even show up in the window

but it worked for wat i needed it to anyway so its cool

---

### Post by crjackson on 2008-05-07
> **Bakon Jarser said:**
> 

**Edit:**  Your drives must not be mounted when you launch the program in order for you to set them to automount

Yes I know.  I didn't think to mention it.

---

### Post by crjackson on 2008-05-07
> **gkrules said:**
> that does make sense

thanks i got it now


Your welcome, glad it got you going...  You can do the same thing by editing the fstab file but it's easier to tell you to install this GUI tool that does the same thing...:)

---

### Post by ptn107 on 2008-05-07
it does run on linux

[http://www.limewire.com/LimeWireSoftLinuxDeb](http://www.limewire.com/LimeWireSoftLinuxDeb)

---

