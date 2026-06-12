---
title: "allocating and initialising a pointer inside a function"
date: 2012-03-17
forum: Programming Talk
---

### Post by PeterP24 on 2012-03-17
Hello,

I am passing a pointer to a function (through call by reference) in order to allocate memory for it with malloc and to put some values into the newly allocated memory cells, i.e. to initialize it. 
I came with the following code:

```
#include <stdio.h>
#include <stdlib.h>

void fct_b(int **b)
{
    int i;
    *b = malloc(10*sizeof(int));
    for(i = 0; i < 10; i++)
    {
        (*b)[i]=i;
        // printf("%d ", (*b)[i]);
    }
   
}

void fct_c(int ***c)
{
    int i, j;
    **c = malloc(10*sizeof(int*));
    for(i = 0; i < 10; i++)
    {
        (*c)[i] = malloc(10*sizeof(int));
        for(j = 0; j < 10; j++)
        {
            (*c)[i][j]=10*i+j;
            //printf("%d", (*c)[i][j]);
        }
    }
}

int main(void)
{
    int *b, **c;

    fct_b(&b);
    fct_c(&c);

    int i, j;
    // level b
    /*for(i = 0; i < 10; i++)
    {
        printf("%d ", b[i]);
    }*/
    // level c
    for(i = 0; i < 10; i++)
    {
        for(j = 0; j < 10; j++)
            printf("%d ", c[i][j]);
    }

    return 0;
}
```

I manage to figure out how to do it for a pointer to pointer type (function fct_b). However I was surprised to see that the initialisation works only if I use: 
```
(*b)[i]=i
```
because
```
*b[i]=i
```
doesn't work.

This would be one issue. Another one would be that I tried to expand the experience learned at fct_b to a pointer to a pointer to a pointer case - like the one implemented in function fct_c. I can check that inside the fct.c the pointer is allocated and initialised however it is not working. 

I have two questions:
(a) in case of fct_b why does the initialisation works with (*b)[i] = i instead of *b[i] = i  ?
(b) in case of fct_c - why does not work?

---

### Post by ofnuts on 2012-03-17
Wouldn't it be simpler to have :
```

int * fct_b()
{
    int i;
    int *b = malloc(10*sizeof(int));
    for(i = 0; i < 10; i++)
    {
        b[i]=i;
        // printf("%d ", b[i]);
    }
   return b;
 }

```And use it as
```

b=fct_b()

```"[]" has a higher precedence than "*", so "*b[i]" takes the i'th element of b and dereferences it.

---

### Post by PeterP24 on 2012-03-17
@ofnuts 
I know it is easier to return the pointer instead of passing it by reference in order to be allocated and initialised - this I already tried with respect to the function fct_b - I don't know if it works for function fct_c. However I am interested in the answers to my original questions. It is not like I have to solve some homework or pressing tasks with these answers - it is something I gave some thought and came to a dead end and I would like to find out how to do it in that particular way.

---

### Post by ofnuts on 2012-03-17
> **PeterP24 said:**
> @ofnuts 
I know it is easier to return the pointer instead of passing it by reference in order to be allocated and initialised - this I already tried with respect to the function fct_b - I don't know if it works for function fct_c. However I am interested in the answers to my original questions. It is not like I have to solve some homework or pressing tasks with these answers - it is something I gave some thought and came to a dead end and I would like to find out how to do it in that particular way.
In fct_c it should be:
```

    *c = malloc(10*sizeof(int*)); 

```

---

### Post by Arndt on 2012-03-17
*b[i] means the same as *(b[i]), not (*b)[i].

---

### Post by Bachstelze on 2012-03-17
Your problem with fct_c is that you have not initialised c in main, but you dereference it in fct_c.

---

### Post by PeterP24 on 2012-03-18
Ok, I think I got the answer to the first question. It has to be (*b)[i] instead of *b[i] because, as @ofnuts says, I am allocating memory for *b then by using *b[i] I am actually dereferencing b first and not *b. However I did not allocated memory for b with malloc - I allocated for *b. Is it right? 

@Bachstelze - I am trying to allocate memory and initialise the pointer c inside the function fct_c. 

For function fct_c the following version works (thanks again @ofnuts):
```
void fct_c(int ***c)
{
    int i, j;
    *c = malloc(10*sizeof(int*));
    for(i = 0; i < 10; i++)
    {
        (*c)[i] = malloc(10*sizeof(int));
        for(j = 0; j < 10; j++)
        {
            (*c)[i][j]=10*i+j;
            //printf("%d ", (*c)[i][j]);
        }
    }
}
```

---

