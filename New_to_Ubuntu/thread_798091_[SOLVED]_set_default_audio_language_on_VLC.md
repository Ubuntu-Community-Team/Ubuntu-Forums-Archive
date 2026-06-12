---
title: "[SOLVED] set default audio language on VLC?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Vicfred on 2008-05-17
How to change the default audio language, I'm playing videos on a playlist and all of they has Catalan as the default language =(

---

### Post by ajmorris on 2008-05-18
hi there,
If you start vlc from the CLI, you can start it with:
```
vlc --audio-language <language>
``` where <language> is the audio language you want to play. However, this will only work if the video you are playing has the language in it that you specify.

AJ

---

### Post by hasenj on 2011-02-08
I know this is old, but I found another solution from [http://sites.google.com/site/thegum7/howtosetdefaultlanguageinvlc](http://sites.google.com/site/thegum7/howtosetdefaultlanguageinvlc)

Edit ~/.config/vlc/vlcrc

Look for 'audio-langauge=' and change it to something like:

```
audio-langauge=English,Japanese
```

---

