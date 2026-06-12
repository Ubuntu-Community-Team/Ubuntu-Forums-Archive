---
title: "VirtualBox &amp; Different Kernals"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Harpz on 2008-08-20
Ive just figured out how to get Virtualbox 1.5.6_OSE on system and im just putting XP on it to see what it runs like,

Only problem i had with Virtualbox so far is i have to boot off Ubuntu 8.04 kernal 2.6.24.16-generic instead of my 8.04 kernal 2.6.24.19-generic from the menu.

Neither my GeForce 6600GT or my onboard sound are detected in Ubuntu 8.04 kernal 2.6.24.16 for some reason but get detected when i boot Ubuntu 8.04 kernal 2.6.24.19-generic.

Ive only been using Ubuntu for just over a week now, how would i get my 6600GT and sound recognized in 2.6.24.16 so i can have decent graphics and sound with VirtualBox? or should i just wait for an update on Virtualbox 1.5.6_OSE so that it works with new kernal (2.6.24.19)

Mike

---

### Post by quibbler on 2008-08-20
Try virtualbox 1.6 download here:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Regards quibbler

---

### Post by Harpz on 2008-08-20
As im still learning whats the reason for the Ubuntu 8.04 kernal 2.6.24.16 not picking up my 6600GT and sound?

If i can get it to do that i can just stick with Virtualbox 1.5.6_OSE until there an update.

I did try Virtualbox 1.6, it said installed but i had no icons to start it in any of my menus. and when i tried to run it from Virtualbox from Terminal it said install Virtualbox OSE. So something didn't install as it should have.

Mike

---

### Post by benerivo on 2008-08-20
Why doesn't virtualbox work with the 2.6.24.19 kernel? See [this]("http://ubuntuforums.org/showthread.php?t=895564&highlight=virtualbox") thread.

---

### Post by Harpz on 2008-08-21
Cool got it running many thanks
Had to use: ```
sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
```

to get correct modules for kernal

Thanks again
Mike

---

