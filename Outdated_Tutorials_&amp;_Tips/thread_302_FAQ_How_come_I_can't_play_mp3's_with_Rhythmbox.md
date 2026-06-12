---
title: "FAQ: How come I can't play mp3's with Rhythmbox?"
date: 2004-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-12
The mp3 codec was recently removed because of patent issues, they cannot install it by default any more.

Try to install the package 'gstreamer0.8-mad' from the universe, which reenables MP3 support for all multimedia applications (using gstreamer, that is). MP3 playback is free for private use.

---

### Post by tanari on 2004-10-15
i can't find gstreamer0.8-mad package  :(

---

### Post by bdoetsch on 2004-10-15
Startup synaptic then go to the menu "Options" (in german it's "Einstellungen") . There should be a menu item "Package Sources" (=&gt;"Paketquellen"). And there should be two inactive sources which are the universe sources. If you activate them you should be able to get the gstreamer package.

---

### Post by tanari on 2004-10-15
thanks
i find it in universe

---

### Post by elwis on 2004-10-20
I can't find it in universe? Did a search for all gstreamer package's but there were no -mad? Has the name changed perhaps?

---

### Post by elwis on 2004-10-20
Sorry about that.. I missed the apt-get update of course.. *shame on me*

---

### Post by thor on 2004-10-25
[QUOTE=ubuntu-geek]The mp3 codec was recently removed because of patent issues, they cannot install it by default any more.

Try to install the package 'gstreamer0.8-mad' from the universe, which reenables MP3 support for all multimedia applications (using gstreamer, that is). MP3 playback is free for private use.[/QUOTE]

I have added "universe" to my package sources, but I can't install gstreamer0.8-mad because it depends on libid3tag0 which is not installable..

Any hints?

---

### Post by thor on 2004-10-25
[QUOTE=thor]I have added "universe" to my package sources, but I can't install gstreamer0.8-mad because it depends on libid3tag0 which is not installable..

Any hints?[/QUOTE]

Sorrty, I have fixed the problem myself..  ;) 

The solution was to uncomment first two lines of sources.list (updated software)..

---

### Post by nolan on 2004-11-22
[QUOTE=thor]I have added "universe" to my package sources, but I can't install gstreamer0.8-mad because it depends on libid3tag0 which is not installable..

Any hints?[/QUOTE]

Just select EVERY depot. Now Synaptic should "find" libid3tag0 and deduce dependencies.

Problem: it wants to download 99mbytes! :/

Just for an mp3 codec? is there a better way to do this?

---

### Post by gravious on 2004-11-24
gstreamer mp3 plugin didn't work for me.
get realplayer 10 from the helix site.
i'd give detailed instructions but if you can't do it you shouldn't be let near a computer.

---

### Post by doni on 2004-11-25
[QUOTE=ubuntu-geek]The mp3 codec was recently removed because of patent issues, they cannot install it by default any more.

Try to install the package 'gstreamer0.8-mad' from the universe, which reenables MP3 support for all multimedia applications (using gstreamer, that is). MP3 playback is free for private use.[/QUOTE]
 good. thanks for posting this, works fine!

good job with your distro, ubuntu guys :) 

it recognized everything on my laptop.

---

### Post by Spacemars88 on 2005-09-02
for people who dont know how to get to synaptic just go to apps>system tools>add/remove programs and then click on the advanced button on the bottom of the window. there you can chose the packages you want to install just scroll down and you will find gstreamer there, tho you may need to update to see -mad

---

### Post by howcani on 2005-09-16
you goddam legend, thank you thank you thank you, now i have mp3 play in my new breezy badger

---

### Post by elyunque on 2007-02-01
For ubuntu 6.10 you can use gstreamer0.10-fluendo-mp3 

Search for it in the Synaptic Package Manager 

Fluendo Web URL: [http://www.fluendo.com/resources/fluendo_mp3.php](http://www.fluendo.com/resources/fluendo_mp3.php)

---

