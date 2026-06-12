---
title: "Need help with pointers and arrays"
date: 2015-07-31
forum: Programming Talk
---

### Post by 3djake on 2015-07-31
Hello

I have just started learning C and I am having some issues with some code in a program I am creating.

Here is a shortened example of what I want to do but I get a "Segmentation fault".

So I want to assign a string "O"(not zero) to each array in board1, essentially creating a 5x5 grid of "O".

If some one can explain briefly what I need to do to get this to work, it would be very much appreciated.
Do I even need to use pointers?
 
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int i, j;
char *board1[5][5];
int main()
{
for(i = 0; i < 5; i++)
    {
    for(j = 0; j < 5; j++)
     {
     strcpy(board1[i][j], "O");
     printf("%s ", board1[i][j]);
     }
    printf("\n");
    }
}

```

---

### Post by 3djake on 2015-08-01
Just an update

So if I remove [j] from my program, I get a 5x5 grid of "O"'s. This is not ideal however because its just printing the same array 5 times. I want a 25 grid.

This is my current solution which I am not too happy about, I am sure there is an easier and less time consuming way.

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int i, j, f, g;
char *board1[25];
int main()
{
  for(i = 0; i < 25; i++)
  {
    if ((board1[i] = malloc(sizeof(char))) == NULL)
     {
            printf("Memory or array Error\n");
            return -1;
     }
     if(i < 5)
     {
         strcpy(board1[i], "O");
         printf("%s ", board1[i]);
     }
     if(i == 4)
     {
        printf("\n");
     }
     if(i >= 5 && i < 10)
     {
        strcpy(board1[i], "O");
        printf("%s ", board1[i]);
     }
     if(i == 9)
     {
        printf("\n");
     }
     if(i >= 10 && i < 15)
     {
        strcpy(board1[i], "O");
        printf("%s ", board1[i]);
     }
     if(i == 14)
     {
        printf("\n");
     }
     if(i >= 15 && i < 20)
     {
        strcpy(board1[i], "O");
        printf("%s ", board1[i]);
     }

     if(i == 19)
     {
        printf("\n");
     }
     if(i >= 20 && i < 25)
     {
        strcpy(board1[i], "O");
        printf("%s ", board1[i]);
     }

     if(i == 24)
     {
        printf("\n");
     }
  }
}

```

---

### Post by dwhitney67 on 2015-08-01
Actually, using a single-dimensional array is not that bad, as long as you manage the arithmetic (with respect to rows and columns) to calculate the offset into the array.

You have not offered an explanation as to why you require to store a string, as opposed to a single character.  If you follow up with a reply to this thread, then you should elaborate as to why you find it necessary to do so.

Otherwise, here's a simple program that initializes an array to all O's, and then prints out the array in a presentable format:
```

#include <stdio.h>

int main(int argc, char** argv)
{
    static int rows = 5;
    static int cols = 5;

    char board[rows * cols];   // no need to allocate on heap; size is small enough for stack

    // initialize board
    for (int r = 0; r < rows; ++r)
    {
        for (int c = 0; c < cols; ++c)
        {
            board[r * rows + c] = 'O';
        }
    }

    // verify board state
    for (int i = 0; i < rows * cols; ++i)
    {
        if (i > 0 && i % cols == 0)
        {
            printf("\n");
        }

        printf("%c ", board[i]);
    }
    printf("\n");

    return 0;
}

```

P.S.  Avoid global variables!!!

---

### Post by spjackson on 2015-08-01
> **dwhitney67 said:**
> 
```

            board[r * rows + c] = 'O';

```

This is only "correct" because rows == cols. For a more general solution you would want:
```

            board[r * cols + c] = 'O';

```
Since it is so easy for even the most experienced to make this mistake, I think it better to use a 2 dimensional array and let the compiler do the math.

---

### Post by dwhitney67 on 2015-08-01
> **spjackson said:**
> This is only "correct" because rows == cols. For a more general solution you would want:
```

            board[r * cols + c] = 'O';

```
Since it is so easy for even the most experienced to make this mistake, I think it better to use a 2 dimensional array and let the compiler do the math.

Thanks for the bug catch.  I don't always bother to test the code I post on UF.

---

### Post by 3djake on 2015-08-01
Thanks for the feedback, I knew there was a more elegant way to do it but I only started learning C 3 weeks ago.

Its for my Battleships game which you can have a look at here.
[https://github.com/3djake/Battleships/blob/master/Battleships.c]("https://github.com/3djake/Battleships/blob/master/Battleships.c")

I will try out some of your suggestions after the weekend, I have got some assignments for Uni to do.

Cheers, Jake.

---

### Post by xb12x2 on 2015-08-01
The reason for the segmentation fault is that strcpy() copies strings, and strings include the terminating null character. 



**strcpy**

char * strcpy ( char * destination, const char * source );

Copy string
Copies the C string pointed by *source* into the array pointed by *destination*, including the terminating null character (and stopping at that point).

To avoid overflows, the size of the array pointed by *destination* shall be long enough to contain the same C string as *source* (including the terminating null character), and should not overlap in memory with *source*.


-
-

---

### Post by trent.josephsen on 2015-08-02
> **xb12x2 said:**
> The reason for the segmentation fault is that strcpy() copies strings, and strings include the terminating null character.
No, it's because the pointer passed to strcpy is uninitialized. This has the same problem despite omitting the terminator:
```
strncpy(board[i][j], "O", 1);
```

---

