---
title: "(C) - Pointer subtraction - why doesn't this work?"
date: 2010-12-21
forum: Programming Talk
---

### Post by trilobite on 2010-12-21
Hi all - 
 I've been aplying around with pointers in C and now feel comfortable with most aspects of them. One thing does puzzle me though.  Have a look at this code - 
```
 
char *foo = "obsidian"; 
char *bar = foo + 3;   /* gives "idian" */ 
char *baz = foo - bar; /* Doesn't work! */ 

``` 

Given that foo points to "obsidian", and bar points to "idian", why does the third statement not work? It just gives me - 
"Warning: Initialization makes pointer from integer without a cast"  

So, how can I make this work, setting "baz" so that it gives the string "obs"? 
Many thanks - 
- trilobite

---

### Post by MadCow108 on 2010-12-21
the result of foo-bar is -3 which, as pointers are unsigned types, get wrapped around to 18446744073709551613 on 64 bit systems or 4294967293 on 32 bit.
using this pointer will certainly result in a segmentation fault.

to obtain "obs" as a cstring you must set *(foo+3) to 0
but this again won't work on string literals as they are in read only memory.

the solution:
create a copy of the first three bytes of foo and don't forget to null terminate
```

char *foo = "obsidian"; 
char baz[4];
strncpy(baz, foo, 3)
baz[3]=0

```

---

### Post by trilobite on 2010-12-21
> **MadCow108 said:**
> the result of foo-bar is -3 which, as pointers are unsigned types, get wrapped around to 18446744073709551613 on 64 bit systems or 4294967293 on 32 bit.
using this pointer will certainly result in a segmentation fault.

to obtain "obs" as a cstring you must set *(foo+3) to 0
but this again won't work on string literals as they are in read only memory.

the solution:
create a copy of the first three bytes of foo and don't forget to null terminate
```

char *foo = "obsidian"; 
char baz[4];
strncpy(baz, foo, 3)
baz[3]=0

``` 
Ahh.... many thanks for that, MadCow! 
There's lots to learn about pointers, that's for sure.... ;)  

So, it looks like the "rule of thumb" is - if you want the last part of the string, you can just add "x" to the original pointer. The beginning of the string can be obtained by using strncpy (as shown above). 
The last question - what about the middle few characters of a string - how could that be obtained? 
- trilobite

---

### Post by worksofcraft on 2010-12-21
> **trilobite said:**
> Ahh.... many thanks for that, MadCow! 
There's lots to learn about pointers, that's for sure.... ;)  

So, it looks like the "rule of thumb" is - if you want the last part of the string, you can just add "x" to the original pointer. The beginning of the string can be obtained by using strncpy (as shown above). 
The last question - what about the middle few characters of a string - how could that be obtained? 
- trilobite

[php]
strncpy(baz, foo+3, 3);
// gives you "idi" I suspect
[/php]

---

### Post by trilobite on 2010-12-21
> **worksofcraft said:**
> [php]
strncpy(baz, foo+3, 3);
// gives you "idi" I suspect
[php] 

Hi worksofcraft, thanks for that! 
Yep, that's what I've just tried, and it worked!  
```

/* Get the middle of the string */  
/* "*foo" is "obsidian". */     
/* "*bar" is *foo + 3. "idian" in other words. */ 
  char middle[4]; 
  strncpy(middle, bar, 3); 
  middle[3]=0; 

```  
- trilobite

---

### Post by worksofcraft on 2010-12-21
> **trilobite said:**
> Hi worksofcraft, thanks for that! 
Yep, that's what I've just tried, and it worked!  
```

/* Get the middle of the string */  
/* "*foo" is "obsidian". */     
/* "*bar" is *foo + 3. "idian" in other words. */ 
  char middle[4]; 
  strncpy(middle, bar, 3); 
  middle[3]=0; 

```  
- trilobite

Kewl :)
The most important bit IMO is that you know why you need
[php]
char middle[4];
// instead of 
char *middle;
// ... or
char middle[3];
[/php]
cuz otherwise you might be asking why you get segmentation errors next :shock:

---

### Post by dwhitney67 on 2010-12-21
> **trilobite said:**
>  
The last question - what about the middle few characters of a string - how could that be obtained? 


What you are asking for is an algorithm which will yield a substring of a whole string.  The substring should not be confined to simply the *middle* of the string, but any portion of the string.

Here's something I threw together real quick.  It is not bullet-proof.
```

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

char* substring(const char* string, size_t start, size_t end)
{
   const size_t len = (string ? strlen(string) : 0);

   if (string == NULL || start >= len || start > end)
      return NULL;

   char* rtnstr = NULL;

   if (end >= len)
   {
      rtnstr = malloc(len - start + 1);
      strncpy(rtnstr, string + start, len - start);
   }
   else
   {
      rtnstr = malloc(len - (end - start) + 1);
      strncpy(rtnstr, string + start, (end - start + 1));
   }

   return rtnstr;
}

int main(int argc, char** argv)
{
   if (argc < 3)
   {
      fprintf(stderr, "Usage: %s <string> <start> [end]\n", argv[0]);
      return -1;
   }

   const char*  str   = argv[1];
   const size_t start = atoi(argv[2]);
   const size_t end   = (argc == 4 ? atoi(argv[3]) : strlen(str));

   char* substr = substring(str, start, end);

   fprintf(stdout, "substring: %s\n", (substr ? substr : "bad input!"));

   free(substr);

   return 0;
}

```

The gotchas are the atoi() calls, which can easily be fooled.  Perhaps sscanf() should be used instead, so that error checking can be done.

---

### Post by trilobite on 2010-12-22
> **dwhitney67 said:**
> What you are asking for is an algorithm which will yield a substring of a whole string.  The substring should not be confined to simply the *middle* of the string, but any portion of the string.

Here's something I threw together real quick.  It is not bullet-proof.
```

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

char* substring(const char* string, size_t start, size_t end)
{
   const size_t len = (string ? strlen(string) : 0);

   if (string == NULL || start >= len || start > end)
      return NULL;

   char* rtnstr = NULL;

   if (end >= len)
   {
      rtnstr = malloc(len - start + 1);
      strncpy(rtnstr, string + start, len - start);
   }
   else
   {
      rtnstr = malloc(len - (end - start) + 1);
      strncpy(rtnstr, string + start, (end - start + 1));
   }

   return rtnstr;
}

int main(int argc, char** argv)
{
   if (argc < 3)
   {
      fprintf(stderr, "Usage: %s <string> <start> [end]\n", argv[0]);
      return -1;
   }

   const char*  str   = argv[1];
   const size_t start = atoi(argv[2]);
   const size_t end   = (argc == 4 ? atoi(argv[3]) : strlen(str));

   char* substr = substring(str, start, end);

   fprintf(stdout, "substring: %s\n", (substr ? substr : "bad input!"));

   free(substr);

   return 0;
}

```

The gotchas are the atoi() calls, which can easily be fooled.  Perhaps sscanf() should be used instead, so that error checking can be done. 

Hi dwhitney67 -  
 Thanks for that, that's great! Yes, having a function like that in the ol' "toolbox" will be very handy. 
Always nice to have a good solid general way of solving a problem, and this is a good example of that.  
Bye for now - 
- trilobite

---

