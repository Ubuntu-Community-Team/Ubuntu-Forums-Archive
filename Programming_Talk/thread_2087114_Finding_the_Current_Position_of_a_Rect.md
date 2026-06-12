---
title: "Finding the Current Position of a Rect"
date: 2012-11-22
forum: Programming Talk
---

### Post by Rogers360 on 2012-11-22
Hello,

I am trying to find the current position of a rect in pygame, but I am a little confused on how to find the new position of a rect:

I have an animation going where I have a sprite moving:

```
 #Animation
    milli = clock.tick()
    seconds = milli/1000.
    dm = seconds*speed
    e_tank_x += dm

    if e_tank_x>640:
        e_tank_x = 0
```

But the problem is that I am trying to add collision detection to this game and I want the sprite to stop where it is at once it collides with another sprite.  But to do this I need to find the current position of the sprite to do so.

Here is my Tank and Bunker classes:

```
class EnemyTank(pygame.sprite.Sprite):
     def __init__(self):
         pygame.sprite.Sprite.__init__(self)
         enemytank = pygame.image.load(enemy_tank).convert_alpha()
         self.image = enemytank
         self.rect = self.image.get_rect()
     def update(self):
         self.pos = self.rect.center

class Bunker(pygame.sprite.Sprite):
    def __init__(self):
         pygame.sprite.Sprite.__init__(self)
         bunker = pygame.image.load(bunk).convert_alpha()
         self.image = bunker
         self.rect = self.image.get_rect()
    def update(self):
         self.pos = self.rect
    def collide(self, EnemyTank):
         return pygame.sprite.collide_rect(self.rect, EnemyTank.rect)
```

And in the main loop I am perfoming an action with the function in the bunker class.  Which will look something like this.

```
if player.collide == True:
         e_tank_x += 0
```

I would appreciate any hints or suggestions that anyone might have.

---

