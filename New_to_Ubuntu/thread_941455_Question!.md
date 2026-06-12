---
title: "Question!"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by KylePosey on 2008-10-08
Okay i have a lil bit of a prob. this guy here (the guy being me) he wants to put on the wine version of linux and i dont know how to boot from the cdrom drive.  Any help is greatly appreciated. (BTW i am runnin Ubuntu right now) Oh and im not sure if my cdrom is bootable and plus this sux to be me.  But could i possibly boot from an extenal HD?

---

### Post by scavenger2008 on 2008-10-08
When you start your computer, it could show the logo of the company that made it. In that screen, look for something like 'boot menu' and hit that key. Then use your arrow keys to move to something like 'CD' or 'DVD drive'. That should start Ubuntu's installation.

When you finished installing Ubuntu (which should be very straightforward), use the Add/remove software tool in the Applications menu to search for and install Wine. Before you can do that, however, you'll need to enable the extra repositories with an app called 'Software sources' or something like that.

---

### Post by Kevbert on 2008-10-08
To boot from a CD will probably be a bios setting.  When you first boot it will ask you to hit a key (Del or F2) to go to the setup menu.  You'll need to find where the set-up order is and make sure that boot from CD comes before boot from hard disk.
Wine can be installed in any version of linux and is normally an add-on program.  Wine will simulate Windows 98/XP/ME so that you can run some Windows programs. It will not run all programs. The normal saying is [COLOR="Red"]W[/COLOR]ine [COLOR="Red"]I[/COLOR]s [COLOR="Red"]N[/COLOR]ot an [COLOR="Red"]E[/COLOR]mulator.

---

### Post by dew5 on 2008-10-08
heres a how to from wine.

[http://www.winehq.org/site/howto](http://www.winehq.org/site/howto)

helped me.

dew5

---

### Post by tarps87 on 2008-10-08
The boot from CD option is in your BIOS as previously said. (The CD drive will need to first to boot from it)
If you made the cd from the .iso it should boot (not just copied the file onto it)
You may be able to use an external hard drive (I'm assuming it is a USB one) When your in you BIOS setting have a look for the option to boot from USB. It will be in the same place as you told it to boot from the CD.
How are you running Ubuntu? If it is from a live-cd you BIOS is already setup, if its from the hard drive you can just type```
sudo apt-get install wine
```
"Wine is an Open Source implementation of the Windows API" not a windows emulator so it is not granted to run all windows programs. If you have a copy of windows you can use something like virtualbox:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by lisati on 2008-10-08
I don't think there's specifically a "Wine" version of Ubuntu. Wine is a program that can be used to run some (but not all) Windows programs within Ubuntu (which can't ordinarily run Windows programs without help)

If you've already installed ubuntu (and not running from the CD), adding "Wine" is fairly straight forward. As previously said, it's probably easiest from the "Add/Remove software" option on your applications menu.

---

### Post by tarps87 on 2008-10-08
Also you can try a program called wine-doors:
[http://www.wine-doors.org/wordpress/?page_id=2](http://www.wine-doors.org/wordpress/?page_id=2)
It makes some things easier to setup in wine
For programs compatibility under wine you can look at:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

