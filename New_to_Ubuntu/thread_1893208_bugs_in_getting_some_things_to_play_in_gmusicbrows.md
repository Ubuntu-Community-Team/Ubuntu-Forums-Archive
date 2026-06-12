---
title: "bugs in getting some things to play in gmusicbrowser"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by 118118 on 2011-12-09
sometimes i get 
```
Playing error : Failed to parse stream at /usr/bin/../share/gmusicbrowser/gmusicbrowser_gstreamer-0.10.pm line 135.

```when i try to play something [always on some songs]
other times i get```

Error reading tag for
```when trying to add something.


thanks.

---

### Post by 118118 on 2011-12-12
no help??

---

### Post by dave0109 on 2011-12-12
I've seen something similar twice.  Once when I had a missing codec for handling MP3, and once when gmusicbrowser hadn't noticed that my files had moved.  In the latter case, I opened up the settings and rescanned my music library and all was well.

---

### Post by 118118 on 2011-12-12
hi,

how can i make sure i have all the MP3 codecs i need :) ??

:popcorn:

---

### Post by dansang on 2011-12-12
To add extra codecs please read and look for the xubuntu link on this page!

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Also ffmpeg may help with music streaming! Search for it in the synaptic package manager!

---

### Post by 118118 on 2011-12-13
hi,

i get the same error messages still, after installing the restricted extras and ffmpeg.

---

### Post by 118118 on 2011-12-13
i tried running the problematic MP3s in banshee and this time get
> 
[Error 00:16:43.926] GStreamer stream error: Decodewhen i play the song that will add and the rest of the songs from that folder just don't add with no error message shown.


i think these MP3s played fine in exaile before i swithched to xubuntu from ubuntu.

---

### Post by dave0109 on 2011-12-16
Might be worth installing exaile just to verify, but either there's an error in your MP3 files (unlikely if you've played them before), there's an error in the MP3 codec, or the codec isn't installed (properly or at all).

That's probably stating the obvious though.

---

### Post by 118118 on 2011-12-19
hi

no they won't run in exaile either :popcorn:

---

### Post by 118118 on 2011-12-20
well i may have recently changed these tags - they are from an album whose tags were annoying me. i tried changing them again in esaytag but that did nothing - i got the same error after deleting the songs from the library and trying again.

i don't have all my library on gmusicbrowser yet. i tied adding all of it and it crashed [the whole of ubuntu i mean - i just got an indecipherable text display] half way through.
recently my external hard drive failed [i dropped it] and its current incarnation was a rushed backup of the former before it clicked itself to death or whatever.

is there any way i can scan the ex hard drive for mp3s or flac that are corrupted??

thanks for any advice whatsoever.

---

