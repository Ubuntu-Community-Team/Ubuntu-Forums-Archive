---
title: "[SOLVED] safe to nuke pidgin-data?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by vikramaditya on 2008-06-23
I want to completely remove pidgin thru synaptic.  When marking **pidgin** itself for complete removal, the **pidgin-otr** plugin gets selected for removal as well, but **pidgin-data** is left unmarked.  Will hardy die if I nuke all 3?  BTW, one of my few peeves with synaptic is that it often fails to select all of the packages that were installed with a particular app. :(

---

### Post by RiceMonster on 2008-06-23
Nothing should happen. I just tried it and it didn't try to remove ubuntu-desktop like I thought it would.

---

### Post by angryfirelord on 2008-06-23
If it's just those three, then Hardy will stay alive. If you see ubuntu-desktop getting removed, then you'll run into problems.

---

### Post by shae on 2008-06-23
No, it is safe to remove ubuntu-desktop.  Just make sure you do not see something like lib-gnome, xorg, linux-*, etc.

---

### Post by tinny on 2008-06-23
> **shae said:**
> No, it is safe to remove ubuntu-desktop.  Just make sure you do not see something like lib-gnome, xorg, linux-*, etc.

Doesnt sound safe to me.

> 
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that it not be removed. 


Found here: [http://packages.ubuntu.com/hardy/base/ubuntu-desktop]("http://packages.ubuntu.com/hardy/base/ubuntu-desktop")

---

### Post by vikramaditya on 2008-06-23
Thanks, all :)  I got rid of **pidgin** and **pidgin-otr**, but when I mark **pidgin-data** for complete removal, it wants to take **libpurple0** along for the ride.  Here's the synaptic description of libpurple0 . . .
> multi-protocol instant messaging library 
libpurple is a library intended to be used by programmers seeking
to write an IM client that connects to many IM networks.
Currently supported are: AIM/ICQ, Yahoo!, MSN, IRC, Jabber, Napster, Zephyr,
Gadu-Gadu, Bonjour, Groupwise, Sametime, SILC, and SIMPLE.

Some extra packages are suggested to use increased functionality:
 * tcl8.4, tk8.4:
   - Support for writing plugins with Tcl/Tk
It doesn't sound vital if one is not doing instant messaging, but then one nevah know, do one? ;)

---

### Post by angryfirelord on 2008-06-23
> **vikramaditya said:**
> Thanks, all :)  I got rid of **pidgin** and **pidgin-otr**, but when I mark **pidgin-data** for complete removal, it wants to take **libpurple0** along for the ride.  Here's the synaptic description of libpurple0 . . .

It doesn't sound vital if one is not doing instant messaging, but then one nevah know, do one? ;)
libpurple0 is the library that pidgin uses for communication, so yes it is ok to remove that package as well since no one else uses it at this moment.

---

### Post by jualin on 2008-06-23
You can remove ubuntu-desktop if you like, however I think that you will end up without a GUI and then you would need to use the command line to install a (*)ubuntu-desktop package. Pretty much Ubuntu-desktop installs the Gnome version of Ubuntu. If you want to try out other versions such as Kubuntu you can install kubuntu-desktop and then choose at every login what Desktop environment you want to run.

---

### Post by vikramaditya on 2008-06-24
> **jualin said:**
> You can remove ubuntu-desktop if you like, however I think that you will end up without a GUI and then you would need to use the command line to install a (*)ubuntu-desktop package. Pretty much Ubuntu-desktop installs the Gnome version of Ubuntu. If you want to try out other versions such as Kubuntu you can install kubuntu-desktop and then choose at every login what Desktop environment you want to run.
Actually, I brazenly removed ubuntu-desktop during an earlier uninstall.  I rebooted with no apparent consequences, but when I reinstalled ubuntu-desktop my wicd network app was replaced by the wretched gnome network manager.  No prob, just reinstalled wicd and carried on.

---

