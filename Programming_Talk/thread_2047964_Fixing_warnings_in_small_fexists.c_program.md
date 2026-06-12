---
title: "Fixing warnings in small fexists.c program"
date: 2012-08-25
forum: Programming Talk
---

### Post by trilobite on 2012-08-25
Hi all - 

 I've written a small C program which is supposed to check if a file exists (in the current directory). 
It compiles (but with warnings) and segfaults when run. 

Here is the code - 
```
 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int fexists(FILE *fptr)
{ 
   if ( fopen(fptr, "r") == NULL ) return -1; 
   
   fclose(fptr);  
   return 0;     	
} 


int main( int argc, char *argv[]) 
{

/*  See if a file exists.  */ 
printf("Result is %d \n", fexists(argv[1]) ) ; 

return 0; 

}  


``` 

This gives me the following warnings - 
gcc -Wall -o "fexists" "fexists.c"  (in directory: /home/andy/pdutils)
Compilation finished successfully.
fexists.c: In function ‘fexists’:

fexists.c:16:4: warning: passing argument 1 of ‘fopen’ from incompatible pointer type [enabled by default]
/usr/include/stdio.h:269:14: note: expected ‘const char * __restrict__’ but argument is of type ‘struct FILE *’
fexists.c: In function ‘main’:

fexists.c:30:1: warning: passing argument 1 of ‘fexists’ from incompatible pointer type [enabled by default]
fexists.c:14:5: note: expected ‘struct FILE *’ but argument is of type ‘char *’
***************************

So, if someone is able to tweaks this code to remove these warnings, that would be great... :)  
Many thanks in advance - 
- t

---

### Post by steeldriver on 2012-08-25
fopen **takes **a pointer to char and **returns **a file pointer

!!! NOT TESTED !!!

```
int fexists(**char *filename**)
{ 
   **FILE * fptr;**
   if ( (**fptr = **fopen(filename, "r")) == NULL ) return -1; 
   
   fclose(fptr);  
   return 0;         
} 
```

---

### Post by trilobite on 2012-08-25
> **steeldriver said:**
> fopen **takes **a pointer to char and **returns **a file pointer

!!! NOT TESTED !!!

```
int fexists(**char *filename**)
{ 
   **FILE * fptr;**
   if ( (**fptr = **fopen(filename, "r")) == NULL ) return -1; 
   
   fclose(fptr);  
   return 0;         
} 
```

Hi steeldriver - thanks for that!  
Woohoo!  The code now works! 
I made one further minor change - here it is -  
```
 

int fexists(char *fname)
{  

   FILE *fptr ;  	
	
   fptr = fopen(fname, "r") ;  
   
   if ( !fptr )  return -1 ; 	
	    
   fclose(fptr);  
   return 0;     	

} 

```  

It now works beautifully - I've tested it for files that do and do not exist. 

thanks very much for your help! 
Bye for now - 
- t

---

### Post by dwhitney67 on 2012-08-25
> **trilobite said:**
> Hi steeldriver - thanks for that!  
Woohoo!  The code now works! 
I made one further minor change - here it is -  
```
 

int fexists(char *fname)
{  

   FILE *fptr ;  	
	
   fptr = fopen(fname, "r") ;  
   
   if ( !fptr )  return -1 ; 	
	    
   fclose(fptr);  
   return 0;     	

} 

```  

It now works beautifully - I've tested it for files that do and do not exist. 

thanks very much for your help! 
Bye for now - 
- t

That's not a very good test (i.e. using fopen()) to determine if a file exists.  If the file is owned by another user and you have no permissions to read it, then your test will indicate that the file does not exist... which in fact is not the case.

Consider using stat() to determine if a file exists, and whether it is indeed a file or a directory, a symbolic link, etc.  If needed, stat() can also be used to discern the permissions on the file.

---

### Post by trent.josephsen on 2012-08-25
A couple of notes:

First, you return 0 when the file exists and nonzero (-1) otherwise. This means if you try to use this in code, it will look like 

```
if (fexists(filename)) {
    /* file DOESN'T exist */
} else {
    /* file exists */
}
```

This will surprise anyone who tries to use it and probably isn't what you want. I'd advise you to invert the test so fexists() returns true when the file does exist.

Second, test your program on /etc/shadow and I think you'll find a telling bug.

The third point takes a bit more explanation. Let's suppose I were to write the program that follows, and link it to your library:
```
#include <stdio.h>
#include "fexists.h"
int main(void)
{
    if (fexists("/etc/passwd")) {
        printf("/etc/passwd exists!\n");
    } else {
        printf("You have seriously borked your system.\n");
    }
    return 0;
}
```

Being a conscientious programmer, I like to enable lots of warnings, and I compile it with this command line:
```
cc -std=c99 -pedantic -Wall -Wextra -Wwrite-strings    testexists.c   -o testexists
```

(This is actually how I like to compile programs, and so I have CFLAGS set in .zshrc to make it do this when I use 'make' without a Makefile.)

```
testexists.c: In function 'main':
testexists.c:12:5: warning: passing argument 1 of 'fexists' discards 'const' qualifier from pointer target type [enabled by default]
testexists.c:4:5: note: expected 'char *' but argument is of type 'const char *'
```

I used a string literal and enabled -Wwrite-strings to cause this warning, but you could also see it anywhere you call fexists() on a piece of appropriately labeled (const) read-only memory. -Wwrite-strings is a good warning to enable anyway, at least for new code.

Since your fexists() doesn't write to the memory pointed to by fname, it would be good practice, and eliminate that warning, to declare the function parameter const -- it documents that your function doesn't modify the string you pass it, and it enforces that you won't accidentally do something like this in the future:

```
if (*fname = '\0') {
    /* code to handle empty string passed as a parameter */
}
```

At least, not without being loudly complained at by the compiler for attempting to modify a const string.

---

### Post by Bachstelze on 2012-08-26
Also, return [font=monospace]bool[/font]. That's what it's for.

---

