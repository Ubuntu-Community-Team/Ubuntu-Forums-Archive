---
title: "[SOLVED] Lost permission to my own USB drive!"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-07-20
I recently reformatted one of my USB drives to ext3.  It mounts ok, but I can't put any files on it, because I no longer have permission.  Is there any way to give myself permission?  I am the administrator on this machine.

Thanks!

BTW the drive was mounted automatically, not manually via the terminal.  It is mounted in /media/SEAGATE_P

---

### Post by macaholic on 2008-07-20
You could try using chmod, by typing ```
sudo chmod -R 755 /media/SEAGATE_P
```

---

### Post by pi.boy.travis on 2008-07-22
I still get:

Error opening file '/media/SEAGATE_P/rockbox.zip': Permission denied

:confused:

---

### Post by hansdown on 2008-07-22
Hi pi.boy.travis. I googled rockbox zip and got thishttp://www.google.ca/search?q=rockbox.zip&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a  Hope it helps.

Sorry. my pasting is doing strange things.  [http://www.google.ca/search?q=rockbox.zip&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=rockbox.zip&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by pi.boy.travis on 2008-07-22
> **hansdown said:**
> Hi pi.boy.travis. I googled rockbox zip and got thishttp://www.google.ca/search?q=rockbox.zip&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a  Hope it helps.

Sorry. my pasting is doing strange things.  [http://www.google.ca/search?q=rockbox.zip&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=rockbox.zip&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)


The Rockbox.zip file was just an example, I get the same message with any file.  I do use Rockbox, which is replacement open source firmware that works on lots of players, like the iPod.  I highly recommend it!  But right now I need to get my USB working.  I don't know how to get permissions back, I never had this problem with FAT 32, but I think that I will really see some performance benefits by switching to ext3.  

Thanks!

---

### Post by pi.boy.travis on 2008-07-24
I noticed something strange.  I can't write anything to the root of any ext3 partition, or any other file system except vfat.  Is there a group or something that I can add myself to?

---

### Post by Potatoj316 on 2008-07-24
I would sugest chown, it changes the owner of the directory
im not sure how to use it though, you will need to specify the directory and the user to own it

---

### Post by pi.boy.travis on 2008-07-24
user: travis

directory: /media/SEAGATE_P

---

### Post by Darkchef on 2008-07-24
> **pi.boy.travis said:**
> I recently reformatted one of my USB drives to ext3.  It mounts ok, but I can't put any files on it, because I no longer have permission.  Is there any way to give myself permission?  I am the administrator on this machine.

Thanks!

BTW the drive was mounted automatically, not manually via the terminal.  It is mounted in /media/SEAGATE_P

try this

in the terminal type:

```
sudo nautilus
```

a browser window should come up, now right click on your usb drive.

go to properties -> permissions

you should be able to set permissions for your access. i fixed my usb pen earlier that way, although my drive is fat32.

---

### Post by pi.boy.travis on 2008-07-24
Thanks!  That did it!

---

