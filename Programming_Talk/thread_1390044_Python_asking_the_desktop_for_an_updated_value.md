---
title: "Python: asking the desktop for an updated value"
date: 2010-01-25
forum: Programming Talk
---

### Post by OgreProgrammer on 2010-01-25
I can set my window start location(line 4), but when the user moves it, I dont know how to get the updated value(line 14). I know its probably in gtk+ somewhere, but that is just immense. I'm having a little trouble sorting through it.

My eventual goal is to have the user move the window into place, then I will write that location to a config file, and turn off the window decorator. Using that value I will draw a section of the desktop wallpaper to simulate a transparent background. 

When the application is restarted it will thus be locked into place. I'll draw effects into that window, enhancing my desktop.

Basically I am customizing my desktop. 

```

import pygame
import os
 
# this passes the string as values... to somewhere?
os.environ['SDL_VIDEO_WINDOW_POS'] = "200, 200"
 
pygame.init()
try:
    screen = pygame.display.set_mode((400, 400))
    # This should show a blank 200 by 200 window centered on the screen
    pygame.display.flip()
 
    while True:
        event = pygame.event.wait()
        if event.type == pygame.QUIT:
            # it is not updated though. What holds the current value?
            print os.environ['SDL_VIDEO_WINDOW_POS']
            break
finally:
    pygame.quit()

```

---

### Post by lavinog on 2010-01-29
There are external ways to query X to get window positions.
```

xwininfo -name WindowTitle

```
Probably not the best way to go about this, but it should be a start.

---

### Post by OgreProgrammer on 2010-01-29
Hey thanks lavinog.

---

