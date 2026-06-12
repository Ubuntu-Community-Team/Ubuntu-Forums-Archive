---
title: "Pygame .bmp problem"
date: 2013-11-05
forum: Programming Talk
---

### Post by mhaggard25 on 2013-11-05
I am learning python 3 and pygame, and I have a problem with one of my computers. I am trying to load in some images in pygame, but for some reason I can only load in windows bitmap files (.bmp). The computer is running Ubuntu 13.04 (idk if that matters or not).  My Python version is 3.3.1 and Pygame version is 1.9.2. I have this exact same setup on my laptop (which is quite a bit newer and runs Linux Mint 15) and it has no problems at all with the file types of the images... Any help is appreciated. Thank you in advance.

Here is my code:
```

import pygame, sys
from pygame.locals import *

pygame.init()

bif = "background.bmp"          # anytime working with alot of colors, make it a .jpg
mif = "baseball.png"          # anytime working with tansparency, make it a .png

screen = pygame.display.set_mode((800, 400), 0, 32)

background = pygame.image.load(bif).convert()
mouse_c = pygame.image.load(mif).convert_alpha()

while True:
    for event in pygame.event.get():
        if event.type == QUIT:
            sys.exit()
    screen.blit(background, (0, 0))

    x, y = pygame.mouse.get_pos()
    
    x -= mouse_c.get_width()/2
    y -= mouse_c.get_height()/2
    
    screen.blit(mouse_c, (x, y))
    
    pygame.display.update()

```

Here is the error I get:
```

mouse_c = pygame.image.load(mif).convert_alpha()
pygame.error: File is not a Windows BMP file

```

---

### Post by ofnuts on 2013-11-05
Your code loads a PNG properly on Ubuntu 12.10, but I have no pygame module for Python v3 and had to run with Python  v2.

---

### Post by mhaggard25 on 2013-11-05
> Your code loads a PNG properly on Ubuntu 12.10, but I have no pygame module for Python v3 and had to run with Python  v2.

Well, I tried that and it worked just fine... Thanks for your input ofnuts. Is there anyway to get this to work with python v3? AND I was wrong about this working on my other computer, tried it again last night, and I was having the same problem, so my apologies.

---

### Post by ofnuts on 2013-11-05
According to the FAQ ([http://www.pygame.org/wiki/FrequentlyAskedQuestions](http://www.pygame.org/wiki/FrequentlyAskedQuestions)) Python3 is supported with Pygame 1.9.2. The pygame on my Kubuntu 12.10 is 1.9.1. But on the site[ I ]("http://www.pygame.org")cannot find any 1.9.2 version for Linux, even in source form.

This could be useful: [http://askubuntu.com/questions/97717/how-can-i-get-pygame-for-python3](http://askubuntu.com/questions/97717/how-can-i-get-pygame-for-python3)

---

