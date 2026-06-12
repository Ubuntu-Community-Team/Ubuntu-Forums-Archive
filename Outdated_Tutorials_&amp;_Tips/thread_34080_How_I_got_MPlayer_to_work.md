---
title: "How I got MPlayer to work"
date: 2005-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by tonyabrams on 2005-05-13
I've been using Ubuntu 5.04 'Hoary' for the last three weeks.  Very pleased except I've never been able to get MPlayer to work in Firefox - until yesterday.  (I was using Totem with Firefox).  I downloaded the Unofficial Ubuntu Add-On CD and decided to do a 'fresh install' with Ubuntu 5.04 Hoary (with a hard disk format) and then immediately install the Add-On CD.  Everything went smoothly (I just typed "Y" and installed all the Add-On CD programs.)  I re-booted my system and then went to the "Sound" choice in the "Preferences" menu (sorry, I'm at work using a Windows XP machine - I don't have Ubuntu in front of me).  The only modification I made is to "uncheck" 'Start Up Sound Server'.  Next I rebooted.  So now, MPlayer works properly.  The only downside (so far) is that I have to use XMMS to play mp3 music files and I have no 'System Sounds' on login.    

Summary:  How I got MPlayer to work in Firefox:

1. Fresh install of Ubuntu 5.04 Hoary.
2. Install 'Unofficial Ubuntu Add-On CD'   [http://ubuntuguide.org/add-on-cd/](http://ubuntuguide.org/add-on-cd/)  
  * find download links at the end of the page.
3. Reboot.
4. Disable 'Start Sound Server' in Preferences..Sound.
5. Use XMMS to play MP3 music.

---

### Post by bored2k on 2005-05-13
[QUOTE=tonyabrams]I've been using Ubuntu 5.04 'Hoary' for the last three weeks.  Very pleased except I've never been able to get MPlayer to work in Firefox - until yesterday.  (I was using Totem with Firefox).  I downloaded the Unofficial Ubuntu Add-On CD and decided to do a 'fresh install' with Ubuntu 5.04 Hoary (with a hard disk format) and then immediately install the Add-On CD.  Everything went smoothly (I just typed "Y" and installed all the Add-On CD programs.)  I re-booted my system and then went to the "Sound" choice in the "Preferences" menu (sorry, I'm at work using a Windows XP machine - I don't have Ubuntu in front of me).  The only modification I made is to "uncheck" 'Start Up Sound Server'.  Next I rebooted.  So now, MPlayer works properly.  The only downside (so far) is that I have to use XMMS to play mp3 music files and I have no 'System Sounds' on login.    

Summary:  How I got MPlayer to work in Firefox:

1. Fresh install of Ubuntu 5.04 Hoary.
2. Install 'Unofficial Ubuntu Add-On CD'   [http://ubuntuguide.org/add-on-cd/](http://ubuntuguide.org/add-on-cd/)  
  * find download links at the end of the page.
3. Reboot.
4. Disable 'Start Sound Server' in Preferences..Sound.
5. Use XMMS to play MP3 music.[/QUOTE]
 I'm sorry but this is really not a recommended/good way to do things at all. There are a gazillion guides here, one of them pointing to make mplayer use esd and that is it. I just wanted to tell people that there are other methods of doing this, as doing it this way will disable your ubuntu sounds without the need to.

---

### Post by tonyabrams on 2005-05-13
My point was that I was trying all those "gazillion" ways - this is the only one that worked for me.  I went through a couple of weeks of trying to make MPlayer work properly following the suggestions on the Ubuntu forums.  I gave up and used Totem.  I wonder how many other people had the same problem with MPlayer and Firefox.

---

### Post by Sniffer on 2005-05-13
You need to disable sound server anyway...if you use audacity like me!

---

### Post by bored2k on 2005-05-13
[QUOTE=Sniffer]You need to disable sound server anyway...if you use audacity like me![/QUOTE]
 Have you tried [http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd](http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd) trick?

---

### Post by Sniffer on 2005-05-16
[QUOTE=bored2k]Have you tried [http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd](http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd) trick?[/QUOTE]

Good how to, it solve the problem.

Thks.

---

### Post by Omarkj on 2005-05-20
Uhm..I just installed it from multiverse and it worked (well, I maybe had to fix the config file in order to use ALSA instead of OSS)..

---

