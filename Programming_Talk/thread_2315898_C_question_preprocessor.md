---
title: "C question preprocessor"
date: 2016-03-03
forum: Programming Talk
---

### Post by afrugh on 2016-03-03
```
int main(void) {
  printf("I am Ubuntu!\n");
  return 0;
}
```

as example; it gives warning but it works even when I remove including stdio.h !

how is that possible ?

---

### Post by trent.josephsen on 2016-03-03
If you're learning C, the first thing you should do is abandon any idea that the compiler will stop you when you mess up :-)

Header files contain function *declarations*. The declaration only exists to tell the compiler what arguments a function takes and what it will return; it doesn't persist beyond the first few compile steps. Removing the declaration doesn't mean the function stops existing; it just means that the compiler has no way to alert you if you use it wrong. As long as you use printf in a manner consistent with its *actual implementation*, it's fine. If you try to call printf(42) or some other such nonsense, you might get weird results, or the program might crash. If you try to use it twice, with different arguments, the compiler might get confused. Or it might work "correctly". It might work half the time, or every day except Wednesday, or work for two years to be broken by an updated libc. That unpredictability is what "undefined behavior" means.

Standard header files exist, basically, to give the compiler enough information to check your work. If you don't give it the information, the compiler can't check your work. But it won't necessarily *not* work; it will just be unchecked.

A large fraction of programming, in any language but especially in C, is organizing data so that your tools will let you know if something's wrong. Don't ignore compiler warnings, even (especially) if the code "seems to work".

---

### Post by mfvpcrec on 2016-03-03
Hi! If I compile 
```


#include <stdio.h>

int main(void) 
{
  printf("I am Ubuntu!\n");
  return 0;
}


```

I do not get any error. But if I compile the same code without stdio.h I get a warning but no a binary to run...
Note: Remember delete the old binary created by the compiler.

Bye!

---

### Post by afrugh on 2016-03-03
trent
thanks for detailed answer and I know what checking preprocessing mean but I don't understand where the compiler finds printf() function when I don't mention the library or header stdio !

[COLOR=#000000]But it won't necessarily [/COLOR][I]notwork; it will just be unchecked.
[/I]yes and that's why my question..

and indeed I absolutely should abandon that idea compiler because now I have another program which works fine but it says:

[I]*** stack smashing detected ****; ./strvars terminated 
core dumbed [/I]

but it terminated after it did the job. 

```


#include <stdio.h>
#include <string.h>


int main (void) {
  
  printf("\n\tSTRS AND VARS..\n\n");
  
  // make vars
  int    myint;
  double mydouble;
  char   mychar;
  char   mystr[23];
  
  //init
  myint     = 10;
  mydouble  = 20.1;
  myint     = myint * 2 + mydouble;
  mychar    = 't';
  mychar    = mychar + 1;
  
  strcpy(mystr, "Mush nisj xbuntu wéwer!"); 
  mystr[10] = mychar;
  
  // %d for int & %f double & %c char & %s string 
  printf("\n");
  printf("My int myint is %d\n", myint);
  printf("My double is %f\n", mydouble);
  printf("My char is %c\n", mychar);
  printf("My string is %s\n", mystr);
  printf("\n");
  
  return 0;


}


```

here the problem with ```
strcpy(mystr, "Mush nisj xbuntu wéwer!"); 
```
replace wéwer by wewer and no smashing !

---

### Post by trent.josephsen on 2016-03-03
> **afrugh said:**
> trent
thanks for detailed answer and I know what checking preprocessing mean but I don't understand where the compiler finds printf() function when I don't mention the library or header stdio !
Sorry, I guess I overlooked that detail. Functions actually exist in libraries which are "linked" in to the binary in the final step. There are two libraries that have C standard library functions, libc and libm. libc, which is most of the standard library, is linked in by default; if you want to use math features (like pow, sin, exp) you have to link in libm. But printf is in libc so you don't have to do anything special to include it.

---

### Post by trent.josephsen on 2016-03-03
*[double post]*

---

### Post by spjackson on 2016-03-04
> **afrugh said:**
> 

here the problem with ```
strcpy(mystr, "Mush nisj xbuntu wéwer!"); 
```
replace wéwer by wewer and no smashing !
Because of the character encoding in use (maybe utf-8?) 'é' is a multi-byte character. Hence the two strings are different lengths.
```

$ cat length.c

#include <stdio.h>
#include <string.h>

int main(void)
{
    printf("Length 1: %d\n", (int) strlen("Mush nisj xbuntu wéwer!"));
    printf("Length 2: %d\n", (int) strlen("Mush nisj xbuntu wewer!"));
    return 0;
}
$ make length
cc     length.c   -o length
$ ./length 
Length 1: 24
Length 2: 23

```
As it happens,  char   mystr[23] isn't big enough for either of them.

---

### Post by afrugh on 2016-03-05
great just great, thank u
but suppose I do ```
putchar('[FONT=Ubuntu Mono][COLOR=#000000]é[/COLOR][/FONT]');
```

[http://en.cppreference.com/w/c/io/putchar](http://en.cppreference.com/w/c/io/putchar) 
says
> 
putchar [C]("http://en.cppreference.com/w/c") [File input/output]("http://en.cppreference.com/w/c/io") 

[TABLE]
[TR]
[TD]Defined in header *<stdio.h>*[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]*int putchar( int ch );*[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]


Writes a character *ch *to *stdout*. _Internally, the character is converted to unsigned char just before being written._

if it's the case then é should be in ascii range 8bit 2^8 = 256 chars and max_char should be 2^8-1 = 255!

[IMG]http://www.asciitable.com/index/extend.gif[/IMG]


é (130)

but

```
char c = 'é';
printf("%d", (int)c);
```and now something crazy is going to happen when you do this:

```

#include <stdio.h>


int main( int argc, char *argv[] )  {
  char c = 'é';
  
  putchar(c);
  putchar('\n');
  
  printf("%d\n", c);
  printf("%c\n", (int)c);
}

```


```

#include <stdio.h>


int main( int argc, char *argv[] )  {
  char c = getchar();
  
  putchar(c);
  putchar('\n');
  
  printf("%d\n", c);
  printf("%c\n", (int)c);
}

```

(full screen)
1. [http://i.imgur.com/sWEGrGF.png](http://i.imgur.com/sWEGrGF.png)

2. [http://i.imgur.com/FCI4tum.png](http://i.imgur.com/FCI4tum.png)

[IMG]http://i.imgur.com/rM6sUXB.png[/IMG]


[IMG]http://i.imgur.com/qAiIhBb.png[/IMG]


lol ! what's going there  ? :D

---

### Post by trent.josephsen on 2016-03-06
é isn't part of the "core C character set"; i.e. it's not guaranteed by the C standard to exist either at compile time or runtime. If you want to use characters outside of the core set ([which see here](https://en.wikipedia.org/wiki/C_%28programming_language%29#Character_set)), you are relying on implementation-defined behavior. So you need to know how your implementation handles characters not in the core set.

There is a Unicode codepoint that represents the é character: [U+00E9 LATIN SMALL LETTER E WITH ACUTE](http://www.fileformat.info/info/unicode/char/e9/index.htm). But it can be encoded different ways. In [UTF-8]("https://en.wikipedia.org/wiki/UTF-8"), it's encoded as two 8-bit bytes: **‹C3 A9›** in hexadecimal. (I'll use ‹ › to represent bytes.) In [CP437]("https://en.wikipedia.org/wiki/Code_page_437"), it's encoded as a single byte: **‹82›**. In [Windows-1252](https://en.wikipedia.org/wiki/Windows-1252), it's a *different* single byte: **‹E9›**. And there are dozens of other possibilities.

When you might be talking about multibyte characters, you have to realize that C's **char** type is *really* just a byte, not a character, and things like putchar() and getchar() operate on bytes. Also, **char** may be (and is) signed, so bytes ‹80› through ‹FF› happen to represent negative numbers. This gives us a basis for understanding what's going on with your examples. (Aside from the fact that you're foolishly ignoring the compiler warnings.)

With ascii1 on Linux, it looks like you have a relatively simple issue. The file encoding is UTF-8, so 'é' is a two-byte character (equivalent to '\xc3\xa9'). Multibyte character literals **are allowed** in C. However, char is still just one byte, so you're trying to stuff two bytes into one. The value overflows, just as if you'd written "c = 0xc3a9". The higher order bits are lost to the overflow and c becomes ‹A9›. As a signed 8-bit number, the *byte* ‹A9› represents the *number* -87, and that's what you get when you print it with %d. But when you print it with putchar() or printf("%c"), you're breaking the rules. ‹A9› isn't a character by itself; it's only valid as part of a multi-byte character. So when it shows up alone, *not* part of a multi-byte character, the terminal (PuTTY) doesn't really know what to do with it, and appears to print some placeholder (might be [U+2592 MEDIUM SHADE](http://www.fileformat.info/info/unicode/char/2592/index.htm)). And that's why ascii1 does what it does.

In ascii2, you try to read a multi-byte character with getchar(). But remember getchar() works on bytes, not whole characters. You entered é, which is actually the multibyte sequence ‹C3 A9›. getchar(), being called only once, returned the first byte: ‹C3›, and the rest was left in the input stream. As a signed 8-bit number, ‹C3› represents -61, and that's what you get when you print it with %d. But again, ‹C3› is *also* not valid unless it's part of a multibyte character, so the terminal has some fallback behavior that displays a placeholder when you use putchar(). You can tell that there's an extra byte by calling getchar() *twice* -- it'll return the "missing" ‹A9› the second time.

Now as for Windows, I'm not really an expert, but it looks like you have an extra "problem": the encoding used for characters in the source code is UTF-8, but the terminal it runs in appears to be using [CP850](https://en.wikipedia.org/wiki/Code_page_850). ascii1 works in exactly the same way it did before, but the terminal in this case has a meaningful representation for the byte ‹A9›: it's the registered trademark symbol ([U+00AE REGISTERED SIGN](http://www.fileformat.info/info/unicode/char/00ae/index.htm) if you're curious). So that's why you get® in this terminal instead of the placeholder &#9618; you got in PuTTY. If you run the same program in a different terminal, or with the encoding settings changed, you'll see something different. (Or if you tell PuTTY to use cp850, they'll both be broken in the same way.)

**tl;dr** - Strings are hard.

FYI, é isn't part of ASCII, and the table you posted is just CP437 -- nothing to do with ASCII. Real ASCII is a 7-bit encoding. "Extended ASCII" isn't an actual encoding, just a way to refer to the "extra" parts of any encoding that's backwards compatible with ASCII.

---

