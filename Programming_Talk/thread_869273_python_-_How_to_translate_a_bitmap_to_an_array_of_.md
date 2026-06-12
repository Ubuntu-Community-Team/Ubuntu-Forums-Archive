---
title: "python - How to translate a bitmap to an array of bits?"
date: 2008-07-24
forum: Programming Talk
---

### Post by rlameiro on 2008-07-24
Hello everyone!
I am going to vacations, but before that I would like to have an insight in how to convert a bitmap image into binary code/HEX.

This is for the project [bicycleledpov]("http://code.google.com/p/bicycleledpov/").
IDEA - 
Translate a Black and White image (for now) to an array (or list, or dictionary) of Binary/HEX data.
Since the idea is to light a wheel, therefore a circumference  the image must have a width(?) of 64 bits 32 from the center to the outer part.

Translation must be from 32 bits words for each line, and 256 lines or 2^8. Image attached 
the final result will be stored in a file and then sent to the hardware via virtual serial/USB port.

Problem -
How can I translate an Image in black and white to 0 and 1 with python?

Modules Ideas anything is welcome since I am a newbie, and here are people that like to help. 
I don't want with this that people come here and post the code to do this, but to guide me and give ideas.
If anyone is interested in joining the project I will also be very happy.
thanks!!!!

---

### Post by angustia on 2008-07-24
[http://docs.python.org/lib/module-struct.html](http://docs.python.org/lib/module-struct.html)

---

### Post by rlameiro on 2008-07-24
> **angustia said:**
> [http://docs.python.org/lib/module-struct.html](http://docs.python.org/lib/module-struct.html)

I don't understand why this link is important. Is it because enables the use of HEX ?

The problem is not the binary/hex code but actually the translation from bitmap to BIN/HEX

---

### Post by mike_g on 2008-07-24
Bitmaps are pretty easy to read as long as they dont use a palette. The first 54 bytes (i think) is header info, which you will need to check for stuff like the bitdepth. The following is just uncompressed image data. If you google bmp file format it should provide you with a list of the header info.

Hexadecimal and binary are just different representations of the same thing.

---

### Post by rlameiro on 2008-07-24
Thanks for the info.
> **mike_g said:**
> 
Hexadecimal and binary are just different representations of the same thing.

I knew about that, just python don't use binary representation so I write bin/hex.

---

### Post by WW on 2008-07-24
That looks like a cool project!

Here is a python script that I think does something like what you want (assuming I really understood your question).  It uses the Python Imaging Library to read an image file.  It also uses numpy, but not in an essential way; it wouldn't be difficult to avoid it if you don't want to use numpy.

**ledconvert.py**
```

#!/usr/bin/python

import sys
import math
import numpy
from PIL import Image

def pixel_to_bit(pixel,threshold=128):
    """Convert the pixel value to a bit."""
    if pixel > threshold:
        return 1
    else:
        return 0

def convert(im,center,inner_radius,outer_radius,fill=255,mark=False):
    """
    Convert the pix data into an integer array of 256 values.
    Each integer value is the LED pattern along a radius.
    
    Arguments:
    im :  An Image; currently the pixels in the imag must be a single
          value (and not, say, an RGB triple)
    center : An (x,y) tuple of the center of the sampling region
    inner_radius : The inner radius of the sampling region
    outer_radius : The outer radius of the sampling region
    fill : The value to use for samples that are outside the bounds of the image.
    mark : If True, the input image im is modified by inverting the value of
           each sampled point in the sampling region.
           
    Return value:
    A list of 256 lists of 32 binary values.  The 32 binary values are the
    samples for each "spoke".
    """
    pix = im.load()
    result = []
    for theta in numpy.linspace(0.0,2*numpy.pi,num=256,endpoint=False):
        spokedata = []
        for r in numpy.linspace(inner_radius,outer_radius,num=32):
            i = int(center[0] + r*math.cos(theta))
            j = int(center[1] + r*math.sin(theta))
            if i >= im.size[0] or i < 0 or j >= im.size[1] or j < 0:
                pixel = fill
            else:
                pixel = pix[i,j]
                if not mark is False:
                    pix[i,j] = 255-pix[i,j]
            bit = pixel_to_bit(pixel)
            spokedata.append(bit)
        result.append(spokedata)
    return result


def use():
    print "Use: ledconvert.py  imagefile [cx=center_x cy=center_y ri=inner_radius ro=outer_radius fill=fill_value mark=0 or 1]"
    print "Default value of the keyword arguments:"
    print "cx : center of the image"
    print "cy : center of the image"
    print "ri : 2"
    print "ro : half the width of the image"
    print "fill : value of the upper left corner of the image"
    print "mark : 0 (meaning False; use 1 for True)"

       

#
# Main script begins here.
#
# First check for keyword arguments on the command line.
#

kwargs = {'cx':None, 'cy':None, 'ri':None, 'ro':None, 'fill':None, 'mark':None }

if len(sys.argv) > 2:
    for kwa in sys.argv[2:]:
        if not '=' in kwa:
            print "Invalid keyword argument '%s'." % kwa
            print "All arguments after imagefile must be keyword arguments."
            use()
            exit(-1)
        (w,v) = kwa.split('=')
        if w in kwargs:
            kwargs[w]=int(v)
        else:
            print "Unknown keyword argument '%s'." % kwa
            use()
            exit(-1)

#
# Open the image file and get the basic information about it.
#
try:
    im = Image.open(sys.argv[1])
except:
    # Eventually this should give more useful information (e.g. file does not
    # exist, or not an image file, or ...
    print "Unable to open %s" % sys.argv[1]
    exit(-1)

print "format: %s   mode: %s   palette: %s" % (im.format,im.mode,im.palette)
width,height = im.size
print "The image is %d x %d" % im.size
if im.mode == "RGB":
    print sys.stderr, "Sorry, this program can't handle RGB images yet."
    exit(0)

#
# Set the default options for any that were not given on the command line.
# (Do this after opening the file, because some of the default options depend
# on the image data.)
#
if kwargs['cx'] is None:
    kwargs['cx'] = width/2
if kwargs['cy'] is None:
    kwargs['cy'] = height/2
if kwargs['ri'] is None:
    kwargs['ri'] = 2
if kwargs['ro'] is None:
    kwargs['ro'] = width/2
if kwargs['fill'] is None:
    pix = im.load()
    kwargs['fill'] = pix[0,0]
if kwargs['mark'] is None:
    kwargs['mark'] = 0

#
# Do it!
#
samples = convert(im,(kwargs['cx'],kwargs['cy']),kwargs['ri'],kwargs['ro'],
                fill=kwargs['fill'],mark=kwargs['mark'])

#
# Write the data to a new file.
# This part needs to be rewritten to put the output file into the desired form.
# For now, just write something readable to "radial_samples.dat"
#
f = open("radial_samples.dat",'w')
for d in samples:
    for b in d:
        f.write("%d " % b)
    f.write('\n')
f.close()

#
# If mark was set, the sampled pixels have been inverted.
# Save the image to a new file, so we can look at the sample pattern.
#
if kwargs['mark'] != 0:
    im.save("tmp.png")

```

For example, the attached file is a monochrome png image.  I ran the program like this:
```

$ ./ledconvert.py skull_and_crossbones.png cy=190  ri=8 ro=195 mark=1
format: PNG   mode: L   palette: None
The image is 344 x 341
$

```
This created two files: "radial_samples.dat", which contains the binary data (256 lines, each with 32 binary values), and "tmp.png", which is a modified copy of the image, with the sample points marked.

If it works for you, use it.  Hack it up however you like.  You'll probably want to change the program to write the sample data into a format that suits your needs.


EDIT:
> **rlameiro said:**
> 
I don't want with this that people come here and post the code to do this, but to guide me and give ideas.

I got a little carried away; I hope the code I posted gives you lots of ideas.    I know it gave me some. For example, how about a GUI that displays the image, and lets you drag and resize a circle superimposed over the image, so you can visually select the part of the image that you want to sample.

---

### Post by rlameiro on 2008-07-30
WW thanks for the info you posted. 
sorry for not replying sooner, if anyone has more thoughts in this matter please don't be shy :)

---

