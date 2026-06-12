---
title: "Pygame sound problem"
date: 2010-02-26
forum: Programming Talk
---

### Post by tyke on 2010-02-26
Hey all.

I apologize if I'm doing something stupid here, but I'm having a real problem getting pygame to play back sound effects.

 This code:

```
import pygame
pygame.init()

pygame.mixer.music.load("some.mp3")
pyagme.mixer.music.play()
```

works fine. I can hear the music, stop and start it, no problems.

However, this code:

```
import pygame
pygame.init()

track1 = pygame.mixer.Sound("some.mp3")
track1.play()
```

does not work. No sound, no nothing.

I've tried running this in the interpretor, and the call to track1.play() appears to be returning a channel object, just as it's supposed to, but I don't get any sound. 

Does anyone have any idea where I'm going wrong?

---

### Post by JDShu on 2010-02-26
From the pygame documentation: 

> The Sound can be loaded from an OGG audio file or from an uncompressed WAV.

It appears that mp3 is not supported, try an ogg file and see if it works?

---

### Post by tyke on 2010-02-27
Tried mp3, wav and ogg files, same thing happens.

---

### Post by donkyhotay on 2010-02-27
I don't understand why you are having a problem either, I have a [project that uses pygame](code.google.com/p/tether) and my code for playing sound effects is almost identical:
```

sound = pygame.mixer.Sound(os.path.join 'data/sounds',chosen_sound)) 

sound.play()  

```
Of course I use this for sound effects in my game (no more then a few seconds) rather then music. My game also plays music but there I use:
```

pygame.mixer.music.load(os.path.join('data/music/',chosen_song))
 
pygame.mixer.music.play(1)  

```
simply because the tutorial I followed to learn how to implement sound/music with pygame did it that way. I don't know what the difference would be and haven't ever really thought about it until now because it works. I only use .ogg's in my game (no MP3's) but I doubt this would be a factor. My project is FOSS so if you want to take a look at the code for my projects audio system here is a [direct link to the complete audio code](http://code.google.com/p/tether/source/browse/trunk/client/moonaudio.py).

---

### Post by JDShu on 2010-02-27
I've been experimenting with mp3 and ogg files and I'm convinced that this is where the problem lies. Using mp3 files, I get the same results as you, they play when you use pygame.mixer.music.load() but they can't be loaded into a Sound object. Meanwhile ogg files can be loaded into Sound objects and played from them.

---

