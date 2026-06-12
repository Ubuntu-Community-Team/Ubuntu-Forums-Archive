---
title: "Add pause to  python"
date: 2011-01-02
forum: Programming Talk
---

### Post by bmanzana on 2011-01-02
hello,
i have been reading everything on this website i can, and cannot figure out how to start new threads and have not been able to find my issue as of yet, so Im just going to post it here sorry if thats the wrong thing to do. i have tried contacting a council member to get help and haven't heard anything yet. Anny way heres my problem. i am building a pong type game as an experiment to get better at using python, and cannot seem to find a way to add a pause feature i have tried a great deal of approaches but nothing seams to work. i will include the full code if any one could offer some advice i would be extatic. 

```
import pygame,sys,random
from pygame.locals import *

pause=0
      

pygame.init()

screen=pygame.display.set_mode((1024,768),0,32)
pygame.mouse.set_visible(False)
background=pygame.image.load('window.jpg').convert()
ball=pygame.image.load('ball.png').convert_alpha()
stopper1=pygame.image.load('bar1.png').convert_alpha()
stopper2=pygame.image.load('bar2.png').convert_alpha()

sound=pygame.mixer.Sound('Laser.ogg')

x=random.uniform(0.0,1000.0)
y=random.uniform(0.0,728.0)
x2=1010
y2=300

speeds=600
speedx=200
speedy=200
clock=pygame.time.Clock()
                                
while True:
    for event in pygame.event.get():
        if event.type==QUIT:
            sys.exit()
            pygame.quit()
            
        if event.type==KEYUP:
            if event.key==K_ESCAPE:
                pygame.display.toggle_fullscreen()
                
        if event.type==KEYUP:
            if event.key==K_p:
                pause=True
            elif event.key==K_s:
                pause==False
                
        if pause==True:
            pygame.time.delay(3000)
        if pause==False:
            pygame.time.delay(0)
            continue                  
            
                                                                                   
    screen.blit(background,(0,0))
    screen.blit(ball,(x,y))
    screen.blit(stopper1,(0,0))
    screen.blit(stopper2,(x2,y2))
    milli=clock.tick()
    seconds=milli/1000.0
    dmx=seconds*speedx
    dmy=seconds*speedy
    dms=seconds*speeds
    
    x-=dmx
    y-=dmy

    if pygame.Rect(0,0,15,768).colliderect(x,y,50,50)==True:
        speedx=-speedx
        sound.play()
          
    if y<=0:
        speedy=-speedy
        sound.play()
        
    if y>=728:
        speedy=-speedy
        sound.play()
        
    if pygame.Rect(x,y,50,50).colliderect(x2,y2,15,50)==True:
        speedx=-speedx*1.1
        sound.play()
        
    if x>=1024:
        break
        
    if event.type==KEYDOWN:
        if event.key==K_UP and y2>15:
            y2-=dms
           
    if event.type==KEYDOWN:
        if event.key==K_DOWN and y2<704:
            y2+=dms  
                          
    pygame.display.update()
    
while True:
    for event in pygame.event.get():
        if event.type==QUIT:
            sys.exit()
            pygame.quit()
            
        if event.type==KEYUP:
            if event.key==K_ESCAPE:
                pygame.display.toggle_fullscreen()          
                            
    screen.blit(background, (0,0)) 
    font=pygame.font.SysFont('liberationserif',100)
    gameover=font.render('Game Over', True, (0,0,0), (255,255,255))
    screen.blit(gameover,(300,100))
    restart=font.render('Restart? y/n', True, (0,0,0), (255,255,255))
    screen.blit(restart, (300,400))
    
    if event.type==KEYDOWN:
        if event.key==K_n:
            sys.exit()
            pygame.quit()
            
        elif event.type==KEYDOWN:
            if event.key==K_y:
                exec file('mypong.py')
              
    pygame.display.update()
```

---

### Post by ziekfiguur on 2011-01-02
change this:
```
        if pause==True:
            pygame.time.delay(3000)
        if pause==False:
            pygame.time.delay(0)
            continue 
```

to this: ```
    if pause==True:
        pygame.time.delay(3000)
        continue
```
note the change in indentation

also, this:
```
exec file('mypong.py')
```
is quite horrible. Why not move the game part to a function and execute that function?

---

### Post by bmanzana on 2011-01-02
first of all thanks for responding i will definitely try and put the main portion into a function and exec that function, as far as the pause feature goes if i change the indention then it waits right away and even with the addition of the continue statement it dose not recover after the wait() function has finished. also i guess i should have said it origionaly but i wanted to be able to then restart the game from where i left of at any time sith user input

---

### Post by Tony Flury on 2011-01-02
Instead of pausing by doing a delay : this is what I do in my "snake" game :


```

.... main loop

if event.type == pygame.KEYDOW and event.key == pygame.K_SPACE:
    while 1: 
        event = pygame.event.wait()
        if event.type == pygame.KEYDOWN and event.key == pygame.K_SPACE:
            break

.... main loop

```

Essentially the pause and unpause by pressing space - and while the game is paused the game does not react to any other event. The pause is also indefinite.

---

### Post by bmanzana on 2011-01-03
> **Tony Flury said:**
> Instead of pausing by doing a delay : this is what I do in my "snake" game :


```

.... main loop

if event.type == pygame.KEYDOW and event.key == pygame.K_SPACE:
    while 1: 
        event = pygame.event.wait()
        if event.type == pygame.KEYDOWN and event.key == pygame.K_SPACE:
            break

.... main loop

```

Essentially the pause and unpause by pressing space - and while the game is paused the game does not react to any other event. The pause is also indefinite.
thanx for the input i will give that a try and see how it works

---

### Post by bmanzana on 2011-01-03
again thank you for trying to help i really appreciate it. i tried that as well and it has the same effect its weird its like the comp is still computing where the ball needs to be next  and  when you un-pause the ball just apears there, so if thats off the screen thats where it goes and it then goes to game over screen or to the next level. im stumped lol

---

### Post by Crazedpsyc on 2011-01-03
I'm not familiar with pygame, but could you just add this? It is a rather hacky approach, but if it works...:
```

import time
while pause == True: time.sleep(1)

```

---

### Post by ziekfiguur on 2011-01-04
> **Crazedpsyc said:**
> I'm not familiar with pygame, but could you just add this? It is a rather hacky approach, but if it works...:
```

import time
while pause == True: time.sleep(1)

```
This wouldn't work, the program would sleep while pause is true, but during that sleep the value of pause is never going to change, so it will sleep forever.

---

### Post by Tony Flury on 2011-01-04
> **bmanzana said:**
> again thank you for trying to help i really appreciate it. i tried that as well and it has the same effect its weird its like the comp is still computing where the ball needs to be next  and  when you un-pause the ball just apears there, so if thats off the screen thats where it goes and it then goes to game over screen or to the next level. im stumped lol

Where are you doing the calculation of the next position ?
if you are doing it in the main loop - or called in a function from the main loop, then my solution stops the main loop, which means no calculation can take place.

If the calculation is taking place in another thread, then you need to ensure that you "pause" that thread too.

---

### Post by Crazedpsyc on 2011-01-04
> **ziekfiguur said:**
> This wouldn't work, the program would sleep while pause is true, but during that sleep the value of pause is never going to change, so it will sleep forever.
How about just adding a function which checks the value of pause each time through the loop (it should be as simple as "pause = [pausebutton].GetValue()", or at least it would be in wxPython ;))

---

### Post by bmanzana on 2011-01-05
i have submitted the entire code you can see it up at the top the calculation is a simple change in y value done with an if statement inside the main loop, i agree it should stop the loop until user input is supplied but application of this idea is proving otherwise, i don't really understand why. it makes perfect sense to me that it should work, but for some reason it just isn't.

---

