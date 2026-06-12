---
title: "Python acting wierd."
date: 2009-06-22
forum: Programming Talk
---

### Post by MuteClown on 2009-06-22
Hey,
i have been trying to become better at python but some scripts start acting all weird, i mean ill execute it and it will make a post script file. I never asked it to make a post script file nor did my program have anything to do with post scripts.

Here is a script which does this, its from a simple pygame tut.
I have Python 2.6

```
#/usr/bin/env python

bif="bg.jpg"
mif="mss.png"

import pygame, sys
from pygame.locals import *
pygame.init()

screen = pygame.display.set_mode((640,360),0,32)
background = pygame.image.load(bif).convert()
mouse_c = pygame.image.load(mif).convert_alpha()

while True:
    for event in pygame.event.get():
        if event.type == QUIT:
            pygame.quit()
            sys.exit()
    screen.blit(background, (0,0))
    
    x,y = pygame.mouse.get_pos()
    x -= mouse_c.get_width()/2
    y -= mouse_c.get_height()/2
    
    screen.blit(mouse_c,(x,y))
    pygame.display.update() 
```

after it closes it says syntax error ln 18,
this has happened with other programs that don't use pygame. 

Any help would be great.

---

### Post by Can+~ on 2009-06-22
> **MuteClown said:**
> Hey,
after it closes it says syntax error ln 18,
this has happened with other programs that don't use pygame. 

Any help would be great.

What error?
What do the images contain? ("bg.jpg", "mss.png")

---

### Post by MuteClown on 2009-06-22
from script posted above:
```

from: can't read /var/mail/pygame.locals
./stm.py: line 10: syntax error near unexpected token `screen'
./stm.py: line 10: `screen = pygame.display.set_mode((640,360),0,32)'
```from another script which, i was playing around with website forms. i dont think this scrip would even work normally but could never fix due to it only ever doing the postscript thing.
```
from: can't read /var/mail/ClientForm
./webtest.py: line 8: url: command not found
./webtest.py: line 10: syntax error near unexpected token `('
./webtest.py: line 10: `response = urlopen(url)'
 
```oh and bg.jpg is just a black and white gradient and the mss.png is a red circle.

---

### Post by Can+~ on 2009-06-22
> **MuteClown said:**
> from script posted above:
```

from: can't read /var/mail/pygame.locals
./stm.py: line 10: syntax error near unexpected token `screen'
./stm.py: line 10: `screen = pygame.display.set_mode((640,360),0,32)'
```from another script which, i was playing around with website forms. i dont think this scrip would even work normally but could never fix due to it only ever doing the postscript thing.
```
from: can't read /var/mail/ClientForm
./webtest.py: line 8: url: command not found
./webtest.py: line 10: syntax error near unexpected token `('
./webtest.py: line 10: `response = urlopen(url)'
 
```oh and bg.jpg is just a black and white gradient and the mss.png is a red circle.

For some reason, it's looking for pygame libraries on the /var/mail folder.

Also, I noticed that you're missing the shebang on the top of the script

```
#!/usr/bin/env python
```

How are you executing your scripts? Seems there's something messed up on your setup.

---

### Post by monraaf on 2009-06-22
Those are not Python but bash error messages!  Your script should start with:

```
#!/usr/bin/env python
```


Note the **!**

---

### Post by MuteClown on 2009-06-22
lol i feel like such an idiot...
it works now thx =]

you have no idea how dumb i feel now =S

---

