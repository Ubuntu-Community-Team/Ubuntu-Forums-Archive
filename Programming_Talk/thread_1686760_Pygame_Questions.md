---
title: "Pygame Questions"
date: 2011-02-12
forum: Programming Talk
---

### Post by colts18 on 2011-02-12
Ok I know this is a really simple question but can someone explain how to add collision detection in pygame?  I have googled it and I keep finding on tutorials they use rect but I don't understand how it works.  Thanks.

---

### Post by juancarlospaco on 2011-02-13
The sprites of the actors have a colision area attached, how to traduce that into code, i dunno.

I migrated to a more easy and fast FrameWork than pygame: [http://www.pilas-engine.com.ar/](http://www.pilas-engine.com.ar/)

Good luck

---

### Post by colts18 on 2011-02-13
Well I have gotten so far into the game that I need to stay with pygame.  My main problem is I have read tutorials and I don't understand how I create a rect around the image I don't want an actual rectangle that is visible.   I also understand that the way to tell the object has hit the object is if the rect is overlapping the other rect.  I have looked through the documentation on the pygame website but I still don't know.

---

### Post by moephan on 2011-02-13
Here's how I do it ...

1. Create images with pygame.image.load(sprite_image)
like: my_image = pygame.image.load(path_to_image)

2. Create sprites with pygame.sprite.Sprite
my_sprite = pygame.sprite.Sprite()

3. Set a sprite's image property
my_sprite.image = my_image

4. Set a sprite's rect property
my_sprite.rect = my_image.get_rect()
(you can tweak the size of the rect if you want)

5. Often, you'll work with sprites in groups
my_group = pygame.sprite.RenderUpdates()
my_group.add(my_sprite)

6. Use various collision detection functions:
To look for collisions between a SpriteGroup and a single sprite:
list_of_sprites =  pygame.sprite.spritecollide(a_sprite, a_sprite_group, False)

If you only need to know if a sprite collided with any sprites from a group:
collided = pygame.sprite.spritecollideany(a_sprite, a_sprite_group)

Between 2 sprites:
collided = pygame.sprite.collide_rect(a_sprite, another_sprite)

etc...

Collision detection methods are all [here]("http://www.pygame.org/docs/ref/sprite.html").

HTH

---

### Post by colts18 on 2011-02-13
Ok I think I almost got it I was thinking that I would need to put a line in to tell it to stop the tank from moving but I don't think I can say tank.x = 0 but I am not sure do I need to put something like tank.x =+ 0. I am new to game creating so I am not completely sure.

---

### Post by moephan on 2011-02-13
I'm not 100% certain what you are asking. I think you are asking about how and when to test for collisions given that a sprite may be moving as well.

Typically, your game loop will have an update function that is called with each clock tick. Within this function, you will first recalculate the positions of all the sprites. Then you will use the various collision functions to see if any sprites have collided since the last tick.

HTH

---

### Post by colts18 on 2011-02-13
Let me explain my question a little more clearly ...  
I have added collision detection to my tank and enemy tank so when the enemy tank runs into the tank the tank movement should stop but I am not sure how to do that. Thanks

---

### Post by moephan on 2011-02-13
It's not possible to answer this question definitively without knowing your project. Are you using some kind of game framework other than straight PyGame?

In any case, I presume you are tracking x and y velocities in some manner. If so, you would so something like:

```

if pygame.sprite.collide_rect(player_tank, enemy_tank):
    player_tank.velocity_x = 0
    player_tank.velocity_y = 0

```

But it's impossible to say specifically without knowing what your code looks like.

---

### Post by colts18 on 2011-02-14
This is what I tried:

```
def Tank_Collision(tank, enemy_tank):
        tank_collide = pygame.sprite.collide_rect(tank, enemy_tank)
        if tank_collide:
                tank.x =+ 0
                tank.y =+ 0
```

---

### Post by colts18 on 2011-02-16
I know I am starting to get a little needy but does someone know what is wrong this is not in the main loop does it need to be?  Or am I forgetting something.

---

### Post by lavinog on 2011-02-16
Can you explain what is happening?
Can you post the code that you have?

```

pygame.sprite.spritecollide
find Sprites in a Group that intersect another Sprite
pygame.sprite.spritecollide(sprite, group, dokill, collided = None): return Sprite_list

```
Is enemy_tank a group?
I am assuming that tank_collide is an empty list when nothing is colliding, have you verified this?

---

### Post by colts18 on 2011-02-17
This is my entire code:

```
import pygame

def Tank_Collision(tank, enemy_tank):
        tank_collide = pygame.sprite.collide_rect(tank, enemy_tank)
        if tank_collide:
                tank.x =+ 0
                tank.y =+ 0
    
                                          
class Tank(pygame.sprite.Sprite):

        def __init__(self):                                     
                self.Tank = pygame.image.load("tank.png")       
                self.x = -200
                self.y = 20
                self.firecountdown=0
                self.rect = self.Tank.get_rect()

        def draw(self, surface):
                surface.blit(self.Tank, (self.x, self.y))                                           
        def update(self, dt):
                if(self.firecountdown > 0):
                        self.firecountdown-= dt
        def fire(self, bullet):
                if(self.firecountdown <=0) :
                        bullet.x = self.x
                        bullet.y = self.y
                        bullet.fired = True     
                        bullet.speed = 10
                        self.firecountdown = 1000
                        

class Bullet(pygame.sprite.Sprite):
        def __init__(self):
                self.bullet = pygame.image.load("tank_bullet.png")
                self.y = 0
                self.x = 0
                self.speed = 0
                self.forwardx = 1
                self.forwardy = 0
                self.fired = False      
        def draw(self, surface):
                surface.blit(self.bullet, (self.x, self.y))
        def update(self, dt):
                self.x += self.forwardx * self.speed 
                self.y += self.forwardy * self.speed 
                if self.x > 640:        
                        self.fired = False
                        
class Lvl_1:
        def __init__(self):
                self.floor = pygame.image.load("floor.png")
        def draw(self, surface):
                surface.blit(self.floor, (0, 0))

class Enemy_tank(pygame.sprite.Sprite):
        def __init__(self):
                self.enemy_tank = pygame.image.load("enemy_tank.png")
                self.fire_countdown_2 = 0
                self.rect = self.enemy_tank.get_rect()
        def draw(self, surface):
                surface.blit(self.enemy_tank, (200, -40))
        def update(self, dt):
                if(self.firecountdown_2 > 0):
                        self.firecountdown_2-= dt
        def fire(self, enemy_bullet):
                if(self.firecountdown_2 <=0) :
                        enemy_bullet.x = self.x
                        enemy_bullet.y = self.y
                        enemy_bullet.fired = True     
                        enemy_bullet.speed = 10
                        self.firecountdown_2 = 1000    
class Enemy_bullet:
        
        def __init__(self):
                self.enemy_bullet = pygame.image.load("enemy_bullet.png")
                self.y = 0
                self.x = 0
                self.speed = 0
                self.forwardx = 1
                self.forwardy = 0
                self.fired = False
        def draw(self, surface):
                surface.blit(self.enemy_bullet, (self.x, self.y))
        def update(self, dt):
                self.x += self.forwardx * self.speed
                self.y += self.forwardy * self.speed
                if self.x > 640:
                        self.fired = False

                        

pygame.init()                                                           
background_color = (0,0,0)                                              
(width, height) = (640, 480)                                    
screen = pygame.display.set_mode((width, height))                       
pygame.display.set_caption('Game Window')                       
clock = pygame.time.Clock()
dt = clock.tick(30)
lvl_1 = Lvl_1()
bullet = Bullet()
enemy_tank = Enemy_tank()
Tank = Tank()
enemy_bullet = Enemy_bullet()
pygame.key.set_repeat(1,50)                                     
running = True                                                  

while running: 
        Tank.update(dt)           
        bullet.update(dt)       

        screen.fill (background_color)                          
        Tank.draw(screen)       
        lvl_1.draw(screen)
        if bullet.fired == True:        
                bullet.draw(screen)
        enemy_tank.draw(screen)
        tank_lives.draw(screen)
        if enemy_bullet.fired == True:
                enemy_bullet.draw(screen)

        pygame.display.flip()                                   
        clock.tick(30)                                          

        for event in pygame.event.get():                        


                if event.type == pygame.QUIT:                           
                        running = False
                elif event.type == pygame.KEYDOWN:
                        if event.key == pygame.K_RIGHT:
                                Tank.x += 5
                        if event.key == pygame.K_LEFT:
                                Tank.x -= 5                             
                        if event.key == pygame.K_SPACE:
                                Tank.fire(bullet)       


```

---

### Post by colts18 on 2011-02-19
Does someone know any lines I am missing or anything that is wrong?

---

### Post by lavinog on 2011-02-20
Can you provide the resources to execute the code (png images..etc)
Or can you provide the error message that you are getting.

---

