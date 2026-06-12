---
title: "[SOLVED] python code doesn't work, what's up?"
date: 2008-08-31
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-31
So I made this python script to check if a point is inside rectangle:
```
	def boxcheck(box, point):
		rx1 = rect[0]
		rx2 = rect[2]
		ry1 = rect[1]
		ry2 = rect[3]
		px = point[0]
		py = point[1]
		# check x
		if (px > rx1 and px < rx2) or (px < rx1 and px > rx2):
			x = True
		else:
			x = False
		# check y
		if (py > ry1 and py < ry2) or (py < ry1 and py > ry2):
			y = True
		else:
			y = False
		# check if x and y
		if (x == True and y == True):
			return True
		else:
			return False
```
But it gives me an error message:
```
arho@ohra-laptop:~/Asiakirjat/anim$ python anim.py
Traceback (most recent call last):
  File "anim.py", line 265, in <module>
    if __name__ == '__main__': main()
  File "anim.py", line 155, in main
    if boxcheck(x.file.get_rect, mpos):
  File "anim.py", line 28, in boxcheck
    rx1 = rect[0]
TypeError: 'builtin_function_or_method' object is unsubscriptable
arho@ohra-laptop:~/Asiakirjat/anim$ python anim.py

```
So whats wrong with that? This time I read manuals, and they said I can handle tuples like lists.

---

### Post by WW on 2008-08-31
According to the traceback, you are calling boxcheck like this:
```

    if boxcheck(x.file.get_rect, mpos):

```
What is x.file.get_rect?  Maybe that should be x.file.get_rect()?

---

### Post by WW on 2008-08-31
P.S. You can simplify this:
```

		# check if x and y
		if (x == True and y == True):
			return True
		else:
			return False

```
to this:
```

		return x and y 

```

---

### Post by unutbu on 2008-08-31
Maybe 
```
def boxcheck(box, point):
```
should be
```
def boxcheck(rect, point):
```
too.

---

### Post by crazyfuturamanoob on 2008-08-31
> **WW said:**
> According to the traceback, you are calling boxcheck like this:
```

    if boxcheck(x.file.get_rect, mpos):

```
What is x.file.get_rect?  Maybe that should be x.file.get_rect()?
Thanks, that solved it.

---

