---
title: "[SOLVED] problems with streaming audio"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by turner9929 on 2008-11-18
hi! I've just started using Ubuntu...hardy heron...which I'm quite pleased with really. 

However I have a nagging problem with audio, specifically from youtube and myspace - I cant hear anything.

I can get audio from my pc...using rhythmbox music player, and also from bbc iplayer...so im guessing the problem is not directly to do with all audio.

I have checked the sound properties to make sure nothing is muted, but everything is on.

I am using a Creative Audigy 2 sound card...if thats any help :)

any help would be most appreciated!

:guitar:

---

### Post by bobnutfield on 2008-11-18
Try installing the following:

> sudo apt-get install flashplugin-nonfree-extrasound

This provides support for sound cards that are not otherwise supported with the flash plugin.

---

### Post by turner9929 on 2008-11-18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree-extrasound is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree-extrasound has no installation candidate

erm....ok. what?!? lol damn i wish i knew what i was doing! :)

---

### Post by bobnutfield on 2008-11-18
OK, I don't think you have the medibuntu repos enabled.  Go to System>Adminstration>Software sources and enable the medibuntu repository, then just put a check in the medibuntu box on the third party tab., then, do:

> sudo apt-get update

Then try installing again.  You shoud also enable the multiverse and universe repos as well.

---

### Post by turner9929 on 2008-11-18
I cant find anything about medibuntu on the software sources dialogbox.

---

### Post by bobnutfield on 2008-11-18
OK, go [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/Medibuntu") and you will find instructions on installing and enabling the medibuntu repository.  This is an important repository to get multimedia applications and updates.  Once you have it installed and enabled, install as indicated in the previous post and your sound in flash should be rectified.

---

### Post by turner9929 on 2008-11-18
hi. all installed and activated (i think) but when i go: sudo apt-get install flashplugin-nonfree-extrasound... it still says the same thing:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree-extrasound is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree-extrasound has no installation candidate

---

### Post by turner9929 on 2008-11-18
hi...i just had a look at the synaptic package manager, and it seems as though flashplugin-nonfree is already installed - version 9.0.125.

i also have: adobe-flashplugin 10.0.12.36-1HARDY2....but this is not installed.

---

### Post by turner9929 on 2008-11-18
hi...i just had a look at the synaptic package manager, and it seems as though flashplugin-nonfree is already installed - version 9.0.125.

i also have: adobe-flashplugin 10.0.12.36-1HARDY2....but this is not installed.

---

### Post by turner9929 on 2008-11-19
Sorted! i had a slow day at work so read the following:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and did what it said. All problems re:streaming media solved.
thanks for the help! :)

---

