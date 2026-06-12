---
title: "Issue with OpenAL and .ogg development"
date: 2007-11-05
forum: Programming Talk
---

### Post by Ominide on 2007-11-05
Hi,
  I'm trying to Make a game for one of my CS classes using OpenGL along with OpenAL/ogg but I'm running into a little snag.  I have a simple program just used to play sounds but will be brought into the game once its working so the Audio and Graphics are currently separated.  I'm not sure whats going on but when I run my audio program with the ogg's they sound like their skipping / choppy.  Its not the code I'm using because I've compiled the same I dentical code on another machine and it works fine (that machine won't do graphics),

Both have integrated audio cards but the openal / ogg will not work on my graphics machine.  Is there any chance that I could get some help in diagnosing this problem.  Also .ogg files play fine in any of the media players on the machine ie totem, xmms etc.

Graphics Machine:
NVidia NForce2 audio (choppy)

not graphics machine:
M5451 AC-Link ??  (works)
Audigy2                (works)

Thanks

---

### Post by Quikee on 2007-11-05
Create a file name .openalrc in your home folder and paste this into it:

```

(define devices '(alsa sdl native))

```

Maybe it will work (it did for me for many games).

---

### Post by RootsLINUX on 2007-12-02
I've experienced the exact same problem on my Ubuntu laptop with the game I develop ( [http://www.allacrost.org](http://www.allacrost.org) ). Our audio engine works beautifully on Linux, OS X, Windows... but not my laptop. I'll try what you said Quikee and hope that it works.

BTW, the contents of  the .openalrc file on my Debian machine is:

```

(define devices                 '(native alsa sdl arts esd null))
(define alsa-device             "dsp0")
(define speaker-num             2)
;(define sampling-rate          22050)


```

---

