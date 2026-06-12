---
title: "Python procedural texture problems. (Voronoi/Worley Noise)"
date: 2010-07-03
forum: Programming Talk
---

### Post by chris_0076 on 2010-07-03
Hey, I have been learning python for a little while now and have just started on some code to generate Voronoi / Worley Noise. I have successfully made a very basic, and to be honest quite awful class that allows generation of the texture.

Now here is where the problem comes in. Anything other than the basic settings or a close variation thereof does not quite come up to par. Examples being changes in the fValue cause weird effects that are not the norm of an F2 of Worley Noise. Also the distances create non-normal patterns... symptoms seem to lead to a problem with number to color conversion. Any ideas?
Goto [http://mines.lumpylumpy.com/Electronics/Computers/Software/Cpp/Graphics/Bitmap/Textures/Noise/Voronoi.php](http://mines.lumpylumpy.com/Electronics/Computers/Software/Cpp/Graphics/Bitmap/Textures/Noise/Voronoi.php) for better examples.

fValue is the number of nearby points to check distance to
points is how many random points to make
 pointsList=[] is if you already have a list of points to use
seed="None" is if you want to use a certain seed
all the rest is pretty self explanatory, but ask if you have any questions

```

import math
import random
import Image
import ImageDraw


class Voronoi:
    def __init__(self, width, height, fValue, points, pointsList=[], seed="None", negative=False, clamp=0):
        self.width = width
        self.height = height
        self.fValue = fValue
        self.pointsList = pointsList
        self.points = points
        self.seed = seed
        self.pixelColorNumbers = range(self.width*self.height)
        self.negative = negative
        self.clamp = clamp
        if self.pointsList == []:
            self.generatePoints(self.points)

    def main(self, distType="Linear"):
        for pixels in xrange(self.width * self.height):
            x, y = self.getLocation(pixels)
            closestCells = self.findNearestPoints(x, y)
            pixelDist = []
            for cellCenter in closestCells:
                cx, cy = cellCenter
                pixelDist.append(self.lenght((x, y), (cx, cy), distType))
                pixelTotal = sum(pixelDist)
                self.pixelColorNumbers[pixels] = pixelTotal
        self.draw()
        
    def findNearestPoints(self, x, y):
        closest = []
        distances = []
        for point in self.pointsList:
            px, py = self.getLocation(point)
            dist = self.lenght((x, y), (px, py))
            distances.append(((dist),(px, py)))
        for number in xrange(self.fValue):
            dist, cords = min(distances)
            closest.append(cords)
            distances.remove((dist,closest[number]))
            tx, ty = closest[number]
        return closest
            
    def lenght(self, (x1, y1),(x2, y2), method="Linear"):
        dx = x2 - x1
        dy = y2 - y1
        if method == "Linear":
            distance = math.sqrt(dx*dx+dy*dy)
        elif method == "SqLen":
            distance = (dx*dx+dy*dy)
        elif method == "Manhattan":
            distance = (dx+dy)
        elif method == "Chebyshev":
            if dx == dy or dx > dy:
                distance = dx
            else:
                distance = dy
        elif method == "Quadratic":
            distance = (dx*dx+dy*dy+dx*dy)
        return distance

    def generatePoints(self, points):
        for number in xrange(points):
            if self.seed != "None":
                random.seed(self.seed)
                self.pointList.append(random.randint(0, self.width * self.height))
                self.seed +=1
            else:
                self.pointsList.append(random.randint(0, self.width * self.height))

    def getLocation(self, number):
        xloc = number % self.width
        yloc = number / self.height
        return (xloc, yloc)

    def draw(self):
        img = Image.new("RGB", (self.width, self.height))
        draw = ImageDraw.ImageDraw(img)
        maxNumber = max(self.pixelColorNumbers) * (1-self.clamp)
        colorSpread = 255 / maxNumber
        for pixel in xrange(self.width * self.height):
            x, y = self.getLocation(pixel)
            color = int(colorSpread * self.pixelColorNumbers[pixel])
            if self.negative == True:
                color = 255 - color
            colorSet = (color, color, color)
            draw.point((x, y), colorSet)
        img.show()
        img.save("here.png")

#Example of how to run
#thing = Voronoi(100, 100, 1, 25, negative=True)
#thing.main()

```[IMG]http://img694.imageshack.us/img694/7982/herez.png[/IMG][IMG]http://img266.imageshack.us/img266/8220/herenegative.png[/IMG]

By the way you will need the Python Imaging Library(PIL) to run it.


Thanks for any and all help,
Chris

PS right now I am working on a griding system to speed it up and so it will have a little more regular results rather than entirely relying on pseudo-chance.

---

### Post by chris_0076 on 2010-07-04
Ok I did a full rewrite of sorts for an algorithm that is about 80-85% faster than before. Although I still have the same sort of problems with the final rendering of it. The ending results for anything other than "Linear" is odd at best, although "Quadratic" and "SqLen" are starting to shape up.

So I guess now I am asking if anyone knows of a better way to normalize the values rather than dividing 255 by the max number...

```

import math
import random
import Image
import ImageDraw

class VoronoiFaster:
    def __init__(self, width, height, fValue, blockSize,
                 pointsList=[], seed="None", negative="False", clip=0):
        self.width = width
        self.height = height
        self.fValue = fValue
        self.pointsList = pointsList
        self.seed = seed
        self.pixelColorNumbers = range(self.width*self.height)
        self.negative = negative
        self.clip = clip
        self.totalBlocks = (height / blockSize) * (width / blockSize)
        self.blockSize = blockSize
        if self.pointsList == []:
            self.generatePoints(self.totalBlocks)
            self.xyPoints(self.pointsList)

    def main(self, distType="Linear"):
        for pixels in xrange(self.width * self.height):
            x, y = self.getLocation(pixels)
            xBlock, yBlock = self.getBlock(x, y)
            neighbors = self.neighborCheck(xBlock, yBlock)
            self.pixelColorNumbers[pixels] = self.findNearestPoints(x, y, neighbors, distType)
        self.draw()
        
    def findNearestPoints(self, x, y, neighbor, distType):
        pixelDist = []
        shortest = []
        for blockCoords in neighbor:
            blockID = self.getBlockID(blockCoords)
            distance =  self.lenght((x, y), self.pointsList[blockID], method=distType)
            pixelDist.append(distance)
        for amount in xrange(self.fValue):
            minNum = min(pixelDist)
            idxNum = pixelDist.index(minNum)
            shortest.append(pixelDist.pop(idxNum))
        final = sum(shortest)
        return final
            
    def lenght(self, (x1, y1), (x2, y2), method="Linear"):
        dx = x2 - x1
        dy = y2 - y1
        if method == "Linear":
            distance = math.sqrt(dx*dx+dy*dy)
        elif method == "SqLen":
            distance = (dx*dx+dy*dy)
        elif method == "Manhattan":
            distance = (dx+dy)
        elif method == "Chebyshev":
            if dx == dy or dx > dy:
                distance = dx
            else:
                distance = dy
        elif method == "Quadratic":
            distance = (dx*dx+dy*dy+dx*dy)
        return distance

    def generatePoints(self, totalBlocks):
        for number in xrange(totalBlocks):
            if self.seed == "None":
                self.seed = random.randint(0, 10000000000000)
            random.seed(self.seed)
            self.pointsList.append((random.randint(0, self.blockSize - 1), random.randint(0, self.blockSize - 1)))
            self.seed +=1

    def getLocation(self, idNumber):
        xloc = idNumber % self.width
        yloc = idNumber / self.height
        return (xloc, yloc)

    def getBlock(self, x, y):
        xblock = x / self.blockSize
        yblock = y / self.blockSize
        return (xblock, yblock)

    def getBlockStartXY(self, ID):
        x = (ID % (self.width / self.blockSize)) * self.blockSize
        y = (ID / (self.height / self.blockSize)) * self.blockSize
        return (x, y)

    def getBlockEndXY(self, ID):
        x = (ID % (self.width / self.blockSize)) * self.blockSize + self.blockSize
        y = (ID / (self.height / self.blockSize)) * self.blockSize + self.blockSize
        return (x, y)

    def getBlockID(self, (xblock, yblock)):
        blockID = yblock * (self.width / self.blockSize) + xblock
        return blockID

    def neighborCheck(self, xblock, yblock):
        neighbors = [(xblock - 1, yblock + 1), (xblock, yblock + 1), (xblock + 1, yblock + 1),
                     (xblock - 1, yblock), (xblock, yblock), (xblock + 1, yblock),
                     (xblock - 1, yblock - 1), (xblock, yblock - 1), (xblock + 1, yblock - 1)]
        for number in xrange(len(neighbors)):
            x, y = neighbors[number]
            maxX = (self.width / self.blockSize) - 1
            maxY = (self.height / self.blockSize) - 1
            if x < 0:
                x = maxX
            if y < 0:
                y = maxY
            if x > maxX:
                x = 0
            if y > maxY:
                y = 0
            neighbors[number] = (x, y)
        return neighbors

    def xyPoints(self, numList):
        for number in xrange(len(numList)):
            x, y = numList[number]
            xB, yB = self.getBlockStartXY(number)
            x = x + xB
            y = y + yB
            numList[number] = (x, y)
            
    def showIt(self, color="color", pointsOn=False, border=False):
        img = Image.new("RGB", (self.width, self.height))
        draw = ImageDraw.ImageDraw(img)
        for number in xrange(len(self.pointsList)):
            start = self.getBlockStartXY(number)
            end = self.getBlockEndXY(number)
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
                draw.point((x, y), fill=(0,0,0))
        img.show()
        img.save("test.png")

    def draw(self):
        img = Image.new("RGB", (self.width, self.height))
        draw = ImageDraw.ImageDraw(img)
        maxNumber = max(self.pixelColorNumbers) * (1-self.clip)
        colorSpread = 255 / maxNumber
        for pixel in xrange(self.width * self.height):
            x, y = self.getLocation(pixel)
            color = int(colorSpread * self.pixelColorNumbers[pixel])
            if self.negative == True:
                color = 255 - color
            colorSet = (color, color, color)
            draw.point((x, y), colorSet)
        img.show()
        img.save("Vornonoi2.png")

#start1 = time.time()
#thing = Voronoi(100, 100, 1, 100)
#thing.main()
#print time.time() - start1
#start2 = time.time()
x = VoronoiFaster(100, 100, 3, 10)
x.main()
#print time.time() - start2
#distType="Linear"
#distType="SqLen"
#distType="Manhattan"
#distType="Chebyshev"
#distType="Quadratic"

```[IMG]http://img153.imageshack.us/img153/2524/vornonoi2.png[/IMG][IMG]http://img815.imageshack.us/img815/3184/vornonoi2neg.png[/IMG]

Anyways thanks for your help,
Chris
14149

PS try className.showIt()  ;)

---

