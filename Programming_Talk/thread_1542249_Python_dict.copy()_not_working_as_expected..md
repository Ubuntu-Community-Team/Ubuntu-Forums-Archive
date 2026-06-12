---
title: "Python dict.copy() not working as expected."
date: 2010-07-30
forum: Programming Talk
---

### Post by MadnessRed on 2010-07-30
Here is part of my code, the whole script is quite large but this is the bit that is confusing me.

```
		for r in nums: numarraydict[r] = [0,0]
		inrow = numarraydict.copy()
		incol = numarraydict.copy()
		inbox = numarraydict.copy()
		
		for i in range(0,dim):
			if not rows[n].squares[i].pen == None:
				inrow[rows[n].squares[i].pen][0] = 2
			else:
				for val in rows[n].squares[i].pencil:
					inrow[val][0] += 1
					inrow[val][1] = i
					
			if not cols[n].squares[i].pen == None:
				incol[cols[n].squares[i].pen][0] = 2
			else:
				for val in cols[n].squares[i].pencil:
					incol[val][0] += 1
					incol[val][1] = i
					
			if not boxs[n].squares[i].pen == None:
				if n==6 and boxs[n].squares[i].pen==2:
					print numarraydict[boxs[n].squares[i].pen],
				inbox[boxs[n].squares[i].pen][0] = 2
				if n==6 and boxs[n].squares[i].pen==2:
					print numarraydict[boxs[n].squares[i].pen]
			else:
				for val in boxs[n].squares[i].pencil:
					if n==6 and val==2:
						print numarraydict[val],
					inbox[val][0] += 1
					inbox[val][1] = i
					if n==6 and val==2:
						print numarraydict[val]
		
		if n == 6:
			print inbox
```
The problem, is that dispite me using the copy() function on the dictionary, it still seems that inbox, inrow, incol and numarraydict are the same thing, and changing one changes them all.

Here is the output from that command:
```
[2, 2] [3, 2]
[4, 3] [5, 3]
[7, 5] [8, 5]
[8, 5] [9, 6]
[13, 8] [14, 8]
{1: [2, 5], 2: [14, 8], 3: [8, 8], 4: [2, 2], 5: [7, 8], 6: [7, 8], 7: [6, 8], 8: [9, 8], 9: [10, 8]}

```

Where it should be

```
[0, 0] [0, 0]
[0, 0] [0, 0]
[0, 0] [0, 0]
[0, 0] [0, 0]
[0, 0] [0, 0]
{1: [2, 5], 2: [5, 8], 3: [3, 8], 4: [1, 2], 5: [4, 8], 6: [3, 8], 7: [2, 8], 8: [7, 8], 9: [8, 8]}
```

For some reason the copy() is not creating separation dictionaries. Any suggestions?

---

### Post by DanielWaterworth on 2010-07-30
I think that copy is doing a shallow copy and you want a deep-copy. [http://docs.python.org/library/copy.html](http://docs.python.org/library/copy.html)

---

### Post by wmcbrine on 2010-07-30
The top-level dictionaries are separate, which you can prove by adding elements to one of them, and not then seeing them in the others. The problem is that, when you did the copy, what you copied was a bunch of *references* to lists.

---

