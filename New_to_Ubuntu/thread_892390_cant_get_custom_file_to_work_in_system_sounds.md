---
title: "cant get custom file to work in system sounds"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by ugly92rs on 2008-08-17
ive been searching everywhere to find this this sound file to use for my login sound. it took a while but i finally found it. now when i select it from the list of files it doesnt play, it is in .wav format though. when i open the system sounds screen all the others work when playing them until i hit the custom one i set for the login, i click play and no sound. after that if i try to play one of the deafault ones no sound from them either. this file will play in other programs so i dunno where i went wrong.:confused:

---

### Post by RadioC1ash on 2008-09-11
I've searched for days for a solution to this same problem. I've come up with a workaround for the login sound (not the other system sounds). Open u package manager and search for mpg123. Select Lame and MPG123 for installation and install them. Now, go to System, Preferences, Sessions. On the Startup Programs tab, select add. Name your new startup program whatever you like, mine is Login Sound. In the command line, type ```
mpg123 -q /path/to/your/file.mp3
``` It can be any random mp3, wav or whatever you want to download codecs for. Works like a charm.

---

### Post by Bulat Sirazetdinov on 2008-09-11
> **ugly92rs said:**
> ive been searching everywhere to find this this sound file to use for my login sound. it took a while but i finally found it. now when i select it from the list of files it doesnt play, it is in .wav format though. 
Maybe it is in compressed WAV format, and your system doesn't support that type of compression ? (ADPCM, etc.)  Sometimes even MP3s come wrapped into WAV headers (or just renamed into WAV :) ).

If that is the case, then you have to convert it back into uncompressed state. Audio editing applications may be of a help.

---

### Post by thirstyghost on 2008-09-20
I've had the same problem with trying to add custom log-in sounds, whether from my own collection or from the web.   The wavs' will show up as 0 seconds and won't work.   I had even tried re-naming the main file used, but it still didn't work.

I'll try the mpg123 and lame.

---

