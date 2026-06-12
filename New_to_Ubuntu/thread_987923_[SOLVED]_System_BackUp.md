---
title: "[SOLVED] System BackUp"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by mesmith on 2008-11-20
I have always used a verbatim backup program such as Drive Image or Norton Ghost.  Is there an equivalent pkg for xubuntu?  If not, can someone suggest a GUI BackUp pkg that will allow me to write the important stuff to a CD/R or DVD?  Verbatim backups have saved me tons of work over the years on Windows based systems.  What are the important parts of Linux to backup if verbatim pkgs don't exist?

Thanks,

Mike

---

### Post by Crafty Kisses on 2008-11-20
You can try "PartImage".

---

### Post by bumanie on 2008-11-20
There is clonezilla, partimage, ghost4linux and dd tools (command line) - I like dd due to its simplicity. Look them up and come back with questions, if you have any.

---

### Post by ddixonr on 2008-11-20
I like remastersys for my system backups. It can back up an entire file system to an iso file, which is actually a live cd version of your system. It can backup the full system as well, but my home directory gets pretty large so I just copy it to an external hard drive, then drop it back in once I restore the file system. Reboot and done.

Best part about remastersys is that you can take your custom live cd to a completely different computer if you'd like. The live cd will install the new hardware just like a fresh install would, or just use the live cd as a completely customized and portable os.

---

