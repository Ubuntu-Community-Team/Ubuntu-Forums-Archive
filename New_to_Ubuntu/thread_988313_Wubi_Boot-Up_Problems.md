---
title: "Wubi Boot-Up Problems"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by shoot2kill on 2008-11-20
i installed ubuntu through the new wubi installer to a second hard drive on my system.

i have recently been troubleshooting my windows problems which involved changing the msconfig boot-up settings, and reset them to default settings not thinking about it deleting the boot-up option for the Ubuntu OS.

does anyone know what file i have to edit, and what needs putting so that windows gives me the option of booting into Ubuntu.

I am currently on a slow-ish internet and do not want to download a full live CD, and fix the grub that way. and re-installing Ubuntu is not an option either due to files that need backing up..

any help appreciated...

---

### Post by CyberPrime on 2008-11-20
sounds to me like you played with the boot.ini. I hear that you can uninstall and reinstall Wubi, and that should take care of it but i am unsure, I don't use Wubi. Post the contents of your boot.ini file (C:\boot.ini), please. If you can not see it open up My Computer, go to Tools, Folder Options, View, Click the "Show Hidden Files and Folders" radio button, Click Ok.

---

### Post by shoot2kill on 2008-11-20
vista doesnt use a boot.ini file like XP does.. :(
thanks anyway.
and i thought that if i re-install wubi, it will re-install my ubuntu and i will lose everything..

---

### Post by Neostar on 2008-11-20
Well all of your files are in /home right, so this is all in a file called home.disk, just look for it and copy it to somewhere safe.

You can then reinstall Ubuntu and mount it from within the new installation using the following commands..

mount -o loop /path/to/home.disk.old /new/mountpoint

By the way you can use something like Parted Magic to mount and copy your files over if you want.

Parted Magic Live CD (47.2M)
[http://downloads.partedmagic.com/](http://downloads.partedmagic.com/)

---

