---
title: "python excel and pil help"
date: 2010-04-06
forum: Programming Talk
---

### Post by syntychakis on 2010-04-06
Hallo everybody, 
 
 
I am a beginner with python. I want to do something, but i didn't not 
succeed yet, so i hope that you could help me. 
 
 
I have a grayscale image. (500 by 500 pixels). The colour of the image 
is gray with some noise (black white) (something like an echography 
image). on the image there are also some round objects. These objects 
are +/- 15 by 15 pixels and have a round shape. In the middel of the 
these objects is the pixel value the greatest. 
What i want is to be able to detect these objects and get their 
position and average pixelvalue into excel. 
 
 
 
Ik was thinking, that i could do something like this; 'cut' the image 
in pieces of 3 by 3 pixels. If in one of the pieces the average pixel 
value is higher than (for example: 150, then i know that, that is an 
object i am looking for. so the position of the object must been 
written to excel. Then python has to make a 15 by 15 pixel piece and 
get the average pixelvalue of it into excel. 
 
 
so, my biggest problem is not to get the data into excel, but to find these objects.
 
I hope you can understand what i mean and you can help me. 
I also hope i am at the right forum to ask this. If not, could 
somebody tell where i have to be? 
thanks in advance,

---

### Post by lavinog on 2010-04-06
What format is the image?

It sounds like you need to get the pixel values for the image. I am kind of working on a similar thing.

```

import Image  #python-pil
def getimgmatrix(img):
    maxx,maxy=img.size
    
    imgdata=list(img.getdata())
    splitdata=[]
    for y in range(maxy):
        splitdata.append( imgdata[y:y+maxx] )
    return splitdata

data = getimgmatrix( Image.open('imagefile.png') )

```

---

### Post by syntychakis on 2010-04-07
thanks, sounds interesting. I 'll try it.

What i want is to cut the image in piecies of 3 by 3 pixels and then search in these piecies, for pieces with an averagepixel value of above the (for example:) 150. later i want to make a slidebar of it!

it's a grayscale 'L' type image

---

### Post by lavinog on 2010-04-07
Once you get the data into a matrix (nested list object) extracting the 3x3 pixel data should be easy, but are you sure that is the way you want to solve the problem?

Are you wanting to ignore the round objects that are clipped at the edges of the image?

Are the objects a solid color?

Could you just start by making a list of which rows and cols contain at least 15 pixels of an object.  Intersection points of these lines should be considered possible objects.  Then you can verify the possible objects by checking the neighboring pixels.

---

