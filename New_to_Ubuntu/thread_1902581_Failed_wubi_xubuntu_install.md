---
title: "Failed wubi xubuntu install"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by brushman on 2011-12-31
I'm trying to install xubuntu with wubi. My memory is fuzzy but it went something like this:

After rebooting for the first time after running the wubi exe, I got a glitched out screen when I tried to use xubuntu (this occured after the blue xubuntu loading screen with the bar the goes back and forth).

I force shutdown my computer and restarted again; this time I ran in safe graphics mode. This avoided the glitched out screen but this time when you have the white text scrolling across the black screen I get stuck at the part that says "checking for battery" or something like that.

I pressed ctrl alt f1 and logged into the console and I don't know what all I did but I typed in some commands like sudo apt-get install gdm, sudo apt-get install update (didn't recognize update), sudo apt-get install upgrade( i don't think it recognized this either but I typed in some other stuff with upgrade in it, maybe just sudo apt-get update or something). 

Anyways, at this point it just goes to the blue xubuntu loading screen, loads for a little bit (the little bar goes back and forth until it finally freezes).

Should I just uninstall and try completely reinstalling? Idk why this isn't working...

---

### Post by jerrrys on 2012-01-01
First off, your commands are a bit off.  Should go something like this:

sudo dpkg --configure -a
sudo apt-get install -f

The above commands will attempt to fix broken packages.

sudo apt-get update
sudo apt-get upgrade

When you run update, take note of any errors.  If it someway offers you a partial upgrade, do not do it.  A partial will likely just add problems.

I do not use WUBI, but sounds like you need to install the right video driver.

Did you try xubuntu before installing?  What kind of computer do you have?

---

### Post by wildmanne39 on 2012-01-01
Hi, you can have a look at this link it may help.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by LinuxFan999 on 2012-01-01
> **brushman said:**
> I'm trying to install xubuntu with wubi. My memory is fuzzy but it went something like this:

After rebooting for the first time after running the wubi exe, I got a glitched out screen when I tried to use xubuntu (this occured after the blue xubuntu loading screen with the bar the goes back and forth).

I force shutdown my computer and restarted again; this time I ran in safe graphics mode. This avoided the glitched out scroeen but this time when you have the white text scrolling across the black screen I get stuck at the part that says "checking for battery" or something like that.

I pressed ctrl alt f1 and logged into the console and I don't know what all I did but I typed in some commands like sudo apt-get install gdm, sudo apt-get install update (didn't recognize update), sudo apt-get install upgrade( i don't think it recognized this either but I typed in some other stuff with upgrade in it, maybe just sudo apt-get update or something). 

Anyways, at this point it just goes to the blue xubuntu loading screen, loads for a little bit (the little bar goes back and forth until it finally freezes).

Should I just uninstall and try completely reinstalling? Idk why this isn't working...
Which version of Xubuntu are you using?
If you are using a version of Xubuntu before 10.04, you should try 10.04 or newer.

---

