---
title: "pyopengl problem (surface blitted black when white)"
date: 2010-06-26
forum: Programming Talk
---

### Post by matmatmat on 2010-06-26
Hi, I've been trying to make a game with python & opengl, I am currently trying to make a menu which will select which game you want to play, it will have an image. This is my class for a menu item:
```

import pygame
from lib.openglframework.surface import Surface

font_title = pygame.font.SysFont("arial", 40)
font_description = pygame.font.SysFont("arial", 30)
offset = 20
    
class Game(object):
    def __init__(self, cls, name, description, image):
        self.cls = cls
        self.x = 0
        self.y = 0
        self.xspeed = 0
        self.yspeed = 0
        try:
            self.image = pygame.image.load(image)
        except:
            self.image = pygame.Surface((0,0))
            
        self.name = font_title.render(name, True, (0,0,0))
        self.description = []
        for line in description:
            self.description.append(font_description.render(line, True, (0,0,0)))

        largest_size = offset + self.name.get_height() + offset 
        largest_size += (self.description[0].get_height() + offset/4) * len(description) 
        largest_size += offset
        largest_height = offset+self.image.get_height()
        self.surface = pygame.Surface((400, max(largest_size, largest_height)))
        self.surface.fill((255,255,255))
        self.surface.blit(self.image, (offset, offset))
        self.surface.blit(self.name, (offset+self.image.get_width(), offset))
        y = self.name.get_height()+offset
        for description in self.description:
            self.surface.blit(description, (offset+self.image.get_width(), y))
            y += offset / 2
        
        self.surface_opengl = Surface(self.x, self.y, self.surface.convert())
        
    def set_x_y((x,y)):
        self.x = x
        self.y = y
        self.surface_opengl.x = x
        self.surface_opengl.y = y
        
    def draw(self):
        self.surface_opengl.draw()

```
the constructor takes in a cls variable, which holds the class of the game (so when it is selected I will be able to do)
```

cls = selected_game.cls()
cls.run()

```
it also takes in name and a description -- the description is a list one line of the description for each list item. It also takes the filename of a screenshot.

Here is the Surface class:
```

import pygame

from OpenGL.GL import *
from OpenGL.GLU import *

from misc import *

class Surface(object):
    """
    Surface class -- displays a 2d surface with OpenGL
    """
    def __init__(self, x, y, surface, z=0, clip=None):
        self.x = x
        self.y = y
        image = surface
        self.width = self.height = 0
        if clip == None:
            self.width, self.height = image.get_rect().size
        else:
            self.width = clip[0]
            self.height = clip[1]
        self.widthp2 = next_power_of_2(self.width)
        self.heightp2 = next_power_of_2(self.height)
        self.backimage = pygame.Surface((self.widthp2, self.heightp2))
        self.backimage.blit(image, (0,0))
        self.blit()
        self.widthfrac = int(float(self.width)/self.widthp2)
        self.heightfrac = int(float(self.height)/self.heightp2)
        self.z = z
        self.surface = self.backimage
      
    def blit(self, surface=None, x=None, y=None):  
        if surface != None and x != None and y != None:
            self.backimage.blit(surface, (x,y))
        texture_data = pygame.image.tostring(self.backimage, 'RGBA', True)
        self.__texture_id = glGenTextures(1)
        glBindTexture(GL_TEXTURE_2D, self.__texture_id)
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR )
        glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR )     
        glPixelStorei(GL_UNPACK_ALIGNMENT, 1)
        
        glTexImage2D( GL_TEXTURE_2D,
                      0,
                      4,
                      self.widthp2,
                      self.heightp2,
                      0,
                      GL_RGBA,
                      GL_UNSIGNED_BYTE,
                      texture_data) 
                              
    def rotate(self, degrees, x, y, z):
        glBindTexture(GL_TEXTURE_2D, self.__texture_id)
        glRotate(degrees, x, y, z)
        
    def scale(self, x, y, z):
        glBindTexture(GL_TEXTURE_2D, self.__texture_id)
        glScalef(x,y,z)
        
    def draw(self):       
        glBindTexture(GL_TEXTURE_2D, self.__texture_id)
        
        glBegin(GL_QUADS)
        glColor(1,1,1,0)
        glTexCoord2f(0, 1-self.heightfrac)
        glVertex3f(self.x-self.width/2, self.y-self.height/2, self.z)

        glTexCoord2f(self.widthfrac, 1-self.heightfrac)
        glVertex3f(self.x+self.width/2, self.y-self.height/2, self.z)

        glTexCoord2f(self.widthfrac, 1)
        glVertex3f(self.x+self.width/2, self.y+self.height/2, self.z)

        glTexCoord2f(0, 1)
        glVertex3f(self.x-self.width/2, self.y+self.height/2, self.z)

        glEnd()        
        
    def __del__(self):
        glDeleteTextures(self.__texture_id)

```

When I run this, event though I have filled the menu item's surface white, it appears black. The text (which is black) should fit the box. Does anyone know why this is happening?

---

