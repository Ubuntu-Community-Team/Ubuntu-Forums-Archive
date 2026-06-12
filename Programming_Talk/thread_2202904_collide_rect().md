---
title: "collide_rect()"
date: 2014-01-31
forum: Programming Talk
---

### Post by blackout2 on 2014-01-31
```

black = (0,0,0)
white = (255,255,255)






import pygame
pygame.init()
Screen = pygame.display.set_mode((1900, 1020))
pygame.display.set_caption("Man_Control/Collision")




class Hero_Sprite(pygame.sprite.Sprite):
	def __init__(self,x,y):
		pygame.sprite.Sprite.__init__(self)
		self.hero = pygame.image.load('/root/Pictures/hero.png').convert()
		self.x = x
		self.y = y
		self.rect = self.hero.get_rect()
	def drawHero(self):
	 	Screen.blit(self.hero, (self.x, self.y))
		
	




class Object(pygame.sprite.Sprite):
	def __init__(self):
		self.object_c = pygame.image.load('/root/Pictures/grass.png').convert()
		self.x = 100
		self.y = 100
		self.rect = self.object_c.get_rect() 
	def drawObject(self):
			Screen.blit(self.object_c, (self.x, self.y))


			
			




















hero_sprite = Hero_Sprite(200,200)
object_c = Object()
x=True
while x:
	for x in pygame.event.get():
		if x.type == pygame.QUIT:
			x=False
	if x.type == pygame.KEYDOWN:
		if x.key == pygame.K_LEFT:
			hero_sprite.x -= 2
		if x.key == pygame.K_RIGHT:
			hero_sprite.x += 2
		if x.key == pygame.K_UP:
			hero_sprite.y -= 2
		if x.key == pygame.K_DOWN:
			hero_sprite.y += 2
      #I know that I need to add in KEYUP, but I know how to do that, it's not the problem.
	if hero_sprite.rect.collide_rect(object_c.rect) == True:#Problem lines
		print "Succes"#I'll add in movement restrictions later
	else:
		print "Fail"
		
	
	
	Screen.fill(white)
	object_c.drawObject()
	hero_sprite.drawHero()
	pygame.display.update()

```

Basically, my statement keeps thinking that I'm colliding with object_c.rect, but I'm not, and I don't know why it's doing that. 
It should be self-explanatory for most of you.
Thanks for the help!

---

### Post by ofnuts on 2014-02-01
I'm not very familiar with pygame programming, but one would expect the bounding rectangle of objects to change when they move... and your rect attribute is a static value, not a function that computes a rectangle given x,y, and some width and height.

Or; since IMHO it's also bad practice to set x,y directly in objects, give them some moveTo(x,y) method, that, in addition to setting the coordinates, also computes the corresponding bounding rectangle.

---

### Post by blackout2 on 2014-02-01
Thanks nuts, I was thinking the same thing, but the problem is, I'm not sure *how*, to change the values of the rect. I'll just experiment passing it values in different ways and do some research. Thanks!
(Oh, and another thing I noticed, I forgot to initialize the pygame.sprite.Sprite instance in Object().) -oops.....

---

### Post by ofnuts on 2014-02-01
Pygame has the necessary API to see if two sprites collide without needing to explicitly  use their rectangles: 
```

if pygame.sprite.collide_rect(hero, object)

```

To move the sprite, move the rectangle with the move_ip() method of the rectangle (the parameters are offsets for X and Y, not an absolute position).

---

### Post by blackout2 on 2014-02-01
Thanks, I know I can rely on good 'ole ofnuts for help.

---

### Post by blackout2 on 2014-02-01
Alright, it's almost there.
Wherever I spawn the "hero_sprite", the "object_c" rect is spawned with it. If I switched the position of "hero_sprite", the object_c rect would spawn right there as well. Basically, my "object_c"'s rect, would be placed at the center of wherever hero_sprite's rect was placed. Weird, I'm not sure why...
```

black = (0,0,0)
white = (255,255,255)
import pygame
pygame.init()
Screen = pygame.display.set_mode((1900, 1020))
pygame.display.set_caption("Man_Control/Collision")




class Hero_Sprite(pygame.sprite.Sprite):
    def __init__(self,x,y):
        pygame.sprite.Sprite.__init__(self)
        self.hero = pygame.image.load('/root/Pictures/hero.png').convert_alpha()
        self.x = x
        self.y = y
        self.rect = self.hero.get_rect()
        self.rect.move_ip(0,0)
    def drawHero(self):
        Screen.blit(self.hero, (self.x, self.y))
        if hero_sprite.x <= 0:
            hero_sprite.x += 2
        if hero_sprite.y <= 0:
            hero_sprite.y += 2
        if collide(hero_sprite, object_c):
            Screen.blit(self.hero, (self.x, self.y))
            print "COLLISION"
        else: 
            Screen.blit(self.hero, (self.x, self.y))
            print "NULL"
            


class Object(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.object_c = pygame.image.load('/root/Pictures/grass.png')
        self.x = 100
        self.y = 100
        self.rect = self.object_c.get_rect()
    def drawObject(self):
            Screen.blit(self.object_c, (self.x, self.y))


def collide(Object1, Object2):
    if pygame.sprite.collide_rect(Object1, Object2):
        return True
    else:
        return False


hero_sprite = Hero_Sprite(200, 200)
object_c = Object()
x=True
while x:
    for x in pygame.event.get():
        if x.type == pygame.QUIT:
            x=False
    if x.type == pygame.KEYDOWN:
        if x.key == pygame.K_LEFT:
            hero_sprite.rect.move_ip(-2, 0)
            hero_sprite.x -= 2
        if x.key == pygame.K_RIGHT:
            hero_sprite.rect.move_ip(2, 0)
            hero_sprite.x += 2
        if x.key == pygame.K_UP:
            hero_sprite.rect.move_ip(0, -2)
            hero_sprite.y -= 2
        if x.key == pygame.K_DOWN:
            hero_sprite.rect.move_ip(0, 2)
            hero_sprite.y += 2
    Screen.fill(black)
    object_c.drawObject()
    hero_sprite.drawHero()
    pygame.display.update()

```

---

### Post by ofnuts on 2014-02-02
When you do this:
```

        if x.key == pygame.K_LEFT:
            hero_sprite.rect.move_ip(-2, 0)
            hero_sprite.x -= 2

```

One wonder why you maintain x and y in hero_sprite. You can just as well obtain them from hero_sprite.rect when you need them.

---

### Post by blackout2 on 2014-02-02
I didn't know that you can do that, I'll have to put some thought into doing that, but for now, do you have any idea what is causing my object_c rect to spawn with the hero_sprite rect?

---

