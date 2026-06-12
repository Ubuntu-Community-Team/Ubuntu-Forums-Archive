---
title: "C: deleting row and column from matrix"
date: 2013-07-11
forum: Programming Talk
---

### Post by erotavlas on 2013-07-11
Hi,

I suppose to have the following matrix A) and I want to remove a generic row and column.                                    
For instance the second row and column, then I get B). How can I realize it in C? I cannot figure out how to do.
    
    A)
a00 a01 a02
a10 a11 a12
a20 a21 a22
B)
a00 a02
a20 a22

Thank you

---

### Post by nvteighen on 2013-07-11
I hope you're not using a double-pointer "matrix", because that makes everything harder.

1) If you're allowed to use a library, take a look at the GNU Scientific Library. [http://www.gnu.org/software/gsl/manual/html_node/Matrices.html](http://www.gnu.org/software/gsl/manual/html_node/Matrices.html)
2) If not, I'd go for a data structure that implements the matrix in C-order, i.e. using a flat structure, so that elemet (row, column) = row * row_size + column.

---

### Post by erotavlas on 2013-07-12
Hi,

I'm using an array in particular a pointer to it. Yes, I'm using the flat structure (row, column) = row * row_size + column and the size of matrix is fixed (preallocated at the beginning in the main). I cannot figure out an algorithm that allows to me to remove a generic row-column from my matrix. As in the example reported above, I have
A)
a00 a01 a02
a10 a11 a12
a20 a21 a22
B)
a00 a02
a20 a22

They are represented in my flat structure as a00 a01 a02 | a10 a11 a12 | a20 a21 a22 -> a00 a02 0 | a20 a22 0 | 0 0 0.
Any suggestion is appreciated.
Thank

---

### Post by nvteighen on 2013-07-12
Observe the following: if you're deleting column x, then you're deleting everything that is x modulo row_size in your linear order; if you're deleting row x, you're deleting everything that is between row_size * x and row_size * (x + 1) in your linear order.

---

### Post by erotavlas on 2013-07-12
> **nvteighen said:**
> Observe the following: if you're deleting column x, then you're deleting everything that is x modulo row_size in your linear order; if you're deleting row x, you're deleting everything that is between row_size * x and row_size * (x + 1) in your linear order.

Ok you are right, but I have also to move the element from the rows and columns that have greater indexes w.r.t. the row-column that I'm removing. For instance if you consider the same example in which the first row and column are removed, the others elements have to be moved
A)
a00 a01 a02
a10 a11 a12
a20 a21 a22
B)
a11 a12
a21 a22
and the linear representation is a00 a01 a02 | a10 a11 a12 | a20 a21 a22 -> a11 a12 0 | a21 a22 0 | 0 0 0. So it seems hard to do. I have not brilliant idea.
Thank

---

### Post by nvteighen on 2013-07-12
Why move them? Return a new matrix and leave the original untouched ;)

---

### Post by erotavlas on 2013-07-12
Ok, if I can copy the matrix with deleted row and column in other matrix it's straightforward. Is there the possibility to do it in place without allocating another matrix?

Thank

---

### Post by alan9800 on 2013-07-12
the following code (extremely basic, to be honest) does what you are looking for, but it needs to be be strongly improved for becoming an acceptable piece of software (I'm sorry but I'm not a C programmer)```
#include <stdio.h>

#define DELETED_ROW 1
#define DELETED_COLUMN 1


int main ()
{
    int A[3][3], B[2][2];
    int i, j;
    for (i = 0; i < 3; i++)
        for (j = 0; j < 3; j++)
            A[i][j] = i * 3 + j + 1;
    for (i = 0; i < 3; i++)
    {
        printf("\n");
        for (j = 0; j < 3; j++)
            printf("A[%d][%d]=%d\t", i, j, A[i][j]);
    }
    for (i = 0; i < 3; i++)
        if (i != DELETED_ROW)
        {
            for (j = 0; j < 3; j++)
                if (j != DELETED_COLUMN)
                {
                    if (i < DELETED_ROW && j < DELETED_COLUMN)
                        B[i][j] = A[i][j];
                    else if (i < DELETED_ROW && j > DELETED_COLUMN)
                        B[i][j-1] = A[i][j];
                    else if (i > DELETED_ROW && j < DELETED_COLUMN)
                        B[i-1][j]=A[i][j];
                    else
                        B[i-1][j-1]=A[i][j];
                }
        }
    for (i = 0; i < 2; i++)
    {
        printf("\n");
        for (j = 0; j < 2; j++)
            printf("B[%d][%d]=%d\t", i, j, B[i][j]);
    }
    return 0;
}
```

---

### Post by erotavlas on 2013-07-13
> **alan9800 said:**
> the following code (extremely basic, to be honest) does what you are looking for, but it needs to be be strongly improved for becoming an acceptable piece of software (I'm sorry but I'm not a C programmer)```
#include <stdio.h>

#define DELETED_ROW 1
#define DELETED_COLUMN 1


int main ()
{
    int A[3][3], B[2][2];
    int i, j;
    for (i = 0; i < 3; i++)
        for (j = 0; j < 3; j++)
            A[i][j] = i * 3 + j + 1;
    for (i = 0; i < 3; i++)
    {
        printf("\n");
        for (j = 0; j < 3; j++)
            printf("A[%d][%d]=%d\t", i, j, A[i][j]);
    }
    for (i = 0; i < 3; i++)
        if (i != DELETED_ROW)
        {
            for (j = 0; j < 3; j++)
                if (j != DELETED_COLUMN)
                {
                    if (i < DELETED_ROW && j < DELETED_COLUMN)
                        B[i][j] = A[i][j];
                    else if (i < DELETED_ROW && j > DELETED_COLUMN)
                        B[i][j-1] = A[i][j];
                    else if (i > DELETED_ROW && j < DELETED_COLUMN)
                        B[i-1][j]=A[i][j];
                    else
                        B[i-1][j-1]=A[i][j];
                }
        }
    for (i = 0; i < 2; i++)
    {
        printf("\n");
        for (j = 0; j < 2; j++)
            printf("B[%d][%d]=%d\t", i, j, B[i][j]);
    }
    return 0;
}
```

Hi,
your solution works but requires two matrices while I'm searching a solution that works directly with the same matrix. Moreover, the matrix is stored as a single array.
Thank anyway

---

### Post by trent.josephsen on 2013-07-13
You need to put in some effort mate. alan was kind enough to give you an almost ready-made solution that just needs a little bit of tweaking. Don't expect people to do your homework for you; take a stab at it, then post the code here when you get stuck.

---

### Post by nvteighen on 2013-07-13
I don't get why it has to be made in-place. It can be done, of course, but my take (of course, due to my FP influence) would be to have this as a function that maps two matrices through deletion/manipulation of rows and columns. Then, if you want to have a destructive function, take the functional one and make the result be saved in the original variable. OK, not the most efficient thing, but quite a good way to start thinking about the problem.

---

### Post by Warren Hill on 2013-07-13
If we consider a simple 2 dimensional matrix say 3 x 4 (3 rows by 4 columns)

A00 A01 A02 A03
A10 A11 A12 A13
A20 A21 A22 A23


This could be treated as a simple linear array

A[] = {A00, A01, A02, A03, A10, A11, A12, A13, A20, A21, A22, A23}

Now let row be the row number (0 to 2) and col be the column number (0 to 3) 

We also let ROWS be the number of rows and COLS be the number of columns.

Any element can then be found within the array as

item(row, col) = A[row*ROWS+col];

If you want to delete a row say row one

then our array would become

A[] = {A00, A01, A02, A03, A20, A21, A22, A23}

Deleting a row is therefore just a case of deleting some elements from the array in this case elements 4 to 7 

so we can create a function delete_row(array, row, rows, cols)

where array is a pointer to the **array** , **row** is the row to delete, **rows** is the number of rows in the array and **cols** is number of columns in the array

So to delete a row you want to move element A[row*rows+cols] into A[row*cols] then A[row*rows+cols+1] into A[row*cols+1] continuing until the end of the array.

I won't post code but it does not sound too difficult a task does it.  If you can't get it to work post your code and we can advise further

Now consider deleting say column 1 from our original array

Result


A00 A02 A03
A10 A12 A13
A20 A22 A23

Which makes our array 

A[] = {A00, A02, A03, A10, A12, A13, A20 A22, A23}

This is still slightly more complicated but again comes down to moving elements in the array can you figure out which?

We want to move A[col+1] in A[col] then A[col+2] into A[col+1] etc continuing until you get to deleting A[1*row+col] at which point you start moving the elements back by 2 then when you get to deleting A[2*row+col] you move the element back by 3 and so on.

Again I am not offering any code here but if you get stuck post your code and we can take a look at it

---

### Post by ofnuts on 2013-07-13
> **Warren Hill said:**
> 

We want to move A[col+1] in A[col] then A[col+2] into A[col+1] etc continuing until you get to deleting A[1*row+col] at which point you start moving the elements back by 2 then when you get to deleting A[2*row+col] you move the element back by 3 and so on.
Yes, but the hard part,  here "left as a exercise to the reader", is to come up wh an efficient way to express this shift from the position you are considering.

> **Warren Hill said:**
> Again I am not offering any code here but if you get stuck post your code and we can take a look at it
I have it but will withhold it for the time being :)

---

### Post by ofnuts on 2013-07-13
> **nvteighen said:**
> I don't get why it has to be made in-place

Because IRL an array can be a significant drain on available memory and  it doesn't really make sense to double the memory usage just to delete  things.

> **nvteighen said:**
> It can be done, of course, but my take (of course, due to my FP influence) would be to have this as a function that maps two matrices through deletion/manipulation of rows and columns. Then, if you want to have a destructive function, take the functional one and make the result be saved in the original variable. OK, not the most efficient thing, but quite a good way to start thinking about the problem.

If I were having a bad day I would says this is a typical anwer for a consultant :) We don't need to think about the problem, we need to solve it and any thinking that doesn't lead to a practical solution is just intellectual M10N.

---

### Post by alan9800 on 2013-07-14
another very simple attempt:```
#include <stdio.h>


#define ROWS 3
#define COLUMNS 3
#define DELETED_ROW 1
#define DELETED_COLUMN 1


int main ()
{
    int A[9];
    int i, j, tmp;
    for (i = 0; i < ROWS; i++)
        for (j = 0; j < COLUMNS; j++)
            A[i*ROWS+j] = i * ROWS + j + 1;
    for (i = 0; i < ROWS; i++)
    {
        printf("\n");
        for (j = 0; j < COLUMNS; j++)
            printf("A[%d]=%d\t", i * ROWS + j + 1, A[i*ROWS+j]);
    }
    for (i = 0; i < ROWS; i++)
        if (i == DELETED_ROW)
            for (j = 0; j < COLUMNS; j++)
                A[i*ROWS+j] = 0;
            else
                for (j = 0; j < COLUMNS; j++)
                    if (j == DELETED_COLUMN)
                        A[i*ROWS+j] = 0;
    printf("\n");
    for (i = 0; i < ROWS; i++)
    {
        printf("\n");
        for (j = 0; j < COLUMNS; j++)
            printf("A[%d]=%d\t", i * ROWS + j + 1, A[i*ROWS+j]);
    }
    if (DELETED_ROW != (ROWS - 1) && DELETED_COLUMN != (COLUMNS - 1))
    {
        for (i = 0; i < ROWS; i++)
            for (j = 0; j < COLUMNS; j++)
                if (i != DELETED_ROW && j == DELETED_COLUMN)
                {
                    tmp = A[i*ROWS+j+1];
                    A[i*ROWS+j+1] = A[i*ROWS+j];
                    A[i*ROWS+j] = tmp;
                }
                if (i == DELETED_ROW && j != DELETED_COLUMN)
                {
                    tmp = A[(i+1)*ROWS+j];
                    A[(i+1)*ROWS+j] = A[i*ROWS+j];
                    A[i*ROWS+j] = tmp;
                }
        for (j = 0; j < COLUMNS; j++)
        {
            tmp = A[(ROWS-1)*ROWS+j];
            A[(ROWS-1)*ROWS+j] = A[DELETED_ROW*ROWS+j];
            A[DELETED_ROW*ROWS+j] = tmp;
        }
    }
    printf("\n");
    for (i = 0; i < ROWS; i++)
    {
        printf("\n");
        for (j = 0; j < COLUMNS; j++)
            printf("A[%d]=%d\t", i * ROWS + j + 1, A[i*ROWS+j]);
    }
    return 0;
}
```


Please note that it's just a try to use a single matrix instead of two, as requested by the OP.

---

### Post by ofnuts on 2013-07-14
My code is a lot simpler :)

---

### Post by Warren Hill on 2013-07-14
Here is a simple test skeleton and the expected output you just have to provide the body to two functions

I have separated deleting a row and a column into two separate functions  

```
#include <stdio.h>

int ROWS = 5;
int COLS = 5;

int A[] = {0x00, 0x01, 0x02, 0x03, 0x04,
           0x10, 0x11, 0x12, 0x13, 0x14,
           0x20, 0x21, 0x22, 0x23, 0x24,
           0x30, 0x31, 0x32, 0x33, 0x34,
           0x40, 0x41, 0x42, 0x43, 0x44};

void printArray(int array[], int rows, int cols){
    int r, c, i = 0;
    for (r = rows; r > 0; r--){
        for(c = cols; c > 0; c--){
            printf(" %02X", array[i]);
            i++;
        }
        printf("\n");
    }
}

void deleteRow(int array[], int row, int rows, int cols){

    /* body can be written in 9 lines or less */
}

void deleteCol(int array[], int col, int rows, int cols){
    /* body can be written in 11 lines or less */
}

int main(void){
    printf("The original Array: \n");
    printArray(A, ROWS, COLS);
    printf("\nDelete row 1; result: \n");
    deleteRow(A, 1, ROWS, COLS);
    ROWS--;
    printArray(A, ROWS, COLS);
    printf("\nDelete col 1; result: \n");
    deleteCol(A, 1, ROWS, COLS);
    COLS--;
    printArray(A, ROWS, COLS);
    return 0;
}
```

And the expected output

```
The original Array: 
 00 01 02 03 04
 10 11 12 13 14
 20 21 22 23 24
 30 31 32 33 34
 40 41 42 43 44

Delete row 1; result: 
 00 01 02 03 04
 20 21 22 23 24
 30 31 32 33 34
 40 41 42 43 44

Delete col 1; result: 
 00 02 03 04
 20 22 23 24
 30 32 33 34
 40 42 43 44


```

---

### Post by erotavlas on 2013-07-14
Hi,

I have found a solution for square matrix that works and seems to be very efficient. This is my code:

```

#define MATRIX_SIZE 100
#define MATRIX_ROW_SIZE 10

double * matrix_ptr[MATRIX_SIZE]; 

bool RemoveFromMatrix(double* matrix_ptr, int matrix_size, int matrix_row_size, int filled, int remove_index)
{
    
    if(remove_index < filled-1)
    {
        for(int i = 0; i < filled; i++)
        {
            for(int j = 0; j < filled; j++)
            {
                if(i != remove_index && j != remove_index)
                {
                    int pos=0;
                    if(j>remove_index)
                    {
                        pos+=1;
                    }
                    if(i>remove_index)
                    {
                        pos+=matrix_row_size;
                    }

                    matrix_ptr[i*matrix_row_size+j-pos]=matrix_ptr[i*matrix_row_size+j];
                }
            }
        }
    }

    for(int i=0; i < filled; i++)
    {
        matrix_ptr[i*matrix_row_size+filled-1]=0;
        matrix_ptr[(filled-1)*matrix_row_size+i]=0;
    }
    return true;
}

```

The extension to general case of non square matrix should be straightforward by introducing additional variables for filled size

```

bool RemoveFromMatrix(double* matrix_ptr, int matrix_size, int matrix_row_size, int matrix_column_size, int row_filled, int column_filled, int remove_index)
{
    
    if(remove_index < row_filled-1)
    {
        for(int i = 0; i < row_filled; i++)
        {
            for(int j = 0; j < column_filled; j++)
            {
                if(i != remove_index && j != remove_index)
                {
                    int pos=0;
                    if(j>remove_index)
                    {
                        pos+=1;
                    }
                    if(i>remove_index)
                    {
                        pos+=matrix_row_size;
                    }

                    matrix_ptr[i*matrix_row_size+j-pos]=matrix_ptr[i*matrix_row_size+j];
                }
            }
        }
    }

    for(int i=0; i < row_filled; i++)
    {
        matrix_ptr[i*matrix_row_size+column_filled-1]=0;
        matrix_ptr[(row_filled-1)*matrix_row_size+i]=0;
    }
    return true;
}

```

Any suggestion is welcome.

---

### Post by alan9800 on 2013-07-14
> **ofnuts said:**
> My code is a lot simpler :)I used "simple" instead of "basic", just to not repeat the same terms of my previous post.
But, as I specified in that post, I'm not a C programmer, thus the mine is nothing else than an elementary attempt.

---

### Post by Warren Hill on 2013-07-14
Well done.

For the sake of completeness my deleteRow function was

```
void deleteRow(int array[], int row, int rows, int cols){
    int newsize, index, i;

    newsize = (rows - 1) * cols;
    if (row != rows){
        index = cols * row;
        for (i = index; i<newsize; i++){
            array[i] = array[i+cols];
        }
    }
}
```

and my deleteCol

```
void deleteCol(int array[], int col, int rows, int cols){
    int newsize, index, i, j, k = 1;

    newsize = rows * (cols - 1);
    index = col;
    j = cols - 1;
    for (i = index; i<newsize; i++){
        array[i] = array[i+k];
        if (--j == 0){
            j = cols - 1;
            k++;
        }
    }
}
```

But your code looks like it should work too.  Have you tested it to make sure you get the correct output?

---

### Post by ofnuts on 2013-07-14
My delete_columns function:

```

    for (int i=deleted_column;i<ROWS*(COLUMNS-1);i++) {
        int di=1+(i-deleted_column)/(COLUMNS-1);
        array[i]=array[i+di];
    }

```

My delete_row() is essentialy the same as Warren Hill's

---

