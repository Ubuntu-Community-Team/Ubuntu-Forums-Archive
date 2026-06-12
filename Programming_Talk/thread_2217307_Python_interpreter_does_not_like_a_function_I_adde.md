---
title: "Python interpreter does not like a function I added recently."
date: 2014-04-16
forum: Programming Talk
---

### Post by pavelexpertov on 2014-04-16
To cut story short, I made an algorithm, in python 3.3, that packs appropriate boxes into slots that have limited height. After I made the algorithm work, I decided to add another function that would print out a list of boxes in a nice format. However the interpreter does not like it when I import the module. 

```


'''This module solves stack up problem, where you have to use slots with limited height
to pack boxes with different heights.'''

boxList = []
maxVal = 0
rack = []


def help():
    '''Method used to display commands to the user.'''
    print('addItem(name, size) -- Add a box to a list, with name and size.')
    print('wipeList() -- wipes a list of boxes.')
    print('setMaxVal -- set maximum height for slots')
    print('setDefault -- set default list of boxes and maximum size for the slot')

def addItem(name, num):
    '''Creates boxes and add them to the list'''    
    #I can not use append with name and num. Create a list and then import
    #it into origList. Also a number is put first then followed by name,
    #because sort() method only sorts the first element of a nested list.
    box = [num, name]
    boxList.append(box)

def wipeList():
    '''wipes list and maximum height of slots''' 
    del boxList[:]
    global maxVal
    maxVal = 0

def setMaxVal(num):
    '''Sets maximum height for slots'''
    global maxVal
    maxVal = num

def setDefault():
    #READ Note2 on why using global and non local keywords.
    global boxList
    global maxVal
    #The reason for using putting size first then name of boxes, because the list's sort method
    #does not look at second element of nested lists but at first, therefore, it can not sort 
    #string letters.
    boxList = [[8, 'A'], [7, 'B'], [4, 'C'], [9, 'D'], [6, 'E'], [9, 'F'], [5, 'G'], [5, 'H'], \
[6, 'I'], [7, 'J'], [8, 'K']]
    maxVal = 15

def printBoxList():
    print('Here is a list of boxes and their sizes')
    print('Name    Size')
    for i in boxList:
        print('{0}    {1}'.format(i[1], i[0])

def calculate():

    printBoxList()
    origList = boxList
    leftList = []
    rackSpace = []
    x = 0
    y = 0
    
    origList.sort()
    
    #Index method does not find anything when skimming through nested lists.
    
    #It's better to use counter, which can be created through a second variable in
    #the for statements and assign to a separate variable.

    for startCounter in range(len(origList)):
        x = origList[startCounter]
        for endCounter in reversed(range(len(origList))):
            y = origList[endCounter]
            #Checks that y's value position is not behind the x's value position            
            #If true, the loop is broken so x gets a new value.            
            if endCounter <= startCounter:
                break
            #If y's value is zero, it gets changed in next iteration.
            if y[0] == 0:
                continue
            if (x[0] + y[0]) == maxVal:
                #x and y values are added to one list separately and then added to rackSpace.s
                #This is because it adds separate boxes into slots, which represent index positions 
                #of real ones. 
                list = []
                list.append(str(x))
                list.append(str(y))
                rackSpace.append(list)
                x[0] = 0
                y[0] = 0
                break
        
    #leftList takes left over boxes
    leftList = [x for x in origList if x[0] != 0]
    if leftList != 0:
        numList = [] #Takes boxes that add up to oldVal
        newVal = 0
        oldVal = 0
        x = 0
        y = 0
        for startCounter in range(len(leftList)):
            x = leftList[startCounter]
            if x[0] == 0:
                continue
            numList.append(str(x))
            for endCounter in reversed(range(len(leftList))):
                y = leftList[endCounter]
                if endCounter <= startCounter:
                    rackSpace.append(numList) #adds x and other values to rackSpace slot
                    break
                if y[0] == 0:
                    continue
                if newVal == 0:
                    newVal = x[0] + y[0]
                elif newVal > 0:
                    newVal = oldVal + y[0]

                if newVal <= maxVal:
                    oldVal = newVal
                    numList.append(str(y))
                    y[0] = 0
                else:
                    rackSpace.append(numList)
                    newVal = 0
                    oldVal = 0
                    numList = []
                    break

    for i in range(len(rackSpace)):
        print('Slot:', (i + 1), 'is filled up with', rackSpace[i])



```

When I added printBoxList() to calculate method, I got this syntax error:
```

>>> import stackUp
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "./stackUp.py", line 60
    def calculate():
      ^
SyntaxError: invalid syntax

```

I have tried to move functions around and then the interpreter was complaining about 'end of line' error. Can anyone help me on this, because I find it very weird for me? Thank you.

PS. Can anyone advise me on how to improve this code, because I am newbie to python? Furthermore, I do not understand what causes EOF syntax errors.

---

### Post by steeldriver on 2014-04-16
unbalanced parentheses maybe ... ?

```

        print('{0}    {1}'.format(i[1], i[0])

```

---

### Post by pavelexpertov on 2014-04-17
Thank you for pointing out, silly me though :P!!!

---

