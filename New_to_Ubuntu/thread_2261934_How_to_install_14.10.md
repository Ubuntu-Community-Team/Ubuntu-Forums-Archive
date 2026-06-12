---
title: "How to install 14.10?"
date: 2015-01-22
forum: New to Ubuntu
---

### Post by flex567 on 2015-01-22
I have 14.04 lubuntu, how can upgrade to 14.10 lubuntu?

---

### Post by mastablasta on 2015-01-22
in your software center got to software sources --> updates and select to be notified about any new ubutnu version. an upgrade option should then appear after you make updates.
or you can do it with command line:
[FONT=Courier New]do-release-upgrade[/FONT]

[http://askubuntu.com/questions/110477/how-do-i-upgrade-to-a-newer-version-of-ubuntu](http://askubuntu.com/questions/110477/how-do-i-upgrade-to-a-newer-version-of-ubuntu)

why do you want to upgrade?

---

### Post by flex567 on 2015-01-22
because I hope it will fix this error: 
[http://ubuntuforums.org/showthread.php?t=2261875](http://ubuntuforums.org/showthread.php?t=2261875)

---

### Post by mastablasta on 2015-01-22
if it's a VLC issue, then you can upgrade VLC using PPA to latest version (if it's not latest already in software center).

if the issue are drivers (i.e. sound doesn't work in other player or system in general) you will need to provide more info. but  a solution is to upgrade only kernel (have a look at hardware enablement stack).

In any case you need to find out what the issue is ( I mean what is causing the problem) before blindly upgrading. and if you really want to upgrade at least try it live first, install VLC inside live session and see if it works out of the box then. if it does not then the issue is probably elsewhere.

hint: from the error you posted you should check the VLC settings to see which audio device is set there. then check which one is set in system. unfortunately I do not use lubuntu, but it probably has some settings panel available or something like that. if not there is always command line available to identify sound chip and selected sound card/chip.

---

