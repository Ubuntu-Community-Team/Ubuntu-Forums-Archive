---
title: "Can you make a more elegant solution? (Python)"
date: 2007-08-24
forum: Programming Talk
---

### Post by triptoe on 2007-08-24
first of all i am not trying to say this solution *IS* elegant.. i am just curious of how i could do it better since I am a begginer. It is problem #11 from the euler site here:

[http://projecteuler.net/index.php?section=problems&id=11](http://projecteuler.net/index.php?section=problems&id=11)

```

# search a grid horizontally, vertically, diag for the largest product of 4 #consecutive values
import re


pat = "[0-9]{2}"
array = []
n = (open("grid.dat").readlines())

def formArray(n):

	for line in n:
		array.append(re.findall(pat,line))
	
	# convert to int

	for i in range(20):
		for y in range(20):
			array[i][y] = int(array[i][y])





def checkRows(array):
	x = 1
	for index in range(len(array)):
		i = 0
		while i < len(array[index]) -3:
			y = array[index][i] * array[index][i+1] * array[index][i+2] * array[index][i+3]
			if y > x:
				x = y
			i += 1
	print x



def checkCols(array):
	x = 1
	for index in range(len(array)):
		i = 0
		while i < len(array) -3:
                        y = array[i][index] * array[i+1][index] * array[i+2][index] * array[i+3][index]
                        if y > x:
				x = y
                        i += 1
	print x

def checkNeg(array):
	newArray = [[]]
	p = 16
	while p >= 0:
		repet = 0
		while repet < (len(array)-p):
			newArray[0].append(array[p+repet][repet])
			repet += 1
		p -= 1
	p = 0
	while p <= 16:
		repet = 0
		while repet < (len(array)-p):

			newArray[0].append(array[repet][repet+p])
			repet += 1
		p += 1
	checkRows(newArray)

def checkPos(array):
	newArray = [[]]
	p = 19
	while p >= 4:
		repet = 0
		while repet < (p+1):
			newArray[0].append(array[p-repet][repet])
			repet += 1
		print	
		p -= 1
	checkRows(newArray)


formArray(n)
checkRows(array)
checkCols(array)
checkNeg(array)
checkPos(array)
```

---

### Post by apetresc on 2007-08-25
Yeah, I got the right answer (70600674) in just a few lines:
```
grid = [[0] * 23 for x in range(23)]
rows = file('data.in','r').read().split("\n")
for i in range(20):
	for j in range(20):
		grid[i][j] = int(rows[i].split(" ")[j])
currMax = 0
for i in range(20):
	for j in range(20):
		currMax = max(currMax, grid[i][j] * grid[i+1][j+1] * grid[i+2][j+2] * grid[i+3][j+3],
			grid[i][j] * grid[i+1][j] * grid[i+2][j] * grid[i+3][j],
			grid[i][j] * grid[i][j+1] * grid[i][j+2] * grid[i][j+3],
			grid[i][j] * grid[i-1][j+1] * grid[i-2][j+2] * grid[i-3][j+3])
print currMax
```
All you need to do is stick the grid data in a file called "data.in" (copy+paste from Euler), and run the script:
```
adrian@rootbeer:~$ time python problem11.py
70600674

real    0m0.047s
user    0m0.036s
sys     0m0.008s
```

If you need help understanding this code, let me know, I'd be glad to help you out :)

---

### Post by triptoe on 2007-08-25
> **AdrianP said:**
> Yeah, I got the right answer (70600674) in just a few lines:
```
grid = [[0] * 23 for x in range(23)]
rows = file('data.in','r').read().split("\n")
for i in range(20):
	for j in range(20):
		grid[i][j] = int(rows[i].split(" ")[j])
currMax = 0
for i in range(20):
	for j in range(20):
		currMax = max(currMax, grid[i][j] * grid[i+1][j+1] * grid[i+2][j+2] * grid[i+3][j+3],
			grid[i][j] * grid[i+1][j] * grid[i+2][j] * grid[i+3][j],
			grid[i][j] * grid[i][j+1] * grid[i][j+2] * grid[i][j+3],
			grid[i][j] * grid[i-1][j+1] * grid[i-2][j+2] * grid[i-3][j+3])
print currMax
```
All you need to do is stick the grid data in a file called "data.in" (copy+paste from Euler), and run the script:
```
adrian@rootbeer:~$ time python problem11.py
70600674

real    0m0.047s
user    0m0.036s
sys     0m0.008s
```

If you need help understanding this code, let me know, I'd be glad to help you out :)

I changed your code to print statements to see what it was doing.... very nice!

don't think it can get much better.

---

### Post by xtacocorex on 2007-08-25
AdrianP, the first line in your code just helped me out immensely.  I've been trying to take my RK2-Heun (Runge-Kutta 2nd Order Heun Method) FORTRAN 90 code, that I wrote in school to solve differential equations for my Computational Fluid Dynamics course, and put it into Python.  

I was having problems because there are no proper arrays like FORTRAN in Python and couldn't figure out how to initialize a nice 2 by X array.  Now I can finish it.

---

### Post by apetresc on 2007-08-25
> **xtacocorex said:**
> AdrianP, the first line in your code just helped me out immensely.  I've been trying to take my RK2-Heun (Runge-Kutta 2nd Order Heun Method) FORTRAN 90 code, that I wrote in school to solve differential equations for my Computational Fluid Dynamics course, and put it into Python.  

I was having problems because there are no proper arrays like FORTRAN in Python and couldn't figure out how to initialize a nice 2 by X array.  Now I can finish it.

Excellent :D Glad I was helpful. List comprehensions are one of Python's nicest features, and they can do a lot more than what I've used them for here. Check out, for example, [this page](http://www.secnetix.de/~olli/Python/list_comprehensions.hawk) for some other things you can do with them :)

---

### Post by xtacocorex on 2007-08-25
> **AdrianP said:**
> Excellent :D Glad I was helpful. List comprehensions are one of Python's nicest features, and they can do a lot more than what I've used them for here. Check out, for example, [this page](http://www.secnetix.de/~olli/Python/list_comprehensions.hawk) for some other things you can do with them :)
The problem I have with Python and the code I'm trying to port over is that lists are almost too powerful for what I need; slightly an odd conundrum, but it happens. 

Thanks for the link, will definitey look at it for harnessing the power of the list.

---

### Post by triptoe on 2007-08-26
is it just me... or could it have been worded better in list comprehensions built into python?

for instance:

> >>> S = [x**2 for x in range(10)]
>>> V = [2**i for i in range(13)]
>>> M = [x for x in S if x % 2 == 0]

Wouldn't it be more readable if it was this:

> S=[for x**2 in range(10)]
>>> V = [for 2**i in range(13)]
>>> M = [for x in S if x % 2 = 0]

or am i missing something??

---

### Post by Klipt on 2007-08-26
> **xtacocorex said:**
> I was having problems because there are no proper arrays like FORTRAN in Python and couldn't figure out how to initialize a nice 2 by X array.

Not in Python as such, but if you're doing serious numerical workouts you should consider the numpy (numeric python) and scipy (scientific python) packages :-D

---

