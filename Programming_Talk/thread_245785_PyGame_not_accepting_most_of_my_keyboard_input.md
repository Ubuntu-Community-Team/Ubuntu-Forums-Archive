---
title: "PyGame not accepting most of my keyboard input"
date: 2006-08-28
forum: Programming Talk
---

### Post by Keffin on 2006-08-28
I've just been messing around with pygame and have a strange problem with it (not) accepting events. I've condensed it down into a very simple program, but I don't know python at all so I have no idea if it's my fault or pygames...

```
import os, sys
import pygame
from pygame.locals import *


def main():
   pygame.init()
   window = pygame.display.set_mode((200, 200))
   pygame.display.set_caption('Test')
   
   while True:
      for event in pygame.event.get():
         if event.type is pygame.QUIT:
            sys.exit(0)
         elif event.type is pygame.KEYDOWN or event.type is pygame.KEYUP:
            if event.key is pygame.K_w:
               print "Pressed w"
            elif event.key is pygame.K_e:
               print "Pressed up"
            elif event.key is pygame.K_SPACE:
               print "Pressed up"
            elif event.key is pygame.K_UP:
               print "Pressed up"
            elif event.key is pygame.K_ESCAPE:
               print "Pressed escape"
            else:
               print event.key


if __name__ == "__main__":
    main()
``` 
When I run this and start pressing keys, it recognises the escape key and prints "Pressed escape", the space key is interpreted as the up key and prints "Pressed up", and the others aren't recognised by the elif statements, but the else statement shows that the event.key value is as would be expected (e.g. w shows event.key as 119, which is correct).

If it makes any odds I have a Logitech Cordless Desktop MX3000 keyboard (UK layout) that works perfectly fine for e.g. typing this message. I have tried turning on/off caps lock, num lock etc, but to no avail.

Does anyone know what is happening?

Thanks.

---

### Post by Cryonic on 2006-08-28
'is' tests for object identity, not object values. 
Check the following link:

[http://rgruet.free.fr/PQR2.2.html#BasicTypes](http://rgruet.free.fr/PQR2.2.html#BasicTypes)

---

### Post by Keffin on 2006-08-28
> **Cryonic said:**
> 'is' tests for object identity, not object values. 
Check the following link:

[http://rgruet.free.fr/PQR2.2.html#BasicTypes](http://rgruet.free.fr/PQR2.2.html#BasicTypes)

That would explain it then. I got carried away when I saw that you use "and" and "or", I saw "is" being used in an example and assumed it was just syntactic sugar over "==" :rolleyes:.

Thanks for setting me straight :).

---

### Post by skymt on 2006-08-28
> **Keffin said:**
> That would explain it then. I got carried away when I saw that you use "and" and "or", I saw "is" being used in an example and assumed it was just syntactic sugar over "==" :rolleyes:.

Thanks for setting me straight :).

That's a general rule in Python. Unlike, say, other popular high-level interpreted languages (cough, Ruby), in Python there's usually only one way to say something. This makes it harder to produce code that looks *just right*, but so much easier to interpret other programmers code.

---

