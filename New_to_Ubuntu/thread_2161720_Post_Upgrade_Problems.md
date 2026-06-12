---
title: "Post Upgrade Problems"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by GaryTheCat on 2013-07-11
Hello

I've recently upgraded to 13.04 and my machine is now painfully slow.  I have no idea why and would welcome any help in diagnosing and fixing the problem.

I'm happy to post anything that will help someone more knowledgeable than me.

Many thanks

Gary

---

### Post by DeathByDenim on 2013-07-11
The first thing I would try, is to see if there are may some processes going berserk. Try this in a terminal:
```
top
```
Are there any processes using more than 80 %CPU?
(you quit top by pressing 'q')

---

### Post by GaryTheCat on 2013-07-11
here's the output, couldn't copy and paste so here's the screenshot

[ATTACH=CONFIG]244627[/ATTACH]

---

### Post by ajgreeny on 2013-07-11
Compiz, xorg and screenshot are all taking a lot of resources.

What hardware are you using and in particular which graphic card as I suspect that is the main cause of your problem; 13.04 has a new xorg version which is presenting difficulties with some hardware.

---

### Post by GaryTheCat on 2013-07-11
lspci gave me this for graphics (at least I think that's what it is)

```
01:00.0 VGA compatible controller: NVIDIA Corporation G84M [GeForce 8600M GT] (rev a1)
```

Can I uninstall compiz?

Screenshot was only open to get the screenshot and I'm not sure what xorg is :-/

---

### Post by DeathByDenim on 2013-07-11
Did you try installing the proprietary NVidia drivers? If not, they may help you.
```
sudo apt-get install nvidia-current-updates
```
You need to reboot after that.

I don't think you can uninstall compiz, since the Unity desktop depends on it as far as I know.
Xorg is the display server. It's basically a layer between what you see on the desktop and your graphics card.

---

### Post by GaryTheCat on 2013-07-11
Thanks for that - I'll give it a try.

I've also noticed some other issues since upgrading - the most irritating is the fact that my laptop stays on when I close the lid and doesn't suspend like it used to - I've fiddled with it but have no idea how to fix it :-/

---

### Post by GaryTheCat on 2013-07-12
would it be a good idea to try one of the other "buntu" desktops?

---

### Post by su:bhatta on 2013-07-12
What is the specifications of your laptop? Xubuntu will definitely be lighter !

---

### Post by craig10x on 2013-07-12
You could always try a fresh install...from what i understand, upgrades can go perfect, or have problems...I am going to try my first upgrade from 13.04 when 13.10 final comes out and keep my fingers crossed for a 100% smooth upgrade, but always keeping in back of my mind that if all doesn't go well, then i will just re-install fresh (which i had planned on doing anyway)...so the upgrading will be a nothing to lose kind of deal...

I'd also recommend running 13.04 on live session to see how well it runs...if it's good then you probably have a pretty good chance that a clean re-install will straighten things out properly...

---

### Post by GaryTheCat on 2013-07-12
I seriously need to tidy up my partitioning before I do anything else, once I've got my /home in its own partition I'll be happier doing a fresh install

---

### Post by GaryTheCat on 2013-07-12
See what I mean:

```
gary@gary-Inspiron-1720:~$ sudo fdisk -l[sudo] password for gary: 


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      449819      224878+  de  Dell Utility
/dev/sda2          450560    21422079    10485760    7  HPFS/NTFS/exFAT
/dev/sda3   *    21422080   229195767   103886844    7  HPFS/NTFS/exFAT
/dev/sda4       229195776   234438655     2621440    f  W95 Ext'd (LBA)
/dev/sda5       229197824   234438655     2620416   dd  Unknown


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71b32ced


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   716951551   358474752    7  HPFS/NTFS/exFAT
/dev/sdb2       716953598   976771071   129908737    5  Extended
/dev/sdb5       716953600   972582911   127814656   83  Linux
/dev/sdb6       972584960   976771071     2093056   82  Linux swap / Solaris



```

---

