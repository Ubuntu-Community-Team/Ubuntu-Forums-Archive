---
title: "JavaSound - Audio Device Unavailable"
date: 2009-08-15
forum: Programming Talk
---

### Post by Finalfantasykid on 2009-08-15
I am working on a Java game, and have previously been using aif files for sound effects and music, but their file sizes were really starting to add up, so I decided to use OGG files instead.  I downloaded [http://www.javazoom.net/vorbisspi/vorbisspi.html](http://www.javazoom.net/vorbisspi/vorbisspi.html), so that the files could be decoded.  It seems like Java is unable to connect to an audio device.

```
javax.sound.sampled.LineUnavailableException: Audio Device Unavailable
at com.sun.media.sound.HeadspaceMixer.nResume(Native Method)
at com.sun.media.sound.HeadspaceMixer.implOpen(HeadspaceMixer.java:346)
at com.sun.media.sound.AbstractMixer.open(AbstractMixer.java:286)
at com.sun.media.sound.AbstractMixer.open(AbstractMixer.java:323)
at com.sun.media.sound.MixerClip.open(MixerClip.java:162)
at com.sun.media.sound.MixerClip.open(MixerClip.java:256)
...
...
...
```

The line where the error is occurring on is 
```
this.oggClip.open(din);
```

where 'din' is the decoded AudioInputStream for the ogg file, and this.oggClip is a Clip.

The same code works fine on Windows XP, but not on Ubuntu 9.04.  I looked this up on google, and it seems many people are having this problem accross many Linux distos.  Are there any ideas on how I might be able to fix this?

---

### Post by froggyswamp on 2009-08-15
Traditionally sound on Linux was bad and the Java support for sound in general was/is bad, when you combine the two you get not quite the best solution.
Also make sure your code never forgets to close a sound pipe before opening another.

---

### Post by Finalfantasykid on 2009-08-30
Are there any other Ideas?  I have resorted to working on the game in Windoze(lame).  At the very least, would you expect this to be fixed in the next version of Ubuntu, since it apparently going to be fixing some of the PulseAudio issues some people have been having.  Or is this a Java thing?

---

### Post by skywriter on 2011-11-08
Got similiar problem. When starting audio player my Java app complains:
> javax.sound.sampled.LineUnavailableException: Audio Device UnavailableAnd it still complain for a while after closing audio player.
Obtained in 10.04.

---

