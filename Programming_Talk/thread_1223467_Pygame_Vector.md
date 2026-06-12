---
title: "Pygame Vector"
date: 2009-07-26
forum: Programming Talk
---

### Post by matmatmat on 2009-07-26
I am using the gameobject class:
```

import pygame
from pygame.locals import *
from sys import exit
from random import randint
from sys import argv
from gameobjects.vector2 import Vector2


screen = pygame.display.set_mode((600,480), 0, 32)
back = pygame.image.load("data/map1.png")
me = pygame.image.load("data/me.png")
clock = pygame.time.Clock()
score = 1000
x = 10
y = screen.get_height()/2 - me.get_height()
distance_moved = 0
speed = 100.
position = Vector2(100.0, 100.0)
heading = Vector2()
destination = Vector2()
left = False
top = False
while True:
	time_passed = clock.tick(30) / 1000.0
	screen.blit(back, (0,0))
	for event in pygame.event.get():
	    	if event.type == QUIT:
            		print score
			exit()
		if event.type == MOUSEBUTTONDOWN:
			destination = Vector2(*event.pos) - Vector2(*me.get_size())/2.
			heading = Vector2.from_points(position, destination)
			heading.normalize()
	distance_moved = time_passed * speed
	position += heading * distance_moved
	screen.blit(me, (position))
	pygame.display.update()

```
I want it to stop once it gets to the destination, how do I do it?

---

### Post by MeLight on 2009-07-26
Not really good with pygame syntax, but what you should do is calculate the distance between your current position and the target position. If you have two 2d vectors (vPos and vTrg) the pseudo code will look like this:

```


while(calcDist(vPos, vTrg) > 0.0001) {
    //keep moving
}

calcDist(v1, v2) {
    dx = v2.x - v1.x;
    dy = v2.y - v1.y;

    return squareRoot(dx*dx + dy*dy);
}

```

Note: If pygame is a game engine the distance function should already be supplied by the environment

---

### Post by lavinog on 2009-07-26
Same thing MeLight said, but in python syntax:
can you just get the difference of the two and test to be less than a small number
```

distance = position - destination
if distance.length() <.001:
    print('we are here')

```
I am not familiar with gameobject yet. It should be able to do vector addition and subtraction. I don't know what the method is for length, but it to get the length of a vector:
```

length = math.sqrt( v[0]**2 + v[1]**2 )

```

---

