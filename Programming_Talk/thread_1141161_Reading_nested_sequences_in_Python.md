---
title: "Reading nested sequences in Python"
date: 2009-04-28
forum: Programming Talk
---

### Post by Sparx139 on 2009-04-28
Hi, I'm new to programming, and am having a bit of trouble with nested sequences. I have tried google, but I'm not exactly sure how to refine what I want into a few keywords.

Basically, is there a way to read one entry in each entry in a nested sequence? I'm probably not making sense, so I'll give an example:

```
x=[(1,2),(3,4)]
```

Is there any way to read the second entry out of each tuple this list? To read

```
1,3
``` or ```
2,4
```

To put my problem in context, I'm a school student (Year 12), and I need to write a small program that could be used by a house painter to calculate a cost and give a quote. Here's what I've done so far.

```
#Paint Quote Program 1.1

#Gives a quote for the cost of to paint a house
#based on information given by the user.

print "**************"
print "*Paint Quoter*"
print "**************"

#Set variables
totalcost = 0
#Each room is stored as a tuple, which is stored in this list.
house = []


#Get adress from the user. Adress is constant after it is set.
address = raw_input("What is the Customer's Address?\n")


#keep adding rooms until the user stops

loop = "y"
while loop !="n":
    #Get information about room from the user
    area = int(raw_input("What is the area to be painted in this room?"))
    colour = raw_input("What colour is the paint?")

    #calculates the price of individual room, and
    #adds it to the total cost.
    paintcost = 1
    if colour != "white":
        paintcost = 2
    cost = area * 5 * paintcost
    totalcost += cost

    #Add room information into house
    house += [(area, colour, cost),]

    #querey if there are any more rooms. Break loop if answer is no.
    loop = raw_input("Are there any more rooms? (y/n)")

#confirm details

rooms = len(house)

print house

print "The address is", address
print "Total number of rooms is", rooms
print "The area to be painted in each of the rooms are:\n", house[0:rooms][0]
print "\nThe colours to be painted are:\n", house[0:rooms][1]
print "\nThe costs of each room are:\n", house[0:rooms][2]
print "\nThe total cost is", totalcost


#Write to file
raw_input("Press enter to write to file")
print "Writing to file..."

text_file = open("paintquote.txt", "w")

text_file.write("**************")
text_file.write("*Paint Quoter*")
text_file.write("**************")

text_file.write("Address:\n", address)
text_file.write("\n\nNumber of rooms:", rooms)
text_file.write("Area of each room:\n", house[0:rooms][0])
text_file.write("Colours to be painted in each room:\n", house[0:rooms][1])
text_file.write("Costs of each room:\n", house[0:rooms][2])

text_file.write("\n\nTotal Cost:", totalcost)

```

Here's a simulation:
> 
**************
*Paint Quoter*
**************
What is the Customer's Address?
123 Fake St.
What is the area to be painted in this room?23
What colour is the paint?white
Are there any more rooms? (y/n)y
What is the area to be painted in this room?14
What colour is the paint?red
Are there any more rooms? (y/n)n
[(23, 'white', 115), (14, 'red', 140)]
The address is 123 Fake St.
Total number of rooms is 2
The area to be painted in each of the rooms are:
(23, 'white', 115)

The colours to be painted are:
(14, 'red', 140)

The costs of each room are:
Traceback (most recent call last):
  File "/home/hayden/Desktop/painter.py", line 63, in <module>
    print "\nThe costs of each room are:\n", house[0:rooms][2]
IndexError: list index out of range

So, I can't get it to read the right data in the first place, and then it hits a fatal error.

Can someone please offer a suggestion to the problem? Yes, I know that the input prompts need work (mainly the adding spaces before ending the strings) but I'd like to get the code to work before I polish it.

Thanks for taking the time to read through this.

---

### Post by simeon87 on 2009-04-28
Here's some output from the Python console: to get a value from a tuple, you can either walk over the list and take the appropriate value or you can directly index the value by saying x[0][0] (which means: first element in the list, first value of the tuple).

```

>>> x = [(1,2),(3,4)]
>>> for l, r in x:
...     print l
... 
1
3
>>> for l, r in x:
...     print r
... 
2
4
>>> x[0]
(1, 2)
>>> x[0][0]
1
>>> 

```

So:

```

>>> q = (23, 'white', 115)
>>> q[0]
23
>>> q[1]
'white'
>>> q[2]
115

```

---

### Post by Sparx139 on 2009-04-29
Thanks, that worked beautifully. I took the code and slipped it in in a few places. Here's the fixed code, for anyone viewing:

```
#Paint Quote Program 1.2

#Gives a quote for the cost of to paint a house
#based on information given by the user.

print "**************"
print "*Paint Quoter*"
print "**************"

#Set variables
totalcost = 0
totalarea = 0
#Each room is stored as a tuple, which is stored in this list.
house = []


#Get adress from the user. Adress is constant after it is set.
address = raw_input("What is the Customer's Address?\n")


#keep adding rooms until the user stops

loop = "y"
while loop.lower() !="n":
    #Get information about room from the user
    area = int(raw_input("What is the area to be painted in this room?"))
    colour = raw_input("What colour is the paint?")

    #calculates the price of individual room, and
    #adds it to the total cost.
    paintcost = 1
    if colour.lower() != "white":
        paintcost = 2
    else:
        paintcost = 1
    cost = area * 5 * paintcost
    totalcost += cost
    totalarea += area

    #Add room information into house
    house += [(area, colour, cost),]

    #querey if there are any more rooms. Break loop if answer is no.
    loop = raw_input("Are there any more rooms? (y/n)")

#confirm details

rooms = len(house)
print "\n----------------\nThe address is:", address
print "Total number of rooms is:", rooms
print "The area to be painted in each of the rooms are:\n",
for a, c, m in house:
    print a
print "\nThe colours to be painted are:\n",
for a, c, m in house:
    print c
print "\nThe costs of each room are:\n",
for a, c, m in house:
    print m
print "\nThe total area to be painted is:", totalarea
print "\nThe total cost is:", totalcost

#Write to file
raw_input("\n------------\nPress enter to write to file")
print "Writing to file..."

text_file = open("paintquote.txt", "w")

text_file.write("**************\n")
text_file.write("*Paint Quoter*\n")
text_file.write("**************\n")

text_file.write("Address:\n")
text_file.write(address)
text_file.write("\n\nNumber of rooms:\n")
text_file.write(str(rooms))
text_file.write("\n\nArea of each room:\n")
for a, c, m in house:
    text_file.write(str(a)+", ")
text_file.write("\n\nColours to be painted in each room:\n")
for a, c, m in house:
    text_file.write(str(c)+", ")
text_file.write("\n\nCosts of each room:\n")
for a, c, m in house:
    text_file.write(str(m)+", ")
text_file.write("\n\nTotal area: ")
text_file.write(str(totalarea))
text_file.write("\n\n----------\nTotal Cost:")
text_file.write(str(totalcost))
text_file.close()

print "Done"
```

Now that it works properly, I can go about adding improvements and fixing bugs that don't kill basic functionality.

Thanks again.

---

