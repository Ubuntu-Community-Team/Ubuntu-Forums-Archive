---
title: "Formatted Disk Properties"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2008-08-30
I recently got a new second hard drive.  I installed it, formatted it with QTparted with Ext2.  Committed changes, remounted and everything worked fine.

I just tried to save something on the disk and it won't let me, it won't even let me create a new folder.

When looking at the permissions, the owner is root so I can't change the permissions.

How can I get this HD working?  I would like to learn both the terminal command and how to do it in the GUI as well.  Can someone please help me with this?

I researched the chown command, but not sure that is correct.

Thanks in Advance,
Eric

---

### Post by Harisz750 on 2008-08-30
open a terminal and type ```
sudo nautilus
```
give password and then try change the read/write permissions for your account. this will fix the problem

---

### Post by Vivaldi Gloria on 2008-08-30
> **Harisz750 said:**
> open a terminal and type ```
sudo nautilus
```
give password and then try change the read/write permissions for your account. this will fix the problem

It' better to use gksudo with graphical apps:

```
gksudo nautilus
```

because sometimes using sudo with  graph. apps. brakes things.

To change the ownership using command line use

```
sudo chown -R your_username:your_username mountpoint_of_the_disk
```

---

### Post by Harisz750 on 2008-08-30
you're right...  i forgot it. my mistake

---

### Post by J0hnnyBr@v0 on 2008-08-30
Thanks to both of you...I used chown and it worked.  I also used the gksudo command...much better as well.

With regard to gksudo and your explanation...should I use it for programs like Qtparted as well?  I think you said any graphical program.

Thanks again!!
Eric

---

### Post by Vivaldi Gloria on 2008-08-30
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)


sudo - terminal

gksudo - gnome

kdesu - KDE

---

