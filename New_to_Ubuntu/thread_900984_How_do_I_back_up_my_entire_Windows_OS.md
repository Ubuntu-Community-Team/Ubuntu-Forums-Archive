---
title: "How do I back up my entire Windows OS?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Qebafhzn on 2008-08-25
Boot loaders and all?
Incase something wierd happens when I try to install Ubuntu...

---

### Post by crispy_420 on 2008-08-25
Are you talking about maybe making an image of the drive in its current state?

---

### Post by Qebafhzn on 2008-08-25
> **crispy_420 said:**
> Are you talking about maybe making an image of the drive in its current state?

Yes, if that means it keeps all the files of the OS.

---

### Post by unca.paka on 2008-08-25
Just back up whatever files you need(music, docs, pics, etc) then install Ubuntu. Shouldnt cause any problems unless you install to your windows drive/partition. 
If something does go wrong after you install grub, pop in your windows cd, goto a recovery console, and fixmbr. That will reload the windows bootload.

If your really worried about it, you can pick up a copy of Norton Ghost and make an image of your windows install, then burn it(or any imaging software, just have experience w/Ghost)

---

### Post by gaspard.leon on 2008-08-25
do you have 2 harddrives?

You can buy another one the same as your first one (equal or larger size) then make a disk image of it...

Or, even better, get a new hard drive, install Ubuntu on it, and put your windows drive away as a backup... or just install with Wubi for now so you can try it out without changing your boot loader.

If you don't have 2 harddrives, you can make a disk image backup onto DVDs, but it's not that easy unless you have some software...

I suggest backing up your actual user data separately as that's the important bit...

so to recap:

if you have 2 hard drives, install ubuntu on one and keep your windows drive unmodified (unplug it).

if you have 1 hard drive I suggest you try Wubi (the windows ubuntu installer) if you're worried about boot loaders.

---

### Post by Qebafhzn on 2008-08-25
Oh... I never even heard about Wubi...

---

### Post by gaspard.leon on 2008-08-26
The Wubi installer:
[http://wubi-installer.org/](http://wubi-installer.org/)

Basically it's a way of installing Ubuntu into a file in your windows drive... it then adds an entry to your boot.ini file so the windows boot menu will have an ubuntu option.

the advantage is you can uninstall it simply from within windows and it will just delete the file with Ubuntu in it, and remove the item from your windows boot menu.

hope this helped.:popcorn:

---

### Post by Gregmond on 2008-08-26
To make a full backup including bootsectors etc would need something like Norton/Symantec GHOST and enough space for the image file.

---

### Post by Gone fishing on 2008-08-26
Well one way: 

1 Add a second hard drive the same size as your primary drive.
2 boot up on gparted disk or the Ubuntu install disk and run gparted
3 Copy your Windows partition from one disk and paste to the other disk. The second disk will have all your windows stuff.
5 Flag the new partition as bootable 
6 Remove the old disk it should work although you may need to start up on your XP disk and run fixboot and fixmbr.
7 Once you've got you spare windows disk you can do all the messing about in full confidence :)

---

### Post by crispy_420 on 2008-08-26
Never used it myself but here is an interesting looking program:

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

