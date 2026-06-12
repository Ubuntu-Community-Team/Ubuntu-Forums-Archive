---
title: "how to uninstall?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Immanuel Magalit on 2008-09-13
I have installed ubuntu on my hard drive.  Unfortunately this has made Windows slower.  I don't have a powerful laptop, and everything I do on windows now is choppy.  Too high a price for me to pay unfortunately.  How do I completely and cleanly uninstall ubuntu?

---

### Post by liquidfunk on 2008-09-13
Ubuntu won't make your Windows partition slow. I suggest you just do a Disk Defragment, and clean all your temp files.

---

### Post by Immanuel Magalit on 2008-09-13
Is it just a coincidence it happened just after I installed Ubuntu?  Anyway I will try your suggestion.  Thanks!

---

### Post by rraj.be on 2008-09-13
> **Immanuel Magalit said:**
> Is it just a coincidence it happened just after I installed Ubuntu?  Anyway I will try your suggestion.  Thanks!

To uninstall ubuntu or any other OS you have to formate the partition in which it has been installed.

---

### Post by arpanaut on 2008-09-13
> **rraj.be said:**
> To uninstall ubuntu or any other OS you have to formate the partition in which it has been installed.
TRUE... but usually it is not so simple.
Ubuntu usually re-writes the mbr of windows partitions and inserts a pointer to grub on the Ubuntu part. 
So one could be left with an unbootable 'puter. To prevent that, before formating/deleting the Ubuntu part. the mbr should be rewritten to the windows part then... delete/format the unwanted OS.

See this for help restoring mbr... 
[http://ubuntuforums.org/showthread.php?t=740221&highlight=NTLDR](http://ubuntuforums.org/showthread.php?t=740221&highlight=NTLDR)

An ounce of prevention is worth a pound of cure.

---

### Post by northern lights on 2008-09-13
> **Immanuel Magalit said:**
> I have installed ubuntu on my hard drive.  Unfortunately this has made Windows slower.  I don't have a powerful laptop, and everything I do on windows now is choppy.  Too high a price for me to pay unfortunately.  How do I completely and cleanly uninstall ubuntu?
Did you use Wubi or the like?
As liquidfunk correctly put it, a standalone OS install will not affect another OS install.

Can you post your partition table, maybe?

---

