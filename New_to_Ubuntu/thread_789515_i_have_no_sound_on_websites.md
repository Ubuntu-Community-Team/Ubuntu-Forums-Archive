---
title: "i have no sound on websites"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by fignig on 2008-05-10
i'm gonna start all the commands that i put in before the sound stopped:

wget [ftp://mplayerhq.hu/MPlayer/releases/codecs/all-20060611.tar.bz2](ftp://mplayerhq.hu/MPlayer/releases/codecs/all-20060611.tar.bz2)

tar xvjf all-20060611.tar.bz

 cd all-20060611

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

 gksudo gedit /etc/apt/sources.list

sudo apt-get purge flashplugin-nonfree gnash gnash-common && sudo apt-get install flashplugin-nonfree

sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse icedtea-gcjwebplugin libflashsupport liblame0 unrar w64codecs

sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player

sudo apt-get install mplayer mozilla-mplayer

gedit $HOME/.mplayer/mplayerplug-in.conf

gksudo gedit /etc/mplayerplug-in.conf

rm $HOME/.mozilla/firefox/pluginreg.dat

sudo apt-get install soundconverter oggconvert


not sure what command did it, but one of them did. and i need help reversing this wretched command and i want it out of my life. i'm sorry about the earlier posts, i was extremely mad and i wanted to yell at everyone. it happens...

---

### Post by Bodsda on 2008-05-10
can i ask, why did you run all those commands? what where you trying to achieve?

---

### Post by guitarthrasher on 2008-05-10
Are you using the Firefox 3 Beta?
I had that same problem, I just reverted to 2. 

Try that and see if it fixes your problem.

---

### Post by fignig on 2008-05-10
> **Bodsda said:**
> can i ask, why did you run all those commands? what where you trying to achieve?

1st i couldn't run videos off websites, then the sound from websites cut-off. i ran all of those commands so i could gain superpowers, i don't believe it worked...

---

### Post by fignig on 2008-05-10
> **guitarthrasher said:**
> Are you using the Firefox 3 Beta?
I had that same problem, I just reverted to 2. 

Try that and see if it fixes your problem.

yes i am on the beta, is 2 more stable?

---

### Post by Bodsda on 2008-05-10
alpha/beta = not necessarily stable

non alpha/beta = stable

---

### Post by fignig on 2008-05-10
> **Bodsda said:**
> alpha/beta = not necessarily stable

non alpha/beta = stable

but i could hear earlier, and when i did a few of those commands my sound went out, but i could see the videos. is this some kind of sick trade-off?

---

### Post by fignig on 2008-05-10
i'm actually on firefox-2 and i still don't have sound... wtf?

---

### Post by halitech on 2008-05-10
What sites are you trying to get sound on? I've been fighting off and on for monthst to get youtube to work (only because my son likes watching land before time videos on there) and haven't gotten it to work yet in Gutsy. It might help to figure it out if it works for others.

---

### Post by fignig on 2008-05-11
> **halitech said:**
> What sites are you trying to get sound on? I've been fighting off and on for monthst to get youtube to work (only because my son likes watching land before time videos on there) and haven't gotten it to work yet in Gutsy. It might help to figure it out if it works for others.

all of them.

---

### Post by ejpyle on 2008-05-11
> **fignig said:**
> all of them.

this is the correct one to install with FF3 

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

choose the .tar.gz link

i had the same prob though installing that corrected my problems

---

### Post by fignig on 2008-05-11
it was actually [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) that helped me w/ all the problems. ty whoever made that thread.

---

