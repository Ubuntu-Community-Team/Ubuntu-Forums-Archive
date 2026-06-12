---
title: "Place Image When Clicked in Pygame -  Python"
date: 2018-09-15
forum: Programming Talk
---

### Post by mousebatteries on 2018-09-15
I'm new to the forums, and I hope that this is the right place to post programming questions... (After all, it is programming talk)
And i was hoping you could help me out with an issue I have with one of my Pygame programs...

```

import pygame as pg


pg.init()
# use an image you have (.bmp  .jpg  .png  .gif)
image_file = "ball_r.gif"



black = (0,0,0)
sw = 800
sh = 800



screen = pg.display.set_mode((sw, sh))
pg.display.set_caption('testprogram')
image = pg.image.load(image_file).convert()



start_rect = image.get_rect()
image_rect = start_rect
running = True
while running:
    event = pg.event.poll()
    keyinput = pg.key.get_pressed()
    if keyinput[pg.K_ESCAPE]:
        raise SystemExit
    elif event.type == pg.QUIT:
        running = False
    elif event.type == pg.MOUSEMOTION:
        image_rect = start_rect.move(event.pos)
        
    screen.fill(black)
    screen.blit(image, image_rect)
    pg.display.flip()

```

The code above is a modified version from Daniweb ([URL]https://www.daniweb.com/programming/software-development/code/217116/image-follows-mouse-click-position-pygame[URL]).

Basically, TL;DR (Too Lazy; Didn't Run) the program makes a picture follow the mouse cursor.
What I want to do (that i cant find anywhere), is when you click with the mouse, place the image. Whilst also keeping the way that the script above works, AND (just to add insult to injury) be able to do this as many times as you want.


Any help would be useful... :) 

_MouseBatteries

---

