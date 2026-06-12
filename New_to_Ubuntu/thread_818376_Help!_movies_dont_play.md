---
title: "Help! movies dont play"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Stargazer777 on 2008-06-04
I am having trouble playing DVDs, .mpg, .MPEG, .AVI, and .mp3 format movies. A box comes up saying > "Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc. Please install the necessary plugins and restart Totem to be able to play this media." and also > "The playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed." for .mpg/.MPEG formats. I am, however, able to play a dvd and AVI files in mplayer. but it still has trouble with .mpgs.

---

### Post by sayakb on 2008-06-04
```
sudo apt-get install vlc
sudo apt-get install ubuntu-restricted-extras
```

VLC can play the files even if you don't install the second package. Installing the second one enables Totem to handle such files.

---

### Post by luke2760 on 2008-06-04
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Stargazer777 on 2008-06-04
I have already installed restricted extras. Is there something I need to download to play these movie formats? (I have ubuntu 7.10 by the way)
also... a message comes up in mplayer when i open an .mpg/.mp3 file > The filename "the holiday.mp3" indicates that this file is of type "MP3 audio". The contents of the file indicate that the file is of type "ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

---

### Post by stchman on 2008-06-04
> **Stargazer777 said:**
> I am having trouble playing DVDs, .mpg, .MPEG, .AVI, and .mp3 format movies. A box comes up saying  and also  for .mpg/.MPEG formats. I am, however, able to play a dvd and AVI files in mplayer. but it still has trouble with .mpgs.

Follow my instructions:

Install CODECs (omit the pitfdll package if using 64 bit)
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Rip CDs to MP3s (use libk3b2-extracodecs if using Hardy for K3b)
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Install DVD playback ability
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

You will be a multi media playing machine after this.

---

### Post by Stargazer777 on 2008-06-04
Ok... I got the dvd working but I am still having trouble with uploaded files.
I installed the codecs from
[http://www.stachman.com/codecs.html](http://www.stachman.com/codecs.html)
how do I install the audio/x-asf-unknown decoder plugin?

---

