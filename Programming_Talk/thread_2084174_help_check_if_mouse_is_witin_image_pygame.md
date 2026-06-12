---
title: "help check if mouse is witin image pygame"
date: 2012-11-14
forum: Programming Talk
---

### Post by snowlizard31 on 2012-11-14
Hi, I want to find a way to check if the mouse is within an image so I can if the user clicks within the image an event happens I'm tying to make a button. can someone help me I have no idea on how and where to start.
okay I have some code and it sort of works the problem is that the image itself isn't click-able but if I click above it; it is click-able
it appears that only the top left corner of the screen if click-able :(
```

import pygame
import sys

pygame.init()
Button = pygame.image.load('button_temp.png')
screen = pygame.display.set_mode((640,480))

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.quit()
    
        if event.type == pygame.MOUSEBUTTONDOWN:
            if Button.get_rect().collidepoint(pygame.mouse.get_pos()):
                print "hey"
    
    screen.fill((255,255,255))
    screen.blit(Button,(100,100))
    pygame.display.flip()

```

---

### Post by ofnuts on 2012-11-15
If the mouse is above one of your windows you should be receiving MOUSEMOTION events. But there is no need to monitor that, if the user clicks in your window you get a MOUSEBUTTONDOWN.

---

### Post by bird1500 on 2012-11-15
As a side note, if you click (and keep the mouse button down) on  a window and  move the cursor outside the window you'll still be getting mouse move/dragged events until you release the mouse button. So, sometimes you get mouse events even if they're not physically over your window(s).

---

### Post by snowlizard31 on 2012-11-15
Ok but how do I check if the MOUSEBUTTONDOWN event is inside the image?

---

### Post by ofnuts on 2012-11-16
> **snowlizard31 said:**
> Ok but how do I check if the MOUSEBUTTONDOWN event is inside the image?

See here: [http://stackoverflow.com/questions/10168447/how-to-make-buttons-in-python-pygame](http://stackoverflow.com/questions/10168447/how-to-make-buttons-in-python-pygame)

---

