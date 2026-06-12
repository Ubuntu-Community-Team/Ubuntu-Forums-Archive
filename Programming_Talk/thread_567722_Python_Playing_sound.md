---
title: "Python: Playing sound"
date: 2007-10-04
forum: Programming Talk
---

### Post by mevets on 2007-10-04
I am making an alarm clock in python. This requires me to play a sound file just once. What is the easiest method to play a wav or ogg? I looked into the solutions and I saw people recommend pyMedia and ossaudiodev. Is pyGame a good idea?

Also, how would I even start to import something like pyGame? I know to add import pygame, but I do not know where I should put all the pygame code.

---

### Post by Billy the Kid on 2007-10-05
You can browse Pygame's music API here:
[http://www.pygame.org/docs/ref/music.html]("http://www.pygame.org/docs/ref/music.html"),
The most simple way to play a sound file with this module might be:
```
import pygame
pygame.init()

pygame.mixer.music.load("soundfile.ogg")
pygame.mixer.music.play()
pygame.event.wait()
```

---

### Post by mevets on 2007-10-05
Where is the lib folder for python so that I can import pyGame? I looked around found /var/lib/python2.5. Is that it?

---

### Post by bobbocanfly on 2007-10-05
You shouldnt need a path to the pygame lib, typing

```
import pygame
```

should do it.

---

### Post by moephan on 2007-10-05
For something this simple, assuming you have mplayer installed, you might consider just using popen to send mplayer the file to play.  That should be quite easy and won't require you to install pygame or other libraries.

Cheers, Rick

---

### Post by Unterseeboot_234 on 2007-10-06
I was surprised to learn the 64-bit python excludes the python sound libraries. I have not investigated my BIOS to see if the mobo onboard speaker is disabled, but

in .msw32 python environment ==> bell() is the command.

on some python installations making a file ==>  print_beep.py

```
print '\a'   # the old ASCII bell, that I bet you thought you'd never use
```

and run ```
python  print_beep.py
```

or, you can type in an NT console, at the python prompt
>>> print '\a'

all of that works, but it appears to be WIN specific

This link shows a rather lengthy built module to play a single signal through OSS. This module does work for me through my sound card / headphones.

**[http://paste.pocoo.org/show/316/]("http://paste.pocoo.org/show/316/")**

And, finally, pygame is a separate org, separate development. The py modules are totally pyCool, e.g. you can micro-manage a CD playback. You download the source, or apt-get install it or Synaptic. I built from source so I could have it linked with Python2.5.

**[pyGame]("http://www.pygame.org/news.html")**

---

### Post by mevets on 2007-10-08
a simple impot pygame does work but I had to
```

sudo apt-get install python-pygame

```
first

---

### Post by cime on 2007-10-09
Maybe you should look after Pyxine.
[http://pyxine.sourceforge.net/](http://pyxine.sourceforge.net/)

Example:
```
>>> import pyxine
>>> xine = pyxine.Xine()
>>> stream = xine.stream_new()
>>> stream.open("music.mp3")
>>> stream.play()
```

---

