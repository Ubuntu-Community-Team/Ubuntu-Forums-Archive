---
title: "Voronoi / Worley Noise Knowlege Dump *56k beware images*"
date: 2010-07-10
forum: Programming Talk
---

### Post by chris_0076 on 2010-07-10
Hello,

For the past week or so, I have familiarized myself with Voronoi/Worley Noise, so as a conclusion to learning about and writing a program for Voronoi I have decided to share what I have learned as a pseudo-tutorial about the subject. Now with out further delay I present what I have learned. Also sorry about some of the pictures... I had more than 8 and had to cut some.




**[SIZE=4]What is Voronoi/Worley Noise?[/SIZE]**
Well in the simplest sense, it is a different representation of points in space, but rather than showing the points themselves they are visualized by the pixels around them. So, 
 as you will see in the pictures below the further the pixel is away from the point the brighter it will be. This of course can be inverted. With this gradients can be formed from the point going outwards in all directions . 
For more info [http://en.wikipedia.org/wiki/Voronoi_diagram](http://en.wikipedia.org/wiki/Voronoi_diagram)

**[SIZE=4]Ways to Measure Distance[/SIZE]**
All of these make the assumptions that:
delta(x) = x1 - x2
delta(y) = y1 - y2
a = delta(x)
b = delta(y)
**
Note: All the pictures use the same same settings other than the distance type
size = 100
fValue = 1
blockSize = 10
**

**Linear**
This is the good old Pythagorean theorem.

[IMG]http://img197.imageshack.us/img197/7417/voronoilinear11.png[/IMG]
_Equation:_
distance^2 = a^2 + b^2  or  
distance = sqrt(a^2+b^2)


**Linear Squared**
This is the same as before except you do not take the square root of the ending total. This in turn saves some computation time.

[IMG]http://img805.imageshack.us/img805/543/voronoisqlen11.png[/IMG]
_Equation:_
distance = a^2 + b^2


**Manhattan**
This method of computing distances is based off of how one would travel in a city. So in this is the shortest distance that could be traveled with no diagonal lines. The main thing here is that the delta(x) and delta(y) must be positive. (Self error note: This was a problem when I first started in that I would have these perfect diagonal gradients on the screen.
 Also if you do not take the absolute value of any of it you will get some weird results.)

[IMG]http://img696.imageshack.us/img696/2103/voronoimanhattan11.png[/IMG]
_Equation:_
distance = abs(a) + abs(b)


**Chebyshev (sometimes seen as chebychev)**
This way is similar to the Manhattan method in that it goes based of individual changes in x or y. The only thing different here is that it includes diagonals. This comes from this methods is based off how a king can move in chess. By adding the diagonal it adds the possibility of traveling both to a and b at the same time. This causes the value to be which ever number is lower.

[IMG]http://img88.imageshack.us/img88/6890/voronoichebyshev11.png[/IMG]
_Equation:_
if abs(a) == abs(b) or abs(a) < abs(b)
    distance = abs(a)
if abs(a) > abs(b)
    distance = abs(b)

 
**Quadratic**
The quadratic method is simple in that it is all the values multiplied together then added up just like a quadratic equation. ex. (x^2 + xy + y^2)

[IMG]http://img210.imageshack.us/img210/8090/voronoiquadratic11.png[/IMG]
_Equation:_
distance = (a*a + a*b + b*b)


**Minkowski**
Minkowski is a little odd in that, from what I have observed, it is controlled by an exponential, and based on that number the results go from being the same as Manhattan (MinkowskiNumber=1) to being more and more square as the number increases leading eventually to look like the Chebyshev. If anyone knows any more about this feel free to correct me. I personally would like to know a little more about this one.

[http://img412.imageshack.us/img412/2486/voronoiminkowski11.png](http://img412.imageshack.us/img412/2486/voronoiminkowski11.png)
MinkowskiNumber=1
[IMG]http://img41.imageshack.us/img41/2486/voronoiminkowski11.png[/IMG]
MinkowskiNumber=3
[http://img268.imageshack.us/img268/2204/voronoiminkowski111.png](http://img268.imageshack.us/img268/2204/voronoiminkowski111.png)
MinkowskiNumber=5
_Equation:_
distance = (abs(a)^MinkowskiNumber + abs(b)^MinkowskiNumber) ^ (1 / MinkowskiNumber)


**[SIZE=4]Voronoi Math[/SIZE]**
Just like any other type of image these can easily be manipulated to render very different results.
 The most common types of math with these are taking different fValues of the same seed and adding or subtracting them. 
With this different patterns can be created by use of variations of the same points.

**fValues**
fValues are what determine how many (and to which points) the induvidaul pixels will calculate distance to. F1 for example is the absolute closest point to said pixel. F2 would be the second closest, and so on and so forth. (Self error note: the fValues are only for that point. They are not cumulative! This will result in some wonky math later on ie (F2 &#8211; F1 = the real F2)(F3 &#8211; F2 = real F3) ect. When I first wrote the code I had it set up this way and was wondering why it did not work right. I don't know whether it was me being dumb or some of the other sites explainations of the subject being weird. Either way I hope that this will stop anyoe else from falling into my mistake.)

**Octaves**
Just like in other noise octaves define how many iterations of the same variables other than the blockSize. This is changed to allow for more detail in the image. By shrinking the blockSize more and more layers of noise are overlayed on each other. By doing this with some modification, this code could create fractals based off  of an ever decreasing blockSize.

[IMG]http://img51.imageshack.us/img51/4643/voronoi1oct.png[/IMG] 
1 Octave
[http://img130.imageshack.us/img130/8527/voronoi2oct.png](http://img130.imageshack.us/img130/8527/voronoi2oct.png) 
2 Octaves
[http://img191.imageshack.us/img191/6613/voronoi3oct.png](http://img191.imageshack.us/img191/6613/voronoi3oct.png) 
3 Octaves
[IMG]http://img191.imageshack.us/img191/4367/voronoi4oct.png[/IMG] 
4 Octaves


**[SIZE=4]Other Stuff[/SIZE]**
**Plated/ Solid Cell Results**
Plated/ Solid Cells can be seen if you set the var plated to True.

**Original Voronoi Results**
You can get the original Voronoi results if you turn on plated and platedLines


**[SIZE=4]My Code:[/SIZE]**
VController.py
```
import math
import random
import Image
import ImageDraw

class Voronoi:
    def __init__(self, size, blockSize=None, octave=None, fValue=None, clip=0,
                 seed=None, distType="Linear", plated=False, platedColor=True, platedLines=False, minkowskiNumber=4):
        self.size = size
        self.octave = octave
        self.blockSize = blockSize
        self.fValue = fValue
        self.seed = seed
        self.clip = clip
        self.distType= distType
        self.plated = plated
        self.platedColor = platedColor
        self.platedLines = platedLines
        self.minkowskiNumber = minkowskiNumber

        if self.seed == None:
            self.seed = random.randint(0, 10)
        if self.fValue == None:
            self.fValue = [1]
        if self.octave == None:
            self.octave = [1]
        if self.blockSize == None:
            self.blockSize = [10]
        self.fValueParser()
        self.octaveParser()
        self.blockSizeParser()
        self.main()

    def fValueParser(self):
        self.fValueRun = []
        self.fValueOld = self.fValue
        self.fValue = []
        for number in xrange(len(self.fValueOld)):
            if self.fValueOld[number] != 0:
                self.fValueRun.append(number+1)
                self.fValue.append(self.fValueOld[number])
                
    def octaveParser(self):
        self.octaveRun = []
        self.octaveOld = self.octave
        self.octave = []
        for number in xrange(len(self.octaveOld)):
            if self.octaveOld[number] != 0:
                self.octaveRun.append(number+1)
                self.octave.append(self.octaveOld[number])

    def blockSizeParser(self):
        self.blockSizeOld = self.blockSize
        self.blockSize = []
        for number in xrange(len(self.blockSizeOld)):
            if self.blockSizeOld[number] != 0:
                self.blockSize.append(self.blockSizeOld[number])

    def main(self):
        self.octaveLoop()

    def octaveLoop(self):
        self.octaveNumbers = []
        for number in xrange(len(self.octaveRun)):
            blockSize = self.blockSize[number]
            self.fValueLoop(blockSize)
            a = self.fValueNumbers
            b = self.octave[number]
            if len(self.octave) == 1:
                if self.octave[number] != 1:
                    self.octaveNumbers = self.mult(a, b)
                else:
                    self.octaveNumbers = a
            else:
                self.octaveNumbers.append(self.mult(a, b))
                if len(self.octaveNumbers) == 2:
                    new = zip(self.octaveNumbers[0], self.octaveNumbers[1])
                    self.octaveNumbers = []
                    newer = []
                    if len(self.octave) == number + 1:
                        for pair in new:
                            self.octaveNumbers.append(sum(pair))
                    else:
                        for pair in new:
                            newer.append(sum(pair))
                        self.octaveNumbers.append(newer)

    def fValueLoop(self, blockSize):
        self.fValueNumbers = []
        for number in xrange(len(self.fValueRun)):
            fValue = self.fValueRun[number]
            thing = VoronoiFaster.VoronoiFaster(self.size, fValue, blockSize, distType=self.distType, seed=self.seed,
                                                plated=self.plated, platedColor=self.platedColor, platedLines=self.platedLines, minkowskiNumber=self.minkowskiNumber)
            a = thing.pixelColorNumbers
            b = self.fValue[number]
            if len(self.fValueRun) == 1:
                self.fValueNumbers = self.mult(a, b)
            else:
                self.fValueNumbers.append(self.mult(a, b))
                if len(self.fValueNumbers) == 2:
                    new = zip(self.fValueNumbers[0], self.fValueNumbers[1])
                    self.fValueNumbers = []
                    for pair in new:
                        self.fValueNumbers.append(sum(pair))

    def mult(self, aList, multNumber):
        for number in xrange(len(aList)):
            aList[number] *= multNumber
        return aList

    def getLocation(self, idNumber):
        xloc = idNumber % self.size
        yloc = idNumber / self.size
        return (xloc, yloc)

    def draw(self):
        self.img = Image.new("RGB", (self.size, self.size))
        draw = ImageDraw.ImageDraw(self.img)
        self.minNumber = min(self.octaveNumbers)
        self.maxNumber = max(self.octaveNumbers) - self.minNumber
        self.colorSpread = 255 / (self.maxNumber * (1 - self.clip)) 
        for pixel in xrange(self.size * self.size):
            coords = self.getLocation(pixel)
            color = int(self.colorSpread * (self.octaveNumbers[pixel] - self.minNumber))
            colorSet = (color, color, color)
            draw.point(coords, colorSet)

        self.img.show()

```VoronoiFaster.py
```
import math
import random
import Image
import ImageDraw
import time

class VoronoiFaster:
    '''Creates Voronoi/Worley Noise using a 3x3 grid to decrease running time.

Known Problems:
Nonsquare Starting Image
    Results in a messed up image. Problem seems to be\n that blocks are being placed on each other.
clip = 1
    Sorry but no one can divide by 0
"Manhattan" and "Chebyshev"
    Results are normally plain white screens at the end.\n Problem seems to come from the method of turnning numbers into colors.
'''
    def __init__(self, size, fValue, blockSize,
                 pointsList=None, distType="Linear", seed=None, clip=0, plated=False, platedColor=True, platedLines=False, minkowskiNumber=4):
        self.size = size
        self.fValue = int(fValue)
        if pointsList == None:
            self.pointsList = []
        else:
            self.pointsList = pointsList
        self.seed = seed
        self.pixelColorNumbers = range(self.size*self.size)
        self.clip = clip
        self.totalBlocks = int((self.size / blockSize) * (self.size / blockSize))
        print "Currently generating %s cell blocks. At and fValue of %f." % (self.totalBlocks, self.fValue)
        self.blockSize = blockSize
        self.distType = distType
        self.plated = plated
        self.platedColor = platedColor
        self.platedLines = platedLines
        self.minkowskiNumber = minkowskiNumber

        #if there is no prelisted points then this will make some
        if self.pointsList == []:
            #makes as many points as their are block in the image
            #note: the points made are relative to the block that they are in, so all numbers range from 0 to blocksize - 1
            self.generatePoints(self.totalBlocks)
            #converts the relative points to the absolute location within the image
            #at this point the index number corresponds to what block it is
            #block(0, 0) = pointsList[0], block(1, 0) = pointsList[1]...
            self.xyPoints(self.pointsList)
        if self.plated == True:
            self.generateCellColors(self.totalBlocks)

        self.main()

    def main(self):
        #loops for total amount of pixels in the image
        for pixels in xrange(self.size * self.size):
            x, y = self.getLocation(pixels)
            xBlock, yBlock = self.getBlock(x, y)
            #finds the neighbors for the pixel
            neighbors, over = self.neighborCheck(xBlock, yBlock)
            #converts the neighbors block coords into xy coords
            neighbors2 = self.over(over, neighbors)
            #finds and saves the distance between the points
            if self.plated == True:
                nothing, ID = self.findNearestPoints(x, y, neighbors2, self.distType)
                self.pixelColorNumbers[pixels] = self.platedCheck(ID, neighbors2)
            else:
                self.pixelColorNumbers[pixels], nothing = self.findNearestPoints(x, y, neighbors2, self.distType)
        if self.platedLines == True:
            self.draw()
        
    def findNearestPoints(self, x, y, neighbor, distMethod):
        pixelDist = []
        shortest = []
        shortestID = []
        for coords in neighbor:
            #self.lenght returns just the distance between the two points
            distance =  self.lenght((x, y), coords, distMethod)
            pixelDist.append(distance)
        for amount in xrange(self.fValue):
            #finds smallest distance
            minNum = min(pixelDist)
            idxNum = pixelDist.index(minNum)
            #removes the number from pixelDist and places it in shortest all in one swoop
            shortest.append(pixelDist.pop(idxNum))
            shortestID.append(idxNum)
        final = shortest.pop()
        ID = shortestID.pop()
        return final, ID

    def platedCheck(self, ID, neighbors):
        (x, y) = neighbors[ID]
        if x < 0:
            x += self.size
        if y < 0:
            y += self.size
        if x > self.size:
            x -= self.size
        if y > self.size:
            y -= self.size
        blockCoords = self.getBlock(x, y)
        bID = self.getBlockID(blockCoords)
        return self.cellColors[bID]
            
    def lenght(self, (x1, y1), (x2, y2), method="Linear"):
        dx = x2 - x1
        dy = y2 - y1
        if method == "SqLen":
            distance = (dx*dx+dy*dy)
        elif method == "Manhattan":
            distance = int(abs(dx)+abs(dy))
        elif method == "Chebyshev":
            #all this does is returns the smaller number out of dx and dy, or dx if they are the same
            if abs(dx) == abs(dy) or abs(dx) > abs(dy):
                distance = int(abs(dx))
            else:
                distance = int(abs(dy))
        elif method == "Quadratic":
            distance = (dx*dx+dy*dy+dx*dy)
        elif method == "Minkowski":
            a = ((abs(dx) ** self.minkowskiNumber) + (abs(dy) ** self.minkowskiNumber))
            distance = a ** (1.0/self.minkowskiNumber)
        else:
            distance = math.sqrt(dx*dx+dy*dy)
        return distance

    def generatePoints(self, amountBlocks):
        if self.seed == None:
            self.seed = random.randint(0, 10)
        seed = self.seed
        for number in xrange(amountBlocks):
            random.seed(seed)
            random1 = random.random() * (self.blockSize - 1)
            random.seed(seed+1)
            random2 = random.random() * (self.blockSize - 1)
            #This xyCoord is relative to the top left corner of the block
            self.pointsList.append((random1, random2))
            seed += 1
            
    def generateCellColors(self, amountBlocks):
        if self.seed == None:
            self.seed = random.randint(0, 10)
        seed = self.seed
        self.cellColors = []
        for number in xrange(amountBlocks):
            random.seed(seed)
            random1 = int(random.random() * 255)
            seed += 1
            self.cellColors.append(random1)
                
    def getLocation(self, idNumber):
        xloc = idNumber % self.size
        yloc = idNumber / self.size
        return (xloc, yloc)
    

    def getBlock(self, x, y):
        xblock = int(x / self.blockSize)
        yblock = int(y / self.blockSize)
        return (xblock, yblock)

    def getBlockStartXY(self, ID):
        x = (ID % (self.size / self.blockSize)) * self.blockSize
        y = (ID / (self.size / self.blockSize)) * self.blockSize
        return (x, y)

    def getBlockEndXY(self, ID):
        x = (ID % (self.size / self.blockSize)) * self.blockSize + self.blockSize
        y = (ID / (self.size / self.blockSize)) * self.blockSize + self.blockSize
        return (x, y)

    def getBlockID(self, (xblock, yblock)):
        blockID = int(yblock * (self.size / self.blockSize) + xblock)
        return blockID

    def neighborCheck(self, xblock, yblock):
        #this is just all the blocks in a 3x3 around the block including itself
        neighbors = [(xblock - 1, yblock + 1), (xblock, yblock + 1), (xblock + 1, yblock + 1),
                     (xblock - 1, yblock), (xblock, yblock), (xblock + 1, yblock),
                     (xblock - 1, yblock - 1), (xblock, yblock - 1), (xblock + 1, yblock - 1)]
        over = []
        #this goes through and checks it any of the blocks are off the picture
        maxX = (self.size / self.blockSize) - 1
        for number in xrange(len(neighbors)):
            x, y = neighbors[number]
            overX = 0
            overY = 0
            #this if/then block determines what kind of overshoot it is
            if x < 0:
                x = maxX
                overX = -1
            if y < 0:
                y = maxX
                overY = -1
            if x > maxX:
                x = 0
                overX = 1
            if y > maxX:
                y = 0
                overY = 1
            if overX != 0 or overY != 0:
                #this was going to be a dict, but i ran some tests and it was about 10% slower
                #structure is: (theIDfortheNumberinNeighbors, (typeOverX, typeOverY))
                over.append((number, (overX, overY)))
            neighbors[number] = (x, y)
        return neighbors, over

    def over(self, over, neighbors):
        neighborsIDs = []
        for roundNumber in xrange(len(neighbors)):
            #this converts all of the blockCoords into what ID they are
            #this is to associate them back with their point from self.pointsList
            neighborsIDs.append(self.getBlockID(neighbors[roundNumber]))
        #neighbors is cleared to get ready for the new numbers to be put in
        neighbors = []
        for nID in neighborsIDs:
            #this puts the xycoords from pointsList into neighbors
            neighbors.append(self.pointsList[nID])
        #now it goes through and checks to see which neighbor IDs have problems and corrects them
        for neighborID, (xOverBlock, yOverBlock) in over:
            x, y = neighbors[neighborID]
            #note: if it a point needs correcting it is moved a full image dimension across.
            #this means that the new numbers will be < 0 and > the height or width
            #this allows for the image to be tiled
            if xOverBlock == 1:
                x = x + self.size
            if xOverBlock == -1:
                x = x - self.size
            if yOverBlock == 1:
                y = y + self.size
            if yOverBlock == -1:
                y = y - self.size
            neighbors[neighborID] = (x, y)
        return neighbors

    def xyPoints(self, numList):
        #this goes through and makes all the points go from being relative to the block to being absolute
        for number in xrange(len(numList)):
            x, y = numList[number]
            #the block starting position
            xB, yB = self.getBlockStartXY(number)
            x = x + xB
            y = y + yB
            numList[number] = (x, y)
            
    def showIt(self, color="color", pointsOn=False,pointsColor=(0,0,0), border=False):
        #this was added in just to visualize all the blocks, and points
        img = Image.new("RGB", (self.size, self.size))
        draw = ImageDraw.ImageDraw(img)
        for number in xrange(len(self.pointsList)):
            start = self.getBlockStartXY(number)
            end = self.getBlockEndXY(number)
            #random generation of color of rectangles
            color1 = random.randint(0, 255)
            color2 = random.randint(0, 255)
            color3 = random.randint(0, 255)
            colorSet = (color1, color2, color3)
            if color == "mono":
                colorSet = (color1, color1, color1)
            elif color == "none":
                colorSet = (255, 255, 255)
            if border == True:
                draw.rectangle([start, end], fill=colorSet, outline="black")
            else:
                draw.rectangle([start, end], fill=colorSet)
        if pointsOn == True:
            for x, y in self.pointsList:
                draw.point((x, y), fill=pointsColor)
        img.show()
        img.save("test.png")

    def draw(self):
        #all the PIL stuff
        self.img = Image.new("RGB", (self.size, self.size))
        draw = ImageDraw.ImageDraw(self.img)

        #This is where the colors of the pixels are determined
        #I am currently in search of a new way to do this
        if self.plated == True:
            for pixel in xrange(self.size * self.size):
                x, y = self.getLocation(pixel)
                colorSet = self.pixelColorNumbers[pixel]
                draw.point((x, y), (colorSet, colorSet, colorSet))
            if self.platedLines == True:
                self.img2 = Image.new("RGB", (self.size, self.size), (255, 255, 255))
                draw2 = ImageDraw.ImageDraw(self.img2)
                for pixel in xrange(self.size * self.size):
                    x, y = self.getLocation(pixel)
                    border = self.isBorder((x,y))
                    if border == True:
                        draw2.point((x, y), (0,0,0))
                        self.pixelColorNumbers[pixel] = 1
                    else:
                        self.pixelColorNumbers[pixel] = 0
                self.img = self.img2
        else:
            if min(self.pixelColorNumbers) < 0:
                self.minNumber = min(self.pixelColorNumbers)
                self.maxNumber = max(self.pixelColorNumbers) - self.minNumber
            else:
                self.minNumber = min(self.pixelColorNumbers)
                self.maxNumber = max(self.pixelColorNumbers) - self.minNumber
            self.colorSpread = 255 / self.maxNumber
            #coloring
            if min(self.pixelColorNumbers) < 0:
                for pixel in xrange(self.size * self.size):
                    coords = self.getLocation(pixel)
                    color = int(self.colorSpread * (self.pixelColorNumbers[pixel] - self.minNumber))
                    colorSet = (color, color, color)
                    draw.point(coords, colorSet)
            else:
                for pixel in xrange(self.size * self.size):
                    coords = self.getLocation(pixel)
                    color = int(self.colorSpread * (self.pixelColorNumbers[pixel] - self.minNumber))
                    colorSet = (color, color, color)
                    draw.point(coords, colorSet)

    def isBorder(self, (x, y)):
        neighbors = [(x-1, y+1), (x, y+1), (x+1, y+1),
                     (x-1, y), (x+1, y),
                     (x-1, y-1), (x, y-1), (x+1, y-1)]
        over = []
        for number in xrange(len(neighbors)):
            x, y = neighbors[number]
            maxX = self.size - 1
            maxY = self.size - 1
            if x < 0:
                x = maxX
            if y < 0:
                y = maxY
            if x > maxX:
                x = 0
            if y > maxY:
                y = 0
            neighbors[number] = (x, y)
        getPixelColor = self.img.load()
        for (nx, ny) in neighbors:
            ncolor = getPixelColor[nx, ny]
            color = getPixelColor[x, y]
            if ncolor != color:
                return True
        return False
    
    def showMe(self):
        #more PIL stuff
        self.img.show()
        name = "Voronoi_" + self.distType + "_%s_" % (self.seed) + str(self.fValue) + ".png"
        self.img.save(name)

    def totals(self):
        #for diagnostic only
        print "self.def_main =", self.def_main
        print "self.def_findNearestPoints =", self.def_findNearestPoints
        print "self.def_lenght =", self.def_lenght
        print "self.def_generatePoints =", self.def_generatePoints
        print "self.def_getLocation =", self.def_getLocation
        print "self.def_getBlock =", self.def_getBlock
        print "self.def_getBlockStartXY =", self.def_getBlockStartXY
        print "self.def_getBlockEndXY =", self.def_getBlockEndXY
        print "self.def_getBlockID =", self.def_getBlockID
        print "self.def_neighborCheck =", self.def_neighborCheck
        print "self.def_xyPoints =", self.def_xyPoints
        print "self.def_showIt =", self.def_showIt
        print "self.def_draw =", self.def_draw
```**[SIZE=4]Using the Code[/SIZE]**
If you run the VController.py the minimum input
 is:

somename = Voronoi(Somesize)
ex: thing = Voronoi(100)


**blockSize=None**
This sets up the block size for each octave. This must be in list form with every octave that you are going to do accounted for.

Examples 
blockSize=[10] would make octave 1 have a block size of 10
blockSize=[20, 5] would make octave 1 have a block size of 20 and octave 2 would have a block size of 5.
blockSize=[0, 10] would make skip octave 1 and octave 2 would have a block size of 10.
**Note the size of you image must be dividable  by the block sizes. Also you must match the block sizes with your selection of octaves**

**octave=None**
This sets up which octaves will be done. This also must be in list form. 

Examples 
octave=[1] would have one octave and it would have a 1x multiplier in relation to the final image.
octave=[1, .5] would have two octaves with the first having a 1x multiplier and the second octave would have a .5x making it to where it is less visible.
Octave=[2, 0, .2] would make the first octave have a 2x multiplier and then give the third octave a .3x multiplier.
**Note octave must match up with blockSize in the location of all non-zero numbers**

**fValue=None**
This works in the same sort of way as the octave and blockSize. The only difference here is that this is your voronoi math spots. So for example for F1 - F2 you would put fValue=[1,-1].

Other Examples 
fValue=[1] this is the basic voronoi. A value of -1 would invert the coloring of the image.
fValue=[2, 1] this would add F1 and F2 together, but F1 would have a 2x multiplier.
fValue=[-1, 0, 2] this is that same as saying   2(F3) - F1 = end picture.

**clip=0**
This does not quite work right but basically  it clips the top how ever much you set clip to off the image resulting in more areas of pure white. I am currently tring to make it to where it will clip from the bottom as well.

**seed=None**
This sets the seed of  the entire thing so that you have the ability to create the same image over and over.

**distType=&#8221;Linear&#8221;**
This sets how distances are determined. These correspond to the descriptions from above.
Options include:
&#8220;Linear&#8221;
"SqLen"
"Manhattan"
"Chebyshev"
"Quadratic"
"Minkowski"
**Note if you use "Minkowski" you need to set the minkowskiNumber as well.**

**plated=False**
This sets whether or not you want to just see the plated view which makes it pixel the color of the  cell rather than showing how far pixels are from the cells.

**platedColor=True**
This sets whether you want the cells to be in color or greyscale.

**platedLines=False**
If you turn this on then it will return normal Voronoi

**minkowskiNumber=4**
Use this to set the number for Minkowski

Explanation of code coming soon...






Well I guess that is it for now, I have been typing this up for about two hours now so there are probably lots of errors and some things are not done yet, but I hope it helps all the same.

Also Feel free to use anything on this page for whatever you want. I am going to keep this under a "Learners Rights License" Trademark of Chris_0076 *wink* , so if you have read anything on this page you are free to use it in any way you like, claim it as your own, mutilate it, make millions off it, or what have you. My concern is not to be a copyright troll, but rather help others learn something new... and of course hope they pass along something in the same sort of manor because knowledge is wasted if you keep it a secret.

Chris

EDIT oops forgot to attach the code.

---

