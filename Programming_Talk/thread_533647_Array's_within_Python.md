---
title: "Array's within Python"
date: 2007-08-24
forum: Programming Talk
---

### Post by Alex Spencer on 2007-08-24
Hi Guys,

I've programmed in VB for over 8 years, have just read a tutorial on Python and I think it's the way forward...for what I want to do anyway.

I've hit a snag though, I'm trying to create two arrays:

1) A 9 x 9 array (hmm...for a Sudoku Solver you ask...yes, in fact)
2) A 9x9 array, with each element being a 9 element list, not tuple.

I've tried array1 = array([8,8]) but it doesn't work...any help would be appreciated.

Alex.

---

### Post by apetresc on 2007-08-24
> **Alex Spencer said:**
> Hi Guys,

I've programmed in VB for over 8 years, have just read a tutorial on Python and I think it's the way forward...for what I want to do anyway.

I've hit a snag though, I'm trying to create two arrays:

1) A 9 x 9 array (hmm...for a Sudoku Solver you ask...yes, in fact)
2) A 9x9 array, with each element being a 9 element list, not tuple.

I've tried array1 = array([8,8]) but it doesn't work...any help would be appreciated.

Alex.

Firstly, "array" in Python is called a "list", but they behave the same.

Secondly, Python does not really support multi-dimensional lists per-se, although it does allow composite lists (as in, lists of lists), which is how you should go about this.

So, you can simply do ```
sudokuGrid = [[[] for x in range(0,9)] for y in range(0,9)]
```
And your new 9x9 grid is ready :)

I used Python's list comprehension to create those. If you haven't learned about them yet, check out this link: [http://www.network-theory.co.uk/docs/pytut/ListComprehensions.html](http://www.network-theory.co.uk/docs/pytut/ListComprehensions.html)

Good luck :)

---

### Post by Alex Spencer on 2007-08-24
Thanks for your quick friendly reply, I'll give nested lists a try!

---

### Post by triptoe on 2007-08-24
Here is a little bit clearer way filling the grids with 1's

```
sudoGrid = []

for x in range(9):
        sudoGrid.append([])
        for y in range(9):
                sudoGrid[x].append([1])

print sudoGrid[0]                       # prints first row
print sudoGrid[0][0]                   # Prints first element of first row
for i in range(len(sudoGrid)):    # Prints first column
        print sudoGrid[i][0]

```

---

### Post by Alex Spencer on 2007-08-24
Thank you.

When I am printing my elements, it is printing [7] instead of 7. How do I strip the []'s?

---

### Post by apetresc on 2007-08-24
> **Alex Spencer said:**
> Thank you.

When I am printing my elements, it is printing [7] instead of 7. How do I strip the []'s?

Well, it's returning a list whose only element is 7. To get the first element, just access element 0 of the list instead of the whole list.

---

### Post by pmasiar on 2007-08-24
Python has excellent and flexible data literals. To create 9 * 9 list of lists sudoku, just use:
sudoku = [ [[]] * 9 for i in range(9)]

First part ("[[]] * 9") creates list of 9 empty lists. Second part does it 9 times. You cannot do the second part using  * 9, because you need different lists.

Another option could be to use a tuple as key: sudoku[(1,2)] instead of sudoku[1][2]. How to create data structure is left as exercise for the reader :-)

---

### Post by CptPicard on 2007-08-24
And as array[][] is so much cleaner, this is yet another reason why I am suspicious of Python... :p

---

### Post by pmasiar on 2007-08-24
LOL I just tried it out -- comma is the tupple builder, you can omit (), and have sudoku[1,2] = 'a'. 1,2 is tuple, and sudoku = dict().

sudoku = dict( ((i,j), []) for i in range(9) for j in range(9))

Python continues to amaze me. It just reads my mind! "wouldn't it be nice if this would work?" Let's try it - and it does! :-)

---

### Post by triptoe on 2007-08-24
in other words if you have a list like 

sequence = [1,2,3,4,5]

print sequence will print the brackets.. but to print it without the brackets you do

for i in sequence:
     print i,

---

### Post by pmasiar on 2007-08-24
Correct. sequence is a list, i is number.
Just try it in the Python shell.... :-)

---

### Post by Smygis on 2007-08-24
> **pmasiar said:**
> LOL I just tried it out -- comma is the tupple builder, you can omit (), and have sudoku[1,2] = 'a'. 1,2 is tuple, and sudoku = dict().

sudoku = dict( ((i,j), []) for i in range(9) for j in range(9))

Python continues to amaze me. It just reads my mind! "wouldn't it be nice if this would work?" Let's try it - and it does! :-)

:popcorn: Awsome!
That's amazing.

---

