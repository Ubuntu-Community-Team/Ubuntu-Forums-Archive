---
title: "Frets On Fire Error"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by JordanII on 2008-11-10
I installed Frets on Fire using the command "sudo apt-get install fretsonfire" (in 8.10 Intrepid Ibex) and everything seemed to go fine until I tried to run it... I then got this error:

```
Traceback (most recent call last):
  File "./FretsOnFire.py", line 68, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/game/Video.py", line 69, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: Couldn't find matching GLX visual

```

I think I have 128MB Integrated Intel graphics if that has anything to do with it...

Any ideas? Thanks!

---

### Post by Arlo012 on 2008-11-10
I'm not sure whether or not this might have anything to do with it, but the Frets on Fire package in the repositories has been broken for awhile now. I installed it months ago and it was completely unplayable. Perhaps since it has not be updated recently there are some compatability issues with 8.10?

Assuming that is not the problem, are your video drivers properly installed? Maybe someone else can shed some light on what exactly that error means because I am not knowledgeable enough to know for certain, but it seems to be relating to the configuration file or the video. Anyone else have a better idea of what exactly that error means?

---

