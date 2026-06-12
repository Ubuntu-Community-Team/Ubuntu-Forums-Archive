---
title: "Backing up"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by weezyrider on 2012-02-25
To avoid flakiness if I want to play around between Unity and Gnome desktops, I'd like to back up. Ubuntu is on its own hard drive on a dual boot and boots through Grub.

I normally don't back up since I always store my data files elsewhere. Which means if I take a computer in for an Windows upgrade - just overwrite the HD. I'll reinstall programs.
I've stored data elsewhere since the comment about "512m being enough" and Windows 95.

It's harder for me to get back settings in Ubuntu, so what I want is to back up all the settings. What do I back up on? Get an external HD, and how big? Is there a command for settings and programs only? And how do you restore?

I can't afford to lose Skype. Mike, camera, etc work, and it's our only visual communication with relative in the UK. 

BTW - I don't want a cloud account. I can sign up for dropbox, but have no desire to.

Thanks

---

### Post by Lars Noodén on 2012-02-25
If you make a separate /home partition then just be sure not to erase it when you do your re-installation.  If you really are saving all your data elsewhere, then you can do a backup of /home on a small usb stick.  Just be sure to empty out any caches first, such as from web browsers.

---

### Post by mapes12 on 2012-02-25
This may be worth a look:-

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by baumanno on 2012-02-25
I can really recommend [this]("http://ubuntuforums.org/showthread.php?t=35087"). 
Helped me after upgrading from 32bit to 64bit, just as Lars Noodén said, empty any caches / go through your /home first to identify any space-hogs.
In genereal, IIRC, all personal settings are saved in dotfiles in /home (like .thunderbird), and all system-related configs are in /etc, but please correct me if I'm wrong...

Good luck and keep us posted ;)

---

