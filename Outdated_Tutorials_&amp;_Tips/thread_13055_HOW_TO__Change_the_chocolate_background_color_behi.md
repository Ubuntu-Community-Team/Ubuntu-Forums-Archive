---
title: "HOW TO:  Change the chocolate background color behind the Ubuntu startup splash"
date: 2005-01-28
forum: Outdated Tutorials &amp; Tips
---

### Post by WirelessMike on 2005-01-28
Found this using grep to locate the hex value for the Ubuntu chocolate color used as the default startup background--

grep -r 4E3E29 /etc/gdm/*

That will tell you that the color is found as "BackgroundColor" in the following files--

/etc/gdm/factory-gdm.conf
/etc/gdm/gdm.conf
/etc/gdm/gdm.conf.dpkg-dist

Simply vi into these files as root, page down until you get into the greeter section where you'll find "BackgroundColor=#4E3E29" Change this to the desired color (I wanted a dark blue, so i changed it to #000045) and viola!

> sudo vi /etc/gdm/factory-gdm.conf
sudo vi /etc/gdm/gdm.conf
sudo vi /etc/gdm/gdm.conf.dpkg-dist

Change BackgroundColor=#4E3E29 to BackgroundColor=#(hex for desired color)

write and quit (:wq)

Restart GUI

You can, of course, simply su root and make these changes without sudo on every file.

 :mrgreen: 

Now you can choose a background color to compliment your custom splash!

---

### Post by WirelessMike on 2005-01-28
***OR***

as XSOS just pointed out in a reply in another thread--

> xsos:

Helo you could click computer - system configuration - login screen setup.
and then goto standart greeter tab, on the backgorund color coloum click the color box and choose your fav color done.

I hope this could help u

A shame that wasn't already in the FAQ or something...

Oh well--  THANX XSOS!!!

---

### Post by #Reistlehr- on 2007-11-02
There is actually two places where the login color are prevailant. It is easier to set it using the login window, but in some cases the Default file will, well, default, and display the color in the Defaults file. This file can be located at /etc/gdm/PreSession/Default

> 
gksudo gedit /etc/gdm/PreSession/Default 

Look for:
BACKCOLOR="#DAB082"

And change, DAB082 to a color of your choice. For a black background try:
BACKCOLOR="#000000"

Save, and restart!


Just a note for some users who notice the color doesn't change after it's changed in the gdm settings. :D

---

