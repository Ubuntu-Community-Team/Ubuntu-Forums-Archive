---
title: "Pygame camera"
date: 2010-06-04
forum: Programming Talk
---

### Post by Tahakki on 2010-06-04
Running a wee experiment with PyGame's camera module - a security camera of sorts that prints 'ping!' when it sees something different. However, it's spitting out 'ping!' every time - is there something wrong with my code, or is it just too sensitive?

```
import pygame
import pygame.camera
from pygame.locals import *
import time
import pygame.image

pygame.init()
pygame.camera.init()
time.sleep(3)
newImage = pygame.Surface((16,12))
otImg = pygame.Surface((16,12))

cam = pygame.camera.Camera("/dev/video0", (16, 12), "RGB")
cam.start()
cam.set_controls(5)
image = cam.get_image()
pygame.transform.smoothscale(image, (16, 12), newImage)
pygame.image.save(newImage, "image.jpg")
billy = pygame.image.tostring(newImage, "RGB")

while 1:
    carl = cam.get_image()
    pygame.transform.smoothscale(carl, (16,12), otImg)
    jim = pygame.image.tostring(otImg, "RGB")
    
    if jim != billy:
        print 'Ping!'
        time.sleep(5)
    if jim == billy:
        print 'Bong.'
        time.sleep(5)
```

Thanks!

---

### Post by feuloren on 2010-06-04
Two images taken at a different time by a camera will "always" be different !
By the way with jim!=billy i'm not even sure you compare the Content of the images.

---

### Post by soltanis on 2010-06-04
Even the slightest changes in light or random sampling error in the camera's CCD will cause your code to be set off. If you want to detect object motion or a big "change" between two frames, you should look into using OpenCV, which has python bindings.

---

### Post by Tahakki on 2010-06-05
With jim!=billy I am checking the string of the image. Is there no way to turn the sensitivity down?

---

