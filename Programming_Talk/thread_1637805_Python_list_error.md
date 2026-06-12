---
title: "Python list error"
date: 2010-12-04
forum: Programming Talk
---

### Post by saphil on 2010-12-04
I have been working on this for a couple of days, but the re is something I don't seem to be seeing.

in the interactive python window, I can see the content of a print list using a matrix

```
>>> r=['a','b','c']
>>> s=['d','e','f']
>>> t=['g','h','j']
>>> m=[r,s,t]
>>> m
[['a', 'b', 'c'], ['d', 'e', 'f'], ['g', 'h', 'j']]
>>> i
1
>>> k
2
>>> m[i][k]
'f'
>>> m[i-1][k-1]
'b'
>>> m[i+1][k-1]
'h'
>>> m[i+1][k]
'j'

```So why is this code not filling the place in the list?

```
def loop(M, error, change, count):
    # Internal variables
    row = 1; col = 1; val = "moo"; j = 1; i = 1; h = 1; sl = 1; t = ""; rows = row - 1; cols = col - 1
    
    for row in range(1, 10):
        for col in range(1, 10):
            print "the row is %d and the col is %d on line 116." %  (row, col)
            # variables rows and cols may solve the issue of unix lists starting with index 0
            rows = row - 1; cols = col - 1
            print "%s is rows and %s is cols on line 119." % (rows, cols)
            val = M[rows][cols]; print M[4][2], " is M[4][2]"  #doesn't print a value for the 
                                                                                  # hard-coded M[4][2] either.
            ll = len(val); print ll, " is length of val on line 121" 
            if ll >= 1:
                continue
            else:
                print "Error at row %d, column %d." % (row, col)
                error = True
```

Here is a piece of the print-line output..
```

3 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 2, cols = 8
0  = sl in line 145
4 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 3, cols = 8
0  = sl in line 145
5 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 4, cols = 8
0  = sl in line 145
6 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 5, cols = 8
0  = sl in line 145

```

]saphil

---

### Post by DangerOnTheRanger on 2010-12-05
First off, I think you should format those internal variables a little better; *never use ; in Python. Period. There's never a reason to.*
Also, *all *lists/arrays start at 0. Not just on *nix.

Now, to your problem...

Can you show me your algorithm, instead of this code? You didn't tell me what this code is supposed to output, so I don't know what *is *expected from this method.

But all in all, showing me your algorithm would be better, so can you post that instead?

---

### Post by DaithiF on 2010-12-05
The output you posted doesn't correspond to the section of code you posted, and I don't know what this sentence means...
> **saphil said:**
> So why is this code not filling the place in the list?

"filling the place in the list" ... what place?  what is 'filling'?

Also, in the attached file you sometimes use range(0,9), and sometimes range(1,10) and  decrement the loop counters ... why?

---

### Post by saphil on 2010-12-05
Hi!
Thanks for the very early morning input

What this thing does is take a sudoku puzzle with some set of values filled in the grid
like the examples below

A sudoku cannot have any duplicate values in a row of 9, a column of 9 or any 3x3 grid box.

This is a text version of the program that has been done in a guified way by several others.  My dad did the original in Mathematica, and I thought it would be fun to try to do it in Python.

The idea of this solver is not to have the program automatically solve the puzzle, but to make a puzzle-book sudoku problem easier to visualize.

 ```
Game Menu
        To start a sample game type   1
        To escape, type               69
Enter your choice :-)>  1
welcome to the sudoku solver!
The sample Sudoku is coming right up

Initial Sudoku Tableau
-----------------------------------------------------------------------------------------------------------------
['123456789', '123456789', '8        ', '9        ', '123456789', '123456789', '123456789', '123456789', '123456789']
['123456789', '7        ', '2        ', '123456789', '123456789', '3        ', '123456789', '123456789', '123456789']
['123456789', '123456789', '6        ', '2        ', '123456789', '4        ', '123456789', '7        ', '123456789']
['123456789', '6        ', '123456789', '7        ', '123456789', '123456789', '8        ', '123456789', '3        ']
['2        ', '9        ', '123456789', '123456789', '4        ', '123456789', '123456789', '6        ', '5        ']
['7        ', '123456789', '5        ', '123456789', '123456789', '6        ', '123456789', '1        ', '123456789']
['123456789', '5        ', '123456789', '4        ', '123456789', '9        ', '3        ', '123456789', '123456789']
['123456789', '123456789', '123456789', '6        ', '123456789', '123456789', '4        ', '5        ', '123456789']
['123456789', '123456789', '123456789', '123456789', '123456789', '8        ', '6        ', '123456789', '123456789']

```
Where there is a single value, that shows a "given" value in the sudoku.  The system should automatically remove all the duplicate digits from all intersecting rows and columns and boxes

```
 
Second Trial Sudoku Tableau
------------------------------------------------------------------------------------------------------------
['1345    ', '134     ', '8       ', '9       ', '1567    ', '1257    ', '125     ', '234     ', '1246    ']
['1459    ', '7       ', '2       ', '158     ', '1568    ', '3       ', '159     ', '489     ', '14689   ']
['1359    ', '13      ', '6       ', '2       ', '158     ', '4       ', '159     ', '7       ', '1389    ']
['145     ', '6       ', '14      ', '7       ', '1259    ', '125     ', '8       ', '249     ', '3       ']
['2       ', '9       ', '13      ', '138     ', '4       ', '1       ', '7       ', '6       ', '5       ']
['7       ', '348     ', '5       ', '38      ', '2389    ', '6       ', '29      ', '1       ', '249     ']
['168     ', '5       ', '17      ', '4       ', '127     ', '9       ', '3       ', '28      ', '1278    ']
['1389    ', '1238    ', '1379    ', '6       ', '1237    ', '127     ', '4       ', '5       ', '12789   ']
['1349    ', '1234    ', '13479   ', '135     ', '12357   ', '8       ', '6       ', '29      ', '1279    ']

```Then you would get an input for variable **str** and put in the single index points you saw that the system made plain.

The system should be able to see if there is an error in the player's choice of inputs. E.g., row 5 column 3 should be a '3' and not a '1.'

The system should be able to remember the series of board states 'M' in an array 'L' so the player can back up to a given one to fix errors that show up later.  Errors can become evident more than one move into the future.  This functionality is not yet coded into the application.

-------------------------
Why sometimes for loops in range 1-10 and sometimes 0-9..
       The loops for checking values ov M[row][col] seemed to work better using 1-10.  The indexes we are addressing are all 0-9, but users will probably be thinking about the grid as row 1 through 9 and column 1-9 - so that is why I started this using range 1-10.  It might be plainer if they all ran the same range, wouldn't it?
The board-drawing piece is entirely internal, so I did it 0-9

Come to think of it, that is almost the only part that is not a python version of a Mathematica program...

```

                for r in range(0, 9):
                    for c in range(0,9):
                        l = " " * (10 - len(M[r][c]))
                        p = "%s %s" % (M[r][c], l) 
                        lst.append(p)
                    print lst; lst = []

```
------------------
> The output you posted doesn't correspond to the section of code you posted, and I don't know what this sentence means...
     Quote:
                                                                      Originally Posted by **saphil**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10200792#post10200792")                 
                 *So why is this code not filling the place in the list?*
                                 
"filling the place in the list" ... what place?  what is 'filling'?That is my picking error. Since the runtime error just runs infinitely and doesn't ever seem to be satisfied, I chose a set where the same issues arise.  There are four sets of checking code lines: 116, 131, 142, 152.  I commented out the area around 152 which checks for errors in the 3x3 blocks.  It was causing out-of-range errors.

"Filling the place in the list" is about how M[0] (for instance) when printed shows empty places instead of the '123456789' strings repeated nine times that I expect, so M[0][3] prints as a blank space and len(M[0][3]) = 0.  When an index place in the same row or column has a matching number with the 'given,' answer, the number is removed from the string and replaced with a null.  

Here are the print lines covering all of the first three 116, 131, 142.  The error comes and goes in the first 2 sections but is almost continual in the third.

```

Initial Sudoku Tableau
-----------------------------------------------------------------------------------------------------------------
['123456789  ', '123456789  ', '8          ', '9          ', '123456789  ', '123456789  ', '123456789  ', '123456789  ', '123456789  ']
['123456789  ', '7          ', '2          ', '123456789  ', '123456789  ', '3          ', '123456789  ', '123456789  ', '123456789  ']
['123456789  ', '123456789  ', '6          ', '2          ', '123456789  ', '4          ', '123456789  ', '7          ', '123456789  ']
['123456789  ', '6          ', '123456789  ', '7          ', '123456789  ', '123456789  ', '8          ', '123456789  ', '3          ']
['2          ', '9          ', '123456789  ', '123456789  ', '4          ', '123456789  ', '123456789  ', '6          ', '5          ']
['7          ', '123456789  ', '5          ', '123456789  ', '123456789  ', '6          ', '123456789  ', '1          ', '123456789  ']
['123456789  ', '5          ', '123456789  ', '4          ', '123456789  ', '9          ', '3          ', '123456789  ', '123456789  ']
['123456789  ', '123456789  ', '123456789  ', '6          ', '123456789  ', '123456789  ', '4          ', '5          ', '123456789  ']
['123456789  ', '123456789  ', '123456789  ', '123456789  ', '123456789  ', '8          ', '6          ', '123456789  ', '123456789  ']
the row is 1 and the col is 1 on line 116.
0 is rows and 0 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 1 and the col is 2 on line 116.
0 is rows and 1 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 1 and the col is 3 on line 116.
0 is rows and 2 is cols on line 119.
8  is M[rows][cols]
1  is length of val on line 121
the row is 1 and the col is 4 on line 116.
0 is rows and 3 is cols on line 119.
9  is M[rows][cols]
1  is length of val on line 121
the row is 1 and the col is 5 on line 116.
0 is rows and 4 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 1 and the col is 6 on line 116.
0 is rows and 5 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 1 and the col is 7 on line 116.
0 is rows and 6 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 1 and the col is 8 on line 116.
0 is rows and 7 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 1 and the col is 9 on line 116.
0 is rows and 8 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
0 variable 'j'-1 on line 131.
0 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
1 variable 'j'-1 on line 131.
0 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
2 variable 'j'-1 on line 131.
0 is rows, 8 is cols on line 132
8  = M[rows][jx] on line 133 
3 variable 'j'-1 on line 131.
0 is rows, 8 is cols on line 132
9  = M[rows][jx] on line 133 
4 variable 'j'-1 on line 131.
0 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
5 variable 'j'-1 on line 131.
0 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
6 variable 'j'-1 on line 131.
0 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
7 variable 'j'-1 on line 131.
0 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
2 = i in line 142
123456789 is t on line 144, content of the t string.  M[ix][cols] is 123456789. ix = 1, cols = 8
9  = sl in line 145
3 = i in line 142
123456789 is t on line 144, content of the t string.  M[ix][cols] is 123456789. ix = 2, cols = 8
9  = sl in line 145
4 = i in line 142
3 is t on line 144, content of the t string.  M[ix][cols] is 3. ix = 3, cols = 8
1  = sl in line 145
5 = i in line 142
5 is t on line 144, content of the t string.  M[ix][cols] is 5. ix = 4, cols = 8
1  = sl in line 145
6 = i in line 142
123456789 is t on line 144, content of the t string.  M[ix][cols] is 123456789. ix = 5, cols = 8
9  = sl in line 145
7 = i in line 142
123456789 is t on line 144, content of the t string.  M[ix][cols] is 123456789. ix = 6, cols = 8
9  = sl in line 145
8 = i in line 142
123456789 is t on line 144, content of the t string.  M[ix][cols] is 123456789. ix = 7, cols = 8
9  = sl in line 145
9 = i in line 142
123456789 is t on line 144, content of the t string.  M[ix][cols] is 123456789. ix = 8, cols = 8
9  = sl in line 145
the row is 2 and the col is 1 on line 116.
1 is rows and 0 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 2 and the col is 2 on line 116.
1 is rows and 1 is cols on line 119.
7  is M[rows][cols]
1  is length of val on line 121
the row is 2 and the col is 3 on line 116.
1 is rows and 2 is cols on line 119.
2  is M[rows][cols]
1  is length of val on line 121
the row is 2 and the col is 4 on line 116.
1 is rows and 3 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 2 and the col is 5 on line 116.
1 is rows and 4 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 2 and the col is 6 on line 116.
1 is rows and 5 is cols on line 119.
3  is M[rows][cols]
1  is length of val on line 121
the row is 2 and the col is 7 on line 116.
1 is rows and 6 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 2 and the col is 8 on line 116.
1 is rows and 7 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 2 and the col is 9 on line 116.
1 is rows and 8 is cols on line 119.               #Note blank outputs
  is M[rows][cols]                                       # for M[rows][cols] which is peculiar
0  is length of val on line 121                      # since on 119 the rows and cols have
Error at row 2, column 9.                             # numeric values
0 variable 'j'-1 on line 131.
1 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
1 variable 'j'-1 on line 131.
1 is rows, 8 is cols on line 132
7  = M[rows][jx] on line 133 
2 variable 'j'-1 on line 131.
1 is rows, 8 is cols on line 132
2  = M[rows][jx] on line 133 
3 variable 'j'-1 on line 131.
1 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
4 variable 'j'-1 on line 131.
1 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
5 variable 'j'-1 on line 131.
1 is rows, 8 is cols on line 132
3  = M[rows][jx] on line 133 
6 variable 'j'-1 on line 131.
1 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
7 variable 'j'-1 on line 131.
1 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
1 = i in line 142
123456789 is t on line 144, content of the t string.  M[ix][cols] is 123456789. ix = 0, cols = 8
9  = sl in line 145
3 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 2, cols = 8
0  = sl in line 145
4 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 3, cols = 8
0  = sl in line 145
5 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 4, cols = 8
0  = sl in line 145
6 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 5, cols = 8
0  = sl in line 145
7 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 6, cols = 8
0  = sl in line 145
8 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 7, cols = 8
0  = sl in line 145
9 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 8, cols = 8
0  = sl in line 145
the row is 3 and the col is 1 on line 116.
2 is rows and 0 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 3 and the col is 2 on line 116.
2 is rows and 1 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 3 and the col is 3 on line 116.
2 is rows and 2 is cols on line 119.
6  is M[rows][cols]
1  is length of val on line 121
the row is 3 and the col is 4 on line 116.
2 is rows and 3 is cols on line 119.
2  is M[rows][cols]
1  is length of val on line 121
the row is 3 and the col is 5 on line 116.
2 is rows and 4 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 3 and the col is 6 on line 116.
2 is rows and 5 is cols on line 119.
4  is M[rows][cols]
1  is length of val on line 121
the row is 3 and the col is 7 on line 116.
2 is rows and 6 is cols on line 119.
123456789  is M[rows][cols]
9  is length of val on line 121
the row is 3 and the col is 8 on line 116.
2 is rows and 7 is cols on line 119.
7  is M[rows][cols]
1  is length of val on line 121
the row is 3 and the col is 9 on line 116.
2 is rows and 8 is cols on line 119.
  is M[rows][cols]
0  is length of val on line 121
Error at row 3, column 9.
0 variable 'j'-1 on line 131.
2 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
1 variable 'j'-1 on line 131.
2 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
2 variable 'j'-1 on line 131.
2 is rows, 8 is cols on line 132
6  = M[rows][jx] on line 133 
3 variable 'j'-1 on line 131.
2 is rows, 8 is cols on line 132
2  = M[rows][jx] on line 133 
4 variable 'j'-1 on line 131.
2 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
5 variable 'j'-1 on line 131.
2 is rows, 8 is cols on line 132
4  = M[rows][jx] on line 133 
6 variable 'j'-1 on line 131.
2 is rows, 8 is cols on line 132
123456789  = M[rows][jx] on line 133 
7 variable 'j'-1 on line 131.
2 is rows, 8 is cols on line 132
7  = M[rows][jx] on line 133 
1 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 0, cols = 8
0  = sl in line 145
2 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 1, cols = 8
0  = sl in line 145
4 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 3, cols = 8
0  = sl in line 145
5 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 4, cols = 8
0  = sl in line 145
6 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 5, cols = 8
0  = sl in line 145
7 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 6, cols = 8
0  = sl in line 145
8 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 7, cols = 8
0  = sl in line 145
9 = i in line 142
 is t on line 144, content of the t string.  M[ix][cols] is . ix = 8, cols = 8
0  = sl in line 145


```

---

### Post by talonmies on 2010-12-05
Surely a numpy array (which can be indexed and sliced any way you like without any addtional code) is a far better choice that trying to do the same thing with lists and strings?

---

### Post by saphil on 2010-12-05
If there is an easier way, I am interested.  I have not done anything with numpy, however.
How much of a rewrite would it be?

---

### Post by talonmies on 2010-12-05
> **saphil said:**
> If there is an easier way, I am interested.  I have not done anything with numpy, however.
How much of a rewrite would it be?

Probably substantiatial, but the result would be a lot less byzantine and easier to maintain. Python code can be the model of elegance and simplicity. Or not.

---

### Post by saulgoode on 2010-12-05
> **saphil said:**
> "Filling the place in the list" is about how M[0] (for instance) when printed shows empty places instead of the '123456789' strings repeated nine times that I expect, so M[0][3] prints as a blank space and len(M[0][3]) = 0.  When an index place in the same row or column has a matching number with the 'given,' answer, **the number is removed from the string and replaced with a null**.
I don't use Python, but is it possible that by substituting a null, the printing of that string halts upon encountering the null (in effect, truncating the string)? Perhaps substituting a space would be better.

---

### Post by saphil on 2010-12-05
str.replace() works pretty well with nulls.  I was a little surprised, but it is the mathematica way of doing it.  

```

>>> str = "words_with_numb3rs"
>>> ex = "3"
>>> print ex, str
3 words_with_numb3rs
>>> str = str.replace(ex, "")
>>> str
'words_with_numbrs'
>>> 

```

I am going to see if I can figure numpy out, unless somebody can see what is causing the error in the base python code I am kludging together here.

---

### Post by raf-kig on 2010-12-05
> **DangerOnTheRanger said:**
> First off, I think you should format those internal variables a little better; *never use ; in Python. Period. There's never a reason to.*

[SIZE=3]Why? Because Python chokes? 
[/SIZE]
It seems perfectly reasonable to separate multiple variable assignments, and even some closely-related program statements, on the same line separated by ";".

---

### Post by nvteighen on 2010-12-06
> **raf-kig said:**
> [SIZE=3]Why? Because Python chokes? 
[/SIZE]
It seems perfectly reasonable to separate multiple variable assignments, and even some closely-related program statements, on the same line separated by ";".

Because of tradition (= PEP guidelines); there's no other reason.

Ok, yes, you may tell me that that is stupid and programmers shouldn't have such style criteria on mind, specially when the so-horrible style practice is still allowed by the language itself. But, remember that language (also natural language) is also social and traditions form up in some way or another... sometimes as "best practices", sometimes as "style guidelines", etc. People expect to read Python code where ; is not used... until it begins to be used massively and the tradition changes...

---

### Post by StephenF on 2010-12-06
> **raf-kig said:**
> [SIZE=3]Why? Because Python chokes? 
[/SIZE]
It seems perfectly reasonable to separate multiple variable assignments, and even some closely-related program statements, on the same line separated by ";".
```

row = 1; col = 1; val = "moo"; j = 1; i = 1; h = 1; sl = 1; t = ""; rows = row - 1; cols = col - 1

```
Reasonable to whom?

A more sane way of grouping.
```

row = col = h = i = j = sl = 1
rows = cols = 0
t = ""
val = "moo"  # wat!?!

```
In this example variables which have common initial values are set on the same line. Typically values like 0, 1, and "" are assigned so this keeps the number of extra lines to a minimum.

---

### Post by ziekfiguur on 2010-12-06
> **DangerOnTheRanger said:**
> First off, I think you should format those internal variables a little better; *never use ; in Python. Period. There's never a reason to.*

Yes, there is. For example when you enter your code as command-line arguments.
```
python -c 'print "like this."; print "spam & eggs"'
```

---

### Post by DangerOnTheRanger on 2010-12-06
That's the exception, rather than the rule.
Are you trying to say that *this*:

```

a = 1; b = 2; c = 3; d = 4; e = 0.3456

```looks better than:

```

a = 1
b = 2
c = 3
d = 4
e = 0.3456

```
Longer code does not necessarily mean worse style. On the contrary, splitting the declaration of the variables has made the code *much clearer.*
I bet you come from a C/C++ or Java background, where ; is mandatory. 
I'm also pretty sure you will be hard-pressed to find any legitimate Python code on the Net that uses ;.

EDIT: One other thing. Anywhere the **-c **switch can be used, the interactive session can be used as well...

---

### Post by DangerOnTheRanger on 2010-12-06
> **raf-kig said:**
> [SIZE=3]Why? Because Python chokes? 
[/SIZE]
It seems perfectly reasonable to separate multiple variable assignments,  and even some closely-related program statements, on the same line  separated by ";".

I bet you also come from a C/C++ or Java background. I have *never* had to use ; in my Python scripts.

---

### Post by ziekfiguur on 2010-12-06
> **DangerOnTheRanger said:**
> Are you trying to say that *this*:

```

a = 1; b = 2; c = 3; d = 4; e = 0.3456

```looks better than:

```

a = 1
b = 2
c = 3
d = 4
e = 0.3456

```

No, I'm just saying that it's not *never*. Even though it may be exceptional, there may be a (good) reason.

---

### Post by DangerOnTheRanger on 2010-12-06
Then *show *me that reason. Otherwise, nobody's sure it even exists...

---

### Post by Arndt on 2010-12-06
> **DangerOnTheRanger said:**
> Then *show *me that reason. Otherwise, nobody's sure it even exists...

Saying that someone must come from a C++ background is sort of a punch in the air. Semicolon is obligatory in C++, yes, but there too, it is more usual to put a row of assignments on one line each.

I'm not sure what you mean by this:

> EDIT: One other thing. Anywhere the -c switch can be used, the interactive session can be used as well..

---

### Post by saulgoode on 2010-12-06
Shouldn't the 'i' and 'j' loops be performed for every 'col'. Python's invisible syntax makes it hard to tell, but it seems like those loops are only executed after the 'col' loop and therefore only for the final value of 'col' (11?).

Also, I (still) think something is amiss with your 'replace' statements. Taking a stab in the dark, I would say 't' should be M[rows][cols] and not M[ix][cols] or M[rows][jx] as the case may be (and shouldn't the replacement only take place if the substitute string's length is 1?).

---

