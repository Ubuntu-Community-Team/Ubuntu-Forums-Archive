---
title: "PyGame: Making Background Scroll Seamlessly"
date: 2009-12-09
forum: Programming Talk
---

### Post by azurepancake on 2009-12-09
Hello!

I'm working on a side-scrolling space shooter and I've ran into a bit of a problem..

At the moment, I'm trying to implement a scrolling background. The window size of the game is 800x600, so I made a 1600x600 image of space in the GIMP. I then defined it as an object:

```
class Space(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image, self.rect = load_image("space.png", -1)
        self.dx = -5
        self.reset()
        
    def update(self):
        self.rect.left += self.dx
        if self.rect.right <= 800:
            self.reset() 
    
    def reset(self):
        self.rect.right = 1600
```

As you can see, when the right-hand side of the background image hits the 800 pixel mark on the screen, it resets. But since it isn't seamless, the reset is very noticeable. Here is the image:

[IMG]http://tristanevans.net/projects/spacequest/space.png[/IMG]

I'm sure it's something easy to do in the GIMP, but I can't seem to figure it out. I did some searches on Google and I tried using, '*Filters > Map > Make Seemless*' and this changed a few things around, but when the image resets, it is still very obvious.

Does anyone know the best way of going about this?

I will really appreciate any tips!

Thank you.

---

