---
title: "[Python] Minesweeper Solver"
date: 2009-10-08
forum: Programming Talk
---

### Post by Pyro.699 on 2009-10-08
So its one of those lazy Thursday evenings and i have all the time in the world to waste away on pointless tasks. I'm currently out of projects and started to play minesweeper; I then thought that i could entertain myself by making a program to solve the game.

So what i have so far is 2 variables (or rather after some calculations the two variables):

[php]
grid = {'top': None, 'bottom': None, 'left': None, 'right': None, 'topLeft': None, 'topRight': None, 'bottomLeft': None, 'bottomRight': None}
[/php]and

[php]game = [
['-', '-', '-', '-', '-', '-', '-', '1', ' ', ' ', ' ', ' ', ' ', ' '],
['-', '-', '-', '-', '-', '-', '-', '1', '1', '1', '1', ' ', ' ', ' '],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '2', ' ', '1', '1'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '2', ' ', '1', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '3', '1', '2', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['1', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-']]
[/php]Now, ive looked at several online programs that people have already used. I turned on wine and looked at [this one]("http://www.wsdh.org/?minesweeper").

I know that **game[2][9]** and **game[3][13]** are defiantly mines; using an algorithm i can get the mines surrounding those two areas.
[php]
//grid for game[2][9]
{'topLeft': '1', 'right': '2', 'bottomLeft': '-', 'bottomRight': '2', 'bottom': '-', 'top': '1', 'topRight': '1', 'left': '-'}

//grid for game[3][13]
{'topLeft': '1', 'right': None, 'bottomLeft': '2', 'bottomRight': None, 'bottom': '-', 'top': '1', 'topRight': None, 'left': '1'}
[/php]
I think i should be heading in a different direction but im not too sure. I'm still gonna work on this while i wait for a response, but id like some help/ideas from you guys :)

Thanks a ton
~Cody Woolaver

---

### Post by tgalati4 on 2009-10-08
The game "mines" is open source under the GPL, so I would first look at that.

Then I would write pseudo code to explore the minefield and post the pseudo code. 

Then others can suggest the most elegant code to solve the explore problem.

---

### Post by Pyro.699 on 2009-10-08
What do you mean by *pseudo code* because i already have the minefield saved to a 2-dimensional array.

---

### Post by Tony Flury on 2009-10-09
Pseudo code is effectively high level code written in almost english (or your native language) the described how you would solve the problem.

For instance the Pseudo code for a sort algorithm might be 

```

Find the item in the center of the field
Move all the items lower than the center item above it 
Move all the items higher than the center item below it
Take the section above the center, and treat that like a new field and repeat.
Take the section below the center, treat that like a new field and repeat.

```

No code, but it does explain (sort of) how you solve the problem.

---

### Post by Pyro.699 on 2009-10-09
*facepalm* Right, somehow i knew that

So i was thinking about this all night and came up with a method; although im not to sure about how well it will work. For reference i have a function GetSurroundings which will return the grid variable that's in my first post; so getting the boxes that are directly touching it are not a problem.

Here was my idea:

1)Take the game array and squish it down to a 5x5 grid
```

game = [
['1', ' ', ' ', ' ', ' '],
['1', '1', '1', '1', ' '],
['-', '-', 'W', '2', ' '],
['-', '-', '-', '2', ' '],
['-', '-', '-', '3', '1']]
//W stands for the squre we are analyzing

```2) Analyze each individual square directly touching ***W*** and their surroundings; squish to a 3x3 grid
_Top_ [B]1
[/B]```

 game = [
 [' ', ' ', ' '],
 ['1', '1', '1'],
 ['-', 'W', '2']
  //W stands for the squre we are analyzing
 
```There are 2 blank squares that 1 is touching.
Odds = 1/**2***100% = **50%**

_TopLeft_ [B]1
[/B]```

 game = [
 [' ', ' ', ' '],
 ['1', '1', ' '],
 ['W', '2', ' ']
  //W stands for the squre we are analyzing
 
```There are 2 blank squares that 1 is touching.
Odds = 1/**1***100% = **100%**

Since we came to a block where the prediction is **100%** we can stop checking and make the assumption that the block is a mine.

3) Process the clicking event that would mark the tile as a mine.

So thats what i have so far, can anyone see a problem with that?

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2009-10-09
My apologies for the double post; but the ideas in this post are quite different from the ones in my previous post.

I have got quite a bit of work done on my own; but have hit a snag that i need some actual programming help with. Here is what i have so far.

[php]
def inArray(needle, haystack):
    for item in haystack:
        if item == needle: return True
    return False
    
def GetSurroundings(main, current_pos):
    #Current location within the master array
    x = current_pos[0]
    y = current_pos[1]
    
    #The width and length of the master array
    width = len(main[0])
    height = len(main)
    
    grid = {'top': None, 'bottom': None, 'left': None, 'right': None, 'topLeft': None, 'topRight': None, 'bottomLeft': None, 'bottomRight': None}
    
    #All of the specially asigned values. If the value excedes the limit of the graph it will remain as None
    if x-1>=0: grid['top'] = {'val': main[x-1][y+0], 'y': "y+0", 'x': "x-1"}
    if x+1<width: grid['bottom'] = {'val': main[x+1][y+0], 'x': "x+1", 'y': "y+0"}
    if y-1>=0: grid['left'] = {'val': main[x+0][y-1], 'x': "x+0", 'y': "y-1"}
    if y+1<height: grid['right'] = {'val': main[x+0][y+1], 'x': "x+0", 'y': "y+1"}
    if x-1>=0 and y-1>=0: grid['topLeft'] = {'val': main[x-1][y-1], 'x': "x-1", 'y': "y-1"}
    if x-1>=0 and y+1<height: grid['topRight'] = {'val': main[x-1][y+1], 'x': "x-1", 'y': "y+1"}
    if x+1<width and y-1>=0: grid['bottomLeft'] = {'val': main[x+1][y-1], 'x': "x+1", 'y': "y-1"}
    if x+1<width and y+1<height: grid['bottomRight'] = {'val': main[x+1][y+1], 'x': "x+1", 'y': "y+1"}
    
    return grid
def GetSubGrid(main, centerPos, padHeight, padWidth):
    #The width and height of the working array
    curWidth = len(main[0])
    curHeight = len(main)
    #The position within  working array. Will be the center
    curX = centerPos[0]
    curY = centerPos[1]
    
    ret = []
    
    #Create the array. 
    #The height will be twice the padding height + the center block
    for y in range(0, 2*padHeight+1):
        ret.insert(y, [])
        #The width will be twice the padding width + the center block
        for x in range(0, 2*padWidth+1):
            ret[y].insert(x, None)
    
    #Need the starting position so to properly assign in the return array
    baseX = curX - padWidth
    baseY = curY - padHeight
    
    for y in range(curY-padHeight,curY+padHeight+1):
        for x in range(curX-padWidth,curX+padWidth+1):
            xReal = x-curX-padWidth
            yReal = y-curY-padHeight
            
            #Aslong as the values dont excede the bounds of the original array, insert.
            if (x >= 0 and x < curWidth) and (y >= 0 and y < curHeight):
                ret[y-baseY][x-baseX] = main[y][x]
    
    return ret

game = [
[' ', ' ', ' ', '1', '-', '-', '-', '-', '-', '-', '-', '-', '1', ' '],
[' ', '1', '1', '3', '-', '-', '-', '-', '-', '-', '-', '-', '2', '1'],
['1', '2', 'M', '2', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['2', 'M', '4', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '1', '1', '2', '-', '-'],
['-', '-', '-', '-', '-', '-', '3', '2', '2', '1', ' ', '1', '-', '-'],
['-', '-', '1', '2', '4', 'M', '2', ' ', ' ', ' ', ' ', '1', '-', '-'],
['-', '-', '1', ' ', '1', '1', '1', '1', '1', '1', ' ', '1', '-', '-'],
['-', '-', '2', ' ', ' ', ' ', '1', '-', '-', '2', ' ', '1', '1', '1'],
['-', '-', '2', ' ', ' ', ' ', '1', '-', '-', '2', ' ', ' ', ' ', ' '],
['-', '-', '3', '1', ' ', ' ', '1', '-', '-', '2', ' ', '1', '1', '1'],
['-', '-', 'M', '2', '2', '2', '1', '-', '-', '2', '1', '2', '-', '-'],
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-']]


for y in range(0, len(game)):
    for x in range(0, len(game[0])):
        #Get a 5x5 grid with x,y as the center point
        sg1 = GetSubGrid(game, [x,y], 2, 2)
        
        #Make sure the block is one that we are unsure of.
        #Not a number, blank space or a mine.
        if sg1[2][2] != "-": continue
        
        ##DEBUG
        #Symbolize the area we are working on with an X
        sg1[2][2] = "X"
        
        #Work on just 1-3 of the first sub grid
        for y2 in range(1, len(sg1)-1):
            for x2 in range(1, len(sg1[0])-1):
                #Now get a 3x3 grid using the 5x5 grid as the starting point
                sg2 = GetSubGrid(sg1, [y2,x2], 1,1)
                #Get the surrounding blocks
                grid = GetSurroundings(sg2, [1,1])
                
                #There are currently no (known) blank blocks
                blank = 0
                val = sg2[1][1]
                
                #We dont want to analize anything but a number
                if val == None: continue
                if not inArray(val, ["1", "2", "3", "4", "5", "6", "7"]): continue
                
                val = int(val)
                for pos in grid:
                    if grid[pos]['val'] == "-" or grid[pos]['val'] == "X":
                        #Blank tile found
                        blank += 1.0
                    if grid[pos]['val'] == "M":
                        #Already a mine present; subtract one from the value to compensate
                        val -= 1
                if blank != 0:
                    if int(val)/blank == 1: #100% chance of a mine being present. DONT CLICK
                        game[y][x] = "?"
                    if int(val)/blank <= 0: #0% chance of a mine being present. SAFE
                        game[y][x] = "C"
                        
#Print out the gameboard with the safe and hot spots marked                        
for xx in game:
    print xx
[/php]

That will print out
```

[' ', ' ', ' ', '1', '-', '-', '-', '-', '-', '-', '-', '-', '1', ' ']
[' ', '1', '1', '3', '-', '-', '-', '-', '-', '-', '-', '-', '2', '1']
['1', '2', 'M', '2', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-']
['2', 'M', '4', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-']
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-']
['-', '-', '-', '-', '-', '-', '-', '?', '?', '1', '1', '2', '-', '-']
['-', '-', '-', '?', '?', '?', '3', '2', '2', '1', ' ', '1', '-', '-']
['-', '-', '1', '2', '4', 'M', '2', ' ', ' ', ' ', ' ', '1', '-', '-']
['-', '-', '1', ' ', '1', '1', '1', '1', '1', '1', ' ', '1', '?', '?']
['-', '-', '2', ' ', ' ', ' ', '1', 'C', '?', '2', ' ', '1', '1', '1']
['-', '-', '2', ' ', ' ', ' ', '1', '?', '?', '2', ' ', ' ', ' ', ' ']
['-', '-', '3', '1', ' ', ' ', '1', '?', '?', '2', ' ', '1', '1', '1']
['-', '-', 'M', '2', '2', '2', '1', '?', '-', '2', '1', '2', '?', '?']
['-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-', '-']

```

If you look at 8-12 & 8-13 (remember, treating these as arrays (starting at 0)) it states that both of them are "defiantly" mines. The fact of the matter is that 8-12 [COLOR=Red]**is a mine**[/COLOR] and 8-13 [COLOR=Green]**is not a mine**[/COLOR]. Another area is the one surrounding the C (which represents **[COLOR=RoyalBlue]Safe to Click[/COLOR]**) is very messy. A 2 with 3 mines, and also a 1 with 3 marked mines.

Hope everything I've said makes sense^^

Thanks
~Cody Woolaver

---

### Post by Arndt on 2009-10-09
> **Pyro.699 said:**
> My apologies for the double post; but the ideas in this post are quite different from the ones in my previous post.

I have got quite a bit of work done on my own; but have hit a snag that i need some actual programming help with. Here is what i have so far.



If you look at 8-12 & 8-13 (remember, treating these as arrays (starting at 0)) it states that both of them are "defiantly" mines. The fact of the matter is that 8-12 [COLOR=Red]**is a mine**[/COLOR] and 8-13 [COLOR=Green]**is not a mine**[/COLOR]. Another area is the one surrounding the C (which represents **[COLOR=RoyalBlue]Safe to Click[/COLOR]**) is very messy. A 2 with 3 mines, and also a 1 with 3 marked mines.

Hope everything I've said makes sense^^

Thanks
~Cody Woolaver

Insert some trace output statements to see why one of the points is given mine status although it shouldn't. Either work forward, or backward from the known faulty point in the code. Cutting down the array may help while looking for the problem.

---

### Post by Pyro.699 on 2009-10-09
I inserted this line after it checks if it is 100% a mine:
[php]
if x == 8 and y == 11:
        print
        for xx in sg2:
             print xx
         print
[/php]

Then got this:
```

['?', '2', ' ']
['X', '2', ' ']
['-', '2', '1']

```

I'm still unsure where i need to head with this >< i know ill hie myelf when i figure it out... ^^;

Thanks again
~Cody

---

### Post by unutbu on 2009-10-09
[list]
[*] I wonder if perhaps modifying game while you loop through may be messing things up.
First game[8][12] is being marked '?', and then game[8][13] is being analyzed. 
game[9][13] should be seeing blank=2, val=1, but perhaps it is seeing blank=1,val=1 because game[8][12] has been altered?

[*]If you had a wall of 1's and 2's:
```

['','',  '', '', '']
['1','2','1','2','1']
```

Then the program should figure out that you have mines here:
```

['?','', '?', '', '?']
['1', '2','1','2','1']
```

My rough understanding suggests blank will equal 3 and val will equal 1 or 2, so no conclusion will be drawn from your algorithm, when in fact, mine positions can be deduced.

[/list]

---

### Post by Pyro.699 on 2009-10-09
GOT IT!

When the program checks for a mine already beside a value, then compensates.. it didn't take into account ones that it already predicted.

Basically i changed:
[php]
if grid[pos]['val'] == "M":
[/php]
into
[php]
if grid[pos]['val'] == "M" or grid[pos]['val'] == "?":
[/php]I have played several games of minesweeper, by hand only moving where the program tells me too, and it seems to work out fine :)

Thanks for all your help :3
~Cody

---

### Post by Pyro.699 on 2009-10-10
Alright, so the program seems to run fine for now except in one area... When given a situation where there are no guarenteed spots that it is a mine or it is safe it has to take a guess... My current method is to pick the one with the lowest odds of being a mine; its at that point that i lose a lot of my games, is there any other method you guys could think of that would help make the "random" picking a bit more accurate?

Thanks
~Cody

---

### Post by tgalati4 on 2009-10-11
I think that's the whole point of the game.  Even with "perfect" play, you run into situations where you have to make a guess.  I would be curious to know if there is a mathematical expression that estimates that probability.  Once you have that, you evaluate the remaining squares and use the lowest probability as your next guess.

In its simplist form:

Number of mines discovered/Number of mines in the game
Spread equally:  divide the above by the number of open squares remaining
Use that as a baseline probability then add to it the probability factors for gaining additional information.

For instance, clicking in the middle of a field will have the same probability as clicking in a corner, but you gain additional information in a corner because of the limits of the sides.  This narrows the selection and delineates the mines faster than simply clicking in the middle of the field.

So using this basic theory, you would proceed along sides and edges and work your way around the existing field to maximize the information gained from each guess.

ps:  Writing pseudo code can help others visualize your problem.  We think and solve problems in different ways.

---

### Post by unutbu on 2009-10-11
Given a game array, generate a dict, vals, which maps sets of points to number
of known mines.

```
For each pair of sets(*), A and B:
    Generate

    C1 = A intersect B
    C2 = A - C1
    C3 = B - C2

    Store the equations

    vals[C1] >= 0
    vals[C2] >= 0
    vals[C3] >= 0
    vals[C1] <= len(C1)
    vals[C2] <= len(C2)
    vals[C3] <= len(C3)
    vals[C1] + vals[C2] = vals(A)
    vals[C1] + vals[C3] = vals(B)
    vals[C1],vals[C2],vals[C3] must be integers.
```

Solve the equations subject to the constraints. I think this reduces it (haha) to an integer linear programming problem. ([http://en.wikipedia.org/wiki/Linear_programming#Integer_unknowns](http://en.wikipedia.org/wiki/Linear_programming#Integer_unknowns))

(*)Actually, come to think of it, taking pairs of sets may not be good enough. You may have to take the intersection of triplets, and quadruplets, etc... Whatever it takes to make them all pairwise disjoint.

Once you solve the equations you could look for sets with only one elements whose value is known to be 0 (is clear) or 1 (has mine). If there are no singleton sets, then the next best thing would be to look for the set with the smallest probability of having a mine. The probability would be given by vals[C]/len(C).

---

### Post by Pyro.699 on 2009-10-15
I'm not quite sure exactly what you mean; but it sounds like you had included steps to recalculate everything. The way that i think of it is you should be able to have a basepoint for the chances.

Count the number of mines found **A**
Count the number of total plausible mines **B**
Count the number of blank spaces **C**

Now; im not sure if this makes and sense so please correct me if i am wrong.

The number of mines left will be **B-A** so the chances that ANY blank space will be a mine is **(B-A)/C**. That would be a base point. Then we can run the main algorithm that we used to calculate the surrounding odds. Something thats puzzling me is weather or not we add our calculated value to the base point for blank tile. Or do we let the script rewrite that value.

First Example:
```

['2', '3', '2', '1', '0', '0', '1', '1', '2', 'M', 'M', '2', '0', '0']
['M', 'M', 'M', '2', '1', '0', '1', 'M', '2', '3', 'M', '2', '0', '0']
['-', '-', '4', 'M', '3', '2', '2', '1', '1', '1', '2', '2', '1', '0']
['-', '-', '4', '4', 'M', 'M', '2', '1', '1', '1', '2', 'M', '2', '1']
['1', '2', 'M', 'M', '3', '2', '2', 'M', '1', '1', 'M', '4', 'M', '1']
['1', '2', '2', '2', '1', '0', '1', '2', '3', '4', '4', 'M', '4', '3']
['M', '1', '0', '0', '0', '0', '0', '2', 'M', 'M', 'M', '4', 'M', 'M']
['2', '2', '1', '0', '1', '1', '1', '2', 'M', '5', 'M', '3', '3', '3']
['1', 'M', '2', '1', '2', 'M', '2', '1', '1', '2', '2', '2', '2', 'M']
['1', '2', 'M', '3', '4', 'M', '2', '0', '0', '0', '1', 'M', '2', '1']
['0', '1', '2', 'M', 'M', '3', '2', '1', '0', '1', '2', '2', '1', '0']
['0', '0', '1', '2', '2', '2', 'M', '1', '0', '1', 'M', '1', '0', '0']
['0', '1', '1', '2', '1', '3', '2', '2', '0', '1', '1', '1', '1', '1']
['0', '1', 'M', '2', 'M', '2', 'M', '1', '0', '0', '0', '0', '1', 'M']

```There is a total of **40** mines and we have already found **39**. The script would pick either **1-2** or **1-3** with a **50% / 50%** accuracy. There are only 4 tiles left, so if we isolated those 4 tiles we could get a percent grid like this:
_Without adding the base number_
```

['?.??', '0.5']
['?.??', '0.5']

```_With the base number_
```

['0.25', '0.75']
['0.25', '0.75']

```Another example:
```

['1', '1', '3', 'M', '2', '0', '0', '0', '0', '0', '2', 'M', '-', '-']
['2', 'M', '5', 'M', '3', '0', '0', '0', '0', '0', '2', 'M', '-', '-']
['2', 'M', '4', 'M', '2', '0', '0', '0', '0', '0', '2', '3', '-', '-']
['1', '2', '4', '3', '2', '0', '0', '1', '1', '1', '1', 'M', '-', '-']
['0', '2', 'M', 'M', '1', '1', '1', '2', 'M', '1', '1', '3', '-', '-']
['0', '2', 'M', '3', '1', '1', 'M', '2', '1', '1', '0', '2', '-', '-']
['0', '1', '1', '2', '1', '2', '1', '2', '1', '1', '1', '2', '-', '-']
['0', '0', '0', '1', 'M', '3', '2', '3', 'M', '3', '2', 'M', '-', '-']
['0', '0', '0', '1', '2', 'M', 'M', '3', 'M', '-', '-', '-', '-', '-']
['1', '1', '0', '1', '2', '4', '3', '3', '3', '-', '-', '-', '-', '-']
['M', '1', '0', '1', 'M', '2', 'M', '3', '3', '-', '-', '-', '-', '-']
['1', '1', '0', '1', '1', '2', '2', 'M', 'M', '-', '-', '-', '-', '-']
['0', '0', '0', '0', '0', '1', '2', '4', '-', '-', '-', '-', '-', '-']
['0', '0', '0', '0', '0', '1', 'M', '2', '-', '-', '-', '-', '-', '-']

```There is a total of **40** mines and we have already found **25**. The script would pick position **12-1** with a **33.33%** accuracy.  If we were to take into consideration the other tiles we would get **(40-25)/48** which is **31.25%** that might not be that much of a differance but it could still have a bigger impact on other examples.


So im not really sure if what i said made any sense, but if it did please let me know :)

Thanks
~Cody Woolaver

---

### Post by gil_johnson on 2009-10-16
Hi,
I know this is late (solved) but I don't see mention of this in the posts here - I stumbled across a number of pages like the following:[B]
Minesweeper is NP complete![/B]
[http://for.mat.bham.ac.uk/R.W.Kaye/minesw/ordmsw.htm](http://for.mat.bham.ac.uk/R.W.Kaye/minesw/ordmsw.htm)
Gil

---

### Post by Pyro.699 on 2009-10-16
I probably should un-mark that, but thank you for that page, i will read it now; it looks interesting.

---

### Post by Pyro.699 on 2009-10-26
Alright, so I'm still working on this project. I even created a game generator (attached below); it has a lot of redundant calculating and process usage but it gets the job done (just make a folder called ***MineSweeperGames*** in the same folder)

My current work for the player is also attached. Although it is still quite buggy and it will only run ***MineSweeper.0001*** for now.

The reason for this reply is i ran into a rather difficult bug; below is the real game and the calculated one.
[U][I][B]
REAL[/B][/I][/U]
```

['1', '1', '1', '0', '1', '1', '1', '0', '0', '1', '*', '1', '0', '0']
['1', '*', '1', '0', '1', '*', '2', '1', '1', '2', '2', '2', '0', '0']
['1', '2', '2', '1', '1', '2', '3', '*', '1', '1', '*', '1', '0', '0']
['0', '1', '*', '2', '1', '2', '*', '2', '1', '1', '1', '1', '0', '0']
['0', '2', '2', '3', '*', '2', '1', '1', '0', '0', '0', '0', '0', '0']
['1', '2', '*', '3', '2', '1', '0', '0', '1', '2', '2', '2', '1', '1']
['*', '2', '2', '*', '2', '1', '0', '0', '1', '*', '*', '2', '*', '1']
['1', '1', '2', '4', '*', '2', '0', '1', '3', '4', '3', '2', '1', '1']
['1', '1', '3', '*', '*', '3', '0', '1', '*', '*', '2', '2', '3', '2']
['1', '*', '4', '*', '*', '3', '0', '1', '2', '2', '2', '*', '*', '*']
['1', '2', '*', '6', '*', '3', '0', '0', '0', '1', '2', '4', '4', '3']
['0', '2', '3', '*', '*', '2', '0', '0', '0', '2', '*', '4', '*', '3']
['1', '3', '*', '4', '2', '1', '0', '1', '1', '3', '*', '5', '*', '*']
['1', '*', '*', '2', '0', '0', '0', '1', '*', '2', '1', '3', '*', '*']

```

[I][U][B]CALCULATED
[/B][/U][/I]```

['1', '1', '1', '0', '1', '1', '1', '0', '0', '1', '*', '1', '0', '0']
['1', '*', '1', '0', '1', '*', '2', '1', '1', '2', '2', '2', '0', '0']
['1', '2', '2', '1', '1', '2', '3', '*', '1', '1', '*', '1', '0', '0']
['0', '1', '*', '2', '1', '2', '*', '2', '1', '1', '1', '1', '0', '0']
['0', '2', '2', '3', '*', '2', '1', '1', '0', '0', '0', '0', '0', '0']
['1', '2', '*', '3', '2', '1', '0', '0', '1', '2', '2', '2', '1', '1']
['*', '2', '2', '*', '2', '1', '0', '0', '1', '*', '*', '2', '*', '1']
['1', '1', '2', '4', '*', '2', '0', '1', '3', '4', '3', '2', '1', '1']
['1', '1', '3', '*', '*', '3', '0', '1', '*', '*', '2', '2', '3', '2']
['-', '-', '-', '-', '*', '3', '0', '1', '2', '2', '2', '*', '*', '*']
['-', '2', '-', '-', '*', '3', '0', '0', '0', '1', '2', '4', '4', '3']
['-', '-', '3', '*', '*', '2', '0', '0', '0', '2', '*', '4', '*', '3']
['-', '-', '*', '4', '2', '1', '0', '1', '1', '3', '*', '5', '*', '*']
['-', '-', '*', '2', '0', '0', '0', '1', '*', '2', '1', '3', '*', '-']

```

_**Problem 1**_
Regardless how many times i run the program i eventually get to this point and it will pick **2-10** with a **25%** chance of it being a mine. From the pre-calculated board we are able to tell that it is in fact a mine. The default set number of mines is **40** so we know that there are **5** left and **9** safe spaces. _So how would i go about telling it to pick something other than **2-10**_

_**Problem 2**_
If you look in the bottom right hand corner you can see how there is a blank tile surrounded by 3 mines. _What would i do to tell the program to take that into account?_ It is in fact a mine.

Thanks again for all your help guys :)
~Cody

P.S. - Feel free to go through the code and offer tips & suggestions, I'm always looking for ways to improve my code!

---

