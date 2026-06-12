---
title: "[python, pygame] Need help getting movement controls right using classes"
date: 2013-02-04
forum: Programming Talk
---

### Post by horizons187 on 2013-02-04
So I have googled for hours and played with this for hours.
I have managed to make a game that works without using classes or other files but I want to make something more substantial and hence I have learned how to utilize these tools. One problem. The old method I used for movement controls doesn't port well to the way I am forced to do things via classes so I have coded a new way of handling it but for the life of me I can't seem to make it all work.

The problems hang around the self.position in __init__. I want it to give the default position of (WINDOWWIDTH // 2, WINDOWHEIGHT // 2) so it will start us in the middle of the screen but if I give it any value thats where I start and stop. I don't think it's being updated from the movement function.

I have managed to make movement sort of work with the use of a for loop before the movement ifs that looks like this:

[PHP]for k in key_states:
     if k.key == pygame.K_UP:
          dy = -1 * MOVESPEEDY * dt
      #etc for all the movement keys[/PHP]

But it only works in such a way that you have to repeatedly tap the movement key to make it work not able to hold it down.

Here is my code.

[PHP]# Lets get to savin peeps
import pygame, sys
import constants
import os.path
from pygame.locals import *

pygame.init()

class Player(object):


	def __init__(self):
		self.color = constants.WHITE
		self.position = None
	
	#Can't remember why I put this here.
	def place(self, position):
		self.position = position

	def draw(self, surface):
		(ix, iy) = (int(self.position[0]), int(self.position[1]))
		pygame.draw.circle(surface, self.color, (ix, iy,), 15)

		
	def movementPlayer(self, dt, key_states, key_pressed):
		#Heres our controls
		dx = 0
		dy = 0
                # key_states is a variable in main.py that reads
                # key_states = pygame.event.get(pygame.KEYDOWN)
		if key_states[pygame.K_DOWN]: 
                     dy = 1 * constants.MOVESPEEDY * dt
		if key_states[pygame.K_UP]:
                     dy = -1 * constants.MOVESPEEDY * dt
		if key_states[pygame.K_LEFT]:
                     dx = -1 * constants.MOVESPEEDY * dt
		if key_states[pygame.K_RIGHT]:
                     dx = 1 * constants.MOVESPEEDY * dt
		(x, y) = self.position
		self.position = (x + dx, y + dy)[/PHP]

Now as the code stands it gives me 

IndexError: Index is out of key range.

for the [pygame.K_WHATEVERS] in the if statements.

Thanks a lot for any help.
and I can post additional information if needed.

---

### Post by Tony Flury on 2013-02-05
> **horizons187 said:**
> So I have googled for hours and played with this for hours.
I have managed to make a game that works without using classes or other files but I want to make something more substantial and hence I have learned how to utilize these tools. One problem. The old method I used for movement controls doesn't port well to the way I am forced to do things via classes so I have coded a new way of handling it but for the life of me I can't seem to make it all work.

The problems hang around the self.position in __init__. I want it to give the default position of (WINDOWWIDTH // 2, WINDOWHEIGHT // 2) so it will start us in the middle of the screen but if I give it any value thats where I start and stop. I don't think it's being updated from the movement function.

I have managed to make movement sort of work with the use of a for loop before the movement ifs that looks like this:

[PHP]for k in key_states:
     if k.key == pygame.K_UP:
          dy = -1 * MOVESPEEDY * dt
      #etc for all the movement keys[/PHP]

But it only works in such a way that you have to repeatedly tap the movement key to make it work not able to hold it down.

Here is my code.

[PHP]
	def movementPlayer(self, dt, key_states, key_pressed):
		#Heres our controls
		dx = 0
		dy = 0
                # key_states is a variable in main.py that reads
                # key_states = pygame.event.get(pygame.KEYDOWN)
		if key_states[pygame.K_DOWN]: 
                     dy = 1 * constants.MOVESPEEDY * dt
		if key_states[pygame.K_UP]:
                     dy = -1 * constants.MOVESPEEDY * dt
		if key_states[pygame.K_LEFT]:
                     dx = -1 * constants.MOVESPEEDY * dt
		if key_states[pygame.K_RIGHT]:
                     dx = 1 * constants.MOVESPEEDY * dt
		(x, y) = self.position
		self.position = (x + dx, y + dy)[/PHP]


Your problem isn't in your __init__ function - I think your problem is here - you set dx and dy to zero right at the start of this function and they never get set to anything else unless you press a key. So if you don't press a key your postion doesn't change.

I think You need to pass your function the current dx & dy values and only calculate a new value when a key is pressed.


As for your index out of range error - I would need to see the code that populates your key_states argument before you call movementPlayer - and it might be helpful to output (maybe to a file) the contents of the key_states argument when the function is called.

---

### Post by micahpage on 2013-02-05
pygame.KEYDOWN only gets events of a keydown press, not holding that key. Upon a keydown, set a variable to True, upon that variable being True execute what is needed to be done while holding down the key. When key is in pygame.KEYUP, stop execution of it, as it means that the key was lifted and no longer held down.

So because all of your logic is based on pygame.KEYDOWN, it only gets executed upon one keypress, and not held keypress.

Although this can get complicated quite quickly, this is a simple example of held keypress doing an action.

```
import pygame


pygame.init()
size = (400,400)
screen = pygame.display.set_mode(size)

pygame.display.set_caption('Title')
clock = pygame.time.Clock()


idle = True

run = True
while run:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False
        elif event.type == pygame.KEYUP:
            if event.key in [pygame.K_UP]:
                idle = True
        elif event.type == pygame.KEYDOWN:
            if event.key in [pygame.K_UP]:
                idle = False
    
    if idle:
        print('character not moving')
    else:
         print('character moving')
    pygame.display.update()
    screen.fill((255,255,255))
    clock.tick(60)
    
pygame.quit()
```

---

### Post by horizons187 on 2013-02-05
> **micahpage said:**
> pygame.KEYDOWN only gets events of a keydown press, not holding that key. Upon a keydown, set a variable to True, upon that variable being True execute what is needed to be done while holding down the key. When key is in pygame.KEYUP, stop execution of it, as it means that the key was lifted and no longer held down.

So because all of your logic is based on pygame.KEYDOWN, it only gets executed upon one keypress, and not held keypress.

Although this can get complicated quite quickly, this is a simple example of held keypress doing an action.

```
import pygame


pygame.init()
size = (400,400)
screen = pygame.display.set_mode(size)

pygame.display.set_caption('Title')
clock = pygame.time.Clock()


idle = True

run = True
while run:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False
        elif event.type == pygame.KEYUP:
            if event.key in [pygame.K_UP]:
                idle = True
        elif event.type == pygame.KEYDOWN:
            if event.key in [pygame.K_UP]:
                idle = False
    
    if idle:
        print('character not moving')
    else:
         print('character moving')
    pygame.display.update()
    screen.fill((255,255,255))
    clock.tick(60)
    
pygame.quit()
```

I've tried something simliar to this but it doesn't want to work when imported as a method. could you give me an example that is using a class?

@Tony Flury

I tried your suggestion but the problem is that dx and dy are modifying the x and y values of self.position they are supposed to be zero when your not moving or else you would be constantly moving. I can get it to move using that function if I add a for loop right before the if statements it's just choppy movement.

---

### Post by micahpage on 2013-02-05
> I've tried something simliar to this but it doesn't want to work when  imported as a method. could you give me an example that is using a  class?well the global value ```
idle
``` would just be an instance variable of the class imported.

---

### Post by horizons187 on 2013-02-05
> **micahpage said:**
> well the global value ```
idle
``` would just be an instance variable of the class imported.

Thanks so much for this. I'm busy trying to dissect it now. Would you ever be able to set up a chat where I could ask you some questions or do you have any reference materials so that I could learn how to come up with something like this on my own?

---

