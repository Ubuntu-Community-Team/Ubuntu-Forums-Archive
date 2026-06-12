---
title: "How to Remove Weatherblink"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by kduffingb on 2013-03-09
I am running EasyPeasy on an Asus 901. I have installed Weatherblink in order to have up to date weather forecasts. It appears to be continuously downloading data from the internet which as I am roaming makes it expensive. It has also slowed my system to the point where it is almost unusable. How can I un-install it?:mad:

TIA

Keith

---

### Post by ptn107 on 2013-03-09
Two things:

a) That website looks shady as hell.
b) The file it wants to download and install is a windows exe file.

That has scam written all over it.  Who knows what it actually installs.  BTW they are run by mindspark which hosts even more "software" of equal shadyness.  How did you install the file on linux.  Wine?  If so just remove the folder from your /home/*USER*/.wine/ folder and pray that's the only place it put stuff.  It apparently also installs a toolbar into your browser without knowledge (red-flag number three).  To remove it they actually give you instructions [_here_]("http://support.mindspark.com/link/portal/30028/30031/Article/222/Uninstalling-Mindspark-toolbar") depending on your browser.  Finally they also hijack your homepage and search engine defaults.  You need to read [_this_]("http://eula.mindspark.com/reset-homepage-default-search-settings/#nt-anchor") to undo it.  Stay away from this kind of stuff.

---

### Post by kduffingb on 2013-03-10
I have completely removed Wine, I hope, and the problem seems to have gone away. Many thanks for your help and advice.:)
Cannot see how to mark this as solved.

---

### Post by Frogs Hair on 2013-03-10
Weatherblink comes up as malware/spyware with a quick search. Purge and Eject !!

---

