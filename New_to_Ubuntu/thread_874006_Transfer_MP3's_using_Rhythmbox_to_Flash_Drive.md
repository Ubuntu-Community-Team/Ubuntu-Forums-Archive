---
title: "Transfer MP3's using Rhythmbox to Flash Drive"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by mntamimi on 2008-07-29
Hi. I'm trying to do what I imagine should be fairly simple but can't seem to figure it out. And all the guide's I've read either didn't work or were for ipod's or MTP devices. 

All I'm trying to do is use the playlists I have in Rhythmbox to transfer mp3's to a USB flash drive. Something similar to the WMP syncing using playlists...

There's probably an easy solution, but I'm missing it.

Thanks!

---

### Post by gjoellee on 2008-07-29
try this:
locate the folder where you keep the music and drag it from there over to the USB flahs drive

---

### Post by El Conquistador on 2008-07-29
or go to the root of your flash drive and make a blank text file and call it [.is_audio_player] whithout the brackets.
this will let rhythmbox know that it is a media player then you can just drag your songs over using rhythmbox.

---

### Post by mordak13 on 2008-07-29
> **gjoellee said:**
> try this:
locate the folder where you keep the music and drag it from there over to the USB flahs drive

This was my initial thought as well. Probably the fastest too.

---

### Post by mntamimi on 2008-07-29
> **gjoellee said:**
> try this:
locate the folder where you keep the music and drag it from there over to the USB flahs drive

Thanks, but this doesn't really work well for me. I am trying to isolate about 8GB's of mp3's out of much more than 8GB' and individually selecting them is very inconvenient. Using existing playlists makes more sense for me. 

> or go to the root of your flash drive and make a blank text file and call it [.is_audio_player] whithout the brackets.
this will let rhythmbox know that it is a media player then you can just drag your songs over using rhythmbox. 

Thanks, this sounds like it is what I'm looking for. But a simple silly question to follow up. Does the text file have a .txt file extension? Or is there no extension?  Thanks again!

---

### Post by El Conquistador on 2008-07-29
no it does not need a .txt extension just go to the root>right-click>create document>empty file and call it .is_audio_player  then it should show up in rhythmbox under devices. glad i could help

Edit: by root i meant root of the flash drive.

---

### Post by eldragon on 2008-07-29
just drag the songs FROM rhythmbox to the newly created folder in the pendrive, thats how ive always done it. nautilus actually takes over.. and does the copying.

---

### Post by halitech on 2008-07-29
Have you tried Amarok? It has a copy to removable drive option and works fine with all 3 of my players

---

