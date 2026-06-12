---
title: "[SOLVED] main screen customize?"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by cairnzi on 2008-10-10
hey people, ive seen this on a few sites but cannot figure out how to do it, im after the menu bar at the bottom and the gauges going up the side ie. hdd temp core's etc, anyways ive attached a pic i found of what i want, many thanks.

---

### Post by tang0delta on 2008-10-10
First of all you'll need to install compiz fusion and the compiz fusion settings manager via synaptic package manager (System >> Admin. >> Synaptic Package Manager) 

To get the bar, u need to install the avant-window-navigator package and its associated plugins (that's one program you can use there are alternatives available). Here's a howto for that:
[URL="http://ubuntuforums.org/showthread.php?t=762363&highlight=howto+install+AWN"]
http://ubuntuforums.org/showthread.php?t=762363&highlight=howto+install+AWN[/URL]

Themes and icons for Gnome can be found at [http://www.gnome-look.org]("http://www.gnome-look.org/") 

I use Gtk 2+ themes on my desk but you can also use a separate window manager like emerald. To use the Gtk themes, just find the theme you like, download the .tar.bz2 or .tar.gz of the file to a folder of your choice (let's say /home/your_userID/themepacks) then run the appearance manager (System >> Preferences >> Appearance). Click the install button and a dialog will pop up for you to choose the path to your .tar.gz or .tar.bz2 theme package. Find the package click open and voila. 

For the Icons, the same idea as the themes applies:

- Goto gnome-look.org
- Find an icon pack (.tar, .tar.gz, .zip)
- Open Appearance manager
- The theme your currently using will be selected in the window. Click the "Customize"   button. Click on the icons tab. Click the "Add" or "Install" button (cant remember what its called atm :tongue:)
- Choose the icon pack you downloaded and click open. 

Tweaking the themes and icons is where you'll spend the real time but most of thats really down to your own preference and creativity. 

As for the bar on the right with your system status, I'm not sure about that as I don't really use one. I do know its called a conky or somethin (little help from the hardcore ubuntu dudes?) so you might want to look into that. 

Hope this info helps. :)

All the best!

tang0delta

---

### Post by tang0delta on 2008-10-10
Here's a howto for conky aswell if it helps:

[http://ubuntuforums.org/showthread.php?t=867076](http://ubuntuforums.org/showthread.php?t=867076)

:)

---

### Post by aeiah on 2008-10-10
the bit on the right is indeed called conky, and its very useful and lightweight. you can get it to display just about any information you want. you dont need compiz for this particular bit, by the way..

unless you've got an intel onboard graphics chip you'll need to install your restricted drivers before trying to install compiz or else it'll crap out. to install them simply go menu > system > administration > restricted drivers manager and you should find your nvidia or ati graphics card drivers there ready for auto download and installation. if your computer is very new you might want to make sure it wont break first.


bet you wish you never asked eh?

---

### Post by tang0delta on 2008-10-10
Thanks for adding that info **aeiah** :). -facepalm- for forgetting to mention restricted drivers :tongue: but hey, I'm new to this whole helping thing lol.  Might even give conky a bash myself. Been messin around with ubuntu for over a year now but I'm only finally beginning to suss it all out.

---

### Post by cairnzi on 2008-10-10
ah! many thanks to all replys, got it working now, thanks again.

---

