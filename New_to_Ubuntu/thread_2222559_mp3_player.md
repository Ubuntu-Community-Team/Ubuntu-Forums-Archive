---
title: "mp3 player"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by sandy59 on 2014-05-07
I can't seem to get ubuntu 14.04 64bit to detect my mp3 player. I have tried pluging it into every usb port on my laptop with the same result. Nothing.
I tried to get amarok to find it but still no joy.
Any suggestions would be very much appreciated.
Thanks
Sandy.

---

### Post by ajgreeny on 2014-05-07
Does the mp3 player connect with mtp as many do unless you change the player setup?  That will require at least the mtpfs package with dependencies to be installed and possibly with a few others.

---

### Post by BBQdave on 2014-05-07
> **sandy59 said:**
> I can't seem to get ubuntu 14.04 64bit to detect my mp3 player. ...I tried to get amarok to find it...

This information helped with Rhythmbox and Sansa Clip+ mp3 player:

*If Rhythmbox Music Player does not detect your device as a portable audio player, you can create an empty file named* [COLOR=#ff0000]**.is_audio_player**[/COLOR] [I]at the top level hierarchy of the filesystem of your player.
[/I]
My Sansa Clip+ is set to MSC mode. And I am able to sync my music with Rhythmbox.

Maybe adding file .is_audio_player will help Amarok see your mp3 player. And I would set your player to MSC mode or try MTP mode :)

---

### Post by Thomas_Robert on 2014-05-07
Try to check your MP3 player on any other OS, I guess its fault with your mp3 player :) or your MP3 player is switched off.

---

### Post by Tar_Ni on 2014-05-07
Have you tried Banshee? I've heard that it support a wide range of devices including Ipods.

[URL="http://banshee.fm/"]http://banshee.fm/
[/URL]
Might be worth giving it a shot! :)

---

