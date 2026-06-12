---
title: "Are there any applications that would......"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by techno-mole on 2008-05-15
work with my palm zire handheld ?

basically i want to know if its possible to sync my palm with ubuntu (hardy) and back up the address book, notes and all the rest of it ?
and if it is whats the best thing to use ?

cheers

---

### Post by dublued on 2008-05-15
i have heard that Synce is the program to use to synchronize your data.

i see that you edited this thread as solved.  what did you use?  i've set aside today to tinker my pda with ubuntu

---

### Post by nowshining on 2008-05-15
jpilot is what u need :) - in the menus find software-sources & check marks all repos except for sources, close and re-load when asked to - u can either sudo apt-get install jpilot or go thru synaptic and do a search for jpilot.

However note - when u need to sync - u need to open up the program + there are TWO options - the first button backup will just backup ur device...

the second

if u want to have all contents stored after a hard-reset click this button.

also jpilot allows u to restore all or one application if u'd like..

once u get that going u'll also need to go into the prefs and set-it up to use the usb port...if it doesn't by default..

---

### Post by AbredPeytr on 2008-05-15
Evolution gets a lot of bad press, but it can easily sync your palm Addresses, Calendar, etc. Under Gutsy I only had to tell it (under options) which com port to find my Palm TX on. The I just hit the sync button. It also copied my media files to my Linux box.

---

### Post by Bruce M. on 2008-05-16
I use jPilot ... and some useful help is here:

[PalmDeviceSetup]("https://help.ubuntu.com/community/PalmDeviceSetup")

Enjoy.
Bruce

---

### Post by lazyart on 2008-05-16
synce would be better for a windows mobile device.  Ubuntu has built-in support for Palm Devices (look in System>Preferences) and it hooks into Evolution.

I prefer and use J-Pilot myself.  It has an interface similar to Palm Desktop for Windows.

---

### Post by techno-mole on 2008-05-17
ive tried jpilot, but it doesnt see my palm, ive tried messing with the settings, but no joy.
ive found the inbuilt one that comes with ubuntu, and it works, but i would rather have a gui like the jpilot one, as its like the palm software anyway.
never mind though.
cheers

---

### Post by Bruce M. on 2008-05-17
> **techno-mole said:**
> ive tried jpilot, but it doesnt see my palm, ive tried messing with the settings, but no joy.
ive found the inbuilt one that comes with ubuntu, and it works, but i would rather have a gui like the jpilot one, as its like the palm software anyway.
never mind though.
cheers

See my post #5 and check out the link, jpilot will see your Palm if you follow the instructions ... especially after creating the 10 rules file if you do what it says a little further down:

> * I used these directions and they worked great. but after upgrading to gusty I had problems again. I seems that in gusty there is a udev rule already set up for palm devices that conflicted with this rule above. in the file "60-symlinks.rules" I commented out the rule that was for palm devices and my treo 650 syncs again like before. With the 2 rules together I was getting /dev/pilot becoming symlink to IT'S SELF. if you see some thing like this:

ls -l /dev/pilot lrwxrwxrwx 1 root root 5 2008-01-21 00:10 /dev/pilot -> pilot you might have a similar problem.

Bruce

---

### Post by techno-mole on 2008-05-18
sorry i didnt reply earlier, ive got jpilot to work now, i think the ubuntu in built palm program was getting in the way, so i removed jpilot, and reset the ubuntu in built app and then re-installed jpilot and set it up and now it works, in fact it works like a charm :)

many thanks for all the help, most appreciated.

@ dublued i used jpilot to sync my zire, works great.

---

### Post by hubiedo on 2008-06-14
Thanks for all the info guys. Switching to jpilot did it for me. I followed the instructions above.

---

