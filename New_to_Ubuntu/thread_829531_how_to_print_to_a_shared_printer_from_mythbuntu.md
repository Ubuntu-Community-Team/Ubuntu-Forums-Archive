---
title: "how to print to a shared printer from mythbuntu?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by allene222 on 2008-06-14
I want to print to a printer that is on another linux box from a mythbuntu system.  I have searched the internet and most posts say to go to system->administration->printing.  There is no administration under system in mythbuntu and no printing icon anywhere.  Additionally, there is no printer icon under applications->settings.  I read that installing the printer icon slows  the system down, which is a bad thing in mythtv as it barely works as it is.  

I installed CUPS and have a configuration page at [http://localhost:631/](http://localhost:631/) but can't get it to print a test page.  I searched its help pages but always get 200 hits or none.

The printer is at //192.168.1.1 and the queue is called "printer".  It is an HP Laser Jet 1200 using PCL5.

Anyone know how to do this?

Allen

---

### Post by perce on 2008-06-15
Maybe it's hidden in the menu: try to right click on system and select 'Edit Menus'. If it works like Ubuntu, it should open an interface to configure the menu. Then you'll see that a lot of the programs are already in the menu, but 
they don't show up unless you check their box.

---

### Post by allene222 on 2008-06-15
Thanks for the reply.  It is clearly different.  For one, I don't click on "systems", I right click on "applications".  I can then click on "edit menu" but there isn't anything useful there.  In fact, all the programs that are in my menu show up here under a sub menu " --include-- system" that I cannot edit.

I actually don't think the graphic print configure program is loaded.  I read on a post that loading it slows down the system so you don't want it there.  That is why I have been trying to configure CUPS through its web interface.  However, the documentation isn't helpful.  There are too many options to try them all.  Probably hundreds of permutations...

My only hope is that someone here knows how to do this and is willing to help.

Allen

PS.  Happy Fathers Day to all the dads out there.

---

