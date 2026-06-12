---
title: "Pygame help"
date: 2011-04-04
forum: Programming Talk
---

### Post by sms27 on 2011-04-04
I want to know how to fill in a color for each cirlce based on the users keyboard input

import pygame
import pygame, math
pygame.init()





def drawStuff(background):
        
    """ given a surface, draws a bunch of things on it """
    #draw rows of rectangles 
    pygame.draw.rect(background, (0, 0, 0), ((15, 7), (200, 40)), 2)
    pygame.draw.rect(background, (0, 0, 0), ((15, 52), (200, 40)), 2)
    pygame.draw.rect(background, (0, 0, 0), ((15, 97), (200, 40)), 2)
    pygame.draw.rect(background, (0, 0, 0), ((15, 142), (200, 40)), 2)                                    
    pygame.draw.rect(background, (0, 0, 0), ((15, 187), (200, 40)), 2) 
    pygame.draw.rect(background, (0, 0, 0), ((15, 232), (200, 40)), 2)

    #draw the back board
    pygame.draw.rect(background, (0, 0, 0), ((10, 2), (210, 277)), 2)

 
    
    #row 1
    pygame.draw.circle(background, (0, 0, 0), (40, 27), 15) 
    pygame.draw.circle(background, (0, 0, 0), (90, 27), 15) 
    pygame.draw.circle(background, (0, 0, 0), (140, 27), 15) 
    pygame.draw.circle(background, (0, 0, 0), (190, 27), 15) 
    #row 2
    pygame.draw.circle(background, (0, 0, 0), (40, 72), 15) 
    pygame.draw.circle(background, (0, 0, 0), (90, 72), 15) 
    pygame.draw.circle(background, (0, 0, 0), (140, 72), 15) 
    pygame.draw.circle(background, (0, 0, 0), (190, 72), 15) 
    #row 3
    pygame.draw.circle(background, (0, 0, 0), (40, 117), 15) 
    pygame.draw.circle(background, (0, 0, 0), (90, 117), 15) 
    pygame.draw.circle(background, (0, 0, 0), (140, 117), 15) 
    pygame.draw.circle(background, (0, 0, 0), (190, 117), 15) 
    #row 4
    pygame.draw.circle(background, (0, 0, 0), (40, 162), 15) 
    pygame.draw.circle(background, (0, 0, 0), (90, 162), 15) 
    pygame.draw.circle(background, (0, 0, 0), (140, 162), 15) 
    pygame.draw.circle(background, (0, 0, 0), (190, 162), 15)
    #row 5
    pygame.draw.circle(background, (0, 0, 0), (40, 207), 15) 
    pygame.draw.circle(background, (0, 0, 0), (90, 207), 15) 
    pygame.draw.circle(background, (0, 0, 0), (140, 207), 15) 
    pygame.draw.circle(background, (0, 0, 0), (190, 207), 15) 
    #row 6
    pygame.draw.circle(background, (0, 0, 0), (40, 252), 15) 
    pygame.draw.circle(background, (0, 0, 0), (90, 252), 15) 
    pygame.draw.circle(background, (0, 0, 0), (140, 252), 15) 
    pygame.draw.circle(background, (0, 0, 0), (190, 252), 15)
    

def main():
    screen = pygame.display.set_mode((640, 480))
    pygame.display.set_caption("_")
    
    background = pygame.Surface(screen.get_size())
    background = background.convert()
    background.fill((255, 255, 255))
    
    drawStuff(background)
    
    clock = pygame.time.Clock()
    keepGoing = True
    while keepGoing:
        clock.tick(30)
        for event in pygame.event.get():
            class Input(object):
                if event.type == pygame.QUIT:
                    keepGoing = False
                if event.type == pygame.KEYDOWN:
                    
                    
                    if event.key == pygame.K_r:
                        #red
                        (255, 0, 0)
                    elif event.key == pygame.K_g:
                        #green
                        (0,255,0)
                    elif event.key == pygame.K_b:
                        #blue
                        (0, 0, 255)
                    elif event.key == pygame.K_o:
                        #orange
                        (255, 165, 0)
                    elif event.key == pygame.K_y:
                        #yellow
                        (255, 255, 0)
                    elif event.key == pygame.K_n:
                        #brown
                        (165, 42, 42)
            
    
    
        screen.blit(background, (0, 0))
        pygame.display.flip()
        pygame.display.update()
if __name__ == "__main__":
    main()

---

### Post by 102jon on 2011-04-04
I suggest cleaning that code up with some for loops.

---

### Post by unknownPoster on 2011-04-04
Please wrap your code with the code tags so the formatting will be preserved. Formatting is syntax in python, and as of now your code won't run on anyone's computer.

---

### Post by cgroza on 2011-04-04
Yeah, some of that code could be written faster and cleaner with some for loops.

---

### Post by 102jon on 2011-04-05
> #row 1
pygame.draw.circle(background, (0, 0, 0), (40, 27), 15) 
pygame.draw.circle(background, (0, 0, 0), (90, 27), 15) 
pygame.draw.circle(background, (0, 0, 0), (140, 27), 15) 
pygame.draw.circle(background, (0, 0, 0), (190, 27), 15) 
#row 2
pygame.draw.circle(background, (0, 0, 0), (40, 72), 15) 
pygame.draw.circle(background, (0, 0, 0), (90, 72), 15) 
pygame.draw.circle(background, (0, 0, 0), (140, 72), 15) 
pygame.draw.circle(background, (0, 0, 0), (190, 72), 15) 
#row 3
pygame.draw.circle(background, (0, 0, 0), (40, 117), 15) 
pygame.draw.circle(background, (0, 0, 0), (90, 117), 15) 
pygame.draw.circle(background, (0, 0, 0), (140, 117), 15) 
pygame.draw.circle(background, (0, 0, 0), (190, 117), 15) 
#row 4
pygame.draw.circle(background, (0, 0, 0), (40, 162), 15) 
pygame.draw.circle(background, (0, 0, 0), (90, 162), 15) 
pygame.draw.circle(background, (0, 0, 0), (140, 162), 15) 
pygame.draw.circle(background, (0, 0, 0), (190, 162), 15)
#row 5
pygame.draw.circle(background, (0, 0, 0), (40, 207), 15) 
pygame.draw.circle(background, (0, 0, 0), (90, 207), 15) 
pygame.draw.circle(background, (0, 0, 0), (140, 207), 15) 
pygame.draw.circle(background, (0, 0, 0), (190, 207), 15) 
#row 6
pygame.draw.circle(background, (0, 0, 0), (40, 252), 15) 
pygame.draw.circle(background, (0, 0, 0), (90, 252), 15) 
pygame.draw.circle(background, (0, 0, 0), (140, 252), 15) 
pygame.draw.circle(background, (0, 0, 0), (190, 252), 15)

could be done with

```
for i in range(27, 253, 45):
	for j in range(40, 191, 50):
		pygame.draw.circle(background, (0, 0, 0), (j, i), 15)
```

or something to that effect. so much nicer.

---

