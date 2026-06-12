---
title: "Spritesheet animations in Python/Pygame"
date: 2011-09-10
forum: Programming Talk
---

### Post by Neoncamouflage on 2011-09-10
I've been working with Python a lot lately and have become greatly interested in Pygame. With a lot of work I was able to make single row spritesheets work as animations. However, the vast majority of spritesheets I find come with multiple rows, and the code I found for creating animations by slicing frames won't work with them. Not just that, but these spritesheets would be infinitely more useful. Now I've seen people talking about them in old Python forums and such, so I know there's a way. Does anybody here have any idea of a function or module that would take a multi-row spritesheet and create animations?

Also, it doesn't have to be Pygame. I'd rather learn another toolkit with a good animation function than continue barely being able to make anything with motion.

---

### Post by Senesence on 2011-09-10
In OpenGL, you can just set the sprite sheet to a texture, and simulate animation by moving texture coordinates around at some set rate.

I don't really know anything about pygame, but if your function only works on a single horizontal stretch of sprites, then take your multi-row sprite sheet and copy all the sprites to a new single-row image.

Then you can just use that new image that conforms to the "one-row" requirement.

PS: If you could set up a simple pygame test-case, so that I can see how you're loading sprites - that would help me write an example for you.

---

### Post by Senesence on 2011-09-10
Ok, I downloaded pygame, and I learned a bit about it from the chimp example, to the point where I can write an example for you:

[PHP]
#!/usr/bin/env python

import os, pygame

main_dir = os.path.split(os.path.abspath(__file__))[0]

def load_image(name, colorkey=None):
    fullname = os.path.join(main_dir, name)
    try:
        image = pygame.image.load(fullname)
    except pygame.error:
        print ('Cannot load image:', fullname)
        raise SystemExit(str(geterror()))
    image = image.convert()
    if colorkey is not None:
        if colorkey is -1:
            colorkey = image.get_at((0,0))
        image.set_colorkey(colorkey, pygame.RLEACCEL)
    return image, image.get_rect()

def make_framemap():

    rect_base = pygame.Rect(30, 0, 71, 128)

    framemap = {}

    walk_left = [rect_base]
    for i in range(3):
        walk_left.append(walk_left[-1].move(127, 0))
    
    framemap["walk_left"] = walk_left

    last = "walk_left"
    for name_cycle in ("walk_right", "walk_down", "walk_up"):
        framemap[name_cycle] = map(lambda rect: rect.move(0, 128), framemap[last])
        last = name_cycle

    return framemap


class Animator:

    def __init__(self, img_spritesheet, dict_framemap):

        self.framemap = {}
        for key in dict_framemap:
            self.framemap[key] = []
            for rect in dict_framemap[key]:
                self.framemap[key].append(img_spritesheet.subsurface(rect))
        
        self.cycle = self.framemap.values()[0]
        self.frame = 0

        self.time_last = pygame.time.get_ticks()

    
    def update(self):
        change = False
        now = pygame.time.get_ticks()
        delta = now - self.time_last
        if delta > 200:
            if self.frame < len(self.cycle) - 1:
                self.frame += 1
            else:
                self.frame = 0
            self.time_last = now
            change = True

        return change



    def getCurrentImage(self):
        return self.cycle[self.frame]

    def setCycle(self, name_cycle):
        self.cycle = self.framemap[name_cycle]


class Hero(pygame.sprite.Sprite):

    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        img_spritesheet, rect_dummy = load_image('walk_cycle.png', -1)
        self.animator = Animator(img_spritesheet, make_framemap())

        self.image = self.animator.getCurrentImage()
        self.rect = self.image.get_rect()
    
    def update(self):
        change = self.animator.update()
        if change:
            self.image = self.animator.getCurrentImage()


def main():
    pygame.init()
    screen = pygame.display.set_mode((640, 480))
    pygame.display.set_caption('Test')

    background = pygame.Surface(screen.get_size())
    background = background.convert()


    screen.blit(background, (0, 0))
    pygame.display.flip()

    clock = pygame.time.Clock()
    hero = Hero()
    allsprites = pygame.sprite.RenderPlain((hero))


    #Main Loop
    going = True
    while going:
        clock.tick(30)

        #Handle Input Events
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                going = False
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_ESCAPE:
                    going = False
                elif event.key == pygame.K_LEFT:
                    hero.animator.setCycle("walk_left")
                elif event.key == pygame.K_RIGHT:
                    hero.animator.setCycle("walk_right")
                elif event.key == pygame.K_DOWN:
                    hero.animator.setCycle("walk_down")
                elif event.key == pygame.K_UP:
                    hero.animator.setCycle("walk_up")


        allsprites.update()

        #Draw Everything
        screen.blit(background, (0, 0))
        allsprites.draw(screen)
        pygame.display.flip()

    pygame.quit()



if __name__ == '__main__':
    main()
[/PHP]

The sprite sheet that I'm using in this example is attached.

I'm just loading in the whole sprite sheet as a single image, and then I'm creating "subsurfaces", which are just like regular surfaces, but a lot less expensive, since they just reference the pixels on the same master image.

These subsurfaces are then used as frames which are set to the current image on the Hero sprite, at appropriate times - I'm doing it every 200 milliseconds, you can try something else if you want.

There are a few other nifty concepts here, relating to how the Animator class works, and how the make_framemap function creates the initial dictionary that's used as a "cycle" table to make sequence setting more natural, but creating subsurfaces from one master surface is the essential operation.

If there is anything you don't understand, feel free to ask.

---

### Post by Neoncamouflage on 2011-09-11
Did you run the code yourself? Not working for me. I understand the concept of it though. I keep getting this:
```
  File "/home/chris/bin/python_scripts/PyTest5", line 146, in <module>
    main()  
  File "/home/chris/bin/python_scripts/PyTest5", line 108, in main
    hero = Hero() 
  File "/home/chris/bin/python_scripts/PyTest5", line 83, in __init__
    img_spritesheet, rect_dummy = load_image('walk_cycle.png', -1) 
  File "/home/chris/bin/python_scripts/PyTest5", line 13, in load_image
    image = image.convert() 
UnboundLocalError: local variable 'image' referenced before assignment

```

---

### Post by Senesence on 2011-09-11
If you look at load_image, you'll notice that it tries to find "walk_cycle.png" in the same directory where your script resides (*Sorry; I should have made that clear in my last post*).

Make sure that the sprite sheet is named "walk_cycle.png", and make sure that it's in the same directory. Then just run "python name_of_script.py" (that runs python 2.7 on my machine).

There is a slight error in the script: "geterror()" should be "pygame.compat.geterror()", but that shouldn't matter if you have the image in the same directory, because that code should never run in that case.

---

### Post by Neoncamouflage on 2011-09-11
Ah, right. My image function grabs it out of a 'data' directory inside the main one, I'm not at all sure why I expected yours to do the same. :P

Will try it again later tonight, thanks for the help mate.

---

### Post by Neoncamouflage on 2011-09-11
```
  File "/home/chris/bin/python_scripts/PyTest5", line 146, in <module>
    main()  
  File "/home/chris/bin/python_scripts/PyTest5", line 108, in main
    hero = Hero() 
  File "/home/chris/bin/python_scripts/PyTest5", line 84, in __init__
    self.animator = Animator(img_spritesheet, make_framemap()) 
  File "/home/chris/bin/python_scripts/PyTest5", line 48, in __init__
    self.framemap[key].append(img_spritesheet.subsurface(rect)) 
ValueError: subsurface rectangle outside surface area

```

Nope. I'll work on it, see if I can fix it.

---

### Post by Senesence on 2011-09-12
This is what I expected you to do:

[LIST=1]
[*]Copy-paste my code to a file named spritetest.py
[*]Download the sprite-sheet (previously attached - 512x512 png image called "walk_cycle.png") to the same directory.
[*]Run "python spritetest.py"
[/LIST]

Is that what you're doing?

---

