---
title: "(C) - Getting simple &quot;fold&quot; program to work"
date: 2010-10-23
forum: Programming Talk
---

### Post by trilobite on 2010-10-23
Hi all - 

 I'm doing a few small "FP-like" programs in C. One of them is this one - scan.c. It's almost working, but I have a problem.
Here's the code - 

```

/*  Apply an operator to all elements of an array.  */  
/*  This code is released to the public domain.  */  

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

/* Declare an array and fill it. */  
int myarray[8] = {1, 2, 3, 4, 5, 6, 7, 8}; 

/*  Scan function. */ 
void scan(char *op, int *array) 
{     
    int i;    
    /*  Length of array */ 
    int length=8; 
    int result=0;   
           
    for( (i=0); (i<length); i++)
    {  
            if (op == '+') { result += array[i]; }                            
       else if (op == '-') { result -= array[i]; }                            
       else if (op == '*') { result *= array[i]; }                           
                                     
   printf("Result is %d \n", result);               
    } 
    
} ; 


int main(void) 
{     
   scan("+", myarray);      
   return 0 ;    
} 

``` 

The code compiles, but I get these warnings - 
gcc -Wall -o "scan" "scan.c" -lm (in directory: /home/andy/pdfpc)
fold.c: In function ‘scan’:
fold.c:28: warning: comparison between pointer and integer
fold.c:29: warning: comparison between pointer and integer
fold.c:30: warning: comparison between pointer and integer
Compilation finished successfully.
*********************

Not only that, but when I run the code, I get this output - 
andy@obsidian:~/pdfpc$ ./scan
Applying operator + to array 
Result is 0 
Result is 0 
Result is 0 
Result is 0 
Result is 0 
Result is 0 
Result is 0 
Result is 0 
andy@obsidian:~/pdfpc$ 

So, can anyone see what is stopping this code from working? I'm sure the fix will be simple, but I'm stumped.... 
Many thanks in advance for any help! 
- trilobite

---

### Post by Some Penguin on 2010-10-23
Using == with pointers is testing whether the pointer points to the same memory address, not whether what's pointed-to is semantically equivalent.  See the warning messages from compilation?  That's why.  '+' is being treated as an integer corresponding to its index in the default character set.  This integer is not going to match a valid memory address except by sheer coincidence.

If you want to support multi-character operators, you should use (char*) operators like "+" (not '+'!) and strcmp or the like; if all operators are going to be single-character operators, you could change the parameter type.

---

### Post by trilobite on 2010-10-24
> **Some Penguin said:**
> Using == with pointers is testing whether the pointer points to the same memory address, not whether what's pointed-to is semantically equivalent.  See the warning messages from compilation?  That's why.  '+' is being treated as an integer corresponding to its index in the default character set.  This integer is not going to match a valid memory address except by sheer coincidence.

If you want to support multi-character operators, you should use (char*) operators like "+" (not '+'!) and strcmp or the like; if all operators are going to be single-character operators, you could change the parameter type.

Hi Some Penguin - thanks for that! 
 Your post gave me a much-needed "mental shakeup" (I guess a bucket of cold water would have worked too... :)  )

 I've now made the first parameter a char (not a char *) and called the function with the operator in single quotes (not double ones), and now it compiles with no warnings and gives the expected results. 

(EDIT: Renamed thread and function to "scan" instead of "fold". Scan gives the intermediate results, fold only the final result.)    

Many thanks for your help!  Bye for now- 
-trilobite

---

