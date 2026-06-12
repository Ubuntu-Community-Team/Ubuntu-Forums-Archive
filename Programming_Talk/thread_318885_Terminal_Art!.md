---
title: "Terminal Art!"
date: 2006-12-14
forum: Programming Talk
---

### Post by Wybiral on 2006-12-14
Post your procedural terminal art here!

Sierpinski Triangle (python):
```

for y in range(64):
	out=""
	for x in range(64):
		if not(x & y):
			out+="#"
		else:
			out+=" "
	print out

```

ASCII Plasma(python):
```

from math import *
char = ["+","*","?","$","@","."]
for y in range(64):
	out=""
	for x in range(64):
		c = int((cos(x/4.0)*3.0+2.0 + sin(y/4.0)*3.0+2.0)/2.0)
		out+=char[c]
	print out

```

Title screen(python):
```

line =[""]
line+=["This is","an easy","way to","make cool","title screens","using only","the command line",""]
line+=["Python makes","these kinds","of things","Incredibly easy","to do!",""]

for y in range(15):
	out=""
	for x in range(12):
		if (x>y or x>15-y):
			out+="=="
	print out+">   "+line[y]

```

---

### Post by fatsheep on 2006-12-14
Very nice! :o

---

### Post by coder_ on 2006-12-14
Ahhh, brings back the memories of [the good 'ole ASCII demos... ]("http://en.wikipedia.org/wiki/Text_mode_demos") :)

---

### Post by Wybiral on 2006-12-14
Yeah, I made a small raycaster (wolf3d style) all in ascii once. In a BASIC language too!!!

---

