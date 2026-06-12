---
title: "[pygame.mixer] Not playing sound apart from in IDLE"
date: 2010-05-04
forum: Programming Talk
---

### Post by Nebelhom on 2010-05-04
Hi guys,

I'm playing around with pygame's mixer module and trying to play .wav and .ogg files

I was using pydev in eclipse to write the script (see below) and couldn't get it to work (Tested with built in Run python). There were no error messages at all. When running from BASH (via 'python Script.py') I didn't get any sound output also. However, when running the script in IDLE it works (?!?).

anyone has any idea why that is? I don't really get it. Needless to say that I am not an experienced programmer, so it is possible that I missed something obvious.

Here is the code (it really is basic)

```
#!usr/bin/python

import pygame.mixer

pygame.mixer.pre_init(44100, 16, 2, 4096)
pygame.mixer.init()

channel1 = pygame.mixer.Sound('Sound/keks.wav') # .ogg work in IDLE
                                                # as well

channel1.play()
```

---

### Post by steeleyuk on 2010-05-04
I got it to work by adding a while loop.

```
#!usr/bin/python

import pygame.mixer

pygame.mixer.pre_init(44100, 16, 2, 4096)
pygame.mixer.init()

channel1 = pygame.mixer.Sound('Sound/keks.wav') # .ogg work in IDLE
                                                # as well
running = True

while running:
    channel1.play()
```

Obviously, you'll need to write a piece of code which allows to exit the loop. As to why it plays in IDLE without the loop, I don't know.

---

### Post by Nebelhom on 2010-05-04
This is just for my understanding.

why do you need a loop there?

thank you so much for your help. This would have given me sleepless nights again otherwise :D

---

### Post by Puru on 2013-02-17
Hello, sorry for resurrecting an old thread, there's no need to loop like that anyway:

```
channel1.play(100)
```

will loop 100 times

```
channel1.play(-1)
```

will loop indefinitely

---

