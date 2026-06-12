---
title: "Reverse strstr() ?"
date: 2010-06-10
forum: Programming Talk
---

### Post by rockom on 2010-06-10
Hello,

I'm using C, not C++.

Is their a string function that works in reverse of strstr?  I'd like to find  the *last* occurrence of the sequence of bytes (excluding the terminating null byte) in string2 located in string1.
 
Thanks,
-Rocko

---

### Post by Tony Flury on 2010-06-10
How much programming do you know - a "laststrstr" function should not be difficult to write to be honest.

---

### Post by Can+~ on 2010-06-10
Or you could just strstr() multiple times until you get to the last one.

[PHP]
#include <stdio.h>
//#include <stdlib.h>
#include <string.h>

int main(int argc, char **argv)
{
	char str[] = "This is a str, which is a string of characters, isn't it great?";
	char lookfor[] = "is";
	
	char *match = str;
	
	while (match != NULL)
	{
		match = strstr(match, lookfor);
		printf("match: %s\n", match);
		
		// Skip
		if (match != NULL)
			match += sizeof(lookfor)-1;
	}
	
	return 0;
}[/PHP]

Pretty sure this will segfault somewhere, but it's the raw idea.

On the other hand, to write your own laststrstr function, take what strstr does:

```
"[Th]is is a str, which is a string of characters, isn't it great?"
"T[hi]s is a str, which is a string of characters, isn't it great?"
"Th[is] is a str, which is a string of characters, isn't it great?" Match
"Thi[s ]is a str, which is a string of characters, isn't it great?"
"This[ i]s a str, which is a string of characters, isn't it great?"
"This [is] a str, which is a string of characters, isn't it great?" Match
"This i[s ]a str, which is a string of characters, isn't it great?"
"This is[ a] str, which is a string of characters, isn't it great?"
...
```

But on the opposite direction.

---

### Post by Some Penguin on 2010-06-10
It's a little more subtle than that.

Try looking for "aaa" in "aaaa".  You'd want the last three a's, and you'll miss them if you jump by the string length.

There are multiple ways to solve this.  One of the more obvious ways is to reverse both strings and do a strstr, and then some math to fix the indices -- but reversing strings is slightly inefficient in C because strings are zero-terminated.  You can still reverse a string in linear time, but the overhead is higher than it would be in a language where you can compute length without a full traversal.  Another obvious but inefficient way is to check at every offset until you're too close to the end of the string for there to be a match, and to keep track of the last one there is.  

For more efficient ways, look at the Wu-Manber / Aho-Corasick / Horspool / Boyer-Moore family of search methods.

---

### Post by Tony Flury on 2010-06-10
```

char *laststrstr(char *target, char *source)
{
    int found, finished ;  
    char *tp, *sp, *spt, *spa ; 
    sp = source + strlen(source) - strlen(target) ; 
    spt = sp;
    found = FALSE ; 
    finished = FALSE ; 
 
    while(!found && !finished)
    {
        found = TRUE ;
        for( tp = target, spa = spt; found && (*spa != '\0') && (*tp != '\0') ; spa++, tp++ ) 
            if (*tp != *spa)
                found = FALSE ;
        if (found == FALSE)
        {   
            spt -- ; 
            if (spt < source)
                finished = TRUE ;
        }    
    }
    if (finished)
        return NULL ;
    else
        return spt ; 
}

```

Minimal testing - but this seems to work - works from the back of the string - and goes back one character at a time.

Also probably sub-optimal - and i know the variable names are not the most efficient.

---

### Post by dwhitney67 on 2010-06-10
This works too:
```

char* strlaststr(const char* haystack, const char* needle)
{
   char*  loc = 0;
   char*  found = 0;
   size_t pos = 0;

   while ((found = strstr(haystack + pos, needle)) != 0)
   {
      loc = found;
      pos = (found - haystack) + 1;
   }

   return loc;
}

```

---

### Post by lisati on 2010-06-10
Good question. The nearest I could come up with in a quick search was strrchr but that's not quite it..... :(

---

### Post by Tony Flury on 2010-06-11
Improved version of my original algorithm - gets rid of all the flag variables

```

char *laststrstr(char *target, char *source)
{
    char *tp, *sp, *spt ; 

    /* Step backward through the source string - one character at a time */ 
    for( sp = source + strlen(source) - strlen(target) ; sp >= source ; sp --) 
    {
        char *tp, *spt ; 
        /* go forward through the search string and source checking characters
           Stop the loop if the character are unequal or you reach the end of the target (or string) */
        for( tp = target, spt = sp ;  (*tp == *spt)  && (*spt != '\0') && (*tp != '\0') ; spt++, tp++ ) ;
        
        /* if the loop above gets to the end of the target string then it must have matched all the characters */
        if (*tp == '\0')
            break ;
    }
    /* If the outer loop finished before getting to the start of the source string then 
        it must have found a matching sub string */
    return (sp < source) ? NULL : sp ;
}

```

---

### Post by nvteighen on 2010-06-11
Idea:
1. Reverse the haystack
2. Reverse the needle
3. strstr() as usual
4. Reverse the result.

---

### Post by rockom on 2010-06-11
Thanks all for your replies.

I've been playing around with dwhitney67's solution.  Seems to work fine.

-Rocko

---

### Post by Compyx on 2010-06-11
> **nvteighen said:**
> Idea:
1. Reverse the haystack
2. Reverse the needle
3. strstr() as usual
4. Reverse the result.

I was playing with the same idea, would work fine for just a few searches on smallish strings. But it would add a lot of overhead for large strings with a lot of searches.

A good example of 'When in doubt, use brute force' :)

---

### Post by rockom on 2010-06-11
My strings are less than 100 characters.  At least for my app, efficiency is not critical.


-Rocko

---

### Post by Roptaty on 2010-06-11
```


char* laststrstr(char* str, const char* look)
{
  // 
  
  char* m = NULL;

  while (*str != '\0')
  {
    char* m2;

    for (unsigned int i=0; look[i] != '\0'; i++)
    {
      if (look[i] != str[i])
      {
        m2 = NULL;
	break;
      }  
      m2 = str;
    }           
    if (m2 != NULL)
      m = m2; 
    str++;
  }

  return m;
}

```

Without checking for the length of the strings.

---

### Post by nvteighen on 2010-06-12
> **Roptaty said:**
> ```


char* laststrstr(char* str, const char* look)
{
  // 
  
  char* m = NULL;

  while (*str != '\0')
  {
    char* m2;

    for (unsigned int i=0; look[i] != '\0'; i++)
    {
      if (look[i] != str[i])
      {
        m2 = NULL;
	break;
      }  
      m2 = str;
    }           
    if (m2 != NULL)
      m = m2; 
    str++;
  }

  return m;
}

```

Without checking for the length of the strings.

Actually, that code is checking for the length by using the NULL-terminator convention ;)

---

### Post by Roptaty on 2010-06-12
> **nvteighen said:**
> Actually, that code is checking for the length by using the NULL-terminator convention ;)

Yes, we have to stop the iteration somewhere. It doesn't run calculate the length of the string at the start of the algorithm. 

If the length is known prior to the call of the function, it could be optimized with starting at the end of the buffer, and traversing backwards.

---

