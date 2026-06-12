---
title: "(C) - Array length - why is it not calculated correctly?"
date: 2010-12-07
forum: Programming Talk
---

### Post by trilobite on 2010-12-07
Hi all - 
 I've written a small program which does a "map" on an array, applying a function to each element and putting the result in a new array. Only problem is - the length of the array is not calculated correctly. 
 Here's the code - 
```
 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h> 
#include <math.h> 
     
/*  A function to apply to an integer. */  
int func(int val) 
{ 
  return pow(val,2) + 5;   
}             
     
void map(int array[], int (*fn)(int)  ) 
{ 
  /* Length of the array */ 
  int len = sizeof(array) / sizeof(int); 
        
  /* An array to store the results  */  
  int resarray[len] ; 
      
  int i; 
  
  for(i=0; i<len; i++) 
  { 
     resarray[i] = fn(array[i]);        
     printf("Array[%d] is %d, Result[%d] is %d\n", i, array[i], i, resarray[i]);                   
  } 
  
} 

   
int main(void) 
{ 
  
/*  A function pointer to use  */ 
  int (*ptr)(int) ;       
    
/*  Point the function pointer at our function */     
  ptr = func;   
  
  int myarray[] = {2, 3, 5, 7, 11, 13, 17}; 
  
  map(myarray, *ptr); 
         
  return 0; 

} 

``` 

When this is run, it only gives one row, as follows - 
Array[0] is 2, Result[0] is 9  

Why is this, and what can I do to ensure the array size is calculated correctly?
Many thanks in advance - 
- trilobite

---

### Post by Barrucadu on 2010-12-07
sizeof() is evaluated at compile time, and is the size of the data-type rather than what it contains. You'll either need to pass the length of the array as a parameter, or end the array with some special marker (such as NULL) so you can calculate the length by counting the elements.

---

### Post by MadCow108 on 2010-12-07
sizeof cann only determine the size of arrays (e.g. int a[5]) not of pointers to memory blocks which you are using

void map(int array[], int (*fn)(int)  ) 
is equivalent to:
void map(int *array, int (*fn)(int)  ) 

=> sizeof(int*) is the size of the pointer (4 or 8 )
you need to explicitly pass the size of the memory block

and remember that arrays convert into pointers when passed into functions!
this will also not work:
```

void f(int * a) {
  for (i < sizeof(a)); // wrong! will give size of pointer
}

main() {
  int a[5];
  f(a);
}

```

---

### Post by trilobite on 2010-12-07
Hi Barrucadu and MadCow108 - 
 Thanks very much for your help! 

 Calculated at compile time - so *that's* the reason that sizeof(array) / sizeof(*array) works in main() but not elsewhere....  

 Ok - this is a big help - thanks again :) 
Bye for now - 
- trilobite

---

