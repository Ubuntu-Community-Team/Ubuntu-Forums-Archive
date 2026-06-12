---
title: "nothing showing up on startup"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Cossar on 2008-10-24
when I boot up, after I go through the login screen, sometimes nothing initializes (no panels, no shortcut keys work, etc), the mouse and keyboard work but i can't see anything except a blank screen. if I try restarting and running the no-script Gnome, it works fine, and if I restart after that and run in normal Gnome it usually works fine. I'm thinking there's a bad script somewhere that's screwing up my desktop, but I dont know what it is. It seems that it just happens randomly, like sometimes I can boot it up fine with no problems and other times it takes several reboots before it's working in normal Gnome mode. any ideas on what I can do? thanks for helping this lowly peon[-o<

---

### Post by wolfen69 on 2008-10-24
are you using hardy or ibex? if hardy, why not try [ubuntu 8.10]("http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-i386.iso")? it's only a few days from being officialy released anyway. alot of people's "problems" are fixed with ibex.

---

### Post by taseedorf on 2008-10-24
Well, first and foremost I would look in the sessions and see if there are any pesky programs booting up which are causing this to happen.  Such as maybe an update program that only loads every 3 boots or something? 
Go to System->Preferences->Sessions and check it out to see if you see anything.   Feel free to disable some things and see if it fixes your problem.

2nd, once your computer boots, try pressing ctrl+alt+backspace and reloading X..... this MAY help so you don't have to reboot

3rd.... Sometimes certain video cards have problems with compiz, are you running it?

4th...I have heard that if you are trying to share files from a drive that isn't mounted at boot time problems can arise....especially if it scans the media directories each time it shares... (certain upnp) programs caused this..)...

im not sure...has this always happened?

go to
/var/log

and look at some logs...check to see whats happening after this happens.

oh btw, i would NOT try ibex yet in your situation...while it is only a few days away from being released, there ARE still many bugs and many fixes will not be implemented until its actual release.

---

### Post by Cossar on 2008-10-25
Thanks alot, it's working now. I went to sessions and unchecked a few of the programs I never used or uninstalled, and now it works fine. Even loads up faster...oh yeah, I was going to upgrade to ibex but I decided I'd wait til the official release. Things are working fine right now and I don't want to screw anything up right now, haha. Thanks!

---

