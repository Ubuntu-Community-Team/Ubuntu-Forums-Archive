---
title: "Sprite follow Sprite"
date: 2011-05-11
forum: Programming Talk
---

### Post by sms27 on 2011-05-11
pygame
I am attempting to have my cloud.group follow the user controlled airplane(controlled with arrow keys) until collision.  Not sure how to or what to add to my Cloud Class.

```

class Cloud(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("puff.gif")
        self.image = self.image.convert()
        self.rect = self.image.get_rect()
        self.reset()

        
    def update(self):
        self.rect.centerx += self.dx
        self.rect.centery += self.dy
        if self.rect.top > screen.get_height():
            self.reset()
        
    
    def reset(self):
         
        self.rect.bottom = 0
        self.rect.centerx = random.randrange(0, screen.get_width())
        
        self.dy = random.randrange(5, 10)
        self.dx = random.randrange(-2, 2)

```

---

### Post by cgroza on 2011-05-11
I think there it has nothing to do with the cloud class.
I think all you need is a function taking a plane position argument.

In your main loop, you just call the function with the argument and with in your function, you loop over your clouds and set the appropriate positions depending on the current cloud and plane position.

---

