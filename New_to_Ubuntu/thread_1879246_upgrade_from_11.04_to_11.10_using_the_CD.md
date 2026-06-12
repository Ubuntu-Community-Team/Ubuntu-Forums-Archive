---
title: "upgrade from 11.04 to 11.10 using the CD"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2011-11-11
Hi guys 
I've tried searching but am getting hit by a flood of related, but not relevant posts.

Is it possible to upgrade from ubuntu 11.04 using the desktop CD of 11.10

---

### Post by bigmonmulgrew on 2011-11-11
> **meth34 said:**
> better to upgrade via internet as the internet will have all the programs

Internet isnt possible on this PC, hence the question

---

### Post by beew on 2011-11-11
A better question would be why do you want to upgrade? Right now many things are still broken in 11.10, if I were you I would wait a few months.

---

### Post by philinux on 2011-11-11
> **bigmonmulgrew said:**
> Hi guys 
I've tried searching but am getting hit by a flood of related, but not relevant posts.

Is it possible to upgrade from ubuntu 11.04 using the desktop CD of 11.10

Yes.
 [http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html](http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html)

---

### Post by philinux on 2011-11-11
> **beew said:**
> A better question would be why do you want to upgrade? Right now many things are still broken in 11.10, if I were you I would wait a few months.

It's running fine on my 2 machines. One a desktop the other a netbook.
They were clean installs and I removed most .config files from my separate home partition.

---

### Post by beew on 2011-11-11
> **philinux said:**
> It's running fine on my 2 machines. One a desktop the other a netbook.
They were clean installs and I removed most .config files from my separate home partition.

It is not running fine on my clean install test partition,--no .conf file to remove as it is a complete clean install. 

To list a few things: EOG doesn't work so cannot open any .png or .jpg file, Firefox extremely jerky and sluggish, genome-alsamixer segfaults on start, Compiz is buggy, rotating the cube flashes a lot and shift+ctr+alt + left/right doesn't work. Nvidia driver seems to be quite screw up resulting in very slow graphic, using nouveau is no good either because I can't update my driver and  mesa with xorg-edgers (it breaks Unity), --if you use the open source driver, xorg-edgers is the only way to go as the Ubuntu offers is old and crappy, most things barely work while the xorg-edgers drivers do magic. I am seeing two battry icons, not one on my panel.When installing many new programs the launchers icons don't go to the proper category in the dash, in fact many don't have a category at all. The dash is suposed to be a menu of some sort, not just a dumping ground of icons,--alacarte doesn't work any more so can't fix that with the Main menu, you can edit the .desktop file manually but that is ridiculous, and most new users wouldn't know how to.

Also some softwares don't work because they have not been properly ported to gtk3 yet.

Gnome3 itself is not ready  and many features are missing. I am talking about gnome3 which both Unity and the Gnome shell sit on top, not just the Gnome shell.

I can go on, but all of these are known bugs (you can check launchpad) so it is not just me. 
 
But more importantly, what is the reason of  skipping Natty to go for something that has been released for less than a month? It took Natty about 3 months to become solid and all the software supports to be in place (ppas, third party software etc) and I think it is going to take longer for 11.10 because of the switch to gnome 3. Now just when Natty finally matures into a great OS to be enjoyed everyone is encouraged to move on to the next buggy beta. I think that is insanity unless your main purpose of using a computer is to beta test for Canonical.

I think new users especially shouldn't be encouraged to install the latest, that is just going to give Ubuntu a bad reputation when things turn out to be broken (with 11.10 it seems a lot will be broken, or feature incomplete like gnome 3,--features are removed to avoid breakage) On the other hand LTS is too conservative,--many things are simply outdated and hardware support is probably not so good on newer hardware due to old kernel,-- I would always go for one release behind, I think that is the best spot.

---

### Post by bigmonmulgrew on 2011-11-14
> **philinux said:**
> Yes.
 [http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html](http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html)

Thanks for your reply.
This is for upgrading from 10.10 to 11.04
Will it work ok for upgrading from 11.04 to 11.10. I dont want to unduly screw things up.

---

### Post by bigmonmulgrew on 2011-11-14
I too can report that on my internet connected machine 11.10 is working fine, besides my question was how to upgrade, not if I should. I'm perfectly willing to troubleshoot problems if they arise.

---

### Post by bigmonmulgrew on 2011-11-14
Using the discs to upgrade I am shown the option to upgrade but I am not able to select it?
Any ideas?

---

