---
title: "C: Reading in multiply numbers from a file"
date: 2008-10-02
forum: Programming Talk
---

### Post by Shaunny23 on 2008-10-02
Hi I'm someone who must really suck at C cause I've been trying to read in a matrix from a file, the format is

2 3
1 10 4.56 3.24 .543
2 8 3.43 1.23 4.53

What I wanna do it get each of the figures and store them into a variable so that I can then use to calculate the total. Can anyone help?

---

### Post by dwhitney67 on 2008-10-02
You are going to need more than just one variable... at least 3.  You have to read in the number of columns and then rows (or the other way around).  Then the values (which appear to be floats or doubles).

The first for the structure... it should model an NxM matrix... or in C lingo, an array of an array.  Since you do not know the value of N or M, you should plan on dynamically allocating the 2-dim array.

Read in the first two numbers (presuming of course you have opened the file):
[PHP]unsigned int rows;
unsigned int cols;

fscanf( fp, "%d %d", &rows, &cols );[/PHP]

Then allocate the array of array:
[php]
// Allocate the number of rows (N)
float ** matrix = malloc( rows * sizeof(float *) );

// Allocate the number of columns (M)
for ( unsigned int r = 0; r < row; ++r )
{
  matrix[r] = malloc( cols * sizeof(float) );
}

// Read in the remaining data from the file
for ( unsigned int r = 0; r < rows; ++r )
{
  for ( unsigned int c = 0; c < cols; ++c )
  {
    fscanf( fp, "%f", &(matrix[r][c]) );
  }
}
[/php]

You should now have all of your values read in.  Remember, the first array subscript is the row, the second is the column.

When you are done with the assignment... that is, your class exercise, relinquish the memory allocated.
[php]
for ( unsigned int r = 0; r < rows; ++r )
{
  free( matrix[r] );
}
free( matrix );
[/php]

P.S.  My answer may be inadequate; I am under the influence of Beer Chang.
-----

Update... Upon looking at the OP again, I do not understand the layout of the data.  I thought the "2 3" represented the rows/columns of the matrix.  Why are there 5 sets of numbers for the columns?

---

### Post by nvteighen on 2008-10-02
@OP: The code by dwhitney67 seems correct to me, but be aware that he uses C99, so, you either have to compile using the **--std=c99** flag or, change the for loops that look like this:

[php]
for(unsigned int i = 0; i < 45; i++)
{
...
}
[/php]

into:
[php]
unsigned int i; /* Or assign here, if you like. */
for(i = 0; i < 45; i++)
{
...
}
[/php]

---

### Post by Shaunny23 on 2008-10-05
Wow that was a quick response.

@dwhitney
The 2 and 3 are both values as well. They are separate values which i need to store to be shown in the main method. The rest of the values (the one on the bottom) are the values which i need to add up, by rows. So my main should show the first two values of the matrix then the total of each of the rows below it.

---

### Post by Shaunny23 on 2008-10-05
bump

---

### Post by dwhitney67 on 2008-10-05
> **Shaunny23 said:**
> bump

Are you kidding?  I gave enough information in my previous post for you to use (that is, how to read in data).  You cannot expect someone to complete the entire exercise for you!

Show us your efforts that you have made to solve the task, and if you have any questions or problems, let us know.

---

### Post by Shaunny23 on 2008-10-05
Yeah i finally got it to work for me. Thanks for the advice :)

---

### Post by dwhitney67 on 2008-10-06
> **Shaunny23 said:**
> Yeah i finally got it to work for me. Thanks for the advice :)

:confused:

You solved the entire problem?  Good for you!

---

