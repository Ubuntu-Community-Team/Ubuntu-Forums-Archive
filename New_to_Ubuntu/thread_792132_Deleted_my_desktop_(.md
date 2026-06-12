---
title: "Deleted my desktop :("
date: 2008-05-12
forum: New to Ubuntu
---

### Post by S0VERE1GN on 2008-05-12
hey all, major problem here. 

I installed ubuntu, and i was trying to delete evolution email client, and accidentally deleted my desktop :( 

when i say desktop, i mean that none of the toolbars show up anymore, i just have a picture of my desktop background. 

i can go into restore mode and get to the dos type terminal from there, i just need to know what the code is to like...reinstall the stuff i deleted, or reinstall ubuntu from there.

Thanks in advance :-D

---

### Post by SunnyRabbiera on 2008-05-12
ah, well sadly the evolution client is tied into gnome in ubuntu.
to get back a desktop try this command:
sudo apt-get ubuntu-desktop

---

### Post by S0VERE1GN on 2008-05-12
didn't work... is there a command to revert to generic ubuntu setup? so i can redownload ubuntu from the terminal?

---

### Post by UnknownFear on 2008-05-12
Unfortunatley, the best bet would be to re-install Ubuntu.

---

### Post by S0VERE1GN on 2008-05-12
can i do that from a terminal? or do i just need to suckit up and ask for a hard copy form the site?

---

### Post by Monicker on 2008-05-12
> **S0VERE1GN said:**
> can i do that from a terminal? or do i just need to suckit up and ask for a hard copy form the site?


```
sudo apt-get install ubuntu-desktop
```


That should have worked. You should do CTRL + ALT + F3 to get to a text screen, then log in and execute that command.

---

### Post by nkri on 2008-05-12
Try forrestcupp's code from [this]("http://ubuntuforums.org/showthread.php?t=774055") thread, it should get things up and running for you...

---

### Post by S0VERE1GN on 2008-05-12
ok, i cant get any of those codes to work, because the desktop won't install from alt ctrl f3, and i can't reconfigure a file that's not there. 
ontop of that, i can't get ubuntu to reinstall from the disk i just made....
how do i boot from a cd using the terminal? maybe that will work.

---

### Post by nkri on 2008-05-13
>  i can't get ubuntu to reinstall from the disk i just made

What do you mean?  Can you not start from the disc, i.e., does it automatically boot into ubuntu (the one on the hard drive) and not the CD?  or can you get to the Live CD but not actually install it?

If it automatically boots from the HDD, post your system specs so we can change your BIOS.  If it can't install, I don't know what you can do.

---

### Post by Inxsible on 2008-05-13
ubuntu-desktop is a meta package and is NOT needed for the proper functioning of Ubuntu. It merely points to all the default applications that need to be installed in a brand new Ubuntu install.

I have removed not only evolution, but also a bunch of other crap like Sound juicer etc...which removes ubuntu-desktop. The only time you need ubuntu-desktop is when you upgrade from one distro to the other -- say from Gutsy to Hardy.

---

