---
title: "OpenCV woes"
date: 2009-08-29
forum: Programming Talk
---

### Post by Samnsparky on 2009-08-29
Hey! I am not sure where this should go, but I will try here. I am using OpenCV to stream images from a logitech quickcam chat, which works with ekiga and gstreamer. However, when running the following program, I get the attached corrupted image.

```
import pygame
import Image
from pygame.locals import *
import sys

import opencv
#this is important for capturing/displaying images
from opencv import highgui 

camera = highgui.cvCreateCameraCapture(0)
def get_image():
    im = highgui.cvQueryFrame(camera)
    # Add the line below if you need it (Ubuntu 8.04+)
    im = opencv.cvGetMat(im)
    #convert Ipl image to PIL image
    return opencv.adaptors.Ipl2PIL(im) 

fps = 30.0
pygame.init()
window = pygame.display.set_mode((640,480))
pygame.display.set_caption("WebCam Demo")
screen = pygame.display.get_surface()

while True:
    events = pygame.event.get()
    for event in events:
        if event.type == QUIT or event.type == KEYDOWN:
            sys.exit(0)
    im = get_image()
    pg_img = pygame.image.frombuffer(im.tostring(), im.size, im.mode)
    screen.blit(pg_img, (0,0))
    pygame.display.flip()
    pygame.time.delay(int(1000 * 1.0/fps))

```
If anyone can help that would be great!

Thanks,
Sam

---

### Post by soltanis on 2009-08-29
And you have verified that in other applications, you can see the image correctly, right? So it isn't a firmware/driver issue?

---

### Post by Samnsparky on 2009-08-29
Thanks for the quick response and, yes, that is correct. The image is fine in Ekiga, Cheese, and gstreamer scripts.

---

### Post by soltanis on 2009-08-29
I noticed you convert to "PIL" format, which I assume stands for Python Imaging Library. However, I don't think that you can directly blit this image (I am under the impression you must blit bitmaps only). This might explain the garbage output.

Reading the PIL documentation, I notice a method for the Image object called "getdata" which returns a linear sequence of the data in the buffer. Assuming its in RGB format (which I am pretty sure it is) you should be able to pass this to the blitter.

---

### Post by Samnsparky on 2009-08-29
Hey! I did not get PIL working, but I was able to use the new camera module in Pygame (after compiling 1.9.1) to get the job done. Python rocks!

Thanks for your help,
Sam

---

