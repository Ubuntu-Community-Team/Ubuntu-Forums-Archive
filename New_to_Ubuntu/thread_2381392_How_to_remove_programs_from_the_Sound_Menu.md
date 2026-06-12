---
title: "How to remove programs from the Sound Menu?"
date: 2017-12-30
forum: New to Ubuntu
---

### Post by scholarlyrunner on 2017-12-30
Hi, I noticed that Banshee is permanently in the sound menu. I could just delete the program, but then another program that I installed and really want to use, Clementine, does the exact same thing. I want to remove these programs (and future programs I install) from the sound menu. Any suggestions?

---

### Post by Autodave on 2017-12-30
Go to either the Software Center or *synaptic *and remove them from there.

---

### Post by Dennis N on 2017-12-30
What desktop environment do you have? Ubuntu? Xubuntu? Lubuntu? Ubuntu MATE or perhaps something else? Depending on the desktop environment, it may be possible to remove players from  the sound menu without uninstalling the player itself.

---

### Post by leunam12 on 2018-01-01
Depending on your desktop environment you may or may not have a GUI method to modify your menu.
 I use the Mate desktop and it has a menu editor that allows me to customize the menus. If you don't 
have such application in your desktop environment then you have to modify the .desktop entry for that
application and remove the word "Sound" from the Category line. or simply rename the .desktop file to something else like this:
```
cd /usr/share/applications/
sudo mv banshee.desktop banshee.bak
```

---

### Post by scholarlyrunner on 2018-01-06
Just a typical Ubuntu desktop.

sudo my command not found

---

### Post by deadflowr on 2018-01-06
You mean the sound icon up in the top panel?
Well it never works right but it can be removed through dconf.
See: [https://www.howtogeek.com/113897/how-to-remove-media-players-from-ubuntus-sound-menu-add-your-own/]("https://www.howtogeek.com/113897/how-to-remove-media-players-from-ubuntus-sound-menu-add-your-own/")

My problem is that it's never permanent,  in that you can remove the app but if you start the app again, it adds it with no regard to what the blacklist says 
This bug sorta hits on that:
[https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1320634]("https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1320634")

---

### Post by mc4man on 2018-01-07
Most media players have a setting to disable, some common in screenshots. After disabling one would still have to clear the dconf entry i.e.
```
gsettings set com.canonical.indicator.sound interested-media-players '[]'
```
Then they would not return.

One current exception may be vlc which seems to have removed the gui option though has a cli option --no-dbus  One could add that to vlc.desktop but would need to remove the current --started-from-file option (- to what unintended affect, if any, don't know..

---

### Post by leunam12 on 2018-01-08
> **scholarlyrunner said:**
> sudo my command not found

It is not 'my' it is 'mv'

---

