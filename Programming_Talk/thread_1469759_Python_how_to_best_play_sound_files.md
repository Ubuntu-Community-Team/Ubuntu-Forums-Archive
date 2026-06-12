---
title: "Python: how to best play sound files"
date: 2010-05-02
forum: Programming Talk
---

### Post by Nebelhom on 2010-05-02
Hi,

I was wondering which python libraries you had the best experience with in playing sound files (.mp3, .wav, .ogg etc.).

for the moment, I just like to have a general, easy to use one that is also cross-platform (that is a must. I like using ubuntu, my mates use windows)

my aim is to just play the file. I don't know which format it will be in yet (most likely .ogg or .mp3). while I was looking around on the interwebs for information I found pygame and pymedia, but (to the best of my knowledge) pygame only plays .ogg and .wav, while pymedia seems to only play .mp3 and .wav. Is there one that does both? Am I right in saying that the built in sound modules are for .wav only?

The ideal scenario would be something that can handle .ogg and .mp3, is easy to use and runs on both windows and linux. I know this may be a lot to ask, but the hope dies last, I guess ;)

Thanks for the feedback.

---

### Post by km0r3 on 2010-05-02
Look at [audiere]("http://audiere.sourceforge.net/"). It does both .ogg and .mp3 and is cross-platform and also has Python bindings.

---

### Post by TheStatsMan on 2010-05-02
Pygame also plays mp3.

---

### Post by km0r3 on 2010-05-02
> **TheStatsMan said:**
> Pygame also plays mp3.

This is true.

Check out the reference:

[http://www.pygame.org/docs/ref/music.html](http://www.pygame.org/docs/ref/music.html)

---

### Post by Nebelhom on 2010-05-03
First of all, thanks a lot for your replies! I will try out audiere.

> Pygame also plays mp3. 

That is strange. before I posted the thread I was trying it out and it didn't work. pygame played .ogg and .wav files just fine, but it didn't play .mp3 and .wma...

quote from webpage

> Be aware that MP3 support is limited. On some systems an unsupported format can crash the program, e.g. Debian Linux. Consider using OGG instead. 

I must have encountered that... :confused:

I find using pygame very user-friendly, so if all else fails, I will just make sure everyone knows that they have to use .ogg files together with the application and stick with pygame.

Thanks again for the help guys. Good to know that there is always someone out there who knows more than me who is also willing to answer my questions ;)

---

### Post by TheStatsMan on 2010-05-03
Definitely works on Ubuntu, I have used it before several times.

---

### Post by Nebelhom on 2010-05-03
@TheStatsMan

I'll give it a go again tonight and see what I can make of it then. If I still can't do it, I shall annoy you a little more with the scripts I wrote :)

---

### Post by steeleyuk on 2010-05-03
I'd just use gstreamer and its Python bindings, as it supports Windows.

It'll also play almost anything you throw at it, assuming you have the correct codecs installed.

---

### Post by Nebelhom on 2010-05-03
Aaaaahhh, I now understand why I couldn't play mp3's (used pygame.mixer not pygame.mixer.music) and I also found another criterium that I need. 

Availability of more than one channel (preferably 4+) because I would like to play more than one sound file at once. pygame.mixer.music unfortunately only provides one channel :( and loading via pygame.mixer.Sound only supports .wav and .ogg (This is where I got the limitations from)

sorry for that late add-on and thanks for the help. apologies, I just don't know enough about this yet :(

---

