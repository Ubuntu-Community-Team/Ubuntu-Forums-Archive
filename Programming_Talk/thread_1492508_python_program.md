---
title: "python program"
date: 2010-05-24
forum: Programming Talk
---

### Post by flyingsliverfin on 2010-05-24
i've made a program that should technically reflect any point you input over any line that you input through two points:
```

#! /bin/usr/python

coordList = []
coordOne = raw_input('enter the first coordinate of the line of reflection: ')
coordTwo = raw_input('enter the second coordinate of the line of reflection; ')
flipCoord = raw_input('enter coordinate you want to reflect: ')
coord = [coordOne, coordTwo, flipCoord]
for y in coord:
    for x in y:
        if x.isdigit() == True:
            coordList.append(x)
slope = (float(coordList[1]) - float(coordList[3]))/(float(coordList[0]) - float(coordList[2]))
perpslope = -(1/(slope))

x1 = coordList[0]
y1 = coordList[1]
b1 = float(y1) - (slope * float(x1)) 
x2 = coordList [4]
y2 = coordList [5]
b2 = float(y2) - (perpslope * float(x2))

midptx = (b2 - b1)/(slope - perpslope)
midpty = (slope * midptx) + b1



finalx = (2 * midptx) - float(x2)
finaly = (2*midpty) - float(y2)

print 'the result is: (',finalx,finaly, ')'

```

I just want to know if this would work reliably, because its difficult to test points by nand and compare with the results my program got to see if it works.

i realize it only works for single digit points right now

---

### Post by Tony Flury on 2010-05-25
You could try exceptions to trap non integer input

```

try:
    a = int(raw_input("Give me a number"))
except VALUE_ERROR:
    print "I said a number dummy"

```

---

### Post by flyingsliverfin on 2010-05-25
i was thinking more along the lines of check for a number, then check for the next character that isn't a number and all the characters inbetween.

i dont know how to use try and except, for now i'll stick with what i know

---

### Post by flyingsliverfin on 2010-05-25
heres my updated version:
```
#! /bin/usr/python

number = ''
coordList = []
coordOne = raw_input('enter the first coordinate of the line of reflection: ')
coordTwo = raw_input('enter the second coordinate of the line of reflection; ')
flipCoord = raw_input('enter coordinate you want to reflect: ')
coord = coordOne + ',' + coordTwo + ',' + flipCoord + ','
for y in coord:																				 
		if y == '-' or y.isdigit() == True:					 
			number = number + y							
		else:											
			if number != '':							
				coordList.append(number)				
				number = ''								

slope = (float(coordList[1]) - float(coordList[3]))/(float(coordList[0]) - float(coordList[2]))  
perpslope = -(1/(slope))																		 

x1 = coordList[0]
y1 = coordList[1]
b1 = float(y1) - (slope * float(x1)) 			
x2 = coordList[4]
y2 = coordList[5]
b2 = float(y2) - (perpslope * float(x2))		



midptx = (b2 - b1)/(slope - perpslope) 		
midpty = (slope * midptx) + b1					


finalx = (2 * midptx) - float(x2)				
finaly = (2*midpty) - float(y2)					

print '\nthe result is: (',finalx, ',',finaly, ')','\n'
                      
                
```

---

### Post by Tony Flury on 2010-05-26
> **flyingsliverfin said:**
> 
i dont know how to use try and except, for now i'll stick with what i know

I just showed you how to use try - now would be a good time to learn :-)

```

def isInteger( value ):
   try:
      a = int( value)
   except VALUE_ERROR:
      return False
   else:
      return True

```
That function should check if the value is a valid integer value - you can do something similar with float if you need to. Far better than checking each character.

---

### Post by flyingsliverfin on 2010-05-29
sorry, im not sure i understand.

wouldnt u have to feed every character into 'value' with a loop or something?

how is it possible without checking every character?
it seems to me like u'd need to check each character with the int...

---

### Post by simeon87 on 2010-05-29
> **flyingsliverfin said:**
> sorry, im not sure i understand.

wouldnt u have to feed every character into 'value' with a loop or something?

how is it possible without checking every character?
it seems to me like u'd need to check each character with the int...

The int function takes care of that:

```

>>> int("12345")
12345
>>> int("12345fail")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: '12345fail'

```

If the string can be converted to an integer, it will do so but if it contains any invalid character, it will throw a ValueError. The try/except is designed to catch that and to return True or False depending on whether int succeeded in converting it to an integer.

---

### Post by flyingsliverfin on 2010-05-30
k i get that now, but i dont think that would work the way i wanted it to. i intended the user to be able to enter any two numbers in any format, and my program picks out the numbers. so for instance if these are the input examples:
(1,1)
coordOneiIs2coordTwoIs-10
123and83
x:8andy:91

then my program finds and picks  out the numbers. i think my way that checks each character is more flexible too.

so as far as i can see the try,except concept wouldnt work with those inputs unless im not seeing something i should be.

---

### Post by Tony Flury on 2010-05-30
Why are you insisting on making the input so complicated ? Most computer programs would not accept input that complicated - but they would reject it, and remind the user that the program only wants a number. In fact most users would not expect to be able to provide complex input like that, and allowing it causes you problems : for instance you would allow : coordOneiIs2coordTwoIs-10 as an input, what about : coord1iIs2coord2Is-10 - that makes sense (same as the first example) but would get read completely differently - and what about coordTwoiIs2coordOneIs-10 - how do you interpret that ?

Keep your program simple - simple to use, simple to code - and use the computer capabilities (in this case to change strings to numbers) to your advantage.

---

