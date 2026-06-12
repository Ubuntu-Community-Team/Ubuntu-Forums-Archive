---
title: "(C) - Is this code using malloc and free correctly?"
date: 2011-10-15
forum: Programming Talk
---

### Post by trilobite on 2011-10-15
Hi all - 
I'm just poking around with doing a few things in C without using library functions.
( I'm doing this to become more familiar with pointers (and now malloc). ) 
This code (to get a substring from a string) works fine, but I'm just wondering if I'm using malloc and free correctly.  
```
 
/* Return a substring from a string.  */ 
/* This code is released to the public domain.     */ 
/* "Share and enjoy...."  ;)    */  


#include <stdio.h>
#include <string.h>
#include <ctype.h> 
#include <malloc.h> 


char *substr(char *str, int first, int last) 
{    
   char *ret = malloc(80); 
                
   int i; 
   int j=0;   
   
   for (i=first; i<last; i++) 
   { 
      ret[j] = str[i];          
      j++;      
   } 
   
   ret[j] = '\0' ; 
   return ret; 
   
   free(ret);         
   
} 



int main() 
{ 
 
char *test = "averyverylongstringindeed"; 
                          
printf("%s \n",substr(test,4,11) );                  
                                
 return 0; 
}  

``` 

Just trying to get comfortable with malloc and free, so confirmation that this code is Ok (or correction of it) would be good. 
Thanks - 
- trilobite

---

### Post by Bachstelze on 2011-10-15
No. When the function hits return, it returns (i.e. exits), so free() is never called. You must call free() in main after you print.

---

### Post by trilobite on 2011-10-15
> **Bachstelze said:**
> No. When the function hits return, it returns (i.e. exits), so free() is never called. You must call free() in main after you print.

Hi Bachstelze, thanks for that -  

Unfortunately, I've just tried that (moving the "free" from the function into main() ), and I get the error "ret undeclared". Hmm... 

I could always make the function "void" and simply print the substring inside it, but I was wanting to keep it as returning a string (and preferably using malloc as well). Looks like that may not be possible. 
- trilobite

---

### Post by Bachstelze on 2011-10-15
Of course you have to store the return value in a variable so you can free() it afterwards.

```
char *p = substr(test, 4, 11);
printf("%s\n", p);
free(p);
```

Note that different calls to substr() will return different values, so you can't do

```
printf("%s\n", substr(test, 4, 11));
free(substr(test, 4, 11));
```

---

### Post by trilobite on 2011-10-15
> **Bachstelze said:**
> Of course you have to store the return value in a variable so you can free() it afterwards.

```
char *p = substr(test, 4, 11);
printf("%s\n", p);
free(p);
```

Note that different calls to substr() will return different values, so you can't do

```
printf("%s\n", substr(test, 4, 11));
free(substr(test, 4, 11));
```

Hi again, and thanks! 
That works perfectly! It's good to now have a useful simple example for using malloc and free. 

( **So** obvious when I saw your code. 
Much better....  :)   )  

Thanks again!  Bye for now - 
- trilobite

---

### Post by cgroza on 2011-10-15
Also, may I suggest that you use the difference between last and first as your argument for malloc?
What happens if:
```

substr(very_long_string, 1, 1000)

```
??

80 won't be enough.

---

