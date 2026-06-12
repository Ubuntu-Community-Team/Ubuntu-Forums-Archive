---
title: "&quot;Brick wall&quot; for pointer to 2-dim CHAR array"
date: 2007-10-11
forum: Programming Talk
---

### Post by nss0000 on 2007-10-11
Gents:

Continuing my excursion in C-land:

I've taken up a text-processing task ... parsing_out  a reasonably long text ( I've chosen one of my favs, Thucydides Peloponesian War )  and then posing various quantitative 'lit-crit' type questions to the parse.

Right-off-the-bat I hit the "brick wall" trying to represent WORDS as pointers to a 2-dim array within the text STRUCT <thuc>.

    *thuc.words[i][j]

.. where each addresses holds an individual char, while the i & j indices holds sentence and word-within-sentence numbers. Natch I MALLOCED each word to reserve space(?)... 

    (thuc.words[i][j] +h)  = malloc( 4*sizeof(char) ) 

but whatever code_blunder I made, I always get SEG-FAULT errors splashing all over the screen when I run the proggie.

Well, eventually I copped-out for a 3-dim char_array which works fine: 

   thuc,words[i][j][k] 

but earns no karmapoints as a learning experience.  I haven't included the actual code here, cause it looks-a-fright, but I would like to know if the multi-dim pointer approach is the better and more flexible syntax.

---

### Post by dwhitney67 on 2007-10-11
Conceptually I think you were trying to achieve something like:

[PHP]#include <stdio.h>
#include <stdlib.h>
#include <string.h>

static const char *strings[] =
{
  "This", "is", "a", "test", "of", "the", "emergency", "broadcasting", "system."
};

int main()
{
  // determine the number of words in our "pool" of words
  const size_t numWords = sizeof(strings) / sizeof(char**);

  // declaration
  char **strArray = 0;

  // allocate the number of words our strArray can hold
  // or if you do not know the number, allocate a max number (e.g. 5000)
  strArray = malloc( sizeof(char*) * numWords );

  // copy each word from "pool" to our allocated strArrray
  for ( int i = 0; i < numWords; ++i )
  {
    strArray[i] = malloc( strlen( strings[i] ) + 1 );

    strncpy( strArray[i], strings[i], strlen( strings[i] ) );
  }

  // display the contents of our strArray and then free the
  // memory allocated to that entry (i.e. the word size dimension)
  for ( int i = 0; i < numWords; ++i )
  {
    printf( "string %d:  %s\n", i, strArray[i] );
    free( strArray[i] );
  }

  // free the strArray (i.e. the number of words dimension)
  free( strArray );
}[/PHP]

To compile:

[FONT="Courier New"]$ gcc -std=gnu99 string.c[/FONT]

---

### Post by hod139 on 2007-10-11
> **dwhitney67 said:**
> Conceptually I think you were trying to achieve something like:
<snip>

The code you wrote is correct and very good, however, I just wanted to point out some details that might not be obvious.

```

[COLOR=#000000][COLOR=#ff8000]// copy each word from "pool" to our allocated strArrray 
  [/COLOR][COLOR=#007700]for ( [/COLOR][COLOR=#0000bb]int i [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000bb]i [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000bb]numWords[/COLOR][COLOR=#007700]; ++[/COLOR][COLOR=#0000bb]i [/COLOR][COLOR=#007700]) 
  { 
    [/COLOR][COLOR=#0000bb]strArray[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]] = [/COLOR][COLOR=#0000bb]malloc[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000bb]strlen[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000bb]strings[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]] ) + [/COLOR][COLOR=#0000bb]1 [/COLOR][COLOR=#007700]); 

    [/COLOR][COLOR=#0000bb]strncpy[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000bb]strArray[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]], [/COLOR][COLOR=#0000bb]strings[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]], [/COLOR][COLOR=#0000bb]strlen[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000bb]strings[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]] ) ); 
  } 
[/COLOR][/COLOR]
```Here you malloc the strArray[i] to be strlen + 1.  This is very important since C style strings must be NULL terminated.  Also, you thankfully used strncpy instead of strcpy.  I just wanted to point out though, that strncpy does not null terminate a string.  This is not a problem here since you allocated enough space and used everything correctly. I find it good practice though to always null terminate my strings after strncpy, just for that extra safety when a bad string is passed in, or you copy over the null terminate.

```

  // copy each word from "pool" to our allocated strArrray
  for ( int i = 0; i < numWords; ++i )
  {
    strArray[i] = malloc( strlen( strings[i] ) + 1 );

    int len = strlen( strings[i] );
    strncpy( strArray[i], strings[i], len );
    strArray[i][len] = '\0'; // just to be safe
  }
```
Like I said earlier though, everything you wrote is correct, I just wanted to mention these subtle details.

---

### Post by nss0000 on 2007-10-12
Gentlemen:

Yep, that's what I (should have) tried to do. Many thanks for your code & thoughtfull comments. I can see they deserve prudent study, and some sell-brewed miniapps.

---

### Post by dwhitney67 on 2007-10-12
> **hod139 said:**
> 
Like I said earlier though, everything you wrote is correct, I just wanted to mention these subtle details.
You're right... I should have used calloc() instead of malloc().

---

