---
title: "Python string formatting"
date: 2008-08-03
forum: Programming Talk
---

### Post by Kolmogorov on 2008-08-03
Hi,

I'm trying to do a nicely formatted table for the following (simple) program:

```
# chaos.py

def main():
        # Introduction
	print "This program illustrates a chaotic function."
	print
        
        # Get user input
	x,y = input("Enter two numbers between 0 and 1 (a,b): ")
	n = input("Enter the number of iterations: ")
	print 
        
        # Create table labels
	print "%5s\t%.2f\t%.2f" % ("index",x,y)
	print "-" * 35

        # Create the table
	for i in range(1,n + 1):
		x = 3.9 * x * (1 - x)
		y = 3.9 * y * (1 - y)
		print "%5d\t%.6f\t%.6f" % (i,x,y)

	print

main()
```

* This is actually a problem from the book : "Python Programming: An introduction to computer science" by John Zelle (chapter 4, problem 12).

I want the labels be centered with the values of the table...is there any suggestions ?

Thanks ;)

Kolmogorov

---

### Post by Wybiral on 2008-08-03
Can you use [ code ] tags so I can read it better?

If you're trying to center a string with spaces as padding:
```

>>> "Hello world".center(25)
'       Hello world       '

```

---

### Post by ghostdog74 on 2008-08-03
you can use rjust, ljust.

---

### Post by Def13b on 2008-08-03
Another option is to give the elements of your string conversion a width.

Used before the '.'
             
```
print "%5s\t%8.2f\t%8.2f" % ("index",x,y)
             ^      ^
```

adjusted to suit your needs obviously, not sure how well this would work if your table width changes though.

---

