---
title: "[SOLVED] Step by step install adobe flash firefox"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by poochhq on 2008-06-20
I am new to Ubuntu. I have downloaded adobe flash as a firefox plug in but I need a step by step guide as to how to use the terminal to install in it.

Many Thanks,

James

---

### Post by ruffEdgz on 2008-06-20
1. Open up terminal
2. type in
```

sudo apt-get install flashplugin-nonfree

```
3. Restart/turn on firefox
4. Type in 'about:plugins' in the address bar
5. See if you see Adobe Flash 9

hope that helps

---

### Post by alienexplorers on 2008-06-20
Did you down load it from Adobe, if so you have to unpack the file.  Just try double clicking on it.  Next once unpacked you need to make flashplayer-installer executable.  Run in terminal sudo chmod 777 /directorywherefileis.
Double click that file and follow the prompts.  The flashplugin should load to your .mozilla/plugins dircetory.  Your done.

---

### Post by Xerp on 2008-06-20
[http://fosswire.com/2008/05/06/installing-flash-player-in-ubuntu-hardy-heron/](http://fosswire.com/2008/05/06/installing-flash-player-in-ubuntu-hardy-heron/)

---

### Post by markbuntu on 2008-06-20
The proper place for Adobe Flash Player is usr/lib/flashplugin-nonfree. If you downloaded the latest flash from Adobe this is where you need to put the libflashplayer.so.

---

### Post by poochhq on 2008-06-22
Thanks, I typed in sudo apt-get install flashplugin-nonfree
and it seemed to install the plug in. 
I opened up Firefox and I typed in about:plugins but Adobe Flash 9 appears nowhere. 
I want to view my charts in Google Analytics you see.

---

### Post by markbuntu on 2008-06-22
Are  you using 386i or amd64 Ubuntu?

If you are using the amd64 version you need to install nspluginwrapper or flash will not work.

If you are using 386i then look in

 usr/share/lib/firefox-addons/plugins 

for a 

Link to libflashplayer.so

with the link target:

usr/share/flashplugin-nonfreee/libflashplayer.so

You can right click on the link and look in properties to find out the link target.

In firefox you can look in Tools/Add-ons/Plugins to see if there is a plugin called: 

Shockwave Flash

---

### Post by poochhq on 2008-06-23
Found the file libflashplayer.so in usr/lib/flashplugin-nonfree. Is this the correct place? If not where should I move it to. I click on properties but I cannot see any links?!!

youtube does not work.

Shockwave Flashplayer is not listed in my add ons in Firefox.

The links to these guides about installing aren't helpful as they presume that I am getting a message to install the missing plug in from the top of my browser and I am not!

I have just followed the instructions about making Ubuntu multimedia friendly hosted on the googlepages site but that does not cure my flash issue.

I still need some more wonderful advice!

---

### Post by aysiu on 2008-06-23
Are you using 64-bit or 32-bit Ubuntu?

---

### Post by RomeReactor on 2008-06-23
Hi. Try this: Close Firefox, open a terminal (Applications->Accessories->Terminal) and paste the following to remove the xpti.dat file:
```
rm ~/.mozilla/firefox/*.default/xpti.dat
```
Also make sure Gnash is not installed, as it conflicts with Flash:
```
sudo aptitude purge gnash gnash-common mozilla-plugin-gnash
```
Open Firefox again and see if Flash now works.

---

### Post by poochhq on 2008-06-24
I am using 32 bit Ubuntu.

---

### Post by poochhq on 2008-06-25
Followed Rome Reactors advice. My Flash now works like a dream.

Thanks the support from this site blows my mind!

James

---

