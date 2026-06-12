---
title: "How to: Build The Desktop from XTERM (X/ubuntu ONLY)"
date: 2009-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by coldReactive on 2009-11-07
Some people have been having issues where GDM is not allowing you to login thanks to packages being uinstalled, resolutions are wrong, or some configurations are wrong. Sad to say, there's nothing you can do yourself to fix the issue but to wait for the developers to fix it. However, do not fret, these "simple" instructions will allow you to build a basic desktop from packages your system already has installed, without having to reinstall the system again.

[CENTER]**[COLOR="RoyalBlue"]Xubuntu[/COLOR] Users**[/CENTER]

For you Xubuntu/XFCE4 users, you should do the following, probably in order.
[LIST]
[*]Run xfce4-terminal (if it isn't installed install it in xterm and then run it)
[*]In the new xfce4-terminal, run xfwm4 --replace
[*]CRTL+SHIFT+T into a new terminal tab on xfce4-terminal and run xfce4-panel.
[*]In the XFCE Menu (if you don't have it, run xfdesktop now in a new terminal tab) select Run program and run the xfdesktop (Do not choose run in terminal.)
[/LIST]
Your basic desktop is now ready to use.

[CENTER]**[COLOR="Sienna"]Ubuntu[/COLOR] Users**[/CENTER]

This has not been tested yet. If it works, kudos to you for trying.
[LIST]
[*]Run gnome-terminal from xterm.
[*]in gnome-terminal, run metacity --replace
[*]CRTL+SHIFT+T into a new tab, run gnome-panel.
[*]Open up a nautilus window and tell it to draw the desktop in its preferences if no icons appear when you open up a place.
[/LIST]

[CENTER]**[COLOR="Red"]WARNINGS[/COLOR]**[/CENTER]
[LIST]
[*]DO NOT CLOSE XTERM UNLESS YOU WANT TO QUIT YOUR SESSION.
[/LIST]

[CENTER]**[COLOR="Purple"]More Permanent Solution[/COLOR]**[/CENTER]

In xterm, run the following commands:
[LIST]
[*]sudo apt-get purge gdm (wait for it to complete)
[*]sudo apt-get install xdm (wait for it to complete)
[*]sudo reboot now (this will reboot the computer)
[/LIST]
When you next login, a shabby looking login screen (with a debian logo) will present itself. To customize this bad boy: [Click Here](http://www.osix.net/modules/article/?id=590) (Use Xsetup and not Xsetup_0, and do not blank your Xresources, just edit it to your needs, as it will already have all the colors/etc. already configured for you to edit.)

---

### Post by Psumi on 2010-03-08
SLiM is being put into lucid. I would suggest using it if lucid gives the same problems instead of xdm.

---

