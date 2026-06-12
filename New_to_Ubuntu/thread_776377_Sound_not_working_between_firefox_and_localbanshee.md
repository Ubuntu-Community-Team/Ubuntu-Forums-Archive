---
title: "Sound not working between firefox and local/banshee"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by farueulogy on 2008-04-30
If I watch a flash video (eg youtube) it works fine. However, if I then go to listen to an mp3/ogg in banshee the song doesn't start.

The inverse is true - If I'm listening to an mp3/ogg and pause it then go to watch a flash video the movie wont play.

I didn't have this problem on 7.04/7.10 or the mint linux equivalents. I assume it's something to do with pulse audio.

Any ideas for a fix? Any ways to regress to the sound software of 7.04/7.10?

---

### Post by farueulogy on 2008-05-04
I sure am getting better at fixing my own problems - and this one isn't as well documented as I'd like.

Basically I installed libflashsupport via

```
sudo apt-get install libflashsupport
```

this resulted in proper mixing of audio. I also set sound to always use pulse audio but I'm not sure if this was involved in my success - it's likely unnecessary.

---

### Post by lamps06 on 2008-05-05
Thank you, farueulogy!  I was having the exact same issue and your solution worked perfectly for me.  This was extremely frustrating.

---

