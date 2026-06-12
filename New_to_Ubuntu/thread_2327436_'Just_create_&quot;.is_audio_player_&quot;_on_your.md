---
title: "'Just create &quot;.is_audio_player &quot; on your USB stick.' How do I do that?"
date: 2016-06-10
forum: New to Ubuntu
---

### Post by badabec on 2016-06-10
[SIZE=2]Hello, Ubuntu 12.04, clean install. Plenty of music in Rhythmbox, I want to transfer to a USB memory stick to use in the car. Copy and paste won't work.

Rhythmbox help says

[COLOR=#3C3C3C][FONT=sans-serif]If [/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif]*Rhythmbox Music Player*[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif] does not detect your device as a portable audio player, you can create an empty file named[/FONT][/COLOR][COLOR=#3C3C3C][FONT=monospace] .is_audio_player[/FONT][/COLOR][/SIZE][COLOR=#3C3C3C][FONT=sans-serif][SIZE=2] at the top level hierarchy of the filesystem of your player.

How do I do this? Idiot's guide please.

Thanks

Peter[/SIZE]
[/FONT][/COLOR]

---

### Post by X-RED_Tech on 2016-06-10
With don't use the file manager?
Rythmbox is a music player. It has no music, the audio files are somewhere else, hopefully grouped together in the default Music folder.
It can't be easier than copy/paste mp3 files/album folders to any USB memory stick.

The playlist sync / file transfer features are not for standard mp3 players (mass storage devices) or any other standard USB flash memory device or USB HDD.

---

### Post by CantankRus on 2016-06-10
> **badabec said:**
> [SIZE=2]Hello, Ubuntu 12.04, clean install. Plenty of music in Rhythmbox, I want to transfer to a USB memory stick to use in the car. Copy and paste won't work.

Rhythmbox help says

[COLOR=#3C3C3C][FONT=sans-serif]If [/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif]*Rhythmbox Music Player*[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif] does not detect your device as a portable audio player, you can create an empty file named[/FONT][/COLOR][COLOR=#3C3C3C][FONT=monospace] .is_audio_player[/FONT][/COLOR][/SIZE][COLOR=#3C3C3C][FONT=sans-serif][SIZE=2] at the top level hierarchy of the filesystem of your player.

How do I do this? Idiot's guide please.

Thanks

Peter[/SIZE]
[/FONT][/COLOR]
Are you saying you can't copy/paste to the usb stick **or** after copy and paste the usb stick doesn't work in the car?

---

### Post by HermanAB on 2016-06-11
$ touch /media/musicplayername/.is_audio_player

---

### Post by badabec on 2016-06-11
Hello, thank you X-Red_Tech, CantankRus and HermanAB for your help. I now realise that Rhythmbox doesn't hold any music files, and as X-Red_Tech said, I copied and pasted the files. Problem solved.
The next problem is getting to play Captain Beefheart, Miles Davis and Talk Talk in the car without my wife turning it off.
Thanks again
Peter

---

### Post by HermanAB on 2016-06-12
"without my wife turning it off" - Maybe provide her with a large 1980s style remote control that doesn't actually do anything to keep her entertained: [http://ecx.images-amazon.com/images/I/41-%2BGsvuMBL._SY355_.jpg](http://ecx.images-amazon.com/images/I/41-%2BGsvuMBL._SY355_.jpg)

---

