---
title: "Floppy Drive Missing"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by elleppahc on 2008-11-02
My Floppy drive is not showing on my system since upgrading to 8.10
Can anyone help please.

---

### Post by an93l on 2008-11-03
I am having the exact same issue, I have been searching for hours on how to sort this but nothing. I will keep looking and post any answers I find here.

---

### Post by ffixcollector on 2009-01-23
I also have the same problem

---

### Post by kansasnoob on 2009-01-23
Look at my /etc/modules:

> lance@lance-desktop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
floppy

If you look at yours by running:

```
cat /etc/modules
```

You'll probably see that the last line "floppy" is not there. To edit the file run:

```
sudo gedit /etc/modules
```

Add floppy just as you see in my /etc/modules, then click on Save, then go to File > Quit.

Floppy Drive should now show up in Places > Removable Media.

---

### Post by Tek-E on 2009-01-23
> **elleppahc said:**
> My Floppy drive is not showing on my system since upgrading to 8.10
Can anyone help please.

I have had the same problem before.  I had to mount mine manually.  You can try it.  Wont garentee it will work for you but it did for me.

```

mount /dev/fd0

```

---

### Post by ffixcollector on 2009-02-10
The floppy drive shows up in "removable media," but when I click on it, nothing happens.

---

### Post by plucky on 2009-02-11
> **ffixcollector said:**
> The floppy drive shows up in "removable media," but when I click on it, nothing happens.

Open a terminal and post output of ```
cat /etc/fstab
```

It needs to have a line for the floppy like ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

You will have to issue the command "sudo mount -a" to enable the floppy file system


Good Luck

---

