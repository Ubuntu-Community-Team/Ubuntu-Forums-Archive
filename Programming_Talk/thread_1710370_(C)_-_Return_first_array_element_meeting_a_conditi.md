---
title: "(C) - Return first array element meeting a condition"
date: 2011-03-19
forum: Programming Talk
---

### Post by trilobite on 2011-03-19
Hi all - 
 I am trying to write a small program to return the first element of an array which meets a given condition. 
For example, given the array - 
{16, 15, 14, 13, 12} 
and the condition - 
(myarray[i] < 15) , the code should return 14 as the first element meeting the condition. 
I've written the code below, but it is not doing this - it always returns -1. 
```
 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <stdbool.h> 
#include <math.h>

/*  Set the array length  */  
#define LEN 5  

/* A helper function.  */  
/* If cond is true, this function will return 1. */ 
/* Otherwise, it will return 0.  */    
bool test(int val, bool cond) 
{  
    return cond; 
}    


/*  Return the first element (if any) of the array */ 
/*  which satisfies the given condition.           */ 
int find(int myarray[], bool mycond)
{          
    bool myval; 
    int retval;        
                        
    for(int i=0; i<LEN; i++)
    {         
       myval = test(myarray[i], mycond);  
                              
       /* If the condition is met, return the */ 
       /* array element and exit.             */                  
       if (myval) {retval = myarray[i]; break; } 
       else retval = -1;
    }      
        
    return retval;                                                                               
}


int main(void)
{
   int i=0;  
         
   int myarray[LEN] = {16, 15, 14, 13, 12};                           
/* Test to see which element first meets the criterion. */              
   printf("Result is %d \n",  find(myarray, (myarray[i] < 15) ) );
   
   int myarray2[LEN] = {8, 10, 12, 14, 16};          
   printf("Result is %d \n",  find(myarray2, (myarray2[i] > 10) ) );
      
   return 0 ;   
}

``` 

So, if someone can show how to fix this so that the code works as described, that would be great! Many thanks in advance-
- trilobite

---

### Post by MadCow108 on 2011-03-19
C is not lazy evaluated.
```
... (myarray[i] < 15) ...
```
is evaluated before it enters the function and thus it only checks the first element and mycond is always false

you need to use a function pointer for this in C.

```

int find(const int * ar, int (*comp)(const int, const int), const int val)
{
  for (int i = 0; i < 5; i++) {
    if (comp(ar[i], val))
      return ar[i];
  }
  return -1;
}

int cmp_gt(const int a, const int val)
{
  return a > val;
}

int main(int argc, const char *argv[])
{
  int a[] = {1,4,53,23,8};
  return find(a, cmp_gt, 2);
}

```

---

### Post by trilobite on 2011-03-19
> **MadCow108 said:**
> C is not lazy evaluated.
```
... (myarray[i] < 15) ...
```
is evaluated before it enters the function and thus it only checks the first element and mycond is always false

you need to use a function pointer for this in C.

```

int find(const int * ar, int (*comp)(const int, const int), const int val)
{
  for (int i = 0; i < 5; i++) {
    if (comp(ar[i], val))
      return ar[i];
  }
  return -1;
}

int cmp_gt(const int a, const int val)
{
  return a > val;
}

int main(int argc, const char *argv[])
{
  int a[] = {1,4,53,23,8};
  return find(a, cmp_gt, 2);
}

``` 

Hi MadCow108! 

Great! Thanks very much for that!  
This will be a useful little function-pointer example for me too. It'll be good for me to become more familiar with them, as they seem to be more powerful (in many ways) than ordinary functions. 
Thanks again - bye for now - 
- trilobite

---

