---
title: "(C++) Convert values to a matrix"
date: 2010-01-22
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-01-22
I acctually have 2 questions.
[I]EDIT:(While your here, I was also curious if there is a random number generator in c++)

[/I] 1)Is it possible to create a matrix from given input values.

--------------
Ex.

I have three columns I want to make
Entering 1 value at a time (or one row)
I give values 

1 2 3
then
3 2 1
then 
1 2 3

and it outputs those to a file that has values

1 2 3
3 2 1 
1 2 3 

From here lets say I want to get value

Input) R1C2
Outputs) 2

or i ask for

input) R2C3
outputs) 1

And more importantly I for all values
and it prints the matrix.

[B]{The end goal here is for me to write a program that not only makes a list for me but will allow me to search the matrix for certain values, and then print ONLY the rows that contain those values.}
{Good starting point is to find how to create the matrix, I will try to figure out the rest from there.}
[/B]
2.) Is it possible to seperate values in a string
---------------------------------------
ex.

I enter the string 0U1F3GH

and the program sets

C1=0
C2=U
C3=1
C4=F
C5=3
C6=G
C7=H





**{{Thx for the help madcow -- I will try that.}}**

---

### Post by MadCow108 on 2010-01-22
of course its possible.

some hints.
use the streams for easy input
double x,y,z;
cin >> x >> y >> z
gets 3 whitespace separated doubles and saves them in the variables.

a matrix you can save in lots of different ways.
a simple one would be to use stack arrays:
double matrix[MAX_ROWS][MAX_COLUMNS]

there are lots more ways, just play around.

separating strings into single characters is trivial, as strings are saved as single characters in some container anyway
just use the [] operator of string to access them.

---

