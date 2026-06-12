---
title: "testing pixel colour of image x and y in Python"
date: 2009-05-04
forum: Programming Talk
---

### Post by UbuKunubi on 2009-05-04
Hello.

I intent to build a CNC machine for engraving, and think that the way to do this is to build a python program to test each pixel in an image to find the boundary between black and white, so the point at which black meets white can be turned into coordinates to aim a stepper motor driven tool carrier towards.

I have all the parallel port code done and dusted, but im stuck on simply testing the x,y of an image to see if it is black or white.

Can anyone help or point me in the right direction?

Thanks for your time

---

### Post by regomodo on 2009-05-04
#

---

### Post by UbuKunubi on 2009-05-05
Thanks for your well-rounded answer.

All I have to do is change the code you've provided to store the x and y coordinates in a table so I can then work on the link to turn the coordinates into stepper motor pulses.


Can you also advise me on which python numpy packages are needed from synaptic manager please?

Once again - thank you.

---

### Post by regomodo on 2009-05-05
#

---

### Post by UbuKunubi on 2009-05-06
After much hunting I have found out the following:

For ubuntu users: numpy is avilable in Jaunty from Synaptic manager.

The code below was found on [http://alwaysmovefast.com/2007/12/05/basic-edge-detection-in-python/](http://alwaysmovefast.com/2007/12/05/basic-edge-detection-in-python/) and I have given my thanks to the author.

I have modified the code to produce a file of coordinates of Edge detection, and I'll work on the code for driving the stepper motor in good time.

My end goal is to produce a GUI for the completed program, and wrap it all up so it is installable from a .deb package (i'll be after help)

So this code requires a greyscale image in the same directory as the code, and will output a image file highlighting the edges, and a text file of the edge coordintaes.


# -*- coding: utf-8 -*-
  

# Uses hashes of tuples to simulate 2-d arrays for the masks.  
def get_prewitt_masks():
    xmask = {}
    ymask = {}

    xmask[(0,0)] = -1
    xmask[(0,1)] = 0
    xmask[(0,2)] = 1
    xmask[(1,0)] = -1
    xmask[(1,1)] = 0
    xmask[(1,2)] = 1
    xmask[(2,0)] = -1
    xmask[(2,1)] = 0
    xmask[(2,2)] = 1

    ymask[(0,0)] = 1
    ymask[(0,1)] = 1

    ymask[(0,2)] = 1
    ymask[(1,0)] = 0
    ymask[(1,1)] = 0
    ymask[(1,2)] = 0
    ymask[(2,0)] = -1
    ymask[(2,1)] = -1
    ymask[(2,2)] = -1
    return (xmask, ymask)

import Image
import os,sys

def FileWrite(x,y):
    fhandle = open("COORDINATES.TXT",'a')
    fhandle.write(str(x))
    fhandle.write(",")
    fhandle.write(str(y))
    fhandle.write(" \n")
    fhandle.close()
    
def prewitt(pixels, width, height):
    xmask, ymask = get_prewitt_masks()
    
    # create a new greyscale image for the output
    outimg = Image.new('L', (width, height))  
    outpixels = list(outimg.getdata())  
    
    for y in xrange(height):  
      for x in xrange(width):  
        sumX, sumY, magnitude = 0, 0, 0  
    
        if y == 0 or y == height-1: magnitude = 0  
        elif x == 0 or x == width-1: magnitude = 0  
        else:
            for i in xrange(-1, 2):
                for j in xrange(-1, 2):
                    # convolve the image pixels with the Prewitt mask, approximating &#8706;I / &#8706;x
                    sumX += (pixels[x+i+(y+j)*width]) * xmask[i+1, j+1]
            for i in xrange(-1, 2):
                for j in xrange(-1, 2):
                    # convolve the image pixels with the Prewitt mask, approximating &#8706;I / &#8706;y
                    sumY += (pixels[x+i+(y+j)*width]) * ymask[i+1, j+1]

            # approximate the magnitude of the gradient
            magnitude = abs(sumX) + abs(sumY)  
     
            if magnitude > 255:
                magnitude = 255
                print "X=",x," Y=",y
                FileWrite(x,y)
            if magnitude < 0: magnitude = 0  
     
            outpixels[x+y*width] = 255 - magnitude
            
    outimg.putdata(outpixels)
    return outimg  

import sys  
if __name__ == '__main__':
    img = Image.open(sys.argv[1])
    # only operates on greyscale images
    if img.mode != 'L': img = img.convert('L')
    pixels = list(img.getdata())
    w, h = img.size
    outimg = prewitt(pixels, w, h)
    outimg.save(sys.argv[2])

To run the program open terminal and type: python edgedetect.py input.jpg output.jpg

---

### Post by UbuKunubi on 2009-11-15
Revisitng - Bump!

This has been on the back-burner for a while now.

If anyone has any tips, urls, example code, etc about how to test for the pixel colour code under the mouse pointer I would really appreciate it.

Ubu.

---

### Post by Can+~ on 2009-11-15
> **UbuKunubi said:**
> Revisitng - Bump!

This has been on the back-burner for a while now.

If anyone has any tips, urls, example code, etc about how to test for the pixel colour code under the mouse pointer I would really appreciate it.

Ubu.

Use a GTK+ Color Selection Dialog, it has an "eyedropper tool" that gets the color of any part of the screen. You don't need to reinvent the wheel.

---

### Post by UbuKunubi on 2009-12-02
Many thanks, I had'nt known that GTK would be able to do this, and your quite right, I dont want to reinvent the wheel.

Cheers,
Ubu

---

