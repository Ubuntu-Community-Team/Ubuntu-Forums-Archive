---
title: "Python Imaging Library problem"
date: 2009-01-15
forum: Programming Talk
---

### Post by RockoTDF on 2009-01-15
I'm having a strange problem with the PIL.  Whenever I use this code:

```

im = Image.open(filename)
data = list(im.getdata())
pixMap = []
newImage = im.load()
imWidth  = im.size[0]
imHeight = im.size[1]

i = 0 #build 2d array to work with
for x in range(0,imWidth):
    tempPix = []
    for y in range(0,imHeight):
        tempPix.append(data[i])
        i = i + 1
    pixMap.append(tempPix)

for x in range(0, imWidth):
    for y in range(0, imHeight):
        if ((pixMap[x][y][0] > aChr[0]) & (pixMap[x][y][0] < aChr[1]) & (pixMap[x][y][1] > aChr[2]) & (pixMap[x][y][1] < aChr[3]) & (pixMap[x][y][2] > aChr[4]) & (pixMap[x][y][2] < aChr[5])):
            temp = (255,0,0)  
            im.putpixel((x,y), temp)
        else:      
            temp = (newImage[x,y])  
            im.putpixel((x,y), temp)     
         
                
im.save(baseName,"BMP")  

```

The output image is very distorted.  The "red-out" area is not actually redded out, but instead is written over the image in the wrong place a few times, like this:

[IMG]http://www.pcs.cnu.edu/~broller/sampleerror.png[/IMG]

Any suggestions?  I have used PIL before with near identical code for image output, and have no idea why this is happening.

---

### Post by RockoTDF on 2009-01-15
Fixed it on my own.  For the sake of future searchers that may run into a similar problem, here is the fixed code:

```

def writeImage(filename, aChr):                  

    im = Image.open(filename)
    data = list(im.getdata())
    pixMap = []
    newImage = im.load()
    imWidth  = im.size[0]
    imHeight = im.size[1]

 
    baseName = "mod_RGB" + filename   
    print "Working on saving", baseName

    for x in range(1, imWidth):
        for y in range(1, imHeight):
            if (newImage[x,y][0] > aChr[0]) & (newImage[x,y][0] < aChr[1]) & (newImage[x,y][1] > aChr[2]) & (newImage[x,y][1] < aChr[3]) & (newImage[x,y][2] > aChr[4]) & (newImage[x,y][2] < aChr[5]):            
                temp = (255,0,0)
                im.putpixel((x,y), temp)
            else:
                temp = (newImage[x,y])  
                im.putpixel((x,y), temp)

    im.save(baseName,"BMP")  
    print baseName, "has been saved."      

```

---

