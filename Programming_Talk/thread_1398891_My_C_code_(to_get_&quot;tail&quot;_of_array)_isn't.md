---
title: "My C code (to get &quot;tail&quot; of array) isn't printing"
date: 2010-02-05
forum: Programming Talk
---

### Post by trilobite on 2010-02-05
Hi all - 

 I've done the following code to get the "tail" of an array (that is, all elements except the first one). I'm doing a few small C programs as a public-domain "functional programming in C" package. 

This code compiles, but the "tailarray" does not print out, and I'm puzzled as to why that is. Here's the code - 
```


#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/*  Function to return the tail of an array.  */ 
void tail( int *array ) 
{ 
    int i ; 
    /* Find the array length   */ 
    int length = sizeof(array) / sizeof(*array); 
    int tailarray[length-1] ; 
    
    for(i=1; i<length; i++)
    {  
       tailarray[i-1] = array[i] ;       
       printf("tailarray[%d] is %d \n", i-1, tailarray[i-1]);          
    }     
                    
} ; 


int main(void) 
{ 
 /*  Declare an array and fill it with data. */     
   int myarray[] = {24, 37, 142, 205} ; 
   int length = sizeof(myarray) /  sizeof(*myarray);     
    
   tail( myarray ); 
  
   return 0 ; 
} 

``` 

So, if anyone is able to fix this so that it prints the elements 37, 142, 205 - that would be very helpful! Many thanks in advance - 
- trilobite

---

### Post by denarced on 2010-02-05
int the function tail, you try to find out the length of the array but this is not possible.
int length will always be 1
you have to provide the function the length of the array
```
void tail(int * array, int length);
```

---

### Post by trilobite on 2010-02-05
> **denarced said:**
> int the function tail, you try to find out the length of the array but this is not possible.
int length will always be 1
you have to provide the function the length of the array
```
void tail(int * array, int length);
```

Ahh... many thanks for that, denarced - that's great! Still finding my way in C after having done Python coding for a while. Anyway, I've just bought two books on C, so I'll get into those - they'll be a big help. 
Thanks again - bye for now - 
 -trilobite

---

### Post by nvteighen on 2010-02-05
Hm... this can be done in one line if you know how arrays work in C. Just think that an array is a pointer to the first element of a region of allocated memory. So, the second element's address is at array + 1; the third, at array + 2, etc.

I think I've given you almost the answer. Use pencil and paper, draw an array with its elements' pointers and the answer should be obvious.

Another hint: In Functional Programming, all functions have to return something. There are no void functions.

---

### Post by trilobite on 2010-02-05
> **nvteighen said:**
> Hm... this can be done in one line if you know how arrays work in C. Just think that an array is a pointer to the first element of a region of allocated memory. So, the second element's address is at array + 1; the third, at array + 2, etc.

I think I've given you almost the answer. Use pencil and paper, draw an array with its elements' pointers and the answer should be obvious.

Another hint: In Functional Programming, all functions have to return something. There are no void functions.

Ok - thanks very much for that, nvteighen! 
I'll try the approach that you've hinted at. 
I'll also amend the code that I've got so that it returns something (rather than being void).
I've been looking at various bits of code for "returning" arrays from a function. Apparently (IIUC) it's not something that C supports directly, but it can be done (or faked) with a bit of "workaround".  
- trilobite

---

### Post by Fraser1987 on 2010-02-05
int length = sizeof(myarray) /  sizeof(*myarray); 

int length = sizeof(myarray) *  sizeof(myarray);  ?

---

### Post by MadCow108 on 2010-02-05
> **trilobite said:**
> Ok - thanks very much for that, nvteighen! 
I'll try the approach that you've hinted at. 
I'll also amend the code that I've got so that it returns something (rather than being void).
I've been looking at various bits of code for "returning" arrays from a function. Apparently (IIUC) it's not something that C supports directly, but it can be done (or faked) with a bit of "workaround".  
- trilobite

you are correct, you can't return an array, because the array automatically converts to a pointer and sizeof operator does not work the same on pointers as on arrays (the source of many many problems)
a common way to get around this is to terminate the array by something (e.g. NULL as with cstrings), so you can still determine the size by scanning the array even after it decayed into a pointer.

other ways are replacing the array by a dynamic memory block which is saved together with its size in a struct or passing functions the size of the array (or pointer to the size so they can modify it)

These are not really "workarounds", the language is designed to work that way, so you can see (almost) every clock cycle directly in the code.
higher level languages just encapsulate this stuff.

---

### Post by dwhitney67 on 2010-02-05
> **MadCow108 said:**
> 
higher level languages just encapsulate this stuff.
correct... except for the poor fellow who had to write the encapsulation.

---

