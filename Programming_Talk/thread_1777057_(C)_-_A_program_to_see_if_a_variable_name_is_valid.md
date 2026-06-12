---
title: "(C) - A program to see if a variable name is valid"
date: 2011-06-07
forum: Programming Talk
---

### Post by trilobite on 2011-06-07
Hi all - 
I've written the following code which is meant to find out if a variable name is valid. A name is valid if it starts with either a letter or underscore, and (after that) contains only alphanumeric characters or underscores. 
However, the code is giving a warning and a note, and it segfaults when I run it. 
```
 

/* Public domain - see if a variable */ 
/* name is valid.  */  

#include <stdio.h>
#include <stdlib.h> 
#include <string.h>
#include <ctype.h>


/* A helper function to test for an underscore.  */ 
int isuscore(char ch)  
{ 
   return ( ch == '_') ; 
} 


/* See if a string is a valid name.  */ 
void validname(char *str) 
{ 
   if ( isalpha(str[0]) || isuscore(str[0]) )  str++ ;   
      else puts("Bad first character! \n");  
   if ( isalnum(str) || isuscore(str) )  str++ ;     
      else puts("Found a char other than alnum or underscore! \n"); 
       
   puts("This is a valid name. \n");  
} 


int main() { 

char *str1 = "_1test" ;   /* Valid */ 
char *str2 = "foo_42" ;   /* Valid */ 
char *str3 = "5bar" ;     /* Not valid */ 

validname(str1); 
validname(str2); 
validname(str3); 
       
return 0;    
} 

``` 

I get the following when I run the code - 
validname.c:35: warning: passing argument 1 of ‘isuscore’ makes integer from pointer without a cast  
validname.c:18: note: expected ‘char’ but argument is of type ‘char *’  

So, any help is much appreciated - I'm sure I'm close, but not quite close enough..... 
- trilobite

---

### Post by dwhitney67 on 2011-06-07
Your code is terribly hard to read!  If you want to make it even harder to read, why not just concatenate all of the lines of your code to make one very large line?  Just make sure that you embed the semi-colon as appropriate to separate the statements.

As to correct your code issues, you need to pass a single character to the ctype.h functions.  Also, it would be better to declare your strings as const char.

```

...

/* See if a string is a valid name.  */
void
validname(**const** char* str)
{
   if (isalpha(***str**) || isuscore(***str**))
   {
      str++;
   }
   else
   {
      puts("Bad first character! \n");
      **return**;
   }
   if (isalnum(***str**) || isuscore(***str**))
   {
      str++;   /* is this needed??? */
   }
   else
   {
      puts("Found a char other than alnum or underscore! \n");
      **return**;
   }

   puts("This is a valid name. \n");
}


int
main()
{

   **const** char* str1 = "_1test";  /* Valid */
   **const** char* str2 = "foo_42";  /* Valid */
   **const** char* str3 = "5bar";    /* Not valid */

...

```

P.S.  I prefer *str in lieu of str[0].

------------

EDIT:

Test your program using the following, and fix the code to show that it is not valid declaration:
```

const char* str4 = "_5*foo";   /* Not valid */

```
Hint:  Use ispunct() and isspace() over the entire range of characters in the string.  Your code is currently only looking at the first two characters.

---

### Post by Arndt on 2011-06-07
> **dwhitney67 said:**
> Your code is terribly hard to read!  If you want to make it even harder to read, why not just concatenate all of the lines of your code to make one very large line?  Just make sure that you embed the semi-colon as appropriate to separate the statements.

As to correct your code issues, you need to pass a single character to the ctype.h functions.  Also, it would be better to declare your strings as const char.

```

...

/* See if a string is a valid name.  */
void
validname(**const** char* str)
{
   if (isalpha(***str**) || isuscore(***str**))
   {
      str++;
   }
   else
   {
      puts("Bad first character! \n");
      **return**;
   }
   if (isalnum(***str**) || isuscore(***str**))
   {
      str++;   /* is this needed??? */
   }
   else
   {
      puts("Found a char other than alnum or underscore! \n");
      **return**;
   }

   puts("This is a valid name. \n");
}


int
main()
{

   **const** char* str1 = "_1test";  /* Valid */
   **const** char* str2 = "foo_42";  /* Valid */
   **const** char* str3 = "5bar";    /* Not valid */

...

```

P.S.  I prefer *str in lieu of str[0].

------------

EDIT:

Test your program using the following, and fix the code to show that it is not valid declaration:
```

const char* str4 = "_5*foo";

```

Other indendation styles exist than the one dwhitney is showing, but I think all have in common that 'if' and 'else' that belong together are aligned, which they are not in the OP. I wouldn't say there is anything intrinsically bad with putting a statement on the same line as an 'if', but only if there is no 'else' following, and the thing is that this practice is so unusual that it will cause the statement to be overlooked by many.

---

### Post by trilobite on 2011-06-07
> **dwhitney67 said:**
> Your code is terribly hard to read!  
(snip) 
 

Hi - thanks for your reply dwitney67 (I'm sure you never sleep...  ;)  )  

Also thanks to Arndt!  

Ooops... sorry about the code being hard to read. I'll keep that in mind!  

Thanks for your help and the hints too. 
I'll work on getting the whole string scanned (yeah, I was wondering why I was able to put a $ sign at the end, and the code didn't complain about it..... ;) )  
Bye for now - 
- trilobite.

---

### Post by simeon87 on 2011-06-07
If there's no else following, then having an if and another statement on one line is quite common. For example:

```
if (!condition) return 0;
if (condition2) break;
```

Other than indentation the code is quite good: well-chosen function names and variable names, organization into functions, etc.

---

### Post by trilobite on 2011-06-07
Hi again all - 
 I've now solved this problem. I decided (for now anyway) to go back to the array notation rather than using pointers. 
Anyway, here is the considerably revised code - it now works as expected - 
```
 

/* Public domain.                */ 
/* "Share and enjoy...... " ;)   */   

#include <stdio.h>
#include <stdlib.h> 
#include <string.h>
#include <ctype.h>


/* A helper function to test for an underscore or alpha character  */ 
int isuscoreoralpha(char ch)  
{ 
   return ( (ch == '_') || isalpha(ch) ) ; 
   return -1; 
} 

/* A helper function to test for an 
underscore or alnum character */ 
int isuscoreoralnum(char ch) 
{ 
   return ( (ch == '_') || isalnum(ch) ) ; 
   return -1; 
} 


/* See if a string is a valid name.  */ 
void validname(const char* str)
{ 
int i;   
int err=0;   
    
for (i=0; i<strlen(str); i++) 
 {     
   if (!isuscoreoralpha(str[0]) ) 
   { 
     puts("Invalid first character.\n");   
     err += 1; 
     break; 
   } 
   else if (!isuscoreoralnum(str[i]) ) 
   { 
     puts("Non-letter-or-underscore found. \n");  
     err += 1;       
     break; 
   }                           
}
     
if (err == 0) puts("This is a valid name. \n");    
}


int main() { 

char *str1 = "_1test" ;   /* Valid */ 
char *str2 = "foo_42" ;   /* Valid */ 
char *str3 = "5bar" ;     /* Not valid */ 
char *str4 = "ab$f" ;     /* Not valid */ 

validname(str1); 
validname(str2); 
validname(str3); 
validname(str4); 
       
return 0;     
} 

``` 

It might be a bit more verbose than a C guru would do, but it does work.... ;)  
Thanks to all those who helped! 
- trilobite

---

### Post by dwhitney67 on 2011-06-07
A couple of comments wrt validname()...

1.  You always check the first character as you loop through each/every character.  You should only have to check it once.

2.  There's really no need (it's a style issue) to set a flag and use break to exit the for-loop when you encounter an invalid variable name; just print the message and return.


As for isuscoreoralpha() and isuscoreoralnum() have two return statements; obviously the second one will never be reached.

Consider including stdbool.h so that you can declare these functions to return a bool type.

-----------

EDIT:  I just realized that there is no way around checking the first character every time.  Here's my spin on your project:
```

/* Public domain.                */
/* "Share and enjoy...... " ;)   */

#include <stdio.h>
#include <ctype.h>
#include <stdbool.h>


/* See if a string is a valid variable name.  */
bool valid_var_name(const char* str)
{
   if (!str) return false;

   const char* s = str;

   while (*s != '\0')
   {
      // Return false if the first character is a digit, OR if any character
      // is non-ascii, is a control character, or is a punctuation character
      // (with the exception of an underscore).
      //
      if ((s == str && isdigit(*s)) ||
          (!(*s == '_') && (!isascii(*s) || iscntrl(*s) || ispunct(*s))))
      {
         return false;
      }

      ++s;
   }

   return true;
}


int main(void)
{
   const char* var[] = {
                          "foo",     /* Valid */
                          "_1test",  /* Valid */
                          "foo_42",  /* Valid */
                          "5bar",    /* Not valid */
                          "ab$f",    /* Not valid */
                          "!f",      /* Not valid */
                          "f~o",     /* Not valid */
                       };

   for (int i = 0; i < sizeof(var) / sizeof(const char*); ++i)
   {
      printf("%s valid? %s\n", var[i], (valid_var_name(var[i]) ? "true" : "false"));
   }

   const char cntrl[] = { 0x01, 0x02, 0x1F, 0x7F };
   printf("cntrl valid? %s\n", (valid_var_name(cntrl) ? "true" : "false"));

   return 0;
}

```

---

### Post by ThatCoolGuy220 on 2011-06-07
Very usefull

---

