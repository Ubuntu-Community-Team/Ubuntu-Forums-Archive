---
title: "(C) - Finding nth &quot;word&quot; in string"
date: 2011-10-14
forum: Programming Talk
---

### Post by trilobite on 2011-10-14
Hi all. Just for fun, I've been trying to write a function in C to find the "nth" word in a string (without using strtok). 
I'm sure that I'm almost there, but the code below (although it compiles without error) gives a segfault when run. 
```
 

#include <stdio.h>
#include <string.h>
#include <ctype.h> 

void nthword(char *str, int num) 
{ 
char ret[80];            
int i=0;     
  
/* Counter for the word number. */ 
int wordnum=0;    
  
/* Pointer to character before *str. */ 
/* Used to find first character of word. */  
  char *prev; 
  prev = NULL;   
          
  while ( *str != '\0' ) 
  {                      
     if (!isspace(*str) )               
     {          
        if ( (prev == NULL ) || isspace(prev) ) wordnum++; 
        if (wordnum == num) ret[i] = *str;  
        i++;
        str++; 
        prev = str - 1;         
     } 
     else if (isspace(*str) ) 
     {                  
       str++; 
       prev = str - 1;                         
     }   
  }  
  
  ret[i] = '\0' ;     
  printf("%s \n", ret); 
                       
} 


int main() 
{ 
 
char *test = "select * from mytable ;" ;  
           
/* This should give "from" */ 
nthword(test, 3) ;           
                       
return 0;  
}  

```  

So... any help with this would be great! 
Many thanks -
- trilobite

---

### Post by heyandy889 on 2011-10-14
Hey, dude! Cool program. As you mentioned, strtok() might be a tad easier. But hey, why not prove we can do the heavy lifting, too?

Where you say
```
char ret[80];
```

Maybe try something like
```
char *ret ="";
```

That automatically allocates memory for a string. Well, not a string. It's an array of characters, specifically an array of characters terminated by a null character '\0'.

So try my code. See if it fixes your problem.
Rock on, dude!

PS: my worry is that you're just writing bytes at address 0. It's basically like having an unitialized pointer, check out Pointer Fun with Binky [http://www.youtube.com/watch?v=6pmWojisM_E](http://www.youtube.com/watch?v=6pmWojisM_E) if you're unclear on the idea of pointers and addresses.

---

### Post by trilobite on 2011-10-14
Hi heyandy - thanks for your reply!  
I tried what you suggested (making the statement "char *ret = "" ;" ) but unfortunately I still get a segfault. 
I'm *sure* that I'm close, but not quite there..... :)  
( Oh, and I'll check out that vid that you mentioned too - thanks for that ) 
- trilobite

---

### Post by Bachstelze on 2011-10-14
> **trilobite said:**
> but the code below (although it compiles without error) gives a segfault when run. 


Without error but with a warning that should tell you something:

```
firas@av104151 ~ % gcc -std=c99 -pedantic -Wall -Wextra -g -o test test.c 
test.c: In function ‘nthword’:
test.c:22: warning: passing argument 1 of ‘isspace’ makes integer from pointer without a cast

```

---

### Post by trilobite on 2011-10-14
> **Bachstelze said:**
> Without error but with a warning that should tell you something:

```
firas@av104151 ~ % gcc -std=c99 -pedantic -Wall -Wextra -g -o test test.c 
test.c: In function &#8216;nthword&#8217;:
test.c:22: warning: passing argument 1 of &#8216;isspace&#8217; makes integer from pointer without a cast

```

Ahhh....  Thanks for that, Bachstelze!  
I'll focus on that and see if I can fix it. Bye for now - 
- trilobite 

(UPDATE) - Success! After a bit of fiddling around, this is the code as it now stands. It works and prints the expected output. 
 
```
 
/* Print the nth "word" in a string.  */ 
/* This code is released to the public domain. */ 
/* "Share and enjoy...."  ;)    */  

#include <stdio.h>
#include <string.h>
#include <ctype.h> 

void nthword(char *str, int num) 
{ 
  char ret[80] ; 
          
  int i=0;     
  
  /* Counter for the string number. */ 
  int strnum=0;    
  
  /* Pointer to character before *str. */ 
  /* Used to find first character of string. */  
  char *prev; 
  prev = NULL;   
          
  while ( *str != '\0' ) 
  {                      
     if ( *str != ' ' )               
     {          
        if ( ( prev == NULL ) || ( *prev == ' ' ) ) strnum++; 
        if ( strnum == num ) {ret[i] = *str; i++;}          
        str++; 
        prev = str - 1;         
     } 
     else if ( *str == ' ' ) 
     {                  
        str++; 
        prev = str - 1;                         
     }   
  }  
  
  ret[i] = '\0' ;     
  printf("%s \n", ret); 
                       
} 


int main() 
{ 
 
 char *test = "select * from mytable where city = \"Auckland\" ;" ;     
           
 nthword(test, 1) ;           
               
 nthword(test, 2) ;    
 
 nthword(test, 3) ;                                   
                       
 return 0;
  
}  

```  

Thanks again to all those who've helped.  
- trilobite

---

