---
title: "combining two 1d arrays into a 2d array"
date: 2010-02-24
forum: Programming Talk
---

### Post by hollowhead on 2010-02-24
I'm trying to combine two one D arrays into a two D array, then sort ascending by row, then separate them back to their respective arrays.
The code below successfully puts the first array in but not the second.  Its simple code but I cannot see why -its doing my head in...  Can anyone see a flaw in my logic?
 
```

rows=6;
cols=2;
int a[6][2];
int position=0;
int temp;
int n=0;
int k=0;
int arrx[6]={6,5,4,7,10,14}; 
int arry[6]={8,9,11,12,13,15}; 

j=0;
for ( i = 0; i < rows; i++)
	{

a[i][j] = arrx[i];
printf("%d\t%d\n", i, a[i][j]);
	}

j=1;
for ( i = 0; i <rows; i++)
	{
a[i+rows][j] = arry[i];
printf("%d\t%d\n", i+rows, a[i+rows][j]);

	}


```

gives output

0	6
1	5
2	4
3	7
4	10
5	14
6	8
7	8
8	11
9	8
10	13
11	11

---

### Post by pbrane on 2010-02-24
Try this:
```

 1 #include <stdio.h>
 2
 3 int main(int argc, char *argv[])
 4 {
 5   int rows=6;
 6   int cols=2;
 7   int a[rows][cols];
 8   int arrx[6]={6,5,4,7,10,14};
 9   int arry[6]={8,9,11,12,13,15};
10   int i;
11
12   for (i = 0; i < rows; i++)  {
13     a[i][0] = arrx[i];
14     a[i][1] = arry[i];
15     printf("%d, %d\n", a[i][0], a[i][1]);
16   }
17   return 0;
18 }

```

If you just want to sort an array you'd be better off writing a function that sorts the array and calling it once for each array. Combining the two arrays, sorting and then splitting the arrays is not very efficient.

---

### Post by Some Penguin on 2010-02-24
[QUOTE=hollowhead;8877246]I'm trying to combine two one D arrays into a two D array, then sort ascending by row, then separate them back to their respective arrays.
The code below successfully puts the first array in but not the second.  Its simple code but I cannot see why -its doing my head in...  Can anyone see a flaw in my logic?
 
```

rows=6;
cols=2;
int a[6][2];
int position=0;
int temp;
int n=0;
int k=0;
int arrx[6]={6,5,4,7,10,14}; 
int arry[6]={8,9,11,12,13,15}; 

j=0;
for ( i = 0; i < rows; i++)
    {

a[i][j] = arrx[i];
printf("%d\t%d\n", i, a[i][j]);
    }

j=1;
for ( i = 0; i <rows; i++)
    {
a[i+rows][j] = arry[i];
printf("%d\t%d\n", i+rows, a[i+rows][j]);

    }


```/QUOTE]

Ask yourself where a[i+rows][j] points to.   What happens when i is 5, for instance?

---

### Post by hollowhead on 2010-02-25
Thanks for your reply, you're right my mistake.  My original code was this

using a separate variable n in the second loop.  It still doesn't work.  It seems to be reading the second array incorrectly I cannot see why.


Giving output

0	6
1	5
2	4
3	7
4	10
5	14
	
6	8	
7	8	
8	11	
9	8	
10	13	
11	11
 
I recognise this method isn't very efficient but I'm trying to program for a statistical test where the two sets of data are sorted separately but ranked together, then the ranks for each set are totalled separately.  The only way I could think of doing this was to 

combine two 1D arrays in one 2D array
sort against row
rank overall against row
pull out against column
score

Ta.   

```


j=0;
for ( i = 0; i < rows; i++)
	{

a[i][j] = arrx[i];
printf("%d\t%d\n", i, a[i][j]);
	}
n=0;
j=1;
for ( i = rows; i <(rows*cols); i++)
	{
a[i][j] = arry[n];
printf("\t\n%d\t%d",    i, arry[n]);
n++;
	}

```

---

### Post by Some Penguin on 2010-02-25
You declared a two-dimension array  -- a[6][2].  Fine.

You store the first row in a[0..5][0].  Fine.

Why do you continue to insist on accessing a[6..11][1] , when your array is only 6x2?

---

### Post by hollowhead on 2010-02-25
Thanks- what an idiot, I tried to set it up using pointers as **array but this didn't work so I will try....


```

int **p; /*declaration of p as: pointer-to-pointer of int */
        int i, j; /*Indexing variables*/

                p = malloc( row * sizeof(*p) ); /*Allocate integer pointers for the rows */
        if(p != NULL)
        {
            for(i = 0; i < row; i++) /* Loop through each row pointer to allocate memory for columns*/
            {
                /* Set p[i] pointer to a block of memory for 'column' number of integers */
                p[i] = malloc(column * sizeof **p); /*Here, sizeof(**p) is same as sizeof(int) */
                if(p[i] == NULL)
                {
                    printf("Memory allocation failed. Exiting....");
                    return 1;
                }
            }

```

In the meanwhile setting it to [12][2] works.  Thanks.

---

### Post by Some Penguin on 2010-02-25
Aiiiiiiiiiiiiiigh.

You have only 12 values to store.  6 x 2 = 12.  You don't need 12 x 2.  You have no reason for the first array index to go outside 0-5, or for the second to go outside 0-1.

---

### Post by howlingmadhowie on 2010-02-25
i must admit i'm still quite confused about what you want to do.

can you use your sample numbers and show how each step in the process should be?

the way i've understood you, you want to do the following, but i may have misunderstood you:

```

arrx: 6 5 4 7 10 14
arry: 8 9 11 12 13 15

step 1:

6  5  4  7 10 14  8  9 11 12 13 15
0  1  2  3  4  5  6  7  8  9 10 11

step 2:

4  5  6  7  8  9 10 11 12 13 14 15
2  1  0  3  6  7  4  8  9 19  5 11

step 3:

??

```

---

### Post by hollowhead on 2010-02-26
Sorry, don't want anyone to go aiiigh!

This is want I want to do...

x sample data 4, 5, 6, 7, 10, 14
y sample data 8, 9, 11, 12, 13, 15

I want to sort the two separate lots of data jointly giving combined *ranks* as follows;

x sample ranks 1, 2, 3, 4, 7, 11 giving a rank of 28
y sample ranks 5, 6, 8, 9, 10, 12 giving a rank of 50

Its a complicated problem to program but simple to do by eye since you are ranking separate data sets combined and after ordering you need to know which rank is from which, hence the idea I described in an earlier post.  I have written code for three different sorts (which work for 1D arrays).  I'll probably use gnomesort since its very simple to program.....

I'm not wanting help with the sorts just the combining the arrays, of course if you can think of a more elegant way I would be interested.  Thanks for your replies anyway.

---

### Post by MadCow108 on 2010-02-26
I don't quite yet get your proposed algorithm
but you could solve it easily by sorting both 1d arrays and just comparing entries of the first array to a certain entry in the second array and increasing the appropriate ranks and advancing the compare element of the second array.
pseudocode:
```

sort(a and b)
j = b.first()
foreach i in a:
  if (i < j)
    increase rank of a
  else
    increase rank of b
    advance(j)
    repeat
handle_rests

```

real code (warning spoiler alert, don't read if you want to try yourself)


```

int a[] = qsort(input1); // this is pseudocode
int b[] = qsort(input2); // this is pseudocode
int rank1=0,rank2=0;
int i,j=0;
for (i=0;i<size;i++) {
  if (a[i] < b[j]) {
    rank1 += i+j+1;
  }
  else {
    rank2 += i+j+1;
    j++; // jump to next entry
    i--; // repeat
  }
}
// handle rest of arrays
while (i < size) {
  rank1 += i + j + 1;
  i++;
}
while (j < size) {
  rank2 += i + j + 1;
  j++;
}
assert(2*size*(2*size+1)/2 == rank1+rank2); // all is well

```

---

### Post by howlingmadhowie on 2010-02-26
> **hollowhead said:**
> Sorry, don't want anyone to go aiiigh!

This is want I want to do...

x sample data 4, 5, 6, 7, 10, 14
y sample data 8, 9, 11, 12, 13, 15

I want to sort the two separate lots of data jointly giving combined *ranks* as follows;

x sample ranks 1, 2, 3, 4, 7, 11 giving a rank of 28
y sample ranks 5, 6, 8, 9, 10, 12 giving a rank of 50

Its a complicated problem to program but simple to do by eye since you are ranking separate data sets combined and after ordering you need to know which rank is from which, hence the idea I described in an earlier post.  I have written code for three different sorts (which work for 1D arrays).  I'll probably use gnomesort since its very simple to program.....

I'm not wanting help with the sorts just the combining the arrays, of course if you can think of a more elegant way I would be interested.  Thanks for your replies anyway.

where are the values for x of 1, 2 and 3 coming from? can you give a full example of every step of the process. i still don't understand what you are trying to do, though i do now know that when you say 'rank' you mean total.

--edit-- oh hang on. i think i've deciphered it. you want to do the following:

```

x_array={4, 5, 6, 7, 10, 14}
y_array={8, 9, 11, 12, 13, 15}

appended_associative_array={'4'->x_array, 
                            '5'->x_array,
                            '6'->x_array,
                            '7'->x_array,
                            '10'->x_array,
                            '14'->x_array,
                            '8'->y_array,
                            '9'->y_array,
                            '11'->y_array,
                            '12'->y_array,
                            '13'->y_array,
                            '15'->y_array}

sorted: {4->x,
         5->x
         6->x
         7->x
         8->y
         9->y
         10->x
         11->y
         12->y
         13->y
         14->x
         15->y}

extract values: {x, x, x, x, y, y, x, y, y, y, x, y}
add_positions_for_x: 1+2+3+4+7+11 =28
add_positions_for_y: 5+6+8+9+10+12 =50

```

here's a simple scheme program to do that.

```

(define array1 (list 6 5 4 7 10 14))
(define array2 (list 8 9 11 12 13 15))

(define add-positions
  (lambda (x-list y-list)
    (let ((x-rank 0)
          (y-rank 0))
      (define add-positions-helper
        (lambda (x-list y-list i)
          (cond ((and (null? x-list) (null? y-list)) #f)
                ((null? y-list)
                 (set! x-rank (+ x-rank i))
                 (add-positions-helper (cdr x-list) '() (+ i 1)))
                ((null? x-list)
                 (set! y-rank (+ y-rank i))
                 (add-positions-helper '() (cdr y-list) (+ i 1)))
                ((< (car x-list) (car y-list))
                 (set! x-rank (+ x-rank i))
                 (add-positions-helper (cdr x-list) y-list (+ i 1)))
                ((> (car x-list) (car y-list))
                 (set! y-rank (+ y-rank i))
                 (add-positions-helper x-list (cdr y-list) (+ i 1)))
                ((= (car x-list) (car y-list))
                 (set! y-rank (+ y-rank i))
                 (set! x-rank (+ x-rank i))
                 (add-positions-helper (cdr x-list) (cdr y-list) (+ i 2))))))
      (add-positions-helper x-list y-list 1)
      (cons x-rank y-rank))))

(display (add-positions array1 array2))

```


---edit---
and here's a version in C:
```

File Edit Options Buffers Tools C Help                                                                          
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv) {
  int x_array[]={4,5,6,7,10,14};
  int y_array[]={8,9,11,12,13,15};
  int length=6, x=0, y=0, i=1, x_rank=0, y_rank=0;
  
  while(x<length && y<length) {
    if(x_array[x]<y_array[y]) {
      x_rank+=i;
      x++;
      i++;
    } else if(y_array[y]<x_array[x]) {
      y_rank+=i;
      y++;
      i++;
    } else if(y_array[y]==x_array[x]) {
      x_rank+=i;
      y_rank+=i;
      x++;
      y++;
      i+=2;
    }
  }
  while(x<length) {
    x_rank+=i;
    x++;
    i++;
  }
  while(y<length) {
    y_rank+=i;
    y++;
    i++;
  }

  printf("x_rank: %d, y_rank: %d\n", x_rank, y_rank);

  return EXIT_SUCCESS;
}

```

---

### Post by hollowhead on 2010-02-26
Yup both of those code snippets seem to do it. Thanks. I did look I confess, although there's plenty more variants on this idea for other tests to write though....  All the median tests involve slightly different ways of using ranks.  Sometimes you just someone to look at a problem from a different angle.

---

### Post by howlingmadhowie on 2010-02-26
oh, sorry. i'm an idiot. i forgot to say that using the code blocks i posted you have to sort the arrays individually beforehand.

also, the method i used doesn't store any information apart from the total rank of each array, so if you wanted to know something like the variance, you'd have to do that differently (however you could do this fairly easily using mean of the squares minus square of the means)

---

### Post by hollowhead on 2010-02-27
Yeah thanks.

---

