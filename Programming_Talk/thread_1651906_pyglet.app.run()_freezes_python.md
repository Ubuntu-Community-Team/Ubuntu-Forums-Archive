---
title: "pyglet.app.run() freezes python"
date: 2010-12-23
forum: Programming Talk
---

### Post by Datweakfreak on 2010-12-23
I was looking at playing sounds using python and stumbled upon pyglet. 

```
import pyglet

foo=pyglet.media.load('abc.mp3')
foo.play()

pyglet.app.run()
```The mp3 file is in the same folder as the .py file. When I run it, it plays the mp3 file, but python freezes up. I noticed that the same thing happens when I type pyglet.app.run() in interactive mode.

I'm a python newbie, just got started with it.

Any help would be much appreciated.

---

### Post by smartbei on 2010-12-24
It doesn't actually freeze python - here is what is going on:
pyglet.app.run() starts pyglet's event loop, meaning that python will be busy inside that function as long as the pyglet app is running (and there isn't a way to close it since there isn't a main window with an X button).

If what you want is to create a GUI to go with the song, this is fine - you don't need the shell to be responsive if you have a GUI (the GUI will be responsive).

If on the other hand, you just want to play a song, there are frameworks that will let you do that - check out pygame:
```

import pygame
pygame.mixer.init()
sound = pygame.mixer.Sound(<path to some file>)
sound.play()

```
Note that mp3 might be problematic - ogg and wave work great.

See also:
[http://www.pyglet.org/doc/programming_guide/index.html](http://www.pyglet.org/doc/programming_guide/index.html)
[http://en.wikipedia.org/wiki/Event_loop](http://en.wikipedia.org/wiki/Event_loop)
[http://www.pygame.org/](http://www.pygame.org/)
[http://www.pygame.org/docs/ref/music.html](http://www.pygame.org/docs/ref/music.html)

---

### Post by Datweakfreak on 2010-12-24
That was enlightening, thanks, smartbei :) Well, I'm half-inclined to use pygame now, but is there a way I can end this event loop once the mp3 has finished playing? So that python descends back to its normal responsive state?

---

### Post by smartbei on 2010-12-24
Well, you can kill the application after the song is finished by scheduling a application-killer function for right after the song:
```

import pyglet

foo=pyglet.media.load("/data/Me/Music/Goo Goo Dolls/[1998] Dizzy Up The Girl/11 - Iris.mp3")
foo.play()

def exiter(dt):
    pyglet.app.exit()
print "Song length is: %f" % foo.duration
# foo.duration is the song length
pyglet.clock.schedule_once(exiter, foo.duration)

pyglet.app.run()

```

Pyglet also lets you queue songs and such:
[http://www.pyglet.org/doc/programming_guide/controlling_playback.html](http://www.pyglet.org/doc/programming_guide/controlling_playback.html)

---

### Post by Datweakfreak on 2010-12-24
Swell, it works, thanks a ton! :p

---

