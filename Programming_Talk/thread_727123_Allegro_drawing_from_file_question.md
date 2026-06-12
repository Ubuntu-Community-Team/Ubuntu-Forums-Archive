---
title: "Allegro drawing from file question"
date: 2008-03-17
forum: Programming Talk
---

### Post by mordi05 on 2008-03-17
Hi, I'm trying to make a poker game as a part of learning some c++.
I currently have most of the game mechanics working, and started looking at some GUI.

I found a nice picture of all the cards in a deck with the google picture search. So now I would like to be able to draw just a part of this picture to the screen. i.e. only the area displaying a give card at a time.
The full card picture is this one:
[http://math.hws.edu/eck/cs124/f05/labs/lab11/cards.png](http://math.hws.edu/eck/cs124/f05/labs/lab11/cards.png)

So far I've done this:
```

BITMAP *xSprite;

    allegro_init();
    install_keyboard();
    set_color_depth(16);
    set_gfx_mode( GFX_AUTODETECT, 1400, 1050, 0, 0);
	
xSprite = load_bitmap( "/home/...../cards.bmp", NULL);
    
    acquire_screen();
 
    draw_sprite( screen, xSprite, 150, 150);
    
 release_screen();
 
readkey();
```

Now, this draws the entire cards.bmp picture to the screen, at coordinates 150,150. Does anyone know how I could select just the area (coordinates )of a single card to be drawn?

any help would be much appreciated.
Needless to say, I'm quite new to c++, and totally so to allegro.

---

