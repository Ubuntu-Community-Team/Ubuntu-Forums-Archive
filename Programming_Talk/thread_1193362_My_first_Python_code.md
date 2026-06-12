---
title: "My first Python code"
date: 2009-06-21
forum: Programming Talk
---

### Post by eckeroo on 2009-06-21
Hello all,

Just wanted to show off my first ever working Python code [Python 2.5] and ask a few questions and get some opinions.

I've created a program for an engineering purpose (works out bolt loads due to thermal expansion). I was drawn to code this program in Python to take advantage of the SciPy module with its linear algebra features.

My intention is to do all my engineering programs in Python. I am currently reading 'Learing Python'2005 edition by O'Reilly and I'm up to part III. I used Josh Cogliati's 'Non-Programmers Tutorial For Python' to get started. The O'Reilly book is good for filling in the details.

I eventually want to start coding TKinter GUIs, currently my code inputs/output with text files.

Have a gander:
[PHP]
#Program to calculate the thermal stresses between a row of bolts for
#a stack of two plies.

#line that reads input data into a list of strings

#bolt forces as applied to the top layer
input =open('thermal input.txt')       
aList=input.readlines()

data=[]

for a in aList:
    if a.find('#')<0 and a <> '\n':
        b = a.split(',')
        c = [float(d) for d in b] 
        data.append(c)

from scipy import *
from scipy.linalg import *

#general equations
def eqn1(boltno):    
    return 1/boltK[boltno]

def eqn2(pitch,topA,btmA,topE,btmE,boltno):
    return -pitch/(btmA*btmE)-pitch/(topA*topE)-1/boltK[boltno]
    
def eqn3(pitch,topA,btmA,topE,btmE):
    return -pitch/(btmA*btmE)-pitch/(topA*topE)

boltK=[]
for a in data[0]:
    b= 10000.0    #'some function TBAL that calculates bolt shear stiffness using the huth method'
    boltK.append(b)

matrix=[]
    
for r in range(0,len(data[3])):
    
    row=[]
    for c in range(0,len(data[0])):
        
        if c==r+1:
            b = eqn1(c)
        elif c==r:
            b = eqn2(data[3][r],data[4][r],data[5][r],data[6][0],data[7][0],c)
        elif c<r:
            b = eqn3(data[3][r],data[4][r],data[5][r],data[6][0],data[7][0])
        elif c>r+1:
            b = 0
        row.append(b)
    
    matrix.append(row)

row=[]
for a in data[0]:
    row.append(1)

matrix.append(row)

A = mat(matrix)

matrix =[]
for a in range(0,len(data[3])):
    row=[]
    b = data[9][0]*data[3][a]*data[10][0]-data[8][0]*data[3][a]*data[10][0]
    row.append(b)
    matrix.append(row)
row=[0]
matrix.append(row)
B = mat(matrix)
C=solve(A,B)
print C[/PHP]

And the 'thermal input.txt' file:

#Input file for thermal
[PHP]
#bolt diameters (mm)				
7.94, 9.53, 7.94, 7.94, 6.35

#Bolt stiffnesses (MPa)				
110000, 110000, 110000, 110000, 110000

#ply thicknesses at bolts(mm)			
5, 5.1, 5.1, 5.2, 5.1

#length of pitch between bolts (mm)		
15, 15.6, 15.8, 16

#effective areas between bolts (mm^2)
#top ply					
200, 210, 210, 200

#bottom ply					
200, 210, 210, 200

#ply stiffnesses (MPa)				
#top ply					
66340

#bottom ply					
45000

#thermal expansion coeefficients
#top ply					
2.3E-5

#bottom ply					
1.2E-6

#temperature difference (degrees centrigade/Kelvin)
50

#huth coeefficent				
2.6[/PHP]

The scipy module is excellent, saves me having to write the code for solving matrices. However, it does take a noticeable amount of time to import when I run the program. If I'm just using one function from the whole module, is there some way of just importing the scipy functions that are used?

---

### Post by MadCow108 on 2009-06-21
I think your searching for the from ... import syntax.
eg:
from scipy import mat
from scipy.linalg import solve

also you can compile your py code to bytecode by
>>> import pythonmodule
this creates a pythonmodule.pyc which should load faster (but won't execute faster)

no warranty on correctness, I'm just learning python too.

---

### Post by days_of_ruin on 2009-06-21
fyi using "<>" is deprecated. Use != instead.

---

### Post by smartbei on 2009-06-21
Using from x import y will not make the module import faster, since it still actually loads the whole module. It just doesn't stick the module into your namespace, just the requested object.

The code generally looks good. Here are some more tips and best practices:
[LIST]
[*] import statemenets are generally placed at the top of the script, for readability.
[*] assuming you will want to use this program, it might be nice if the filename is read from the command line arguments (take a look at sys.argv)
[*] This:
```

boltK=[]
for a in data[0]:
    b= 10000.0
    boltK.append(b)

```
looks like it could be replaced with:
```

boltK = [10000.] * len(data[0])

```
[*] lastly, it might be nice if all of the code would be in a function, so that the module could be imported and used as a part of an even larger program. To do that, and still have the current functionality, use:
```

def main():
    # All of the program logic should be placed here.

if __name__ == "__main__":
   # We are here only if the program was run as the main script, not if it
   # was imported.
   main()

```
[/LIST]
Regardless, great work on the script! That is quite complicated for your first program.

I would really like to see what you do with Tk in the future.

---

### Post by asdfhjkla on 2009-06-22
Nice work - a much more interesting first Python program than "Hello World!", that's for sure :D

The only things I can think to add to previous advice is...

1. Close files after you're finished with them, if anything just for good practice.

[PHP]
#bolt forces as applied to the top layer
input =open('thermal input.txt')       
aList=input.readlines()

input.close()
[/PHP]

2. This could be shortened to just "print solve(A, B)"

[PHP]
C=solve(A,B)
print C[/PHP]

3. I suppose it's not a huge deal for short scripts like this, and it's purely a matter of style - but I'd recommend giving more descriptive names to your variables rather than a, b, c.


One thing you could do which would make your code re-usable in future, which could be handy if you're considering adding a GUI, is to break it down into functions. You could stick most of the code into a function named **main()** for example, and add this at the end of the program:

[PHP]if __name__ == "__main__":
    main()[/PHP]

If you execute this script directly from the terminal, then __name__ has the value "__main__" and so is executed normally. If you have a different program in which you want to re-use your code, you could import your script and just call the appropriate functions. This isn't a critique, just something you may want to consider if you are going to be using something in future :)

---

### Post by Can+~ on 2009-06-22
[PHP]input =open('thermal input.txt')       
aList=input.readlines()

data=[]

for a in aList:
    if a.find('#')<0 and a <> '\n':
        b = a.split(',')
        c = [float(d) for d in b] 
        data.append(c)[/PHP]

I didn't like that, one bit.

1. readlines() actually uploads the whole file to memory, when, instead, using your typical [FONT="Courier New"]for line in file() [/FONT] buffers the file to memory automatically. It's more scalable.

2. The word "input" is reserved.

3. Variable names are very unhelpful "aList", "a", "b", "c". You should try to use expressive variable names that actually reflect what you're doing. It's better for you, it's better for everyone, and the interpreter couldn't care less what name you use.

4. I get the feeling that [FONT="Courier New"]data = [][/FONT] could be a dictionary [FONT="Courier New"]data = {[]}[/FONT] so you can keep a hash of each object you need, for example, after parsing and storing it, it would look like:

data["diameter"] = [7.94, 9.53, 7.94, 7.94, 6.35]
data["stifness"] = [110000, 110000, 110000, 110000, 110000]
...

which is more manageable.

---

### Post by unutbu on 2009-06-22
eckeroo, you are doing a great job considering this is your first Python program.

However, you are missing out on the fun (and power) of numpy arrays.

Instead of using loops to compute each component of a matrix one by one, you can use numpy arrays to write vector equations. For example, if a and b are numpy arrays, then a*b multiplies a and b component-by-component, resulting in another numpy array of the same shape.

3*a magnifies each component of a by 3
3+a adds 3 to each component of a.
Below I use this to simplify your equations.

Read 
[http://www.tau.ac.il/~kineret/amit/scipy_tutorial/](http://www.tau.ac.il/~kineret/amit/scipy_tutorial/)
[http://www.tramy.us/numpybook.pdf](http://www.tramy.us/numpybook.pdf) (Guide to Numpy)

they will blow your mind, and then make you very happy.

Minor quibbles:
[list]
[*] input is a built-in function used for evaluating input from stdin. When you  use it as a variable name, you lose the ability to call the built-in function. It is better to rename your variable 'input' something else.
[*] range(0,len(data[3])) can be shortened to range(len(data[3]))
[*] Although you are reading everything into a data list of lists, some rows of data are really just 1-element lists. If you can give those constants names instead of referencing them as data[6][0], data[7][0], etc, it would make your equations easier to read.
[/list]

[PHP]
#!/usr/bin/env python

#Program to calculate the thermal stresses between a row of bolts for
#a stack of two plies.

#line that reads input data into a list of strings

#bolt forces as applied to the top layer

from scipy import array,select,ones,ones_like,append,arange
from scipy.linalg import solve

data=[]
filehandle=open('thermal input.txt')       
for line in filehandle:
    if line.find('#')<0 and line.strip():
        data.append(array([float(val) for val in line.split(',')]))   

bolt_diameters=data[0]
pitch=data[3]
area=data[4]
bottom_ply=data[5]
ply_stiffness=data[6][0]
bottom_ply_const=data[7][0]
top_ply_thermal_expansion_coeff=data[8][0]
bottom_ply_thermal_expansion_coeff=data[9][0]
temp_diff=data[10][0]

# Make boltK a vector the same shape as bolt_diameters
boltK=10000.0*ones_like(bolt_diameters)

num_bolts=len(bolt_diameters)
# Make A a square matrix filled with 1's.
A=ones((num_bolts,num_bolts))

# row1 is a vector, the same shape as boltK.
row1=1/boltK

# No need for repeatedly calling eqn3. We can compute the 
# whole thing at once.
row3=-pitch/(bottom_ply*bottom_ply_const)-pitch/(area*ply_stiffness)

# arange is like range, but it makes a numpy array
c=arange(num_bolts)
# I wish I could get rid of this loop
for r in range(num_bolts-1):  
    # This is the equivalent of eqn2
    row2=row3[r]-row1
    choices=[row1,row2,row3[r]]
    conditions=[c==r+1,c==r,c<r]
    # select returns an array. The mth element of A[r] equals the mth element
    # of either row1, row2 or row3[r], depending on which condition is true.
    A[r]=select(conditions,choices,default=0)

B=(bottom_ply_thermal_expansion_coeff-top_ply_thermal_expansion_coeff)*temp_diff*pitch
B=append(B,0)
print(A)
print(B)
C=solve(A,B)
print C  

[/PHP]

---

### Post by Paul Miller on 2009-06-22
> **Can+~ said:**
> 
2. The word "input" is reserved.


That's not true.  "input" is the name of a builtin function.  Admittedly, most of the time, you don't want to use a variable with the same name as a builtin, because doing so reassigns that name, and that can get confusing.  But, there are legitimate reasons to shadow builtins like that, and to say it's always wrong to do so is, well, wrong. 

That said, the code here has no reason to mask the input builtin function, so it should use a different name, like "data" or something.

---

### Post by Greyed on 2009-06-23
> **eckeroo said:**
> Just wanted to show off my first ever working Python code [Python 2.5] and ask a few questions and get some opinions.

Very nice first project.  Heck, even better than some of my not-so-first Python projects.  ;)

[php]
for a in aList:
    if a.find('#')<0 and a <> '\n':
[/php]

Others have addressed points but I haven't seen anything touch on this one.  First, is it your intention to skip any line with a # anywhere in it or just in the first position?  IE,

[php]
# full line comment
Some random data # with a comment at the end
[/php]Your a.find('#') will catch both and ignore the entire line where normal commenting convention (as the highlighting suggests) looks for the # and ignores anything past it.

As pointed out, <> is depreciated.  Also searching for just '\n' means you're not stripping the lines.  A good practice since wayward newlines can cause problems later on in the program.  It also has the side effect, as Unutbu showed but didn't explain, of making it so an empty line (IE, '\n') becomes an empty string (IE, '') and thus evaluates to a negative.  Then you can just test its truth/false directly.

[php]
>>> a = 'foo\n'
>>> if a.strip():
...     print a
... 
foo

>>> a = '\n'
>>> if a.strip():
...     print a
... 
[/php]

---

### Post by eckeroo on 2009-06-23
Thanks everyone for the advice.

To answer a few points:

yes, my intention was that a # character in the input file represented a comment thereafter and not to ignore the entire line. I'll try and improve it.

I'm looking at importing the data line by line instead of using 'readlines()'

I'll check out the Numpy arrays.

I'm getting rid of the variable names and replacing them with more descriptive ones.

I'll not use 'input' as a variable name from now on.

I'll leave out wrapping my whole code in a function for now (I need to create another program to call it from first!)

A wee confession: although this is my first Python code, I've got a little experience on VBA, so it's not my first ever program. The Scipy module means I can do some clever stuff. I also intend to do frequent recycling, so it will be worthwhile to get this thermal code up to scratch and ready for a GUI for when I get on to them.

I'll update this code at the weekend using the advice given and I'll post up the new and improved code.

Cheers

---

### Post by blackxored on 2009-06-23
> **eckeroo said:**
> Hello all,

Just wanted to show off my first ever working Python code [Python 2.5] and ask a few questions and get some opinions.

I've created a program for an engineering purpose (works out bolt loads due to thermal expansion). I was drawn to code this program in Python to take advantage of the SciPy module with its linear algebra features.

My intention is to do all my engineering programs in Python. I am currently reading 'Learing Python'2005 edition by O'Reilly and I'm up to part III. I used Josh Cogliati's 'Non-Programmers Tutorial For Python' to get started. The O'Reilly book is good for filling in the details.

I eventually want to start coding TKinter GUIs, currently my code inputs/output with text files.

Have a gander:
[php]
#Program to calculate the thermal stresses between a row of bolts for
#a stack of two plies.

#line that reads input data into a list of strings

#bolt forces as applied to the top layer
input =open('thermal input.txt')       
aList=input.readlines()

data=[]

for a in aList:
    if a.find('#')<0 and a <> '\n':
        b = a.split(',')
        c = [float(d) for d in b] 
        data.append(c)

from scipy import *
from scipy.linalg import *

#general equations
def eqn1(boltno):    
    return 1/boltK[boltno]

def eqn2(pitch,topA,btmA,topE,btmE,boltno):
    return -pitch/(btmA*btmE)-pitch/(topA*topE)-1/boltK[boltno]
    
def eqn3(pitch,topA,btmA,topE,btmE):
    return -pitch/(btmA*btmE)-pitch/(topA*topE)

boltK=[]
for a in data[0]:
    b= 10000.0    #'some function TBAL that calculates bolt shear stiffness using the huth method'
    boltK.append(b)

matrix=[]
    
for r in range(0,len(data[3])):
    
    row=[]
    for c in range(0,len(data[0])):
        
        if c==r+1:
            b = eqn1(c)
        elif c==r:
            b = eqn2(data[3][r],data[4][r],data[5][r],data[6][0],data[7][0],c)
        elif c<r:
            b = eqn3(data[3][r],data[4][r],data[5][r],data[6][0],data[7][0])
        elif c>r+1:
            b = 0
        row.append(b)
    
    matrix.append(row)

row=[]
for a in data[0]:
    row.append(1)

matrix.append(row)

A = mat(matrix)

matrix =[]
for a in range(0,len(data[3])):
    row=[]
    b = data[9][0]*data[3][a]*data[10][0]-data[8][0]*data[3][a]*data[10][0]
    row.append(b)
    matrix.append(row)
row=[0]
matrix.append(row)
B = mat(matrix)
C=solve(A,B)
print C[/php]And the 'thermal input.txt' file:

#Input file for thermal
[php]
#bolt diameters (mm)                
7.94, 9.53, 7.94, 7.94, 6.35

#Bolt stiffnesses (MPa)                
110000, 110000, 110000, 110000, 110000

#ply thicknesses at bolts(mm)            
5, 5.1, 5.1, 5.2, 5.1

#length of pitch between bolts (mm)        
15, 15.6, 15.8, 16

#effective areas between bolts (mm^2)
#top ply                    
200, 210, 210, 200

#bottom ply                    
200, 210, 210, 200

#ply stiffnesses (MPa)                
#top ply                    
66340

#bottom ply                    
45000

#thermal expansion coeefficients
#top ply                    
2.3E-5

#bottom ply                    
1.2E-6

#temperature difference (degrees centrigade/Kelvin)
50

#huth coeefficent                
2.6[/php]The scipy module is excellent, saves me having to write the code for solving matrices. However, it does take a noticeable amount of time to import when I run the program. If I'm just using one function from the whole module, is there some way of just importing the scipy functions that are used?

my points:

use from .. import .. with care, but sometimes you should use it, right?
[PHP]aList = input.readlines()[/PHP]
that's one of the most inefficient ways or reading a file, since it reads it all at once, without buffering. One simple alternative, using the iteration protocol and list comprehensions:
[PHP]
aList = [line for line in file_name]
[/PHP]
<> is deprecated in python2.5 and I don't remember now whether it has been removed in 2.6, 3.0 or not removed at all, but is a fact it will. 

Your code seems like an old C veteran. I'm talking about conventions, method/variable names, the way of aproaching loops. But anyways this is your first start. 

hope it helps you something, ran out of time.

---

### Post by Greyed on 2009-06-26
> **eckeroo said:**
> I'm looking at importing the data line by line instead of using 'readlines()'


I think someone else mentioned it already.  File handles can be used like any other iterator.  IE, the standard "for x in y" works just fine.

[php]
infile = open('spam')
for line in infile:
    print(line)
[/php]

---

### Post by smartbei on 2009-06-26
> **blackxored said:**
> my points:
```
aList = input.readlines()
```
that's one of the most inefficient ways or reading a file, since it reads it all at once, without buffering. One simple alternative, using the iteration protocol and list comprehensions:
```

aList = [line for line in file_name]

```

Using readlines is slightly faster (around 10%) from my tests. This makes sense, since readlines is probably implemented in C, and so would be faster than implementing the same thing using a list comprehension in python. Of course, simply iterating over the file object is better, since it will only use the memory for a single row at any point.

I am not sure what you mean by buffering - using a list comprehension in the manner you described gives you the exact same result as calling .readlines() - I think you have list comprehensions and iterators (or perhaps generator expressions) confused.

---

### Post by Paul Miller on 2009-06-26
> **smartbei said:**
> Using readlines is slightly faster (around 10%) from my tests. This makes sense, since readlines is probably implemented in C, and so would be faster than implementing the same thing using a list comprehension in python. Of course, simply iterating over the file object is better, since it will only use the memory for a single row at any point.

I am not sure what you mean by buffering - using a list comprehension in the manner you described gives you the exact same result as calling .readlines() - I think you have list comprehensions and iterators (or perhaps generator expressions) confused.

I don't think .readlines() is faster than for line in file because .readlines() is implemented in C.  Rather, it's because .readlines() slurps the whole file into memory first (using buffered IO), and you end up iterating over something that's entirely in memory.

---

### Post by nvteighen on 2009-06-26
> **Paul Miller said:**
> I don't think .readlines() is faster than for line in file because .readlines() is implemented in C.  Rather, it's because .readlines() slurps the whole file into memory first (using buffered IO), and you end up iterating over something that's entirely in memory.
Er... Any call to open() will load the whole file into memory. You always read from memory unless you start using device block reading (à la **dd**).

---

### Post by monraaf on 2009-06-26
> **nvteighen said:**
> Er... Any call to open() will load the whole file into memory. You always read from memory unless you start using device block reading (à la **dd**).

I don't think so.  I did a quick test with a million line text file (63MB).

With:

```

f = open ('foo')
aList = f.readlines()

```

and:

```

f = open ('foo')
aList = [line for line in f]

```

Resident memory of the python interpreter jumped to 100MB

With:
```

f = open ('foo')
for line in f:
    print line

```

Resident memory remained low at ~3MB

---

### Post by asdfhjkla on 2009-06-26
> **monraaf said:**
> I don't think so.  I did a quick test with a million line text file (63MB).

With:

```

f = open ('foo')
aList = f.readlines()

```

and:

```

f = open ('foo')
aList = [line for line in f]

```

Resident memory of the python interpreter jumped to 100MB

With:
```

f = open ('foo')
for line in f:
    print line

```

Resident memory remained low at ~3MB

Is that really a fair test though? With the first two you are building a list - which is actually stored in memory. With the third you just take a line at a time and print it.

---

### Post by simeon87 on 2009-06-26
> **asdfhjkla said:**
> Is that really a fair test though? With the first two you are building a list - which is actually stored in memory. With the third you just take a line at a time and print it.

That's the idea though: by not storing every line in memory but just processing one at a time (which is what you ultimately want), you can save lots of memory.

---

### Post by monraaf on 2009-06-26
> **simeon87 said:**
> That's the idea though: by not storing every line in memory but just processing one at a time (which is what you ultimately want), you can save lots of memory.

Exactly

---

### Post by asdfhjkla on 2009-06-26
> **simeon87 said:**
> That's the idea though: by not storing every line in memory but just processing one at a time (which is what you ultimately want), you can save lots of memory.

> **monraaf said:**
> Exactly

Good point. I'm not thinking straight today :roll:

---

### Post by Greyed on 2009-06-26
> **Paul Miller said:**
> I don't think .readlines() is faster than for line in file because .readlines() is implemented in C.  Rather, it's because .readlines() slurps the whole file into memory first (using buffered IO), and you end up iterating over something that's entirely in memory.

The form given...

[php]
aList = [line for line in f]
[/php]...and readlines() both pull the entire file into memory.  Don't believe me?  Believe the code.

[php]
>>> infile = open('5lines')
>>> a = infile.readlines()
>>> infile.close()
>>> infile = open('5lines')
>>> b = [line for line in infile]
>>> infile.close()
>>> a
['line 1\n', 'line 2\n', 'line 3\n', 'line 4\n', 'line large value of 4 which comes to 5.\n']
>>> b
['line 1\n', 'line 2\n', 'line 3\n', 'line 4\n', 'line large value of 4 which comes to 5.\n']
>>> if a == b:
...     print "Tada!"
... 
Tada!
[/php]Identical outcomes, difference is that the first is implemented mostly in C under the hood while the latter is done in Python with the associated overhead.

> **nvteighen said:**
> Er... Any call to open() will load the whole file into memory. You always read from memory unless you start using device block reading (à la **dd**).

  If that were the case then why does the file object have both read() and seek() methods?

[quote=Python 2.6.2 Documentation]
file.read([*size*])Read at most *size* bytes from the file (less if the read hits EOF before obtaining *size* bytes).
 Note
 This function is simply a wrapper for the underlying fread C function, and will behave the same in corner cases, such as whether the EOF value is cached.
 
 file.seek(*offset*[, *whence*])Set the file&#8217;s current position, like stdio&#8216;s fseek.[/quote]

---

### Post by nvteighen on 2009-06-27
When discussing about low-level issues, you ought to know how C works or you will misunderstand everything!

```

#include <stdio.h>

int main(void)
{
    FILE *myfile = fopen("file", "r");

    char a[90]; /* Using a stack-based buffer to simplify example. */
    fgets(a, sizeof(a), myfile); /* Reading file into variable. */

    printf("%s\n", a); /* Print! */
    
    fclose(myfile);

    return 0;
}

```

If you see, myfile is a pointer to some memory chunk. The I/O operations like fprintf(), fscanf() and friends (**fgets()** in the example), if the FILE * would be read stagewise (like popping a stack), then those functions would need a double pointer as argument so, in case there's reallocation they could adapt the pointer to the new position... but that's not the case, so the FILE * during its usage in C is never changed when accessed. Conclusion: The memory address used is the definite one and therefore the file is loaded entirely there.

EDIT: Passing that code through valgrind will show that just 1 allocation is done.

Python uses the C functions. No matter how you access the file, the open() method will call fopen(). The memory usage is the same, believe me or better, believe C.

---

### Post by monraaf on 2009-06-27
> **nvteighen said:**
> 
If you see, myfile is a pointer to some memory chunk. The I/O operations like fprintf(), fscanf() and friends (**fgets()** in the example), if the FILE * would be read stagewise (like popping a stack), then those functions would need a double pointer as argument so, in case there's reallocation they could adapt the pointer to the new position... but that's not the case, so the FILE * during its usage in C is never changed when accessed. Conclusion: The memory address used is the definite one and therefore the file is loaded entirely there.

I'm sorry but you're wrong here. The FILE* is just a pointer to a structure, allocated by the C library on fopen, that holds the OS specific file descriptor, some pointers to buffers and some other information, and should really be treated as an opaque handle.

Reading the entire contents of a file into memory by merely opening it would be a rather inefficient approach that neither Python nor the standard C library takes.

---

### Post by nvteighen on 2009-06-27
> **monraaf said:**
> I'm sorry but you're wrong here. The FILE* is just a pointer to a structure, allocated by the C library on fopen, that holds the OS specific file descriptor, some pointers to buffers and some other information, and should really be treated as an opaque handle.

Reading the entire contents of a file into memory by merely opening it would be a rather inefficient approach that neither Python nor the standard C library takes.
Hmm... I did some tests and ran them through gdb to unveil the FILE *'s mysteries.

Ok, it seems that what it does is to take the file after the first access and not on fopen().

Here's the sample source:
```

#include <stdio.h>

int main(int argc, char **argv)
{
    FILE *myfile = fopen(argv[1], "r");

    if(myfile != NULL)
    {
        while(!feof(myfile))
            printf("%c", fgetc(myfile));
    
        fclose(myfile);
    }
    else
        fprintf(stderr, "Argh! %s couldn't be opened!", argv[1]);

    return 0;
}

```

Opening /usr/share/common-licenses/GPL through it, placing a breakpoint at line 10, at the first iteration of our while-loop, we get this:
```

(gdb) print *myfile
$1 = {_flags = -72539000, _IO_read_ptr = 0x0, _IO_read_end = 0x0, 
  _IO_read_base = 0x0, _IO_write_base = 0x0, _IO_write_ptr = 0x0, 
  _IO_write_end = 0x0, _IO_buf_base = 0x0, _IO_buf_end = 0x0, 
  _IO_save_base = 0x0, _IO_backup_base = 0x0, _IO_save_end = 0x0, 
  _markers = 0x0, _chain = 0xb7f74560, _fileno = 6, _flags2 = 0, 
  _old_offset = 0, _cur_column = 0, _vtable_offset = 0 '\0', _shortbuf = "", 
  _lock = 0x9eab0a0, _offset = -1, __pad1 = 0x0, __pad2 = 0x9eab0ac, 
  __pad3 = 0x0, __pad4 = 0x0, __pad5 = 0, _mode = 0, 
  _unused2 = '\0' <repeats 39 times>}

```

If we let the program do one more iteration ("continue" command), asking for the same info, we get:
```

(gdb) print *myfile
$2 = {_flags = -72539000, 
  _IO_read_ptr = 0xb7f88001 "\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n o"..., _IO_read_end = 0xb7f89000 "d\220&#65533;&#65533;Kb&#65533;&#65533;", 
  _IO_read_base = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., 
  _IO_write_base = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., 
  _IO_write_ptr = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., 
  _IO_write_end = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., 
  _IO_buf_base = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <htt---Type <return> to continue, or q <return> to quit---
p://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., _IO_buf_end = 0xb7f89000 "d\220&#65533;&#65533;Kb&#65533;&#65533;", _IO_save_base = 0x0, 
  _IO_backup_base = 0x0, _IO_save_end = 0x0, _markers = 0x0, 
  _chain = 0xb7f74560, _fileno = 6, _flags2 = 0, _old_offset = 0, 
  _cur_column = 0, _vtable_offset = 0 '\0', _shortbuf = "", _lock = 0x9eab0a0, 
  _offset = -1, __pad1 = 0x0, __pad2 = 0x9eab0ac, __pad3 = 0x0, __pad4 = 0x0, 
  __pad5 = 0, _mode = -1, _unused2 = '\0' <repeats 39 times>}

```

There the text starts to appear... Continuing several times, we see how the myfile->_IO_read_ptr advances "consuming" the text. The "consumed" text can be found at myfile->_chain->_chain.
```

(gdb) print *myfile
$12 = {_flags = -72539000, 
  _IO_read_ptr = 0xb7f88023 "\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n of this license document, but chang"..., _IO_read_end = 0xb7f89000 "d\220&#65533;&#65533;Kb&#65533;&#65533;", 
  _IO_read_base = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., 
  _IO_write_base = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., 
  _IO_write_ptr = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., 
  _IO_write_end = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., 
  _IO_buf_base = 0xb7f88000 "\n\t\t    GNU GENERAL PUBLIC LICENSE\n\t\t       Version 3, 29 June 2007\n\n Copyright (C) 2007 Free Software Foundation, Inc. <htt---Type <return> to continue, or q <return> to quit---
p://fsf.org/>\n Everyone is permitted to copy and distribute verbatim copies\n "..., _IO_buf_end = 0xb7f89000 "d\220&#65533;&#65533;Kb&#65533;&#65533;", _IO_save_base = 0x0, 
  _IO_backup_base = 0x0, _IO_save_end = 0x0, _markers = 0x0, 
  _chain = 0xb7f74560, _fileno = 6, _flags2 = 0, _old_offset = 0, 
  _cur_column = 0, _vtable_offset = 0 '\0', _shortbuf = "", _lock = 0x9eab0a0, 
  _offset = -1, __pad1 = 0x0, __pad2 = 0x9eab0ac, __pad3 = 0x0, __pad4 = 0x0, 
  __pad5 = 0, _mode = -1, _unused2 = '\0' <repeats 39 times>}

```
```

(gdb) print *myfile->_chain->_chain
$14 = {_flags = -72537468, 
  _IO_read_ptr = 0xb7f87000 "\t\t    GNU GENERAL PUBLIC LICENSE\n", 
  _IO_read_end = 0xb7f87000 "\t\t    GNU GENERAL PUBLIC LICENSE\n", 
  _IO_read_base = 0xb7f87000 "\t\t    GNU GENERAL PUBLIC LICENSE\n", 
  _IO_write_base = 0xb7f87000 "\t\t    GNU GENERAL PUBLIC LICENSE\n", 
  _IO_write_ptr = 0xb7f87001 "\t    GNU GENERAL PUBLIC LICENSE\n", 
  _IO_write_end = 0xb7f87000 "\t\t    GNU GENERAL PUBLIC LICENSE\n", 
  _IO_buf_base = 0xb7f87000 "\t\t    GNU GENERAL PUBLIC LICENSE\n", 
  _IO_buf_end = 0xb7f87400 "", _IO_save_base = 0x0, _IO_backup_base = 0x0, 
  _IO_save_end = 0x0, _markers = 0x0, _chain = 0xb7f74420, _fileno = 1, 
  _flags2 = 0, _old_offset = -1, _cur_column = 0, _vtable_offset = 0 '\0', 
  _shortbuf = "", _lock = 0xb7f750e8, _offset = -1, __pad1 = 0x0, 
  __pad2 = 0xb7f746c0, __pad3 = 0x0, __pad4 = 0x0, __pad5 = 0, _mode = -1, 
  _unused2 = '\0' <repeats 39 times>}

```

So, it seems that it loads the whole thing into memory... Watch how the myfile->_IO_read_base doesn't change its pointer value. IIRC, the file descriptor system only works using open() not fopen() in C.

Of course, I may be utterly wrong :p if so, please enlighten me! :)

---

### Post by monraaf on 2009-06-27
> **nvteighen said:**
> So, it seems that it loads the whole thing into memory... Watch how the myfile->_IO_read_base doesn't change its pointer value. IIRC, the file descriptor system only works using open() not fopen() in C.

Of course, I may be utterly wrong :p if so, please enlighten me! :)

Just because the standard IO library uses some kind of buffering strategy doesn't mean it will load the entire file contents in memory. Off course for small files the buffer used may large enough to hold the entire file contents. But it would be a rather silly approach to allocate a buffer large enough to hold the entire file contents regardless it's size. 

If the standard C library would load the entire contents of a file into memory, how on earth would I be able to open and read from a > 6GB matroska file that I have here when I got less then 2GB ram?

---

### Post by nvteighen on 2009-06-27
> **monraaf said:**
> Just because the standard IO library uses some kind of buffering strategy doesn't mean it will load the entire file contents in memory. Off course for small files the buffer used may large enough to hold the entire file contents. But it would be a rather silly approach to allocate a buffer large enough to hold the entire file contents regardless it's size. 

If the standard C library would load the entire contents of a file into memory, how on earth would I be able to open and read from a > 6GB matroska file that I have here when I got less then 2GB ram?
Point taken. Thanks! Learning is always fun :D

---

### Post by eckeroo on 2009-06-28
I've updated my code with the advice from this thread. I've left the matrix builder as is until I'm ready to use NumPy arrays. I was impressed by unutbu's demonstration of the array functions. The array functions use fewer lines of code and reduce the number of functions and loops required.

The only main change is the file reading code. It now reads line at a time and ignores all text after the # instead of ignoring the whole line.

[PHP]#Program to calculate the thermal stresses between a row of bolts for
#a stack of two plies.

#line that reads input data into a list of strings

#bolt forces as applied to the top layer

from scipy import *
from scipy.linalg import *

#all new and improved input code, disregards data only after the # and no longer uses readlines()

rawinput =open('thermal input.txt')
data=[]
for lines in rawinput:
    lines.rstrip()
    line = lines[:lines.find('#')]
    parsed = line.split(',')
    if bool(parsed[0])==True:
        flt = [float(entry) for entry in parsed]
        data.append(flt)
rawinput.close()       

#general equations
def eqn1(boltno):    
    return 1/boltK[boltno]

def eqn2(pitch,topA,btmA,topE,btmE,boltno):
    return -pitch/(btmA*btmE)-pitch/(topA*topE)-1/boltK[boltno]
    
def eqn3(pitch,topA,btmA,topE,btmE):
    return -pitch/(btmA*btmE)-pitch/(topA*topE)

boltK=[10000.0]*len(data[0])#'some function TBAL that calculates bolt shear stiffness using the huth method'


#arrange the simultaneous equations in matrix form, with x and y representing the column and row of the cell
#In future however, I will be using NumPy arrays to reduce the functions and loops - thanks to unutbu for
#demonstrating them to me!

matrix=[]
    
for y in range(len(data[3])):
    
    row=[]
    for x in range(len(data[0])):
        
        if x==y+1:
            cell = eqn1(x)
        elif x==y:
            cell = eqn2(data[3][y],data[4][y],data[5][y],data[6][0],data[7][0],x)
        elif x<y:
            cell = eqn3(data[3][y],data[4][y],data[5][y],data[6][0],data[7][0])
        elif x>y+1:
            cell = 0
        row.append(cell)
    
    matrix.append(row)

row=[1]*len(data[0])

matrix.append(row)

A = mat(matrix)

#arrange column matrix with equation constants

matrix =[]
for y in range(len(data[3])):
    x = [data[9][0]*data[3][y]*data[10][0]-data[8][0]*data[3][y]*data[10][0]]
    matrix.append(x)
x=[0]
matrix.append(x)

B = mat(matrix)

#solve simultaneous equations

print solve(A,B)[/PHP]

---

### Post by Greyed on 2009-06-28
> **eckeroo said:**
> The only main change is the file reading code. It now reads line at a time and ignores all text after the # instead of ignoring the whole line.

Very nice.  Just an observation.  After talking about the hash being in the middle of the line I was wonder how you would solve for it...

[php]
    line = lines[:lines.find('#')]
[/php]

...vs. how I would solve for it...

[php]
line = lines.split('#')[0]
[/php]

Always fun to see how a simple problem can spawn a variety of answers.  :D

---

### Post by unutbu on 2009-06-28
lines.rstrip() in nugatory, by which I mean it is filled with nougat, that white semihard candy which sticks to your teeth.

(Also, lines.rstrip() returns a string. It does not alter the value of the 'lines' variable.)

---

### Post by Can+~ on 2009-06-28
> **Greyed said:**
> Very nice.  Just an observation.  After talking about the hash being in the middle of the line I was wonder how you would solve for it...

[php]
    line = lines[:lines.find('#')]
[/php]

...vs. how I would solve for it...

[php]
line = lines.split('#')[0]
[/php]

Always fun to see how a simple problem can spawn a variety of answers.  :D

True. I think the second one is "clearer" though.

---

### Post by eckeroo on 2009-06-28
I was looking at a 'list comprehension' and wondered why the line.close() raised an error.

[PHP]lines = [line.rstrip( ) for line in open('thermal input.txt') if line[0]!='\n']    

line.close()[/PHP]

[PHP]
  File "test2.py", line 66, in <module>
    line.close()
AttributeError: 'str' object has no attribute 'close'[/PHP]

so I gather you don't need line.close() when you you use open() like this?

---

### Post by simeon87 on 2009-06-28
> **eckeroo said:**
> I was looking at a 'list comprehension' and wondered why the line.close() raised an error.

[PHP]lines = [line.rstrip( ) for line in open('thermal input.txt') if line[0]!='\n']    

line.close()[/PHP]

[PHP]
  File "test2.py", line 66, in <module>
    line.close()
AttributeError: 'str' object has no attribute 'close'[/PHP]

so I gather you don't need line.close() when you you use open() like this?

line is a string, you're now trying to 'close' a string which isn't possible. Or more formally put, the 'str' object has no attribute 'close'.

---

### Post by eckeroo on 2009-06-28
Would there be anything to close though to compliment the open?

---

### Post by ideaplan9 on 2009-06-28
> **eckeroo said:**
> Would there be anything to close though to compliment the open?

I don't think it is necessary because at that point *lines* is a string that need not be closed.  I actually think the file would be auto-closed after that statement anyways.  If you want to play it safe, declare a file variable outside.  Use it to retrieve the lines, and then close the file right after.

It is verbose, but it makes it easy to see that a file is being opened, used, then closed.

---

### Post by eckeroo on 2011-04-23
> I would really like to see what you do with Tk in the future.

I've now published a general purpose stress calc GUI manager using wxpython (TKinter I've been informed isn't as good)

[http://bazaar.launchpad.net/~eckeroo/+junk/yeoman/files](http://bazaar.launchpad.net/~eckeroo/+junk/yeoman/files)

I've created a new thread on the Ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=1737568](http://ubuntuforums.org/showthread.php?t=1737568)

Check it out!

---

