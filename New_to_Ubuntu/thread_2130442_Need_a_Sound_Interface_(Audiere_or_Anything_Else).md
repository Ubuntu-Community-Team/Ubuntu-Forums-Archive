---
title: "Need a Sound Interface (Audiere or Anything Else)"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by Pinhound on 2013-03-29
Posting this here under "Beginners" -- some of this is not beginner material, but I'm stumped on how to load a package, so that makes me feel like a beginner.

Running 12.04 on a Dell laptop (Latitude D620). Everything is as it should be, especially the sound. It can play MP3s, flash video. (I even learned about the [FONT=courier new]alsamixer[/FONT] and how to turn on the pc speaker. Or more importantly, turn it back off.)

The goal was to play sound files (not picky which type) through perl. I tried to use Audiere, but can't seem to figure out how to install it properly. After a failed manual attempt (configure-make-make install) I tried opening the .deb file through the Ubuntu Software Center. It seemed to work, but installed it (it appears) in the Downloads folder. (I know not where else to put it.) It's apparently in the wrong location because anything that compiles and needs [FONT=courier new]audiere.h[/FONT] in order to work can't find it.

After some more searching, I see that the .deb package I had was for lucid (not precise). Looking through the precise packages, I don't see it.

Any thoughts on the up-to-date version of Audiere (or its equivalent) or any audio package that has a perl api, plays mp3s and (preferably) works with precise would be great.

---

