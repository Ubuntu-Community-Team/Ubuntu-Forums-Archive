---
title: "Pygame error"
date: 2007-09-02
forum: Programming Talk
---

### Post by yuvlevental on 2007-09-02
Today, I started experimenting with PyGame. I checked out the [Pygame intro]("http://www.pygame.org/docs/tut/intro/intro.html"). When I ran the program with an appropriate ball image in the same directory, i got 

```

  File "/home/user/Desktop/game1.py", line 7, in <module>
    ball = pygame.image.load("ball.gif")
pygame.error: Couldn't open ball.gif

```

I experimented and found out that I need to change ball = pygame.image.load("ball.gif") to ball = pygame.image.load("/home/user/Desktop/ball.gif").

The problem is, when I distribute future programs to the public, I don't want them to cause the trouble to enter in the full directory.

Is there a good solution to this problem?

Thanks,
Yuvlevental

---

### Post by Wybiral on 2007-09-02
Have you tried "./ball.gif" ?

---

### Post by yuvlevental on 2007-09-02
Thanks, but still doesn't work

---

### Post by Wybiral on 2007-09-02
I've loaded images in PyGame using "pygame.image.load(some_image)" without the entire path... Could you post the entire code?

---

### Post by yuvlevental on 2007-09-02
Here it is:

```

import sys, pygame
pygame.init()
size = width, height = 320, 240
speed = [2, 2]
black = 0, 0, 0
screen = pygame.display.set_mode(size)
ball = pygame.image.load("ball.jpg")
ballrect = ball.get_rect()
while 1:
	for event in pygame.event.get():
		if event.type == pygame.QUIT: sys.exit()
	        ballrect = ballrect.move(speed)
        	if ballrect.left < 0 or ballrect.right > width:
                        speed[0] = -speed[0]
                if ballrect.top < 0 or ballrect.bottom > height:
                        speed[1] = -speed[1]
screen.fill(black)
screen.blit(ball, ballrect)
pygame.display.flip()

```

---

### Post by Wybiral on 2007-09-02
You realize that the indentation is mixed and that you're loading ".jpg" instead of ".gif"?

---

### Post by yuvlevental on 2007-09-02
I fixed the errors, but no luck. This isn't my work btw, I got it from one of the Pygame tutorials [http://www.pygame.org/docs/tut/intro/intro.html]("http://www.pygame.org/docs/tut/intro/intro.html"). I just changed the bmp to jpg

---

### Post by Wybiral on 2007-09-02
I gimped up a simple 64x64 gif and saved it in the same directory as this code:

```

import sys, pygame
pygame.init()
size = width, height = 320, 240
speed = [2, 2]
black = 0, 0, 0
screen = pygame.display.set_mode(size)
ball = pygame.image.load("ball.gif")
ballrect = ball.get_rect()
while 1:
    for event in pygame.event.get():
    	if event.type == pygame.QUIT:
            sys.exit()
    	ballrect = ballrect.move(speed)
        if ballrect.left < 0 or ballrect.right > width:
            speed[0] = -speed[0]
        if ballrect.top < 0 or ballrect.bottom > height:
            speed[1] = -speed[1]
        screen.fill(black)
        screen.blit(ball, ballrect)
        pygame.display.flip()

```

And all worked fine.

---

### Post by yuvlevental on 2007-09-02
I copied the code, created an image in the GIMP, placed them both on the desktop, and it still didn't work. It seems other pygame users have the same problem such as[ here]("http://www.learningpython.com/2006/03/19/creating-a-game-in-python-using-pygame-part-two-creating-a-level/").

---

### Post by yuvlevental on 2007-09-02
Oh yeah, it said that for compatibility on the official reference [here]("http://pygame.org/docs/ref/image.html#pygame.image.load"), > 
You should use os.path.join() for compatibility.


Even that doesn't work.

---

### Post by yuvlevental on 2007-09-02
The file and the image were both on my desktop. I accessed the file by typing in "python" then dragging the file into the terminal. This apparently wasn't a good idea.

Typing in "cd ~/Desktop, then typing in "python game.py" worked. However, this leaves me with one question: is there anyway do define the full path for the image on any system so when the program is run like how I did originally, it will work. Does anyone know how to do this?

Thanks,
yuvlevental

---

### Post by pmasiar on 2007-09-02
Maybe you want relative path - from current working directory, where you python program lives?

---

### Post by nanotube on 2007-09-02
well, if you want to load the file from the same directory where the script is located, you'd have to detect where the script is, because otherwise, depending on where you start the script from, the working directory will change. one way to do it would be 
```

import os.path
import sys
print os.path.normpath(os.path.join(sys.path[0], sys.argv[0]))
```
that will give you the full path to where the script is located. sys.path[0] alone will give you the directory without the scriptname.

---

