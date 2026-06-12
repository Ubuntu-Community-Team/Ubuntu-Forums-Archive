---
title: "ubuntu disappeared!!!"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by atif7865 on 2008-10-25
Hi,
I am new to Linux. i had set up triboot on my laptop. I had winxp , winVista and Ubuntu. recently i had a problem with my vista and i had to reinstall the vista ( i installed it on its previous location, i did not overwrite the ubuntu partition). but now that i have finished the installation after restart i dont see the boot manager for Ubuntu. i can only see two options now, windows vista and previous versions of window..
how can i bring back the linux boot manager so that i can boot into either of the 3 operating systems.

i really appreciate your help.

thanks

---

### Post by lordadi on 2008-10-25
Hi,

I think you should boot off of your Ubuntu live disk, then you can get your stuff off on to an external HDD, followed by a reinstall. I believe this is the easiest way. The only other way I know is to reinstall grub but am unaware how to do that.



Lordadi.

---

### Post by Helios1276 on 2008-10-25
This should help ya, sounds like Vista destroyed Grub.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Aaron850679 on 2008-10-25
> **atif7865 said:**
> Hi,
I am new to Linux. i had set up triboot on my laptop. I had winxp , winVista and Ubuntu. recently i had a problem with my vista and i had to reinstall the vista ( i installed it on its previous location, i did not overwrite the ubuntu partition). but now that i have finished the installation after restart i dont see the boot manager for Ubuntu. i can only see two options now, windows vista and previous versions of window..
how can i bring back the linux boot manager so that i can boot into either of the 3 operating systems.

i really appreciate your help.

thanks

try this [http://www.acronis.com/homecomputing/products/diskdirector/?source=us_google&keyword=bootdisk&gclid=CJbA4KTZw5YCFQIMswodWkJkyw]("http://www.acronis.com/homecomputing/products/diskdirector/?source=us_google&keyword=bootdisk&gclid=CJbA4KTZw5YCFQIMswodWkJkyw")

just use the free trial and use it on XP not Vista



:)

---

### Post by drowner on 2008-10-25
Vista has overwritten your boot manager with it's own.
Does the boot manager look different? 

You will need to reinstall grub.

[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by eternalnewbee on 2008-10-25
All I can tell you is that when you reinstalled windows, it took over grub. There is a solution to your problem, so be patient, til a more experienced user can guide you through the process
Good luck.

---

### Post by drowner on 2008-10-25
> **lordadi said:**
> Hi,

I think you should boot off of your Ubuntu live disk, then you can get your stuff off on to an external HDD, followed by a reinstall. I believe this is the easiest way. The only other way I know is to reinstall grub but am unaware how to do that.



Lordadi.

Hi - there's no need to reinstall just yet. The OP should try to reinstall GRUB first. THere are at least 2 links already on this page that deal with the 'SuperGrubDisk' that will do that.... take care with what advice you offer - a reinstallation is generally a last, last resort.

---

### Post by Aaron850679 on 2008-10-25
or use the acronis boot manager it will install grub also

---

### Post by drowner on 2008-10-25
> **Aaron850679 said:**
> or use the acronis boot manager it will install grub also

Really? Or does it install it's own boot manager? I'm not familiar with it.

---

### Post by atif7865 on 2008-10-25
I am gonna try the Super_Grub_Disk.
i will let you guys know what happened in afew moments,

thanks for all the help.

GOD! this forum is ACTIVE !!! :)

---

### Post by bapoumba on 2008-10-26
> **drowner said:**
> hi - there's no need to reinstall just yet. The op should try to reinstall grub first. There are at least 2 links already on this page that deal with the 'supergrubdisk' that will do that.... Take care with what advice you offer - a reinstallation is generally a last, last resort.

+1 !

---

