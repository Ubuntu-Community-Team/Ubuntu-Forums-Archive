---
title: "g++ bug... is it worth reporting?"
date: 2011-02-11
forum: Programming Talk
---

### Post by worksofcraft on 2011-02-11
We all know that in C++ a \\ introduces a comment to the end of line and according to the standard we can put anything we like in that comment right?
[php]

// g++ bug.cpp
#include <cstdio>

int main() {
	const char * pString = "I am a string with \\ in me";
	// scan the string for a \
	do
	{
		if (*pString == '\\') return !printf(
			"this string has a \\ in it!\n"
		);
	}
	while (*pString++);
	
	return !printf("no \\ found!\n");
}
[/php]
... so do you think above program should report a back slash or not ?

---

### Post by cipherboy_loc on 2011-02-11
Have you tried it under different compilers  and different versions of gcc?



Cipherboy

---

### Post by Vaphell on 2011-02-11
so \ at the end of the //comment line continues that comment in the next line. I don't know if it should happen but i don't have a problem with that.

```

//something \
printf( "text1\n" ); \
printf( "text2\n" );
printf( "text3\n" );
```

this will print only text3 as first 3 lines are a multiline comment thanks to \ joining them, even my gedit agrees (these lines are blued out)

---

### Post by Dark_Stang on 2011-02-12
Edit: Nvm, now I get what you meant. So it looks like the lexical analyzer is looking for the next character and is skipping white space. But to put it into perspective, this is what it's seeing.


```

...
// scan the string for a \(\n\t)do(\n\t)
...

```

Not sure what you'd have to do to compensate for that.

---

### Post by johnl on 2011-02-12
> **worksofcraft said:**
> We all know that in C++ a \\ introduces a comment to the end of line and according to the standard we can put anything we like in that comment right?


actually a // introduces a comment to the end of the line? '\\' in a string emits the character '\'.

[php]

// g++ bug.cpp
#include <cstdio>

int main() {
	const char * pString = "I am a string with \\ in me";
	// scan the string for a \
	do
	{
		if (*pString == '\\') return !printf(
			"this string has a \\ in it!\n"
		);
	}
	while (*pString++);
	
	return !printf("no \\ found!\n");
}
[/php]
> 
... so do you think above program should report a back slash or not ?


> 
The following are the first four (of eight) phases of translation specified in the C Standard:

    *Trigraph replacement &#8212; The preprocessor replaces trigraph sequences with the characters they represent.
    [B]*Line splicing &#8212; Physical source lines that are continued with escaped newline sequences are spliced to form logical lines.
    *Tokenization &#8212; The preprocessor breaks the result into preprocessing tokens and whitespace. It replaces comments with whitespace.[/B]
    *Macro expansion and directive handling &#8212; Preprocessing directive lines, including file inclusion and conditional compilation, are executed. The preprocessor simultaneously expands macros and, in the 1999 version of the C standard, handles _Pragma operators.


```


// g++ bug.cpp
#include <cstdio>

int main() {
	const char * pString = "I am a string with \\ in me";
	// scan the string for a \	do
	{
		if (*pString == '\\') return !printf(
			"this string has a \\ in it!\n"
		);
	}
	while (*pString++);
	
	return !printf("no \\ found!\n");
}


```

Line splicing is not syntax aware and occurs before comments are stripped out.  It doesn't care if it's in a comment or not.  Not a bug.

---

### Post by worksofcraft on 2011-02-12
> **Vaphell said:**
> so \ at the end of the //comment line continues that comment in the next line. I don't know if it should happen but i don't have a problem with that.

```

//something \
printf( "text1\n" ); \
printf( "text2\n" );
printf( "text3\n" );
```

this will print only text3 as first 3 lines are a multiline comment thanks to \ joining them, even my gedit agrees (these lines are blued out)

then you should try appending a space after the \ ;)

---

### Post by Vaphell on 2011-02-12
so the \ has to be the last thing in line to join lines according to gedit, oh noes! :P it's not like gedit syntax highlight is pefect, i see glitches all the time.

I didn't know about the stuff johnl posted but it's not the first time i see \ joining lines so i just assumed it's normal.

---

### Post by worksofcraft on 2011-02-12
> **johnl said:**
> ...
Line splicing is not syntax aware.  It doesn't care if it's in a comment or not.  Not a bug.

That is debateable... the standard IMO says that ANYTHING inside a comments is skipped and ignored and so perhaps it shouldn't be splicing comment lines... especially when you put a space after the \
:shock:

Anyway I changed the layout so it reads:

[php]
// g++ bug.cpp
#include <cstdio>

int main() {
	const char * pString = "I am a string with \\ in me";
	// scan the string for a \	
 	do {
		if (*pString == '\\') return !printf("this string has a \\ in it!\n");
	} while (*pString++);
	
	return !printf("no \\ found!\n");
}
[/php]

and now the compiler alerts me to the problem:
```

$ g++ bug.cpp
bug.cpp:9: error: expected unqualified-id before &#8216;while&#8217;
bug.cpp:11: error: expected unqualified-id before &#8216;return&#8217;
bug.cpp:12: error: expected declaration before &#8216;}&#8217; token

```

then I changed the comment style to be /* scan the string for a \ */

---

### Post by worksofcraft on 2011-02-12
> **cipherboy_loc said:**
> Have you tried it under different compilers  and different versions of gcc?



Cipherboy

I happen to know that in the 1990's a company named Zortech decided it was a bug in their compiler according to the standard and that they fixed it.

I don't think it's a problem just it resulted in unexpected behavior with above construct compiling just fine... serves me right for commenting but not changing the borrowed code to my usual indentation style in the first place :P

---

### Post by johnl on 2011-02-12
> **worksofcraft said:**
> That is debateable... the standard IMO says that ANYTHING inside a comments is skipped and ignored and so perhaps it shouldn't be splicing comment lines... especially when you put a space after the \
:shock:

There are two distinct parts to compilation of C code: pre-processing, and compiling.  

The four stages of pre-processing I posted before are specified in the C standard and it's required that they are performed in that order (or at least the results are the same as if they are).Therefore line splicing will always occur before comments are removed or the source is tokenized.  

You can view the pre-processor output for your code with 'gcc -E' or 'cpp'.Regardless, compile your code with -Wall and you won't run into this issue because you will see:

```

gcc -Wall -ggdb3 -std=c99 -pedantic  -c test.c -o test.o
test.c: In function &#8216;main&#8217;:
test.c:6: warning: multi-line comment

```

The GCC manual even mentions this:

> 
# Continued lines are merged into one long line.

A continued line is a line which ends with a backslash, `\'. The backslash is removed and the following line is joined with the current one. No space is inserted, so you may split a line anywhere, even in the middle of a word. (It is generally more readable to split lines only at white space.)

The trailing backslash on a continued line is commonly referred to as a backslash-newline.

**If there is white space between a backslash and the end of a line, that is still a continued line.** However, as this is usually the result of an editing mistake, and many compilers will not accept it as a continued line, GCC will warn you about it. 

[cpp line control](http://gcc.gnu.org/onlinedocs/cpp/Initial-processing.html#Initial-processing#Line-Control)

---

### Post by Vaphell on 2011-02-12
if you compiled with -Wall flag you'd get
```
warning: multi-line comment
``` and there would be no surprises

---

### Post by ibuclaw on 2011-02-12
> **worksofcraft said:**
> I happen to know that in the 1990's a company named Zortech decided it was a bug in their compiler according to the standard and that they fixed it.


And that fix is in his current software project too. ;)

---

### Post by worksofcraft on 2011-02-12
> **ibuclaw said:**
> And that fix is in his current software project too. ;)

Do you mean in the "D" language compiler that [Walter Bright's new company]("http://en.wikipedia.org/wiki/Digital_Mars") is now renowned for ?

---

