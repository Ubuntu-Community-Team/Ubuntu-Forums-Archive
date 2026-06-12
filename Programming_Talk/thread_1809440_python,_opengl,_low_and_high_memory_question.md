---
title: "python, opengl, low and high memory question"
date: 2011-07-21
forum: Programming Talk
---

### Post by oedipuss on 2011-07-21
I've read that low memory is memory the kernel can access directly, usually about 896mb and the rest is high memory. 

I have the following test script :
```

SCREEN_SIZE = (800, 600)

from OpenGL.GL import *
from OpenGL.GLU import *

import pygame
from pygame.locals import *

def resize(width, height):
    
    glViewport(0, 0, width, height)
    glMatrixMode(GL_PROJECTION)
    glLoadIdentity()
    gluOrtho2D(-10,10,-10,10)
    glMatrixMode(GL_MODELVIEW)
    glLoadIdentity()


def init():
    
    glClearColor(1.0, 1.0, 1.0, 0.0)
    glEnable(GL_TEXTURE_2D)

def CreateTexture(width, height):
    texture = glGenTextures( 1 )
    glBindTexture( GL_TEXTURE_2D, texture )

    glTexImage2D( GL_TEXTURE_2D, 0, GL_RGBA,\
                  width, height, 0,\
                  GL_RGBA, GL_UNSIGNED_BYTE, None )

    glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR )
    glTexParameteri( GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR ) 

    glBindTexture( GL_TEXTURE_2D, 0 )

    return texture

def DrawTextures(textures):
    for tex in textures:
        glBindTexture(GL_TEXTURE_2D,tex)
        glBegin(GL_QUADS)
        glVertex2f(-5,-5)
        glVertex2f(-5,5)
        glVertex2f(5,5)
        glVertex2f(5,-5)
        glEnd()
        

def run():
    
    pygame.init()
    screen = pygame.display.set_mode(SCREEN_SIZE, HWSURFACE|OPENGL|DOUBLEBUF)
    
    resize(*SCREEN_SIZE)
    init()

    cont = 'y'
    textures = []

    while cont in ['y','Y']:

# The following line creates the texture. After 3 or 4 loops my system freezes.
# Uncomment to check memory, but be prepared :P

#        tex=CreateTexture(8192,8192) 
            #max texture size for my gpu

        textures.append(tex)
        DrawTextures(textures) #draws nothing, just to pretend to actually use
                               #the textures
        cont=raw_input("Continue? [y] :")


    glDeleteTextures(tex)
    pygame.display.flip()

run()

```
( the commented line prevents it from doing anything, just to be safe with the forum TOS, as it can freeze up my system easily)

 All it does is create large blank textures and draw them, just to check system memory consumption. I can see that there's a local copy of each texture in system memory, because it goes down after each repetition. The problem is it all goes only in low memory.
 What's worse, after all the low memory is gone,(but with enough system memory still left, and practically the entire swap) either oom-killer is activated, or the system hangs completely.
 What I'd expect instead is for all available memory to be used (+swap) even if it slowed the system down, before the oom-killer pops up or anything, and for the textures to be swapped back and forth between gpu mem and system mem.

I have 2gb ram, about 730mb of low memory free after boot, about 250 mb high mem free, 1gb swap, the gpu has 512 mb, and I'm using the nvidia binary driver. Oh and I'm checking free mem with /proc/meminfo

Basically what I want to ask is what's happening exactly? Is opengl supposed to only use those 896mb for textures with the nvidia driver? That seems kind of unlikely... 

Also googling for permutations of 'opengl' 'linux' and 'low memory' or 'lowmem' gives completely irrelevant results, so even search term suggestions would be welcome.

---

### Post by Zugzwang on 2011-07-22
> **oedipuss said:**
> I have 2gb ram, about 730mb of low memory free after boot, about 250 mb high mem free, 1gb swap, the gpu has 512 mb, and I'm using the nvidia binary driver. Oh and I'm checking free mem with /proc/meminfo


I've never heard of something like "low" and "high" memory in the Linux context. In good old DOS times, when the processor was running in the so-called "real mode", there was indeed this distinction. Note however that "low+high memory" doesn't add up to the 2GB of RAM in your list. Perhaps you actually only have 1GB of RAM, as I don't think that all the Linux stuff together add up to 1GB. And then, as textures really can't go into the swap memory, you run out of memory "naturally".

---

### Post by oedipuss on 2011-07-22
I haven't heard of it either, until recently. But yes, I do have 2gb ram and the linux stuff actually did take about 1gb ram at that time, including buffers. I expect the free high mem value above is actually much higher, but I haven't found a way to see it. 'free -l' only shows a buffer adjusted sum of high and low mem, not for each individually.
Even if texture copies can't go to swap, I would think other stuff would get pushed to swap to make room. 
The most unexpected thing is actually that the out of memory killer is activated with a certain amount of free mem still left, more than what it would need for one more big texture in the example. Without warning, as it were.

---

