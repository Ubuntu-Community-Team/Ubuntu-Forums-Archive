---
title: "(C) Getting rid of a couple of warnings"
date: 2010-10-25
forum: Programming Talk
---

### Post by trilobite on 2010-10-25
Hi all - 
 I've got a small C program here which converts the argument to a string and finds the string length. Unfortunately, I'm getting a couple of warnings with it. Here's the code - 
```
 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h> 

void length(void *arg)  
{    
 char foo[80];      
   
 snprintf(foo, 79, "%d", (int)arg); 
             
 int len = strlen(foo);         
   
 printf("Length is %d \n", len);                     
} 

int main(void) 
{           
   length("foobarbaz"); 
   length(123);            
   return 0 ;    
} 

``` 

When I compile this, it does compile but I get the warnings - 
typeof2.c: In function ‘main’:
typeof2.c:33: warning: passing argument 1 of ‘length’ makes pointer from integer without a cast
typeof2.c:18: note: expected ‘void *’ but argument is of type ‘int’
******************   

Btw - the program gives the expected output when run - it prints 9 and 3 as the lengths. 

How can I get rid of these warnings?  I'm puzzled that the compiler is complaining about an int being passed to a void * function (which I thought accepted args of all types). 

Many thanks in advance - 
- trilobite

---

### Post by worksofcraft on 2010-10-25
> **trilobite said:**
> Hi all - 
 I've got a small C program here which converts the argument to a string and finds the string length. Unfortunately, I'm getting a couple of warnings with it. Here's the code - 
```
 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h> 

void length(void *arg)  
{    
 char foo[80];      
   
 snprintf(foo, 79, "%d", (int)arg); 
             
 int len = strlen(foo);         
   
 printf("Length is %d \n", len);                     
} 

int main(void) 
{           
   length("foobarbaz"); 
   length(123);            
   return 0 ;    
} 

``` 

When I compile this, it does compile but I get the warnings - 
typeof2.c: In function &#8216;main&#8217;:
typeof2.c:33: warning: passing argument 1 of &#8216;length&#8217; makes pointer from integer without a cast
typeof2.c:18: note: expected &#8216;void *&#8217; but argument is of type &#8216;int&#8217;
******************   

Btw - the program gives the expected output when run - it prints 9 and 3 as the lengths. 

How can I get rid of these warnings?  I'm puzzled that the compiler is complaining about an int being passed to a void * function (which I thought accepted args of all types). 

Many thanks in advance - 
- trilobite

No void * accepts a pointer to all types, but 123 is a number and not a pointer.

note that when you pass it the string "foobarbaz" what arrives in your function is the memory address of that text and you then cast that into a number and format it in astring of which you return the length. It is pure coincidence that the string representing that memory address happens to be a 9 digit number and you would get similar length even if you just passed it an empty string :shock:

p.s. Here I made subtle changes.... see if you can explain the lengths it reports now:
[php]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h> 

void length(void *arg)  
{    
 char foo[80];      
   
 snprintf(foo, 79, "%d", (int)arg); 
             
 int len = strlen(foo);         
   
 printf("Length is %d \n", len);                     
} 

int main(void) 
{           
   length(""); 
   length(00000123);            
   return 0 ;    
}
[/php]

enjoy ;)

---

### Post by trilobite on 2010-10-25
> **worksofcraft said:**
> No void * accepts a pointer to all types, but 123 is a number and not a pointer.

note that when you pass it the string "foobarbaz" what arrives in your function is the memory address of that text and you then cast that into a number and format it in astring of which you return the length. It is pure coincidence that the string representing that memory address happens to be a 9 digit number and you would get similar length even if you just passed it an empty string :shock:

p.s. Here I made subtle changes.... see if you can explain the lengths it reports now:
(snip) 
 

Hi worksofcraft - thanks for your reply. 

Hmm... good question. The amended code gives lengths of 9 and 2. Nine will be the length of the memory address, but the "2" has me stumped. 

The background to this: The eventual aim was to get a "typeof" function. What I was trying to do was to convert the arg to a string. 

Then, check the type of the characters in the string. If any of them are non-digits, the function had a string as an argument. If they were all digits, the argument was a number. 

( But even that won't work, given that you can pass it things like "123". That's a string rather than a number. ) 

I think I'd better forget this bit of code.
I'd thought that it might be possible to do a typeof function, using the approach above, but it now seems that it can't be done. Anyway, I guess it's still possible to learn from reaching a dead-end... :) 
- trilobite

---

### Post by worksofcraft on 2010-10-25
> **trilobite said:**
> Hi worksofcraft - thanks for your reply. 

Hmm... good question. The amended code gives lengths of 9 and 2. Nine will be the length of the memory address, but the "2" has me stumped. 

The background to this: The eventual aim was to get a "typeof" function. What I was trying to do was to convert the arg to a string. 

Then, check the type of the characters in the string. If any of them are non-digits, the function had a string as an argument. If they were all digits, the argument was a number. 

( But even that won't work, given that you can pass it things like "123". That's a string rather than a number. ) 

I think I'd better forget this bit of code.
I'd thought that it might be possible to do a typeof function, using the approach above, but it now seems that it can't be done. Anyway, I guess it's still possible to learn from reaching a dead-end... :) 
- trilobite

Yes definitely, I fully support creative exploring like this. I do it all the time too :)

I think what you want to do is better supported in C++ but even there the type of primitive data like text and integer and float are only really known at compile time. Per chance I'm just reading up about run-time typeid, dynamic casting and such things.

p.s. that length of 2 is because the C compiler takes numbers starting in a 0 to be octal: 123 octal, when you snprintf it in decimal comes out as 83... ;)

---

