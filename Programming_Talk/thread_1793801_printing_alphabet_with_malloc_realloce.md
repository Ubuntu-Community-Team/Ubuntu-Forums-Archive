---
title: "printing alphabet with malloc realloce"
date: 2011-06-30
forum: Programming Talk
---

### Post by ddimit on 2011-06-30
```
#include "stdafx.h"
#include <stdlib.h>
#include <stdio.h>


int _tmain(int argc, _TCHAR* argv[])
{ int i; char *pa;

  pa[0]='a';
  for(i=1;i<26;i++){  
  pa= (char *) realloc (pa, i+1 * sizeof(char));
  pa[i]='a'+i;    
  
 


}
printf("%s",pa);
    
   
}
```

really whats the problem

---

### Post by Tony Flury on 2011-06-30
You don't allocate any memory for pa to point to in the first place.

All that 
```

char *pa ; 

```
will do is to allocate space for the pointer - which subsequently could be pointing anywhere

you need to call malloc to allocate a memory segment to p - before you do 

```

pa[0] = "a" ;

```

In short you should do :
```

char *pa;
pa= (char *) malloc (1 * sizeof(char));
pa[0] = 'a' ;

```

---

### Post by ddimit on 2011-06-30
> **Tony Flury said:**
> You don't allocate any memory for pa to point to in the first place.

All that 
```

char *pa ; 

```will do is to allocate space for the pointer - which subsequently could be pointing anywhere

you need to call malloc to allocate a memory segment to p - before you do 

```

pa[0] = "a" ;

```In short you should do :
```

char *pa;
pa= (char *) malloc (1 * sizeof(char));
pa[0] = 'a' ;

```
oh thanks sir
when its in the last state of loop i=25 it creates the last memory block and puts the last letter why when im printing the alphabet it prints some more random letters can you explain please? i have this query because i tell to the program do exactly the necessary blocks of memory
edit oh it does that because it has some other data from other programs at the next blocks of memory?

---

### Post by dwhitney67 on 2011-06-30
> **ddimit said:**
> 
edit oh it does that because it has some other data from other programs at the next blocks of memory?

I'm not sure why you had any questions performing this little project; I provided you with an example of this same project [here]("http://ubuntuforums.org/showpost.php?p=10996685&postcount=5").

As for why you have "garbage" printing out, it is because you did not null-terminate the char array, which you want interpreted as a string.

---

### Post by ddimit on 2011-06-30
> **dwhitney67 said:**
> I'm not sure why you had any questions performing this little project; I provided you with an example of this same project [here]("http://ubuntuforums.org/showpost.php?p=10996685&postcount=5").

As for why you have "garbage" printing out, it is because you did not null-terminate the char array, which you want interpreted as a string.
ok sorry for being annoying but i wanted to make it somehow like i was doing 
because i had exercise in univercity about malloc and i didnt write well
one more question and i promise i will dont post again 
when the loop ends the i gets the value 26;
why we write i-1 = '\0'
the i-1 place isnt the last letter of the alphabet?  so it will replace the z with '\0'? this is my last question
0 a
1 b
25 z

---

### Post by dwhitney67 on 2011-06-30
> **ddimit said:**
> 
one more question and i promise i will dont post again

Don't say that; you are free to post as often as you like.  :-)

> **ddimit said:**
> 
when the loop ends the i gets the value 26;
why we write i-1 = '\0'
the i-1 place isnt the last letter of the alphabet?  so it will replace the z with '\0'? this is my last question
0 a
1 b
25 z
There are 26-letters in the English alphabet, 'a' through 'z'.  If you want to store each letter of the alphabet in an array, one can think of 'a' being at position 0, and 'z' as being at position 25. Remember, in C, an array index is zero-based.

To treat the array as a string of characters, then one must append a null-character at the end of the array, or at position 26 using the example above.

Using your approach:
```

int   num_chars = 0;
char* array = 0;

++num_chars;
array = (char*) malloc(num_chars * sizeof(char));  /* here we allocate one space */

array[0] = 'a';   /* or array[num_chars - 1] = 'a'; */

for (int i = 1; i < 26; ++i)
{
   ++num_chars;   /* increment the number of characters */

   array = (char*) realloc(num_chars * sizeof(char));

   array[i] = 'a' + i;
}

/* here we have an array with values ranging from 'a' through 'z' */

/* now we want to add a null character so that the array can be treated as a string */

++num_chars;  /* we will be inserting another char, which will give a total of 27 chars (26 + 1) */

array = (char*) realloc(array, num_chars * sizeof(char));

array[num_chars - 1] = '\0';  /* insert null-char at position 26 */

```
I hope this makes sense; just remember, arrays are indexed using an index that is zero-based, not one-based.

---

