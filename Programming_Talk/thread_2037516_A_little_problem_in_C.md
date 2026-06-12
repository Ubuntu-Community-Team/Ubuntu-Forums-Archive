---
title: "A little problem in C"
date: 2012-08-04
forum: Programming Talk
---

### Post by ZelAlex on 2012-08-04
```
/*
This is used as write operation

Input from the user is in the string user_buffer
count is used to store the total number of characters yet unwritten to
    destination
ptr is used to make a char 2D array with maximum 4 elements in a row
    -it is the destination
*/
#include<stdio.h>
#include<malloc.h>
#include<string.h>
#define MAX_COLUMN 4.0

int main()
{
    char user_buffer[] = "HELLO TO THE WORLD";
    int count = strlen(user_buffer);
    char **ptr;
    int pass;
    register int i, j;
    
    if( (count%4) ==0)
        pass = (count/4);
    else
        pass = (count/4) + 1;
    
    ptr = (char **) malloc(  pass  * sizeof(char *) );
    //I used pass to make enough number of rows to handle all count
    //with max 4 elements in each

    if(ptr == NULL)
    {
        printf("\nMemory Allocation failed at beginning.");
        return -1;
    }

    for(i = 0; count > 0; i++)
    {//Memory Allocation for the 2D array (formed by the double pointer) and placing the values from the user buffer into it 
                
        if(count >= MAX_COLUMN)
        {
            ptr[i] = (char *) malloc ( (int)MAX_COLUMN * sizeof(char) );
            printf("\nMemory allocated to ptr[%d] is %d", i, (int)MAX_COLUMN * sizeof(char) );
        }
        else
        {
            ptr[i] = (char *) malloc ( count * sizeof(char) );
            printf("\nMemory allocated to ptr[%d] is %d",i, count * sizeof(char) );
        }
        
        //printf("\nMemory allocated for %d row\n", i);
    
        if(*ptr == NULL)
        {
            printf("\nMemory Allocation failed later at %dth row.\n", i);
            return -1;
        }
        
        printf("\n");

        for( j = 0; (j < MAX_COLUMN) && (count > 0) ; j++)
        {
            ptr[i][j] = user_buffer[i+j];
            printf("count is %d %c ",count, ptr[i][j]);
            count--;
        }
    }
    
    for(i=pass; i >=0; i--)
        free(ptr[i]);
    free(ptr);
    
    return 0;
}

```
I was trying double pointers as I was told this was needed before I start linux programming. But this is giving segmentation faults again and again. Don't know why.

LOGIC OF THE CODE:
> 
Using double pointers to make a 2D array
Maximum column in the array should be 4.
String is to be placed in this dynamically created array.

I have taken the string to be in the char array.

Can anyone see what's the problem?:confused:

---

### Post by lisati on 2012-08-04
A segmentation fault *can* mean that something's not quite right with what a poitner is pointing to.

What do you mean by "double" pointers? Are you referring to a pointer to a pointer, a "double" data type for a pointer, or something else?

---

### Post by vexorian on 2012-08-04
whenever I get seg faults, I use "valgrind". More about it in your software center.

---

### Post by steeldriver on 2012-08-04
Doesn't your main loop only create 'count' rows, not 'pass' rows?

```
for(i = 0; count > 0; i++)
```For your particular string, pass = 5 (rows) while count = 4 (columns), but you only malloc 4 x 4 sizeof(char) in total - then you try to free 5 I think

Also your copy needs an arithmetic check I think - i+count*j perhaps?

```
ptr[i][j] = user_buffer[i+j];
```

---

### Post by Bachstelze on 2012-08-04
This works. Try to figure out what was wrong in yours.

```
/*
   This is used as write operation

   Input from the user is in the string user_buffer
   count is used to store the total number of characters yet unwritten to
   destination
   ptr is used to make a char 2D array with maximum 4 elements in a row
   -it is the destination
   */
#include <stdio.h>
#include <malloc.h>
#include <string.h>
#define MAX_COLUMN 4

int main()
{
        char user_buffer[] = "HELLO TO THE WORLD";
        int count = strlen(user_buffer);
        char **ptr;
        int pass;
        int i, j;

        if (count%4 == 0) {
                pass = (count/4);
        } else {
                pass = (count/4) + 1;
        }

        ptr = malloc(pass*sizeof(char*));

        if (ptr == NULL) {
                printf("\nMemory Allocation failed at beginning.");
                return -1;
        }

        for (i = 0; count > 0; i++) {           
                if (count >= (MAX_COLUMN)) {
                        ptr[i] = malloc((MAX_COLUMN)*sizeof(char));
                        printf("\nMemory allocated to ptr[%d] is %lu", i, (MAX_COLUMN)*sizeof(char));
                } else {
                        ptr[i] = malloc(count*sizeof(char));
                        printf("\nMemory allocated to ptr[%d] is %lu", i, count*sizeof(char));
                }

                if (ptr[i] == NULL) {
                        printf("\nMemory Allocation failed later at %dth row.\n", i);
                        return -1;
                }

                printf("\n");

                for (j = 0; (j < (MAX_COLUMN)) && (count > 0); j++) {
                        ptr[i][j] = user_buffer[(MAX_COLUMN)*i+j];
                        printf("count is %d %c \n",count, ptr[i][j]);
                        count--;
                }
        }

        for (i=0; i<pass; i++) {
                free(ptr[i]);
        }
        free(ptr);

        return 0;
}

```

---

### Post by ZelAlex on 2012-08-05
Firstly, Thanks to all of you for your replies.

**lisati**,
I was talking about this
char **ptr; 
that I have used in my code. But thnx for pointing out that "double pointers" that I was using was ambiguous. I will bear that in my mind.

**vexorian**
I will try out valgrind. 

[B]steeldriver;
[/B]No my code creates pass number of columns. See that in the conditional check there is count>0 and not count>i. 
About the second thing about arithmetic check in assignment. Yes, that needs to be done. Thnx.

[B]Bachstelze
[/B]Thank you for taking the pain to correct my code.

I can understand why you changed the assignment statement. That was silly of me to overlook that simple thing.

Figured out the thing causing the segmentation fault. Loop problem.

You replaced %d with %lu. I can understand why %u should be used but not why %lu is used here. Can you explain?

---

### Post by Bachstelze on 2012-08-05
> **ZelAlex said:**
> 
You replaced %d with %lu. I can understand why %u should be used but not why %lu is used here. Can you explain?

%u is for unsigned, %lu is for long unsigned. On my machine the result of sizeof has type long unsigned, so any other conversion specifier causes a warning. However, I was a bit too hasty, because the only requirement on result of sizeof is that it must be an integer, so assuming it to be long unsigned is wrong. You should probably cast it to an appropriate type, and use the appropriate conversion specifier for that type, something like

```
printf("\nMemory allocated to ptr[%d] is %lu", i, (long unsigned) (count*sizeof(char)));
```

---

### Post by trent.josephsen on 2012-08-05
In C99 and later, %zu is the correct format specifier for sizeof.

Also, <malloc.h> is not a standard header. Use <stdlib.h> if you need to use malloc() and friends.

---

