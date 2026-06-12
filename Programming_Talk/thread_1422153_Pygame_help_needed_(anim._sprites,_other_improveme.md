---
title: "Pygame help needed (anim. sprites, other improvements...)"
date: 2010-03-05
forum: Programming Talk
---

### Post by bc54 on 2010-03-05
hi.
i started teaching myself python about a month ago, and recently i have attempted to make some games using the [pygame module.]("http://pygame.org/news.html") so far i have followed multiple pygame tutorials, and i decided i wanted to make a clone of the iphone/ipod touch app ["Falling Balls".]("http://itunes.apple.com/us/app/falling-balls/id301545989?mt=8") right now i have a mostly done product, however i am having trouble with animated sprites. full sources is attached, and here is a look at the player class:
```
class Player(pygame.sprite.Sprite):
    """A Sprite class for the player."""
    #---------------------------------------------------------------------------
    def __init__(self):
        """Initiate some variables such as position, rect, horizontal speed
        (dx), horizontal top speed (topdx), and different images for different
        states.
        """
        pygame.sprite.Sprite.__init__(self, self.containers)
        # This was used so I could test and refine collision detection. It made
        # seeing the player sprite's rect.
        if len(sys.argv) == 2 and sys.argv[1] == 'test_stuff':
            self.image = pygame.image.load(os.path.join('data', 'Player', 'Player.png')).convert()
        else:
            self.image = pygame.image.load(os.path.join('data', 'Player', 'Player.png')).convert_alpha()
        self.rect = self.image.get_rect()
        self.x = SCREENRECT.center[0]
        self.dx = 0
        self.topdx = 25
        self.cant_run = 0
        # Different images for different states.
        self.img_normal = pygame.image.load(os.path.join('data', 'Player', 'Player.png')).convert_alpha()
        self.img_run = pygame.image.load(os.path.join('data', 'Player', 'Run.png')).convert_alpha()
        self.img_duck = pygame.image.load(os.path.join('data', 'Player', 'Duck.png')).convert_alpha()
        self.img_dead = pygame.image.load(os.path.join('data', 'Player', 'Dead.png')).convert_alpha()
    #---------------------------------------------------------------------------
    def update(self):
        """First test for collision with the circle, then make sure the player
        isn''t off screen, then update the player sprite's position.
        """
        # Difference in the y-value between the center of the circle and the top
        # of the player sprite's rect.
        deltay_squared = (self.rect.top - CIRCLES.rect.centery) ** 2
        # If the center of the circle is in the player sprite's rect
        if self.rect.collidepoint(CIRCLES.rect.center):
            self.dead()
        # If the player's left side is right of the circle's center
        elif self.rect.left >= CIRCLES.rect.centerx:
            # If the circle's center is below the top of the player sprite's
            if self.rect.top <= CIRCLES.rect.centery:
                # If the player's left side and the circle's right side overlap
                if self.rect.left < CIRCLES.rect.right:
                    self.dead()
            # If the circle's center is above the top of the player sprite's
            elif self.rect.top > CIRCLES.rect.centery:
                # If the distance between the circle's center is less than or
                # or equal to circle's radius
                if CIRCLES.radius ** 2 >= deltay_squared + (self.rect.left - CIRCLES.rect.centerx) ** 2:
                    self.dead()
        # If the circle's center is above the player
        elif self.rect.left <= CIRCLES.rect.centerx <= self.rect.right:
            # If the circle's bottom overlaps the player's top
            if self.rect.top <= CIRCLES.rect.bottom:
                self.dead()
        # If the player's right side is left of the circle's center
        elif self.rect.right <= CIRCLES.rect.centerx:
            # If the circle's center is below the top of the player sprite's
            if self.rect.top <= CIRCLES.rect.centery:
                # If the player's right side and the circle's left side overlap
                if self.rect.right > CIRCLES.rect.left:
                    self.dead()
            # If the circle's center is above the top of the player sprite's
            elif self.rect.top > CIRCLES.rect.centery:
                # If the distance between the circle's center is less than or
                # or equal to circle's radius
                if CIRCLES.radius ** 2 >= deltay_squared + (CIRCLES.rect.centerx - self.rect.right) ** 2:
                    self.dead()
        # Make sure the player is within the screen
        if self.dx == - self.topdx and self.rect.left <= self.topdx:
            self.x = self.rect.width / 2
        elif self.dx == self.topdx and self.rect.right >= SCREENRECT.width - self.topdx:
            self.x = SCREENRECT.width - self.rect.width / 2
        else:
            self.x += self.dx
        self.rect.midbottom = (self.x, SCREENRECT.bottom)
    #---------------------------------------------------------------------------
    def input(self, event):
        """Test for input, then call the appropiate method."""
        if event.type == KEYDOWN:
            if event.key == K_RIGHT:
                self.run(0, 'right')
            elif event.key == K_LEFT:
                self.run(0, 'left')
            elif event.key == K_DOWN:
                self.duck()
            elif event.key == K_RETURN:
                GAME.GamePause()
        elif event.type == KEYUP:
            if event.key == K_RIGHT:
                self.run(1)
            elif event.key == K_LEFT:
                self.run(1)
            elif event.key == K_DOWN:
                self.duck(1)
    #---------------------------------------------------------------------------
    def run(self, stop, dir='right'):
        """Move the player according to input."""
        if self.cant_run == 0:
            # Used so that there was no need of a stop_run() method
            if stop == 0:
                if dir == 'right':
                    self.image = self.img_run
                    self.dx = self.topdx
                elif dir == 'left':
                    self.image = pygame.transform.flip(self.img_run, 1, 0)
                    self.dx = - self.topdx
            else:
                self.image = self.img_normal
                self.dx = 0
    #---------------------------------------------------------------------------
    def duck(self, stop=0):
        """I put this in here because on smaller screens this game is
        ridiculously hard. Just press down and the player drops to his belly.
        Used same stop = 0 argument so I wouldn't need a unduck() method.
        """
        if stop == 0:
            self.x = self.rect.centerx
            # A little test so the player will face the oncoming circle.
            if self.x < CIRCLES.x:
                self.image = self.img_duck
            else:
                self.image = pygame.transform.flip(self.img_duck, 1, 0)
            self.cant_run = 1
            self.dx = 0
            self.rect = self.image.get_rect()
            self.rect.midbottom = (self.x, SCREENRECT.bottom)
        else:
            self.cant_run = 0
            self.x = self.rect.centerx
            self.image = self.img_normal
            self.rect = self.image.get_rect()
            self.rect.midbottom = (self.x, SCREENRECT.bottom)
    #---------------------------------------------------------------------------
    def dead(self):
        """When the circle collides with the player, draw blood and set
        Game.active to 0.
        """
        self.x = self.rect.centerx
        self.image = self.img_dead
        self.rect = self.image.get_rect()
        self.rect.midbottom = (self.x, SCREENRECT.bottom)
        GAME.active = 0

#-------------------------------------------------------------------------------

```

so basicly, if you look at the full source youll see i already have a very simple 14 sprite spritesheet. i want the player class to load up that image, splice it up, the create an array with the spliced sprites that i can use create an animation. (have the update method keep track of frames, and update the player.image accordingly.)

also, if anyone could suggest some other improvements, they would be much appreciated.
thanks.

---

### Post by bc54 on 2010-03-06
bump.

also, i forgot to mention a few other questions.
one is that if the game begins with the circle starting on the left side, upon the first update the game thinks the circle and player collide, resulting in a gameover. obviously they are not colliding, and i have no idea why its doing that.
another thing is that i would like to implement a way to increase the number of circles as the score increases, making the game harder as it progresses. something along the line of this:
```
num_circles = scoresprite.score / 10 +1
```
but i dont know how to use this (i think i tried calling circle.init() but that didnt work)
any ideas?

---

