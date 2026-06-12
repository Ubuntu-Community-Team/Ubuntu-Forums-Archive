---
title: "pygame help sprite rotation/spites close in on player"
date: 2011-05-10
forum: Programming Talk
---

### Post by sms27 on 2011-05-10
for the following code i was attempting to have the plane move as well as rotate accordingly to the arrow keys. For the cloud sprites i wanted them to close in on or chase the user/plane sprite. plz help

```
import pygame, random
pygame.mixer.init()
pygame.init()

screen = pygame.display.set_mode((640, 480))

class Squeaker(pygame.sprite.Sprite):
         
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("balloon.gif")
        self.image.convert()
        self.rect = self.image.get_rect()
        self.rect.centerx = random.randint(0, screen.get_width())
        self.rect.centery = 0 
        self.dx = 0
        self.dy = random.randint(1, 10)
        
    def reset(self):
        self.rect.centery=0
        self.rect.centerx=random.randint(0, 640)
        self.dx = 0
        self.dy = random.randint(1, 10)
        
    def update(self):
        self.rect.centery += self.dy
        self.rect.centerx += self.dx
       
        if self.rect.top > screen.get_height():
            self.reset()
            
    

class Plane(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("plane2pi.gif")
        self.image = self.image.convert()
        self.rect = self.image.get_rect()
        self.rect.centerx = 100
        self.rect.centery = 240
        self.dx=0
        self.dy=0
        self.dying=False
        
        if not pygame.mixer:
            print "problem with sound"
        else:
            pygame.mixer.init()
            self.pop = pygame.mixer.Sound("Pop.ogg")
            self.crash = pygame.mixer.Sound("engineOff.ogg")
            self.Engine = pygame.mixer.Sound("engine.ogg")
            self.Engine.play(-1)
    def update(self):
        if not self.dying:
            self.rect.centerx+=self.dx
            self.rect.centery+=self.dy
            
  
            
    
        
    def changeUp(self,halt):
        if not self.dying:
            if halt:
                self.dy=0
            else:
                self.dy=-3

    def changeDown(self,halt):
        if not self.dying:
            if halt:
                self.dy=0
            else:
                self.dy=3

    def changeRight(self,halt):
        if not self.dying:
            if halt:
                self.dx=0
            else:
                self.dx=3
            
    def changeLeft(self,halt):
        if not self.dying:
            if halt:
                self.dx=0
            else:
                self.dx=-3

        
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
        
class Sky(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("sky4.jpg")
        self.rect = self.image.get_rect()
        self.dy = 5
        self.reset()
        
    def update(self):
        self.rect.bottom += self.dy
        if self.rect.bottom >= 1440:
            self.reset() 
    
    def reset(self):
        self.rect.top = -960
        
class Scoreboard(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.lives = 5
        self.score = 0
        self.font = pygame.font.SysFont("None", 50)
        
    def update(self):
        self.text = "planes: %d, score: %d" % (self.lives, self.score)
        self.image = self.font.render(self.text, 1, (255, 0, 0))
        self.rect = self.image.get_rect()
        
def game():
    screen = pygame.display.set_mode((640, 480))
    pygame.display.set_caption("Project 7")

    background = pygame.Surface(screen.get_size())
    background.fill((0, 0, 0))
    screen.blit(background, (0, 0))
    
    
    plane = Plane()
    cloud1 = Cloud()
    cloud2 = Cloud()
    cloud3 = Cloud()
    cloud4 = Cloud()
    squeaker = Squeaker()
    squeaker1 = Squeaker()
    squeaker2 = Squeaker()
    squeaker3 = Squeaker()
    squeaker4 = Squeaker()
    squeaker5 = Squeaker()
    sky = Sky()
    scoreboard = Scoreboard()
    
    friendSprites = pygame.sprite.Group(sky, plane)
    squeakerSprites = pygame.sprite.Group(squeaker, squeaker1, squeaker2, squeaker3, squeaker4, squeaker5)
    cloudSprites = pygame.sprite.Group(cloud1, cloud2, cloud3, cloud4)
    scoreSprite = pygame.sprite.Group(scoreboard)
    
    
    
    clock = pygame.time.Clock()
    keepGoing = True
    while keepGoing:
        clock.tick(30)
        pygame.mouse.set_visible(False)
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                keepGoing = False
            elif event.type == pygame.KEYDOWN:
                if event.key==pygame.K_UP:
                    plane.changeUp(False)
                elif event.key==pygame.K_DOWN:
                    plane.changeDown(False)
                elif event.key==pygame.K_LEFT:
                    plane.changeLeft(False)
                elif event.key==pygame.K_RIGHT:
                    plane.changeRight(False)
            elif event.type==pygame.KEYUP:
                if event.key==pygame.K_UP:
                    plane.changeUp(True)
                elif event.key==pygame.K_DOWN:
                    plane.changeDown(True)
                elif event.key==pygame.K_LEFT:
                    plane.changeLeft(True)
                elif event.key==pygame.K_RIGHT:
                    plane.changeRight(True)

        pointGain=pygame.sprite.spritecollide(plane, squeakerSprites, False)
        for squeaker in pointGain:
            plane.pop.play()
            squeaker.reset()
            scoreboard.score += 100
        #if score==500:
            #Cloud().append (cloud6)
        hitClouds = pygame.sprite.spritecollide(plane, cloudSprites, False)
        if hitClouds:
            plane.crash.play()
            scoreboard.lives -= 1
            if scoreboard.lives <= 0:
                keepGoing = False
            for theCloud in hitClouds:
                theCloud.reset()
                
        friendSprites.update()
        squeakerSprites.update()
        cloudSprites.update()
        scoreSprite.update()
        
        friendSprites.draw(screen)
        squeakerSprites.draw(screen)
        cloudSprites.draw(screen)
        scoreSprite.draw(screen)
        

        pygame.display.flip()
    
    plane.Engine.stop()
    #return mouse cursor
    pygame.mouse.set_visible(True)
     
    return scoreboard.score

def instructions(score):
    pygame.display.set_caption("Bermuda Triangle")

    plane = Plane()
    sky = Sky()
    
    allSprites = pygame.sprite.Group(sky, plane)
    insFont = pygame.font.SysFont(None, 40)
    insLabels = []
    instructions = (
    "Bermuda Triangle. Last score: %d" % score ,
    "Instructions:  You are a pilot,",
    "flying through the bermuda triangle.",
    "",
    "Fly through the balloons to gain points,",
    "but be careful not to fly too close",    
    "to the clouds. Your plane will fall ",
    "many times. Steer with the mouse.",
    "",
    "good luck!",
    "",
    
    )
    
    for line in instructions:
        tempLabel = insFont.render(line, 1, (255, 255, 0))
        insLabels.append(tempLabel)
    
    keepGoing = True
    clock = pygame.time.Clock()
    pygame.mouse.set_visible(False)
    while keepGoing:
        clock.tick(30)
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                keepGoing = False
                donePlaying = True
            if event.type == pygame.MOUSEBUTTONDOWN:
                keepGoing = False
                donePlaying = False
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_ESCAPE:
                    keepGoing = False
                    donePlaying = True
                    
   

        for i in range(len(insLabels)):
            screen.blit(insLabels[i], (50, 30*i))

        pygame.display.flip()
    plane.Engine.stop()
    pygame.mouse.set_visible(True)
    return donePlaying
        
def main():
    donePlaying = False
    score = 0
    while not donePlaying:
        donePlaying = instructions(score)
        if not donePlaying:
            score = game()


if __name__ == "__main__":
    main()
    
```

---

