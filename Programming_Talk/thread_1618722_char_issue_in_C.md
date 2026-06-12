---
title: "char* issue in C"
date: 2010-11-11
forum: Programming Talk
---

### Post by Mr.Macdonald on 2010-11-11
I honestly have no clue what or why it is happening, but this is what I see.

If I print a char* before calling a certain function, it prints fine. If I then also print the same char*, but inside the function it was called, it prints all but the last char.

[PHP]
char* a = "Anything"
printf(a); --> Anything
func(a);

func(char* b) {
 printf(b); --> Anythin
}
[/PHP]

I printed out the char* as a list of integers of the char (ie '1' == 49). I found that when passed into the function, something changes the last char to a ascii value of 25 (End of Medium). No clue as to why.

PreFunc and InFunc
(+ 1 1 1 1 1) 40 43 32 49 32 49 32 49 32 49 32 49 41 
(+ 1 1 1 1 1  40 43 32 49 32 49 32 49 32 49 32 49 25

This problem (not error, somebody thought this was a good idea), started when I began using strtok and string.h. It probably isn't that, but I don't know. I am also using realloc to cut off the unused tail to char*, but haven't noticed a difference when I allow for a longer tail (cut less).

Ill show my code if you want, but it is quite odd and requires a lot of files as the program is a macro style this (like CPP).

Thank you

---

### Post by saulgoode on 2010-11-11
You should not use your text string as the format string in a printf statement.

Instead use:

```
printf("%s", a);
```

---

### Post by trent.josephsen on 2010-11-11
First, when you're posting code, especially code that's exhibiting weird issues like this, post a minimal compilable example.  This code works as I expect:
```
#include <stdio.h>
void func(char* b) { 
        printf(b);
}

int main(void)
{
        char* a = "Anything";
        printf(a);
        func(a); 
}
```

Second, it's not advisable to pass strings directly to the first argument of printf, because someone might inject % sequences into them that could compromise security.

Third, you're aware that a declaration like
```
char *a = "Anything";
```
puts "Anything" into read-only shared memory, right?  Any attempt to modify it results in undefined behavior.  If you're passing pointers to read-only memory around without a const qualifier, that's a big red flag.  Use -Wwrite-strings to warn about this kind of problem, and change the declaration (if you have such in your code) to
```
 char a[] = "Anything";
```
to make sure you get a modifiable string.

Finally, since the string is not dynamically allocated, it's quite possible (and even very likely) that some out-of-bounds operation in an entirely different part of the program overwrites it by accident (if the string were dynamically allocated, the behavior would likely be erratic).  Undefined behavior affects *your entire program*, not just the function or compilation unit in which it occurs.

---

### Post by Mr.Macdonald on 2010-11-11
I understand the whole memory issue. It is not a const string. It is read from file and modified several times. The issue occurs at a distinct point during one of those times.

The point that it occurs is similar to the example, in that I print before the call and inside the called function. Look at the byte by byte read of the char*. It was generated with the code below. Same code was called both before and inside the function for the same pointer.

[PHP]
/* char* expr */
printf("%s", expr);
for (i=0;expr[i] != '\0';i++)
  printf("%d ", (int)expr[i]);
printf("\n");[/PHP]

> Finally, since the string is not dynamically allocated, it's quite possible (and even very likely) that some out-of-bounds operation in an entirely different part of the program overwrites it by accident (if the string were dynamically allocated, the behavior would likely be erratic). Undefined behavior affects your entire program, not just the function or compilation unit in which it occurs.

Behavior is not erratic. It is consistent and exact for every compilation and execution. I also get the same issue (inserted 25) in another part of my program with a different pointer.

---

### Post by Mr.Macdonald on 2010-11-11
Something weird is going on. I ran my code in valgrind, and it worked perfectly. None of the above issues existed at all.

---

### Post by Some Penguin on 2010-11-11
Generally speaking, people here have better things to do than play "guess the code" with people who post misleading, irrelevant and incomplete code segments.  You're clearly overwriting data when you're not expecting to, and you've also clearly choosing to not show any code which might possibly do so; nor are you showing how it's being initialized; nor any of the call stacks; or anything at all, really.

---

### Post by dwhitney67 on 2010-11-11
> **Some Penguin said:**
> Generally speaking, people here have better things to do than play "guess the code" with people who post misleading, irrelevant and incomplete code segments.  You're clearly overwriting data when you're not expecting to, and you've also clearly choosing to not show any code which might possibly do so; nor are you showing how it's being initialized; nor any of the call stacks; or anything at all, really.

My favorite is when the person seeking help inserts and/or modifies their code with the correct solution, but then states that it still doesn't work.  It turns out they failed to recompile the code.

---

### Post by trent.josephsen on 2010-11-11
> **Mr.Macdonald said:**
> I understand the whole memory issue. It is not a const string.
Terminology:  "const" is not the same as "read-only".  There's nothing const about
```
char *a = "something";
```
> The point that it occurs is similar to the example, in that I print before the call and inside the called function.
Oh, well, that answers your question then.  You've obviously got a stack pointer load failure on line 28.  That *always* happens when I print something and then call a function.
> Behavior is not erratic. It is consistent and exact for every compilation and execution. I also get the same issue (inserted 25) in another part of my program with a different pointer.
Well, sounds like it's either a systematic problem in the way you have chosen to deal with strings, or undefined behavior somewhere else that happens to manifest itself in a systematic way.  There's also a slim possibility that you've found a bug in your compiler or standard library.  Either way, we're helpless without code that exhibits the bug.

---

### Post by worksofcraft on 2010-11-11
> **trent.josephsen said:**
> Terminology:  "const" is not the same as "read-only".  There's nothing const about
```
char *a = "something";
```


That is true, but while we got nothing to actually discuss here we could talk about const-ness ;) What do you think of this one:

[php]
// g++ invalid.cpp
#include <cstdio>
#include <cstring>

// Don't you love how they do things like this:
// (so then you are kinda encouraged to cast things unnecessarily)
typedef unsigned char FcChar8;

// and somewhere deep in their obscure library code is something like this
void Fc_ProcessText(FcChar8 *pSomeText) {
	strcpy((char *) pSomeText, "read only data was trashed!");
}	

int main() {
	// Hey Mr Compiler, I really don't want this text to change OK!
	const char aMyText[] = "I really don't expect this text to change";

	// Dang! I'm gunna hafta cast regular chars into FcChar8 again
	// for that obscure library malarkey!
	Fc_ProcessText((FcChar8 *) aMyText);

	printf(
		"Sorry your program crashed %s: Please use proper ROM chips next time :P\n",
		aMyText
	);
	return 0xBAD;
}
[/php]

---

### Post by trent.josephsen on 2010-11-11
> **worksofcraft said:**
> That is true, but while we got nothing to actually discuss here we could talk about const-ness ;) What do you think of this one:

<code snipped>

What about it?

Obviously it's hideous and your best bet is to declare things the way they will be used.  In particular, if a library author feels inclined to insist that the argument to Fc_ProcessText be a pointer-to-FcChar8, they should provide some documented way to convert an ordinary pointer-to-char into a pointer-to-FcChar8.  Alternatively, with this declaration you could do the following:

```
const FcChar8 aMyText[] = "This should not change";
Fc_ProcessText(aMyText);
```

which will allow the compiler to warn you just about discarding qualifiers (but might raise other issues; I'm not sure what the rules are for initializing an array of unsigned-char with a string literal on a system where char is signed).

The real problem here (as I'm sure you understand) is the cast.  The only reason to have a cast here is to suppress the compiler warning; if you wanted to be warned about this kind of thing, you shouldn't have used it.

---

### Post by Arndt on 2010-11-11
> **worksofcraft said:**
> That is true, but while we got nothing to actually discuss here we could talk about const-ness ;) What do you think of this one:

[php]
// g++ invalid.cpp
#include <cstdio>
#include <cstring>

// Don't you love how they do things like this:
// (so then you are kinda encouraged to cast things unnecessarily)
typedef unsigned char FcChar8;

// and somewhere deep in their obscure library code is something like this
void Fc_ProcessText(FcChar8 *pSomeText) {
	strcpy((char *) pSomeText, "read only data was trashed!");
}	

int main() {
	// Hey Mr Compiler, I really don't want this text to change OK!
	const char aMyText[] = "I really don't expect this text to change";

	// Dang! I'm gunna hafta cast regular chars into FcChar8 again
	// for that obscure library malarkey!
	Fc_ProcessText((FcChar8 *) aMyText);

	printf(
		"Sorry your program crashed %s: Please use proper ROM chips next time :P\n",
		aMyText
	);
	return 0xBAD;
}
[/php]

It's not a good thing to return larger values from main than 255.

---

### Post by worksofcraft on 2010-11-11
> **trent.josephsen said:**
> 
Obviously it's hideous and your best bet is to declare things the way they will be used.


Yes well that's easy to say, but it's not actually a practical suggestion. In general the "Fc" library isn't going to be the only one we use. Typically I might be passing the very same strings to Glib. They consistently use something known as "gchar" and so immediately the question is do I declare my strings as gchar or FcChar8?
Well according to [basic types documentation]("http://library.gnome.org/devel/glib/stable/glib-Basic-Types.html"):
[php]
typedef char   gchar;
[/php]
IMHO they are BOTH just wasting my time making up new names for standard things... but anyway how many programmers are going to actually be writing type safe conversion routines, especially when we know that half the time these libraries did't use attributes like *const* when appropriate? The "hideous" damage is in what we are given to work with not in what we are trying to produce.

>  
The real problem here (as I'm sure you understand) is the cast.  The only reason to have a cast here is to suppress the compiler warning; if you wanted to be warned about this kind of thing, you shouldn't have used it.

Well let's see how that works then. Compile it with the following changes:
[php]
// g++ invalid.cpp
#include <cstdio>
#include <cstring>

typedef unsigned char FcChar8;
typedef char gchar;

void Fc_ProcessText(FcChar8 *pSomeText) {
	strcpy((char *) pSomeText, "Thou shalt use unsigned char!");
}	

void glib_ProcessText(gchar *pSomeText) {
	strcpy((char *) pSomeText, "Thou shalt use signed char!");
}	

int main() {
	char aMyText[] = "Elsewhere I have strings that can change at run time";

	// Hey I'ld like to be warned about type mismatches
	// so I'm not going to do any casting
	Fc_ProcessText(aMyText);
	glib_ProcessText(aMyText);

	printf(
		"Sorry your program won't compile because %s :P\n",
		aMyText
	);
	return 0xBAD;
}
[/php]
... and what do we get?
```

$ g++ invalid.cpp
invalid.cpp: In function &#8216;int main()&#8217;:
invalid.cpp:21: error: invalid conversion from &#8216;char*&#8217; to &#8216;FcChar8*&#8217;
invalid.cpp:21: error:   initializing argument 1 of &#8216;void Fc_ProcessText(FcChar8*)&#8217;

```

so basically if I do want to compile my code and I do use different libraries like glib and font config... then I'm virtually forced to put in the type cast that also removes the compile time checks.

So it's all very well to say you should or shouldn't do this but you should tell that to the people who provide the libraries and not to the ones trying to use them IMHO.

---

### Post by Mr.Macdonald on 2010-11-11
[parc.h]("http://pastebin.com/frVTHHZ2")
[parc.c]("http://pastebin.com/XFVumYJq")
[test.pc]("http://pastebin.com/Aw04G5Sq")

> gcc parc.c -o parc && ./parc test.pc test.c && gcc test.c -o test && ./test

---

### Post by worksofcraft on 2010-11-11
> **Arndt said:**
> It's not a good thing to return larger values from main than 255.

Are you sure?
maybe it shouldn't be larger than 127 incase you have a system where ints are signed and only 8 bits :shock:

---

### Post by Arndt on 2010-11-11
> **worksofcraft said:**
> Are you sure?
maybe it shouldn't be larger than 127 incase you have a system where ints are signed and only 8 bits :shock:

I think the C standard actually only provides for SUCCESS and FAIL (with some suitable prefix), without even specifying their values, but I was thinking of Unix, where it has always been 8 bits. If the receiver of the value chooses to sign-extend it, it doesn't harm its uniqueness.

I've never used other than 0 to 3 myself, but I've seen 255 sometimes. I've also seen -1, in which case 255 is better.

---

### Post by worksofcraft on 2010-11-11
> **Mr.Macdonald said:**
> [parc.h]("http://pastebin.com/frVTHHZ2")
[parc.c]("http://pastebin.com/XFVumYJq")
[test.pc]("http://pastebin.com/Aw04G5Sq")

Ah... I see you are making some kind of cool C pre-processor... we might have to have a look at the C code it is producing but so far all I got was:

```

$ gcc parc.c -o parc && ./parc testpc.pc testpc.c && gcc testpc.c -o test && ./test
/tmp/ccC0kXV7.o:(.data+0x38): undefined reference to `_div'
collect2: ld returned 1 exit status

```

---

### Post by worksofcraft on 2010-11-11
> **Arndt said:**
> I think the C standard actually only provides for SUCCESS and FAIL (with some suitable prefix), without even specifying their values, but I was thinking of Unix, where it has always been 8 bits. If the receiver of the value chooses to sign-extend it, it doesn't harm its uniqueness.

I've never used other than 0 to 3 myself, but I've seen 255 sometimes. I've also seen -1, in which case 255 is better.

Hum... well in that case they should declare main as char and not as int!

... or perhaps even:
```

enum exit_status { EXIT_SUCCESS, EXIT_FAIL };

exit_status main(int argc, char *argv[]) {...

```

Just typical... the standard is [SNAFU]("http://en.wikipedia.org/wiki/SNAFU") to start with IMO

---

### Post by Arndt on 2010-11-11
> **worksofcraft said:**
> Hum... well in that case they should declare main as char and not as int IMO.

... or perhaps even:
```

enum exit_status { EXIT_SUCCESS, EXIT_FAIL };

exit_status main(int argc, char *argv[]) {...

```

Just typical... the standard is SNAFU to start with IMO

enum is type-equivalent with 'int', or at least I'm pretty sure it was up to C90. I don't know why the return type of 'main' is not 'char', but one good enough reason is that they wanted to avoid unspecified behaviour due to signedness or not of 'char'. With 'int', there isn't that problem as long as you don't use the full range of 'int', which presumably no operating system did at the time.

Besides, when Unix was made, C wasn't standardized yet. Later, they standardized the current practice.

All this has no doubt been explained much better on the News group comp.lang.c dozens of times by Chris Torek. Any article at all by him is worth reading. I thought of him recently, when there was talk about the difference between arrays and pointers.

---

### Post by worksofcraft on 2010-11-11
> **Arndt said:**
> enum is type-equivalent with 'int'

[php]
// gcc enumtest.c
#include <stdio.h>

typedef enum { EXIT_SUCCESS, EXIT_FAIL } exit_status;

exit_status enumIsInt() { return 0xBAD; }

int main(int argc, char *argv[], char *envp[]) {
	return enumIsInt();
}
[/php]

```

$ gcc -Wall -pedantic enumtest.c
enumtest.c:1:1: warning: C++ style comments are not allowed in ISO C90
enumtest.c:1:1: warning: (this will be reported only once per input file)

```

Yes indeed as you can see, not so much as a warning although it seems to think the comment issue is worth mentioning. Like I said SNAFU.

---

### Post by Arndt on 2010-11-11
> **worksofcraft said:**
> [php]
// gcc enumtest.c
#include <stdio.h>

typedef enum { EXIT_SUCCESS, EXIT_FAIL } exit_status;

exit_status enumIsInt() { return 0xBAD; }

int main(int argc, char *argv[], char *envp[]) {
	return enumIsInt();
}
[/php]

```

$ gcc -Wall -pedantic enumtest.c
enumtest.c:1:1: warning: C++ style comments are not allowed in ISO C90
enumtest.c:1:1: warning: (this will be reported only once per input file)

```

Yes indeed as you can see, not so much as a warning although it seems to think the comment issue is worth mentioning. Like I said SNAFU.

What is this meant to illustrate?

---

### Post by worksofcraft on 2010-11-11
> **Arndt said:**
> What is this meant to illustrate?

Well what do you think it illustrates?

The standard says that main() returns an int. If that is not so, then there is absolutely no reason why it can't be updated to return a type that is the explicit set of legitimate values and remain fully compatible. Allusions to what someone else may have said on the subject are irrelevant. This is what I am saying on the subject here and now.

p.s. anyway far more important is the practical issue of how to deal with const, char and unsigned char.

---

### Post by dwhitney67 on 2010-11-11
> **worksofcraft said:**
> This is what I am saying on the subject here and now.

You misread the warning; the compiler was bitching about the fact that you used a C++-style comment in your code, which does not conform with the C90 standard.

Either specify -std=c99 (or -std=gnu99), or just pretend as you always do when you write C code, that it is C++ by using the g++ compiler.

---

### Post by worksofcraft on 2010-11-11
> **dwhitney67 said:**
> You misread the warning; the compiler was bitching about the fact that you used a C++-style comment in your code, which does not conform with the C90 standard.

Either specify -std=c99 (or -std=gnu99), or just pretend as you always do when you write C code, that it is C++ by using the g++ compiler.

No I didn't misread the warning.

I'm showing that the compiler did NOT consider it even worth mentioning that I'm returning a value outside the range of the declared enumerated type.

Apart from the fact that the return type of main is utterly irrelevant to the discussion, you seem to be missing my point completely.

If you could make suggestions regarding the issues in posts #10 and #12 it would be much more constructive and possibly help people who have problems with read-only and constant string issues... which is AFIK what this thread is actually about.

---

### Post by dwhitney67 on 2010-11-11
> **worksofcraft said:**
> ... you seem to be missing my point completely.
And you missed mine; I'm merely giving you a hard time.  Think of it as sport.

---

### Post by worksofcraft on 2010-11-11
> **dwhitney67 said:**
> And you missed mine; I'm merely giving you a hard time.  Think of it as sport.

Isn't that what they call "trolling" ?

---

### Post by trent.josephsen on 2010-11-11
> **worksofcraft said:**
> Yes well that's easy to say, but it's not actually a practical suggestion.

<snip>

So it's all very well to say you should or shouldn't do this but you should tell that to the people who provide the libraries and not to the ones trying to use them IMHO.

I repeat my statement that the **only** function of that cast is to suppress the compiler warning.  Suppose we had
```
typedef struct { int flags; char x; } FcChar8;
```

The call wouldn't work at all, cast or no cast.  What I'm saying here is that a cast is not an acceptable workaround for the problem you're seeing.  In the case of a data structure whose definition is not part of the **public API**, you *cannot* assume that it can be safely cast to *anything*.  Even if it could, parameter passing performs implicit conversion (as by assignment), so the cast would not be necessary in the first place.

If a library doesn't provide a well-documented way to convert into its "special" types from C standard types, then either it is the intention of the author not to permit that (most types, like glib's GIOChannel, don't have a simple analog), or the API is incomplete and you should file a bug report against it.

---

### Post by worksofcraft on 2010-11-11
> **trent.josephsen said:**
> I repeat my statement that the **only** function of that cast is to suppress the compiler warning. 
...

Well then you are not telling the truth.
As the example you (expediently) snipped clearly shows: when you remove the cast it doesn't compile, but put it in and you won't get warnings...

Look if you just want to play a one up-manship trolling game like that other dude, then I have better things to do with my time and so does the OP probably :P

---

### Post by saulgoode on 2010-11-11
> **worksofcraft said:**
> [php]
// gcc enumtest.c
#include <stdio.h>

typedef enum { EXIT_SUCCESS, EXIT_FAIL } exit_status;

exit_status enumIsInt() { return 0xBAD; }

int main(int argc, char *argv[], char *envp[]) {
	return enumIsInt();
}
[/php]

```

$ gcc -Wall -pedantic enumtest.c
enumtest.c:1:1: warning: C++ style comments are not allowed in ISO C90
enumtest.c:1:1: warning: (this will be reported only once per input file)

```

Yes indeed as you can see, not so much as a warning although it seems to think the comment issue is worth mentioning. Like I said SNAFU.

There is no warning generated for (at least) two reasons. Firstly, per the ANSI standard (section 6.2.1.1) enum types are integral and will be implicitly promoted to int in the return statement.

Secondly, even if the example code did not not conform to the standard, it would not necessarily mean that a warning should be issued. The ANSI standard does not require that *all* conformance failures get reported, and GCC (invoked with -pedantic and -ansi) only guarantees reports for those failures which the standard requires.

---

### Post by johnl on 2010-11-11
> **worksofcraft said:**
> Well then you are not telling the truth.
As the example you (expediently) snipped clearly shows: when you remove the cast it doesn't compile, but put it in and you won't get warnings...

A common problem for beginners to C is the get an error like this:

```

function foo expects 'char*', but argument is of type 'int'

```

So they change their code to cast to an int, and wonder why it segfaults. 

When you cast a variable in C, you are telling the compiler that you know the conversion is appropriate and safe.  The compiler will trust you (in most cases).  This has nothing to do with character arrays or pointers or const/not-const.  

For example:

```

#include <stdlib.h>
#include <stdio.h>

void do_something(FILE* x, int y, const char* z) 
{
}


int main(int argc, char* argv[]) 
{
    long a = 0;
    char b[] = "frumpdizzle";
    unsigned long c = 0xBAADF00D;

    /* your compiler will happily accept this,
     * albeit with warnings depending on sizeof(long) vs sizeof(void*)
     */
    do_something((FILE*)a, (int)b, (const char*)c);
    /* but it knows this is wrong. */
    do_something(a, b, c);
    
    
    return 0;
}

```

You can't claim that "if I cast X to Y things don't work, the compiler should have caught that."  You cast it.  You told the compiler it was OK.  If the cast is not appropriate you should, as Trent says, use the appropriate conversion function or the appropriate type in the first place.

---

### Post by worksofcraft on 2010-11-11
> **saulgoode said:**
> There is no warning generated for (at least) two reasons. Firstly, per the ANSI standard (section 6.2.1.1) enum types are integral and will be implicitly promoted to int in the return statement.

Secondly, even if the example code did not not conform to the standard, it would not necessarily mean that a warning should be issued. The ANSI standard does not require that *all* conformance failures get reported, and GCC (invoked with -pedantic and -ansi) only guarantees reports for those failures which the standard requires.

Exactly :)

So... were return type of main genuinely restricted to a sub-set of int then there would have been absolutely no reason the standard should not be amended to reflect that with appropriate enumerated type.

OTOH as it has not been amended there is no reason to exclude returning the value 0xBAD or even 0xBAD - 0xA55 :D

---

### Post by worksofcraft on 2010-11-11
> **johnl said:**
> 
You can't claim that "if I cast X to Y things don't work, the compiler should have caught that."  You cast it.  You told the compiler it was OK.  If the cast is not appropriate you should, as Trent says, use the appropriate conversion function or the appropriate type in the first place.

Exactly,

You can't expect the compiler to catch things when you cast away the checks, and you can't blame programmers for casting away these things when it's the only way they can make their code compile with the packages we are given to work with... Just about everyone who progams using existing C libraries will have plenty of opportunities to do this and there simply aren't appropriate conversion routines.

The case in question, I was using Glib::ustring with XftDrawStringUtf8 and while they both support utf8, one used signed chars and the other unsigned chars and AFIK there ain't no conversion routines defined and it's only a typical example from the non-ideal real world of programming outside of accademia.

---

### Post by worksofcraft on 2010-11-11
Anyway instead of debating hypothetical policies I think we should return to the OP's topic now that he/she has provided us with details of the actual code.

So the first thing is the unresolved reference to _div... well that's easy. The code defines _add, _mult... etc... but no _div so rather than write one I just made it refer to _mult in parc.h and then it compiles... just need to stay aware of the fact that / ain't doing what is expected... but the next step:
```


 ./parc testpc.pc testpc.c
(+ 1 1 1 1 1 1 1 1 1 1 1 1)40 43 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 41 
(+ 1 1 1 1 1 1 1 1 1 1 1!40 43 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 33 
Segmentation fault

```

so not good :(
IDK, but perhaps we need that _div function to be added ?
basically this needs to be debugged one step at a time and not throw the whole shooting match on one command line and sadly IDk what it's supposed to be doing so it's a bit hard to debug.

---

### Post by Mr.Macdonald on 2010-11-11
Not that all that other stuff isn't interesting, but can we get back on topic.

> $ gcc parc.c -o parc && ./parc testpc.pc testpc.c && gcc testpc.c -o test && ./test
/tmp/ccC0kXV7.o:(.data+0x38): undefined reference to `_div'
collect2: ld returned 1 exit status

I didn't copy this into the code
[PHP]char* _div(int argc, char** argv) {
  int i, len=0, rlen = 4*argc, slen;
  char* ret = malloc(rlen+sizeof(char));

  for (i=1;i<argc;i++) {
    if (len == 0)
      ret[len++] = '(';

    if (len+ (slen = strlen(argv[i])) >= rlen-2) {
      rlen += (rlen-len)*(argc-i)*4;
      ret = realloc(ret, rlen*sizeof(char));
    }

    strcat(ret+len, argv[i]);
    len += slen;
    ret[len++] = '/';
  }
  if (len==0) {
    free(ret);
    return NULL;
  }
  
  ret[len++] = ')';
  ret = realloc(ret, len*sizeof(char));
  return ret;
}[/PHP]

append that to parc.c, its basically a copy of _add. I believe I modified _add after the fact, but it doesn't matter now because I don't call _div

---

### Post by worksofcraft on 2010-11-11
> **Mr.Macdonald said:**
> Not that all that other stuff isn't interesting, but can we get back on topic...


lol - must be telepathy ;)
I'm checking it now

brb

update: nope, soz... still segfaults... you cannot rely on anything after that.

update on update: hum as for more details... looks like johnl below well and truly beat me to it ;)

---

### Post by johnl on 2010-11-11
Here is your problem:

```

Starting program: /home/ledbettj/Projects/parc/parc test.pc test.c
(+ 1 1 1 1 1 1 1 1 1 1 1 1)40 43 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 41 
(+ 1 1 1 1 1 1 1 1 1 1 1!40 43 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 32 49 33 

Program received signal SIGSEGV, Segmentation fault.
__strlen_sse2 () at ../sysdeps/x86_64/multiarch/../strlen.S:31
31	../sysdeps/x86_64/multiarch/../strlen.S: No such file or directory.
	in ../sysdeps/x86_64/multiarch/../strlen.S
(gdb) bt
#0  __strlen_sse2 () at ../sysdeps/x86_64/multiarch/../strlen.S:31
#1  0x0000000000400e48 in _add (argc=12, argv=0x6034d0) at parc.c:137
#2  0x0000000000400d85 in eval (expr=0x603490 "(+ 1 1 1 1 1 1 1 1 1 1 1!")
    at parc.c:118
#3  0x0000000000400bf9 in scheme (in=0x603010, out=0x603250) at parc.c:70
#4  0x0000000000400a75 in parse (in=0x603010, out=0x603250) at parc.c:40
#5  0x0000000000400a1b in main (argv=3, argc=0x7fffffffe268) at parc.c:24
(gdb) print argc
No symbol "argc" in current context.
(gdb) up 1
#1  0x0000000000400e48 in _add (argc=12, argv=0x6034d0) at parc.c:137
137	    if (len+ (slen = strlen(argv[i])) >= rlen-2) {
(gdb) print argc
$1 = 12
(gdb) print argv[0]
$5 = 0x6034b1 "+"
(gdb) print argv[1]
$6 = 0x6034b3 "1"
(gdb) print argv[10]
$15 = 0x6034c5 "1"
(gdb) print argv[11]
$16 = 0x41 <Address 0x41 out of bounds>
(gdb) print i
$17 = 11

```

You are somehow calling _add with argc=12 but your argv[] only contains 11 items.  You then call strlen() on argv[11] (which is out of bounds) which causes the segfault.

If you continue to go up the backtrace, you'll see that the param to eval() that triggers this is:

```

70	  fputs(eval(str), out);
(gdb) print str
$21 = 0x603490 "(+ 1 1 1 1 1 1 1 1 1 1 1!"

```

I suspect that it might be a problem with your split() function.

---

### Post by Mr.Macdonald on 2010-11-11
There is definitely an issue with split().

[PHP]struct margs split(char* expr) {
  printf("%s\n", expr);
}

struct margs osplit(char* expr) {
  struct margs args;
  char *cpy, *tmp;
  int i;
  cpy = malloc(20*sizeof(char));

  printf("%s\n", expr);

  strcpy(cpy, expr);
  expr=NULL;
  const char delims[] = "( )\t\n\r";

#define ARGV args.argv
#define ARGC args.argc

  ARGV = malloc(BUFSIZE*sizeof(char*));
  ARGC=0;
  while ( (tmp = strtok(cpy, delims)) != NULL ) {
    cpy = NULL;

    ARGV[ARGC++] = tmp;
  }

#undef ARGV
#undef ARGC

  return args;
}
[/PHP]

When I play with flip these functions around (removing the "o" and such), I get different prints of expr (I removed all other printing statements).

With the split with strtok in it, I get
(+ 1 1 1 1 1
With the new one, I get
(+ 1 1 1 1 1 1)

I changed test.pc to
int a = $(+ 1 1 1 1 1 1)$;

This is what is bothering me the most. I simply don't know what to make of it. The segfault, I will take care of but this seems a bigger issue

---

### Post by Mr.Macdonald on 2010-11-11
Removing "ret = realloc(ret, len*sizeof(char))" from _add fixed the SEGFAULT

with either split() func

I could of sworn I tested for that

Anyone care to explain whats wrong with this, I did it in other functions

---

### Post by saulgoode on 2010-11-12
```
int main(int arg**v**, char** arg**c**) {
```

---

### Post by Some Penguin on 2010-11-12
```

ret[len++] = ')'; 
ret = realloc(ret, len*sizeof(char)); 
return ret; 

```

looks very dangerous, as the string is no longer zero-terminated and the caller has no idea how long the string is.

```

struct margs split(char* expr) { 
  printf("%s\n", expr); 
} 

```

clearly must be missing something, because what it returns is undefined.

```

cpy = malloc(20*sizeof(char)); 

  printf("%s\n", expr); 

  strcpy(cpy, expr); 

```

is a buffer overflow waiting to happen, especially since "int a = $(+ 1 1 1 1 1 1)$;" has more than 20 characters.

---

### Post by worksofcraft on 2010-11-12
> **Some Penguin said:**
> ```

ret[len++] = ')'; 
ret = realloc(ret, len*sizeof(char)); 
return ret; 

```

looks very dangerous, as the string is no longer zero-terminated and the caller has no idea how long the string is.
...
is a buffer overflow waiting to happen, especially since "int a = $(+ 1 1 1 1 1 1)$;" has more than 20 characters.

yes I spotted the following and changed it to add a terminator
[php]
 while ( (tmp = fgetc(in)) != EOF &&
          tmp != '$') {
    if (i >= BUFSIZE-1) { /* added -1 here so there is room for... */
	buf[i] = '\0'; /* terminate  */
      str = realloc(str, (si+i)*sizeof(char));
      strncat(str+si, buf, i);
      si += i;
      i=0;
    }
[/php]

... but that wasn't the problem :(
however I think it's a true case of "many heads" > "one"
;)

---

### Post by Mr.Macdonald on 2010-11-12
> is a buffer overflow waiting to happen, especially since "int a = $(+ 1 1 1 1 1 1)$;" has more than 20 characters.

I had no clue that I actually did that! Wow

As for the realloc, I have done that before and had no issue with the string termination ('\0'). I tested it with different allocation length (ie len, len+1, len+2, ...) with no difference as far as I could see. I realize the danger, but have yet to stream out my RAM (in this case), so I think its ok?

---

### Post by worksofcraft on 2010-11-12
> **Mr.Macdonald said:**
> I had no clue that I actually did that! Wow

As for the realloc, I have done that before and had no issue with the string termination ('\0'). I tested it with different allocation length (ie len, len+1, len+2, ...) with no difference as far as I could see. I realize the danger, but have yet to stream out my RAM (in this case), so I think its ok?

Actually I was probably over cautious because strncat() limits the number of characters, but when it appends one string to the other it does look for a null terminator to know where to append it so I didn't try to think it through any further and just put one in to be on the safe side.

p.s. I'll probably get flamed for saying this, but all that C realloc and strcat malarkey really does my head in and I wouldn't hesitate to start using std::string, even if nothing else from the C++ repertoire, were it my code ;)

---

### Post by Arndt on 2010-11-12
> **Mr.Macdonald said:**
> [parc.h]("http://pastebin.com/frVTHHZ2")
[parc.c]("http://pastebin.com/XFVumYJq")
[test.pc]("http://pastebin.com/Aw04G5Sq")

Are these things (pastebin) time-limited? When I click on one of the above, I get "502 bad gateway".

---

### Post by Mr.Macdonald on 2010-11-12
Pastebin stuff is still there

---

