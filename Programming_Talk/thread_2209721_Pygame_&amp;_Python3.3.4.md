---
title: "Pygame &amp; Python3.3.4"
date: 2014-03-07
forum: Programming Talk
---

### Post by malone2 on 2014-03-07
Hello Guys,

I don't know if this is the correct forum for my qustions, but I have been searching for 3 days for an answer without success.

I have Pyhton "3.3.4" installed on my Ubuntu 12.04LTS system. I also installed Pygame "1.9.2pre".
I am trying to capture a single image from my webcam using the Pygame library. The camera is working fine with "Cheese".
Here you are the code I am using:
```

# Testing a webcam capture

import pygame
import pygame.camera
from pygame.locals import *

pygame.init()
pygame.camera.init()
cam = pygame.camera.Camera("/dev/video1",(640,480))
cam.start()

```

The line ```
**pygame.camera.init()**
``` gives the error :

```

Traceback (most recent call last):
  File "Michael/Programming/Python/WebCam.py", line 8, in <module>
    pygame.camera.init()
  File "/usr/local/lib/python3.3/site-packages/pygame/camera.py", line 42, in init
    import _camera
ImportError: No module named '_camera'

```

Thank you guys for your help.

---

### Post by ofnuts on 2014-03-07
Did you try to run /usr/share/pyshared/pygame/examples/camera.py ?

---

### Post by malone2 on 2014-03-07
First of all, thanks for your reply.
Second of all, the examples are for Python 2.7.6 and they are working fine.
I managed also to get my camera work on WinXP on Python 2.7.6

The problem is that all my work with Python was done on 3.3.4 and it will take me weeks to modify the code to run on 2.7.6
Is there a version for Python 3.3.4?

---

