---
title: "[SOLVED] File handling and 2d arrays"
date: 2008-01-14
forum: Programming Talk
---

### Post by S15_88 on 2008-01-14
quick question i've written up a little something but i'm stuck as to what to do now.  

The purpose of my program is to open a text file containing numbers having this format:

2 5
3 5 7 8 9 
1 2 1 1 5

the purpose of the 2 5 is to indicate 2 rows, 5 colums.  
I need to somehow take those 2 numbers to create a 2d integer array of that size...in this case int a[2][5];

then calculate the sum of the colums and output it like so:

4 7 8 9 14

This is what i have so far but i'm not sure how exactly to grab the first two numbers and make an array of that size then store the rest of the numbers in their appropriate space and then sum them and output it.  any help would be greatly appreciated!

thanks, Alain

```

#include <stdio.h>

int main()
{
    char filename[50];
    int i, j, k, a[50][50];
 
    FILE * infile;
    
    printf("Please Enter The Name And The Extension Of The File You Would Like To Fetch \n");
    scanf("%s", filename);

    infile = fopen(filename, "r");    
    
    if(infile == NULL) 
    {
        printf("Error: can't open file.\n");
        return 1;
    }
    else
    {
        printf("File opened successfully.\n");
        k = 0;
    }
    while(!feof(infile))
    {
        fscanf(infile, "%d", &a[i][j]);
        k++;
    }

    for(i=0; i<k; i++)
    {
        for(j=0; j<k; j++)
        {
            printf("%d\n", a[i][j]);
        }
    }

    fclose(infile);
	       
    return 0;
}

```

---

### Post by S15_88 on 2008-01-14
just thought i'd give you a headsup i'm compiling with gcc  -ansi -Wall

thanks, Alain

---

### Post by dwhitney67 on 2008-01-15
1.  Open the file
2.  Verify the file is open; exit if not.
3.  Use fscanf() to read the two numbers (representing the number of rows and columns)
4.  Declare the array as a pointer to a pointer of ints (e.g. int **array)
5.  Allocate, using malloc(), the number of rows.
6.  For each row, allocate the number of integers to be stored, or in your case, the number of columns multiplied by 4 bytes.  An integer takes up 4 bytes.

For instance:

[PHP]int **array = malloc( rows );
for ( int r = 0; r < rows; ++r )
{
  array[r] = malloc( sizeof(int) * cols );
}[/PHP]

From this point onward you should be able to access array as you normally would using the square-brackets.  E.g.  array[1][3] = 10;

P.S.  I always compile C programs with:  gcc --std=c99

---

### Post by S15_88 on 2008-01-15
i've done some tinkering and i am able to read the numbers for the rows and columns form the file...create an array of that size...store the rest of the numbers in the text file to the array!

now i'm stuck!

once they are in the array how would i add up the values of the columns then print them out?

here is my new code:
```

#include <stdio.h>

int main()
{
    char filename[50];
    int i, j, row, col;
    int **array;

    FILE * infile;            /*File pointer*/
    
    printf("Please Enter The Name And The Extension Of The File You Would Like To Fetch \n");
    scanf("%s", filename);/*Reads in user specified filename and stores it in character array filename*/

    infile = fopen(filename, "r");/*opens the file specified by the user*/  

    if(infile == NULL) 
    {
        printf("Error: can't open file.\n");
        return 1;
    }
    else
    {
        printf("File opened successfully.\n");
    

        fscanf(infile, "%d%d", &row, &col);
        /*printf("%d %d\n", row, col);*/
    
        array = malloc(sizeof(int*)*row);

        for(i=0;i<row;i++)
        {
            array[i] = malloc(sizeof(int)*col);
            
            for(j=0;j<col;j++)
            {
                fscanf(infile, "%d", &array[i]); 
                /*printf("%d\n", array[i]);*/
            }
        }
        
    }
    return 0;
}
/*    for(x=0;x<row;x++)
    {
        for(y=0;y<col;y++)
        {
             printf("%d", array[row][col]);
        }
    }
*/

```

Thanks for all the help!
Alain

---

### Post by dwhitney67 on 2008-01-15
> **S15_88 said:**
> 
```

        for(i=0;i<row;i++)
        {
            array[i] = malloc(sizeof(int)*col);
            
            for(j=0;j<col;j++)
            {
                fscanf(infile, "%d", &array[i]); 
                /*printf("%d\n", array[i]);*/
            }
        }

```

Your code should be:
```

        for(i=0;i<row;i++)
        {
            array[i] = malloc(sizeof(int)*col);
            
            for(j=0;j<col;j++)
            {
                fscanf(infile, "%d", **&array[i][j]**); 
            }
        }

```

Remember... it is a 2-dimensional array, not a single dimension.

---

### Post by S15_88 on 2008-01-15
righty right...now as for the adding of the colums i was thinking of making another array, 1dimensional, and putting something like:
newarray = array[0][col] + array[1][col];

inside the nested for loop posted above...i'm about to try it out...if you've got any ideas on how to go about adding the columns it would be greatly appreciated.

Thanks, Alain

---

### Post by dwhitney67 on 2008-01-15
This exercise of yours seems very trivial.  By now I would hope that you have an understanding of for-loops, declaring arrays, initializing arrays, allocating memory, etc.

The rest of the stuff you are asking is implementation, which I could tell you the answer, but then you would learn nothing in as far as s/w design is concerned.

If you need help with syntax or if you've come to a roadblock, then post your query.  But please don't expect me or anyone else to serve you the complete answer to what seems like a homework assignment.  IMO, I've already supplied you with more than enough information on how to complete your exercise.  Use your intuition/imagination to come up with a solution.  The thoughts you posted seem reasonable, so go with that.

P.S.  The only thing that I have not discussed in my previous posts concerns the de-allocation of the memory you have allocated.  You will need to read up on the free() C-library call.  Reference the man-pages for info on that topic.

---

### Post by S15_88 on 2008-01-15
thanks for all your help so far, i decided to just statically allocate the memory for the array as oppose to using malloc(), and i've almost got the column addition working!  thanks again for the help!

Alain

---

### Post by Majorix on 2008-01-15
Pardon my ignorance, but I am no expert in this :D
> **dwhitney67 said:**
> [PHP]int **array = malloc( rows );
for ( int r = 0; r < rows; ++r )
{
  array[r] = malloc( sizeof(int) * cols );
}[/PHP]

My questions:
1. Is "array" a keyword or just a random variable name?
2. What is an "int **array"? I know a little about pointers, and I thought you read them from right to left; but this would produce a "pointer to a pointer" in this case? How come?

Thanks for clarifying :)

---

### Post by Wybiral on 2008-01-15
> **Majorix said:**
> Pardon my ignorance, but I am no expert in this :D


My questions:
1. Is "array" a keyword or just a random variable name?
2. What is an "int **array"? I know a little about pointers, and I thought you read them from right to left; but this would produce a "pointer to a pointer" in this case? How come?

Thanks for clarifying :)

You use a pointer-to-pointer because the column is a dynamic array (which is handled by a pointer) and the row is a dynamic array of columns (handled by a pointer). So a row is basically an array of pointers, each pointer being a dynamically allocated column. Multidimensional arrays work like this too. And yes, "array" is the variable name.

---

### Post by Majorix on 2008-01-15
OK thanks a lot, I think I got it... We have to make it a pointer because the row is a dynamic array itself too. So an int **array is a dynamic array of a dynamic array. I think. Haha, pointers always confuse me, that's the whole reason I stay out of C/C++ :D

Sorry for interrupting but I see the thread is SOLVED anyways :) Sorry again.

---

### Post by Wybiral on 2008-01-15
> **Majorix said:**
> So an int **array is a dynamic array of a dynamic array. I think.

Basically, yes. It might help to think back to C-style strings where "char*" is a string (because it's an array of characters) so when you need an array of strings you would use "char**" because you need an array of arrays.

Here's a fun question that usually makes people scratch their heads, is "char *x[]" a pointer to an array, or is it an array of pointers? :)

---

