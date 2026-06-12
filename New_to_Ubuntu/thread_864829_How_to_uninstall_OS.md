---
title: "How to uninstall O/S?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Bomber Ben on 2008-07-20
Hi!
to simplify things, can anybody advise me how to uninstall my ubuntu ultimate edition system, so I can then either locate or reinstall my windows xp???

---

### Post by Martje_001 on 2008-07-20
Just pop in your XP disc. You'll be asked to format your drive. Answer yes.

[SIZE="1"](if you had googled, you've found this answer also..)[/SIZE]

---

### Post by Canis familiaris on 2008-07-20
Boot with XP install CD.
Go to recovery mode.

Type: FIXBOOT

Delete your Ubuntu Partitions.
Done.

---

### Post by sharks on 2008-07-20
if u have ubuntu live cd boot it and then go to system--administration--gparted(partition editor). then select the partition u have installed ubuntu ultimate and format it. then reinstall window$.

---

### Post by waspbr on 2008-07-20
kk, to get rid of ubuntu you can just use a live cd and use gparted

it shoudl be  in the tab system> administration> partition editor

alternatively you can just do a alt+F2 and type gparted

once you are in you just need to identify where you linux partition is, you can distiniguish by the size and file system, if u still have windows installed just erase everything that is not ntfs (considering you don't have any other linux partitions). once you are done reboot.

k,you may get an error message,treboot pop the winxp cd in and go to the recovery console (press r), once you go through the formalities,  there you do "fixmbr". your previous windows install should pop up on reboot.

alternatively just use the gparted in the live cd to wipe the whole thing and install windows xp from scratch.

if I may ask is there any reason you want to remove ubuntu?

---

### Post by sharks on 2008-07-20
> **waspbr said:**
> 
If I May Ask Is There Any Reason You Want To Remove Ubuntu?

+1

---

### Post by zipperback on 2008-07-20
> **Bomber Ben said:**
> Hi!
to simplify things, can anybody advise me how to uninstall my ubuntu ultimate edition system, so I can then either locate or reinstall my windows xp???



You can pretty easily setup your system to dual boot Ubuntu and Windows.

Check the following link.
[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

I posted links to several how to pages.

If you just want to remove Linux and reinstall Windows XP, then you can read the following page from the Microsoft.com website.
[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)


- zipperback
:popcorn:

---

