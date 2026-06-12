---
title: "Pygame game -- help!"
date: 2010-01-18
forum: Programming Talk
---

### Post by DanielJackins on 2010-01-18
Hello,

I'm just starting to play around with pygame. Right now I'm trying to get it so I can click and drag around a ball on the screen; here is what I've got so far:

```

import pygame, sys, os, random, time
from pygame.locals import *

pygame.init()

w = 640
h = 480

window = pygame.display.set_mode((w,h))
screen = pygame.display.get_surface()

class Ball():
    def __init__(self):
        self.x_position = w/2
        self.y_position = h/2
        self.color = (random.randint(0,255),random.randint 
                      (0,255),random.randint(0,255))
        self.radius = 10
        
ball = Ball()        
pygame.draw.circle(screen, ball.color, (ball.x_position,ball.y_position), ball.radius)
pygame.display.flip()

while True:
    for event in pygame.event.get():
        if event.type == MOUSEBUTTONDOWN:
            position = pygame.mouse.get_pos()
            if position[0] >= ball.x_position-ball.radius and position[0] <= ball.x_position+ball.radius and position[1] >= ball.y_position-ball.radius and position[1] <= ball.y_position+ball.radius:
                    while event.type == MOUSEBUTTONDOWN:
                        ball_position = pygame.mouse.get_pos()
                        ball.x_position = ball_position[0]
                        ball.y_position = ball_position[1]
                        pygame.draw.circle(screen, ball.color, (ball.x_position,ball.y_position), ball.radius)
                        pygame.display.flip()

```

For some reason, it only draws one new ball and then freezes up. Anyone know why?

Also, how do I go about erasing the original ball?

Thanks a lot!

---

### Post by OgreProgrammer on 2010-01-18
When you draw something it draws it off screen and then flips it on. The suggestion is that flip erases... but it doesnt. Draw a black square that is the same size as the last circle location. Do it before you draw the new circle.

---

### Post by DanielJackins on 2010-01-18
Okay so now that works, but it still freezes up after I click it the first time

---

### Post by DanielJackins on 2010-01-19
Update - 

So I changed the while loop to an if, and now I can move the ball around, but I have to click repeatedly rather than drag.

---

### Post by Senesence on 2010-01-19
I'm not a big fan of PyGame. 

I mean, for something that's using Python, it makes you do a whole lot of manual labor just to create some basic facilities. If you're using Flash, and programming graphics in AS3, things like "blitting", and "dirty rects" are not something you have to concern yourself with. Also, there are common functions for things like drag and drop, 2D effects, and other useful things.

Luckily, the Flex SDK is now open source: [http://www.adobe.com/cfusion/entitlement/index.cfm?e=flex3sdk](http://www.adobe.com/cfusion/entitlement/index.cfm?e=flex3sdk)

So you might give that a try (and as a bonus, you could actually publish your games on the web).

As for your pygame problems, this should do what you want:
[PHP]
import pygame, random, math
from pygame.locals import *

pygame.init()

w = 640
h = 480

window = pygame.display.set_mode((w,h))
screen = pygame.display.get_surface()

background = pygame.Surface(screen.get_size())
background = background.convert()
background.fill((0,0,0))

clock = pygame.time.Clock()

class Ball():
    def __init__(self):
        self.x_position = w/2
        self.y_position = h/2
        self.color = (random.randint(0,255),random.randint 
                      (0,255),random.randint(0,255))
        self.radius = 10

        self.dragged = False
        self.dragoffset = []
   
    def getDistanceTo(self, point):
        dx = point[0] - self.x_position
        dy = point[1] - self.y_position
        return math.sqrt(dx**2 + dy**2)

    def mouseOver(self): 
        mpos = pygame.mouse.get_pos()
        if self.getDistanceTo(mpos) < self.radius:
            return True
        else:
            return False

    def drag(self):
        mpos = pygame.mouse.get_pos()
        self.x_position = mpos[0]
        self.y_position = mpos[1]

    def draw(self):
        screen.blit(background, (0,0))
        pygame.draw.circle(screen, self.color, (self.x_position,self.y_position), self.radius)
        pygame.display.flip()

ball = Ball()        
pygame.draw.circle(screen, ball.color, (ball.x_position,ball.y_position), ball.radius)
pygame.display.flip()

running = True
while running:
    for event in pygame.event.get():
        if event.type == QUIT:
            running = False
        elif event.type == MOUSEBUTTONDOWN and ball.mouseOver():
            ball.dragged = True
        elif event.type == MOUSEBUTTONUP:
            ball.dragged = False
    if ball.dragged:
        ball.draw()
        ball.drag()
    clock.tick(60) # Frame rate
[/PHP]

Mind you, this is still very bad code, because I'm just clearing everything out by repainting the screen black, and then redrawing everything.

If you plan to use pygame, I recommend you learn how to use their their Sprite class, because that's what pygame was design to work best with.

PS: If you're interested in making 3D games with Python, there is a piece of software (open source) called Blender 3D, and it comes with an internal game engine which allows you to write python scripts for your 3D models, and then control them with a push of a button.

More information here: [http://en.wikipedia.org/wiki/Game_Blender](http://en.wikipedia.org/wiki/Game_Blender)

Download blender from: [http://www.blender.org/](http://www.blender.org/)

---

### Post by DanielJackins on 2010-01-20
Thanks for all the info! Maybe I will check out the flex thing, so it's just Flash? With some other stuff?

Also - I've changed my code around:

```

import pygame, sys, os, random, time
from pygame.locals import *

pygame.init()

w = 640
h = 480
lives = 3

window = pygame.display.set_mode((w,h))
screen = pygame.display.get_surface()
background = pygame.Surface(screen.get_size())
background = background.convert()

class Ball:
    def __init__(self):
        self.x_position = random.randint(50,590)
        self.y_position = random.randint(50,430)
        self.color = (random.randint(50,255),random.randint 
                      (50,255),random.randint(50,255))
        self.radius = 25
        self.x_velocity = random.randint(-50,50)/100.0
        self.y_velocity = random.randint(-50,50)/100.0
    def update(self):
        self.x_position += self.x_velocity
        self.y_position += self.y_velocity

ball = Ball()
pygame.draw.circle(screen, ball.color, (ball.x_position,ball.y_position), ball.radius)
pygame.display.flip()
score = 0
running = True

while lives > 0 and running:

    if pygame.font:
        font = pygame.font.Font(None, 36)
        text = font.render("Score: " + str(score) + "   Lives: " + str(lives), 1, (255, 255, 255))
        textpos = text.get_rect()
        textpos.centerx = background.get_rect().centerx
        background.blit(text, textpos)
        pygame.display.flip()
        screen.blit(background, (0, 0))
        pygame.draw.rect(background, (0,0,0), (0,0,640,30))
    for event in pygame.event.get():
        if event.type == QUIT:
            running = False
        if event.type == MOUSEBUTTONDOWN:
            position = pygame.mouse.get_pos()
            if position[0] >= ball.x_position-ball.radius and position[0] <= ball.x_position+ball.radius and position[1] >= ball.y_position-ball.radius and position[1] <= ball.y_position+ball.radius:
                pygame.draw.circle(screen, (0,0,0), (int(ball.x_position),int(ball.y_position)), ball.radius)
                pygame.display.flip()
                score += 1
                ball = Ball()
    pygame.draw.circle(screen, (0,0,0), (int(ball.x_position),int(ball.y_position)), ball.radius)            
    Ball.update(ball)
    pygame.draw.circle(screen, ball.color, (int(ball.x_position),int(ball.y_position)), ball.radius)  
    if ball.y_position + ball.radius <= 50 or ball.y_position + ball.radius >= h:   #Makes the ball bounce off walls
        lives -= 1
        pygame.draw.circle(screen, (0,0,0), (int(ball.x_position),int(ball.y_position)), ball.radius)
        pygame.display.flip()
        ball = Ball()       
    if ball.x_position + ball.radius <= 50 or ball.x_position + ball.radius >= w:   #Makes the ball bounce off walls
        lives -= 1    
        pygame.draw.circle(screen, (0,0,0), (int(ball.x_position),int(ball.y_position)), ball.radius)
        pygame.display.flip()
        ball = Ball()                     

```

It's doing everything I want it to, but I want it to create an extra ball once a certain score is reached. How would I do that without changing all my code? It all depends on the object being named ball and the original ball is already occupying that name. Suggestions?

And any other code-critique would be greatly appreciated :D don't go easy!

---

### Post by OgreProgrammer on 2010-01-20
Simply make ball into a list of balls.

---

### Post by Senesence on 2010-01-20
> **DanielJackins said:**
> Thanks for all the info! Maybe I will check out the flex thing, so it's just Flash? With some other stuff?

No, it's the develpment tools (compiler, debuger, build files, some examples, etc) that allow you to make your own Flash applications (.swf files).

The programming language is ActionScript 3.0, so if you want to program flash games that's the language you'll have to learn.

> Also - I've changed my code around.

*snip*

It's doing everything I want it to, but I want it to create an extra ball once a certain score is reached. How would I do that without changing all my code? It all depends on the object being named ball and the original ball is already occupying that name. Suggestions?

And any other code-critique would be greatly appreciated :D don't go easy!

Well, the most glaring problem with your code is the lack of helpful encapsulation: you don't seem to be using any additional functions/classes to encapsulate the details of moving and drawing your object.

In addition, you "hard-coded" all the functionality for a single ball object, rather than making things generic, where you could apply the same functions to multiple objects by iterating over a common list.

Lastly, and this is no less important than anything listed above, you are not subclassing the pygame.sprite.Sprite class, which should by itself provide you with a system to update and redraw your game objects, without having to do so explicitly -> that's what you should do, because that's what PyGame was designed for.

In short, you shouldn't be looking for a way to avoid rewriting your program, because it *needs* to be re-written.

This is one way to do it:

[PHP]
#Import Modules
import sys, pygame, math, random
from pygame.locals import *

window_width = 640
window_height = 480

class Ball(pygame.sprite.Sprite):
    """Ball class"""
    def __init__(self, score_board):
        pygame.sprite.Sprite.__init__(self) #call Sprite intializer

        # Keep reference to score_board
        self.score_board = score_board
        
        # Create the surface for the ball, and draw to that surface:
        self.radius = 20
        self.image = pygame.Surface((self.radius*2, self.radius*2))
        self.image = self.image.convert_alpha()
        self.image.fill((0,0,0,0));
        pygame.draw.circle(self.image, (255,0,0,255), (self.radius, self.radius), self.radius)
        self.rect = self.image.get_rect()
        
        # Set initial position
        self.position = [random.randint(50,590), random.randint(50,430)] 
        self.rect = self.rect.move(tuple(self.position))
        
        # Set initial velocity
        range = 2
        self.velocity = (random.randint(-range,range), random.randint(-range,range)) 
        #self.velocity = (0,0)

    def offScreen(self):
        off_right_left = self.position[0] < 0 or self.position[0] > window_width
        off_up_down = self.position[1] < 0 or self.position[1] > window_height
        if off_right_left or off_up_down:
            return True
        else:
            return False

    def update(self):
        # allsprites.update() runs this function
        # allsprites.draw() will blit the self.image surface to the screen
        self.position[0] += self.velocity[0]
        self.position[1] += self.velocity[1]
        if self.offScreen():
            self.score_board.lives -= 1
            if self.score_board.lives < 1:
                sys.exit()
            self.kill()
        else:
            self.rect = self.rect.move(self.velocity) 


    def getDistanceTo(self, point):
        dx = point[0] - (self.position[0] + self.radius)
        dy = point[1] - (self.position[1] + self.radius)
        return math.sqrt(dx**2 + dy**2) 

    def mouseOver(self): 
        mpos = pygame.mouse.get_pos()
        if self.getDistanceTo(mpos) < self.radius:
            return True
        else:
            return False     

        
class ScoreBoard(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        
        self.score = 0
        self.old_score = 0
        
        self.lives = 5
        self.old_lives = 0

        self.font = pygame.font.Font(None, 36)
        self.image = self.font.render("Score: "+str(self.score)+"  "+"Lives: "+str(self.lives), 1, (255, 255, 255))
        self.rect = self.image.get_rect()

    def update(self):
        update_score = self.score != self.old_score
        update_lives = self.lives != self.old_lives

        if update_score or update_lives:
            self.image = self.font.render("Score: "+str(self.score)+"  "+"Lives: "+str(self.lives), 1, (255, 255, 255))
            self.rect = self.image.get_rect()



def main():
    """this function is called when the program starts.
       it initializes everything it needs, then runs in
       a loop until the function returns."""
#Initialize Everything
    pygame.init()
    screen = pygame.display.set_mode((window_width, window_height))
    pygame.display.set_caption('Test Game')

#Create The Backgound
    background = pygame.Surface(screen.get_size())
    background = background.convert()
    background.fill((0, 0, 0))

#Create the Score Board
    score_board = ScoreBoard()

#Display The Background
    screen.blit(background, (0, 0))
    pygame.display.flip()

#Clock and object list
    clock = pygame.time.Clock()
    allsprites = pygame.sprite.RenderPlain()
    allsprites.add(score_board)

    ball_count = 2

#Main Loop
    while 1:
        clock.tick(60)  #  SAVES CPU!

    #Handle Input Events
        for event in pygame.event.get():
            if event.type == QUIT:
                return
            elif event.type == MOUSEBUTTONDOWN:
                for sprite in allsprites:
                    try:
                        if sprite.mouseOver():
                            sprite.kill()
                            score_board.score += 1
                            break
                    except:
                        pass


        if len(allsprites) < 2:
            for i in range(ball_count):
                allsprites.add(Ball(score_board))

        allsprites.update()

    #Draw Everything
        screen.blit(background, (0, 0))
        allsprites.draw(screen)
        pygame.display.flip()

#Game Over


#this calls the 'main' function when this script is executed
if __name__ == '__main__': main()
[/PHP]

Notice how short and understandable the main loop is in my code, relative to your code. It's more code, but it's more understandable, and it's something that can be built upon without rewriting everything from scratch.

That's what you should aim for.

PS: Oh, and don't forget to look at the official chimp example ([http://www.pygame.org/docs/tut/chimp/ChimpLineByLine.html](http://www.pygame.org/docs/tut/chimp/ChimpLineByLine.html)), that's what I used as a base for my program.

---

### Post by DanielJackins on 2010-01-21
> No, it's the develpment tools (compiler, debuger, build files, some examples, etc) that allow you to make your own Flash applications (.swf files).

The programming language is ActionScript 3.0, so if you want to program flash games that's the language you'll have to learn.


And it's all 100% free?

I asked my brother's opinion on it (he is more programming-apt than me) and while he's never used it, he seemed skeptical -

> an open source framework used to create flash applications? there are so many things wrong with this. they call it open source but you need to pay for the editor, and I'm sure you need either that or the flash software to actually export into flash files...

the less flash on the internet the better, in my opinion. The only time I find it appropriate is for browser games. This software looks like its designed for exactly the kind of thing I hate, those shitty flash webpages that eat up all my cpu and break the back button on the browser

... you can tell I'm not the biggest fan of adobe these days...

I should say that I don't think their whole adobe air thing doesn't seem like a bad idea, at least for little games. I don't really see it taking off though, I mean why buy into some development environment when there are so many good free ones? and your customers need the right software to even run your application. 


As for the pygame, thanks for all the information! I'm still not very comfortable with OOP and I don't fully understand your code, but I will try to pick it apart and make sense of it all :)

Thanks a lot for the very informative posts :)

---

### Post by Senesence on 2010-01-21
> **DanielJackins said:**
> And it's all 100% free?

I asked my brother's opinion on it (he is more programming-apt than me) and while he's never used it, he seemed skeptical

Heh, your brother sounds like an interesting guy, but I think his information is a little outdated (or maybe he just assumes the worst whenever Flash is mentioned).

The Flex SDK is %100 free, as far as I know. There are additional development tools (IDE's, or just plug-ins for eclipse) that you could buy, but it's not mandatory, and you don't need them to compile ActionScript 3.0 code into .swf files.

As for publishing to the web: the .swf file *is* the flash application, so the only thing you need to do is put the .swf on the webserver, and write some fairly trivial embed code to make it available on an HTML page. Or, if you want to play your game locally, just open the .swf file with firefox, or you can even use the nice standalone player that comes with the SDK.

Now, this is not to say that Flash and AS3 don't have their flaws, but when it comes to 2D game development, it's a much better environment than something like PyGame (in my opinion).

---

