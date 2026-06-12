---
title: "C explode equivalent?"
date: 2009-09-22
forum: Programming Talk
---

### Post by carlosgs91 on 2009-09-22
Hi, I'm learning C and I'd like to find (or make) A PHP explode equivalent, in PHP you have this:

$text = "This is just a test";
$explode = explode(" ", $text);
//

This gives you 1 array with this elements:

$explode[0] = This;
$explode[1] = is;
$explode[2] = just;
$explode[3] = a;
$explode[4] = test;

I want the same but in C, I mean, I want to input a string like that an get the five elements separated by the space (or whatever y select as separator).

I found some pages that have an explode funcion, but they require including files as vector and my compiler (gcc in Ubuntu) has not them.

---

### Post by hessiess on 2009-09-22
Would be better in programming talk: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39). To split a string like that you can loop over the whole string charicter by charicter dumping into an array, then start a new array eleement when you hit a space charicter.

---

### Post by hobo14 on 2009-09-22
**strtok** will let you do something similar in C.

---

### Post by RiceMonster on 2009-09-22
> **hessiess said:**
> Would be better in programming talk: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39). To split a string like that you can loop over the whole string charicter by charicter dumping into an array, then start a new array eleement when you hit a space charicter.

Yep, that's the most straight forward way.

Remember, there are no strings in C, just an array of characters.

---

### Post by carlosgs91 on 2009-09-22
Thanks, I found this, that works:

/* strtok example */
#include <stdio.h>
#include <string.h>

int main ()
{
  char str[] ="- This, a sample string.";
  char * pch;
  printf ("Splitting string \"%s\" into tokens:\n",str);
  pch = strtok (str," ,.-");
  while (pch != NULL)
  {
    printf ("%s\n",pch);
    pch = strtok (NULL, " ,.-");
  }
  return 0;
}

But I don't understand this:

pch = strtok (NULL, " ,.-");

anyone knows why you have to put that? If I quit it my terminal doesn't stop putting -

---

### Post by hobo14 on 2009-09-22
> **carlosgs91 said:**
> Thanks, I found this, that works:

/* strtok example */
#include <stdio.h>
#include <string.h>

int main ()
{
  char str[] ="- This, a sample string.";
  char * pch;
  printf ("Splitting string \"%s\" into tokens:\n",str);
  pch = strtok (str," ,.-");
  while (pch != NULL)
  {
    printf ("%s\n",pch);
    pch = strtok (NULL, " ,.-");
  }
  return 0;
}

But I don't understand this:

pch = strtok (NULL, " ,.-");

anyone knows why you have to put that? If I quit it my terminal doesn't stop putting -

I don't really understand what you're asking now.
pch = strtok (str," ,.-");  gives you the first token,
pch = strtok (NULL, " ,.-");  gives you the token after the previous token.

" ,.-" are the possible delimiters between tokens.

---

### Post by carlosgs91 on 2009-09-22
I'm new and I don't understand some basics about Pointers. pch is a pointer, but I don't understand more... do you know a good manual? The manuals I'm reading only says the basics about pointers:

int number = 45;
char * pointer = &number;

*pointer = number = 45 
pointer = &number = 0xbf98eec0 (for example)

---

### Post by coldReactive on 2009-09-22
You might also want to try to write/find a compiler/whatever that understands PHP for your OS. I've seen people make programs out of PHP for Windows this way.

---

### Post by hobo14 on 2009-09-22
> **carlosgs91 said:**
> I'm new and I don't understand some basics about Pointers. pch is a pointer, but I don't understand more... do you know a good manual? The manuals I'm reading only says the basics about pointers:



Not really the place for this discussion...

int number = 45;
char* pointer = &number;  *<-- pointer is a var of type char*, a ptr to a char*

*pointer = number = 45   *<--this * is dereferencing pointer*
pointer = &number = 0xbf98eec0 (for example)

The two '*' don't have the same meaning.  
In declaration (the first one) it is just part of the type.
When you use it later, it is dereferencing, ie "whatever this pointer is pointing at"

---

### Post by MadCow108 on 2009-09-22
> **carlosgs91 said:**
> But I don't understand this:

pch = strtok (NULL, " ,.-");

anyone knows why you have to put that? If I quit it my terminal doesn't stop putting -


strtok is a quite unusual standard C function as it maintains a state to remember where to continue on the next call
the source in libc looks like that:
```

static char *olds;
...
char *
strtok (s, delim)
     char *s;
     const char *delim;
{
  char *token;

  if (s == NULL)
    s = olds;
...

```
so if you give NULL as the first argument it uses the previously saved state = the string without the already split of token.

this is of course not threadsafe so there is also the reentrant version on unix:
char* strtok_r(char*,char*,char**)
this version does not have a state but instead it saves the new start position after removing the token in the third parameter and this is used when the first parameter is NULL in the next calls

example
```

char s[] = "abc-fgh-def";
// pointer where the new position should be saved
char *sp;

// first call: tokenizes s with delimiter - and saves the position after the first token in the pointer sp
// note the the value of the pointer should be changed
// so we pass the address of the pointer and not the pointer itself (which would then be
//copied and any change will be lost then the function returns
char * x = strtok_r(s, "-", &sp);
printf("%s\n",x); // abc

// second call, first parameter NULL so it uses the string pointed to by sp
// instead and returns the next token and updates the position sp
x = strtok_r(NULL, "-", &sp);
printf("%s\n",x); // fgh

// same again
x = strtok_r(NULL, "-", &sp);
printf("%s\n",x); // def

```

I find this version less confusing as it behaves more like the rest of the C standard function (although it itself is not a standard function)
not to forget the great advantage of thread safeness

---

### Post by carlosgs91 on 2009-09-22
Thanks, I'm doing a explode function, here is what I have:

```
#include <stdio.h>
#include <string.h>

int main() {

int explode(char find[], char text[]) {

printf("\n--------------------------------\nLooking for... %s in %s\n--------------------------------\n\n", find, text);

int characterstext = strlen(text);
int countfind = strlen(find);
char word[100];
int i;
int j;
int k;

for(i=0;i<characterstext;i++) {

for(j=0;j<countfind;j++) {

k = i + j;
sprintf(word, "%s%c", word, text[k]);
printf("%s\n", word);

**if(word==find) {**
printf("Word found");
}

}

sprintf(word, "");


}





}

explode("test", "this is a test, yes I've said a test xD");

}
```

The problem is that when word is equal to find it should say Word found, but it doesn't.

I've displayed both variables, find and word, and the program should works as it displays two times find and word being the same, the problem is that the message doesn't appear, is like the if sentence was bad written, why is this happening?

EDIT: Sorry, I always forget it, C stores characters no strings, if I want to know if two strings are the same I must use strcmp...

[COLOR="Red"]EDIT2:[/COLOR] if((strcmp(word,find)) == "0") { doesn't work, the compiler says:

explode.c: In function &#8216;explode&#8217;:
explode.c:25: warning: comparison between pointer and integer

word is a string, and find is also a string, aren't they?

---

### Post by hobo14 on 2009-09-22
Remove the " "  from around the 0.

---

### Post by carlosgs91 on 2009-09-22
Thanks, it was that!

The manual I'm reading was written in 2000 and hasn't changed since, has C had important changes since? I mean, should I read other manual?

---

### Post by MadCow108 on 2009-09-22
if it told you to compare an integer with a string literal you should definitely change.
Otherwise the C language has not changed much on the basic level in the last standard (C99)
so its probably ok.

I hope your writing that explode function for practice, because its terribly inefficient :)
strtok is a perfectly fine function to use

---

### Post by dwhitney67 on 2009-09-22
Or the strstr() function can be used.

It seems the OP is only interested in determining whether a string is present within another string, not so much as tokenizing a string... which is what his first post seemed to imply.  Thus I am confused.  Also, I am interested in how he was able to implement a nested function (ie. explode() was implemented within main()).

Here's some code I threw together that employs strstr():
```

#include <string.h>
#include <stdio.h>

void explode(const char* find, const char* source)
{
   char* loc = strstr(source, find);

   while (loc != 0)
   {
      printf("Found %s...\n", find);

      loc = strstr(loc + strlen(find), find);
   }
}

int main()
{
   const char* find = "test";
   const char* str  = "This is a test, indeed a real test.";

   explode(find, str);   // instead of using the term explode, perhaps findstr would be more appropriate?

   return 0;
}

```

---

### Post by carlosgs91 on 2009-09-22
I had almost finished the explode function but it's a completely mess and I don't know what I deleted and what I've not. Over 100 lines lost...

The point was to get this:

explode("test", "This is just a test, yes a test, testing this");

to get this arrays:

This is just a
, yes a 
, 
ing this

But now I'll start again using strstr that is much simplier.

---

### Post by Maz_ on 2010-01-30
Hi dee Ho peeps!

My first drop in this board. But as I saw the topic, I could not help joining and answering :) I've heard this question so many times (explode function in C/C++), that I've put up a blog post about it :D And actually wrote a thing which reminds the PHP explode. Naturally, as has been told, the character strings in C, are actually just blocks of memory, containing 8 bit wide values represented as characters, and ending at 8 bits block where all the bits are zero. And since there's no higher level structures like php's lists in native C, excat copy of explode is hard to do. I could have written function which just returns an array of pointers to cutted pieces of string, but it would be inconvenient to use & errorprone. Hence I did my "Cexplode" which offers quite a bunch of functions to get the pieces of strings in convenient way. It's not as efficient as it could, but it is easy to use.

So, here is a link to it: 
[http://maz-programmersdiary.blogspot.com/2008/09/c-explode.html](http://maz-programmersdiary.blogspot.com/2008/09/c-explode.html)

Anyways, what ever way you'll do this, I do not recommend strtok. For following reasons:
1. It is not thread safe. Eg. in multithreaded environment it must not be used from two places simultaneously. This is often hard to control.

2. It mutilates the original string. This is often something we do not wish to happen.

---

### Post by dwhitney67 on 2010-01-30
> **Maz_ said:**
> 
Anyways, what ever way you'll do this, I do not recommend strtok. For following reasons:
1. It is not thread safe. Eg. in multithreaded environment it must not be used from two places simultaneously. This is often hard to control.

2. It mutilates the original string. This is often something we do not wish to happen.
It is great that you are aware of these two issues; many programmers are not (I guess they do not like to read the "fine print" that comes with the man-pages).

Anyhow, for multi-threaded applications, strtok_r() is safe to use.

Concerning the mutilation of the given string, one can counter this by making a temporary duplicate of the original string, thus preserving the original.
```

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

int main()
{
   const char* original = "hello;world;end;transmission";
   char*       dup      = strdup(original);
   char*       tmp      = dup;
   char*       token    = strtok(tmp, ";");

   while (token)
   {
      printf("token = %s\n", token);
      token = strtok(0, ";");
   }

   free(dup);

   printf("Original: %s\n", original);

   return 0;
}

```

---

### Post by PmDematagoda on 2010-01-30
At Maz_ & dwhitney67:- Please continue this discussion in a new thread without resurrecting old ones.

Thread closed due to necromancy.

---

