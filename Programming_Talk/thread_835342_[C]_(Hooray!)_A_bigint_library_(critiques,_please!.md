---
title: "[C] (Hooray!) A bigint library (critiques, please!)"
date: 2008-06-20
forum: Programming Talk
---

### Post by nvteighen on 2008-06-20
**Please, people, don't use this for your projects! Use the GMP or any well-established bigint library. This was a programming exercise I did years ago!** (nvteighen, 1/3/2011)

****EDIT**: There's a newer version uploaded in a post below**

Hi there!

Pretty happy today :): I finished a big integers library in C I have been working on for some time! I've attached it as a .tar.gz including source file, header, binaries and a make file ('make' to build library. 'make test' to build test suit).

But, it **only supports** (so forget using this for your great calculus project...):
1. Positive/Negative "unlimited" (i.e. memory available) numbers storing.
2. Addition.
3. Substraction.
4. Data copying, memory resizing, allocation, freeing (and the usual stuff).
5. Logical comparisons: greater than, less than, equal to.
6. Output to File streams.

I'd be very glad to hear your comments on it, of course, only if you have some spare time to lose with this. It is meant to be statically linked for simplicity, so you don't have to copy stuff to /usr/lib, but it does work as shared library too if compiled properly.

The API is very straightforward, *I think*, and should be easily deduced either from the test file and my comments in source code. I also think the source is pretty modular enough...

All GPL'ed... (because I failed to understand LGPL clearly...). This has been a great exercise on logics and data management; also, reduced memory issues to exactly zero!

---

### Post by LoneWolfJack on 2008-06-20
interesting... even though your code is a bit messy (no offense).

too bad it's GPL. if you release a LGPL version I may give it a closer look.

---

### Post by nvteighen on 2008-06-20
> **LoneWolfJack said:**
> interesting... even though your code is a bit messy (no offense).

No offense taken, that's the kind of things I want to fix. Any special general problem?

> too bad it's GPL. if you release a LGPL version I may give it a closer look.

Well, I don't like to use licenses I don't understand myself...

---

### Post by smartbei on 2008-06-20
Yes, it is a little messy, but it is well-commented (at least for personal code).

I can't stand though the use of a 'result' varaible. I like to return functions as soon as I can.

---

### Post by Vadi on 2008-06-20
Here is lgpl in human: [http://creativecommons.org/licenses/LGPL/2.1/](http://creativecommons.org/licenses/LGPL/2.1/)

---

### Post by nvteighen on 2008-06-20
> **smartbei said:**
>  (...)
I can't stand though the use of a 'result' varaible. I like to return functions as soon as I can.

Well, it's something on which I'm not still sure on what's best. at the beginning I returned functions as you say, but I began to confuse exit codes easily and some functions would need too many return statements, so I took this approach, which is not my usual one.

> **Vadi said:**
> Here is lgpl in human: [http://creativecommons.org/licenses/LGPL/2.1/](http://creativecommons.org/licenses/LGPL/2.1/)

Thanks! This may help me. I'll give it a new chance to the LGPL right now and see if I apply it to the library.

---

### Post by LoneWolfJack on 2008-06-20
> 
No offense taken, that's the kind of things I want to fix. Any special general problem?


Nah, it's reasonable readable and I guess any changes would be considered personal style.

But here's how I would do it:

```

char bigint_gt(bigint *a, bigint *b)
{
	char result = 0;

	if(a->sign > b->sign)
		result = 1;

	if((result == 0) && (a->size > b->size))
		result = 1;

	if(result == 0)
	{
		size_t i;
		for(i = 1; (i <= b->size) && (result == 0); i++)
		{
			if((a->cont[OFFS(a, i)] * a->sign) >
			(b->cont[OFFS(b, i)] * b->sign))
				result = 1;
			else
				result = 0;
		}
	}

	return result;
}

```

to

```

char bigint_gt(bigint *a,bigint *b)
	{
	char result = 0;

	if(a->sign > b->sign)
		{result = 1;}

	if((result==0) && (a->size > b->size))
		{result = 1;}

	if(result==0)
		{
		size_t i;
		for(i=1;(i<=b->size) && (result==0);i++)
			{
			if((a->cont[OFFS(a,i)]*a->sign) > (b->cont[OFFS(b,i)]*b->sign))
				{result = 1;}
			else
				{result = 0;}
			}
		}
	return result;
	}

```

Too many spaces are irritating... and even a single line if statement deserves braces for the purpose of clarity. :)

Also I am not yet getting the idea why you need so many different files to scatter your code in... I may understand it once I have time to take a closer look though.

As for LGPL.. I'm looking at it from a business point of view. If a company like... say SAP would approach me asking to do something with bigints, I would probably not be able to sell them the idea of having to release the source.

---

### Post by Vadi on 2008-06-20
'sell'? Unless he dual-licenses it, the code under being LGPL will be freely taken by them and be happy if they even mention you in the credits.

---

### Post by nvteighen on 2008-06-20
OK. v.0.0.2

Basically:
1. Got rid of those result variables and made functions return ASAP. Yes, the code seems less cluttered! Thanks smartbei!
2. Catched a non-serious bug there was "thanks" to one of those result variables.
3. Simplified the for-loop at bigint_trim_zero().
4. Deleted "input.c" from tar file and Makefile dependencies... It was a failed attempt to create a fscanf-like function some time ago.
5. LGPL'ed library (what I needed was to drink a coffee, print the license and read it from paper instead of screen!). Yes, more suited to a library's needs. Test suit remains GPL'ed.

Thanks for your input so far! Any other comments are really welcomed!

*EDIT* Argh, network issues made you answer before me... I'll look to your comments.

---

### Post by nvteighen on 2008-06-20
> **LoneWolfJack said:**
> Nah, it's reasonable readable and I guess any changes would be considered personal style.

Thanks! Should I feel proud? :) (ah, today I did a great exam too... that's why I'm so happy today!)

> 
(...)

Too many spaces are irritating... and even a single line if statement deserves braces for the purpose of clarity. :)

Hey, those braces are a good one I never knew about.

> Also I am not yet getting the idea why you need so many different files to scatter your code in... I may understand it once I have time to take a closer look though.

To play around with Makefiles, actually :p... And to keep things ordered in some way if I happen to write multiplication and division or whatever else.

> **Vadi said:**
> 'sell'? Unless he dual-licenses it, the code under being LGPL will be freely taken by them and be happy if they even mention you in the credits.

I'm not sure if I could really sell such a thing as this... ;)

---

### Post by mike_g on 2008-06-20
>  No offense taken, that's the kind of things I want to fix. Any special general problem?
Nah, it's reasonable readable and I guess any changes would be considered personal style.

But here's how I would do it:
I prefer nvteighen's original coding style, and, its far more widely used.

Also, I dont see why this:
```
if(a->sign > b->sign)
    {result = 1;}
```
Is in any way more clear than:
```
if(a->sign > b->sign)
     result = 1;
```
If youre going to enforce braces on each single line block, then to be clear they should really be given their own line.

But thats just my opinion.

---

### Post by nvteighen on 2008-06-20
Ugh... we're discussing programming styles... as usual in C-threads!

```

if(a == b)
    {result = zzz;}

```

I believe that it has an advantage: gives more visual focus to the single-lined block, but without wasting two lines for a bracket pair.

Here,
```

if(a == b)
    result = zzz;

```
the second line may get lost to the reader's eye more easily if you then have an "else if" which is a multi-lined block. Anyway, I'm not going to rewrite the code to LoneWolfJack's style; it's that I'd like to know as many styles as possible (and not just choosing one style because of not knowing others, which is silly).

Of course, the only important thing is to take a style and use it...

Any comment on the algorithms, data structures, etc.?

---

### Post by collinstocks on 2008-10-31
Wow, thanks! This sort of library was exactly what I was looking for! I wanted one that did all the "hard" stuff so that I could focus on multiplication and exponential algorithms. If I ever *actually* get around to implementing anything, I'll attach it back here.

---

### Post by collinstocks on 2008-10-31
You still have a bug in the program when setting a bigint to a value, the first leading "1" (if any) is ignored, even if there is a negative sign before it. I'm not sure what is causing the problem.

---

### Post by nvteighen on 2008-11-01
Wow... I abandoned this a long time ago... :p

I guess it may be probably because the numbers are stored backwards... and the reversed.

But, if you want to use a Bigint library for something serious, I'd really recommend you not to use this code of mine and go for some well-established library. (If you're just playing, it's fine :))

I'm really busy these days, I doubt I'll have time to check this...

---

### Post by hijayanth on 2011-01-02
Hi,
 
Firstly Thanks to the Library. 
 
I didn't had a chance to go through the code but I have a question - 
 
I'd give the input as 2 arguments :
1.0949B0F6F0023313C4499050DE38F34E( which isin hexa decimal and in 16 bytes) and 
2. 10(Base)
 
It guess it should output this value : 12345678901234567890123456789012345678 which is in decimal.
 
Can this is addressed?
 
Thanks in advance for any reply.
 
Regards,
Jayanth

---

### Post by Vox754 on 2011-01-02
> **hijayanth said:**
> Hi,
 
Firstly Thanks to the Library. 
 
I didn't had a chance to go through the code but I have a question - 
 ...

He he. Read the last post. This library was an amateur attempt at developing a multi-precision library for C, only for the learning experience of it. It is not actively maintained.

If you really want to use bignums, you should probably use a more professional library, like the LGPL-licenced [GNU Multiple Precision Arithmetic Library,](http://gmplib.org/) which already comes installed with Ubuntu. Install the packages "libgmp3-dev", and "gmp-doc" or read the [manual online.](http://gmplib.org/manual/)

By the way, nvteighen, you should edit the first post to clarify this, unless you want people to come after you with endless requests for support (it don't wrk!).

Also, LOL on the coding style you thought was good. You never adopted it, did you?

---

### Post by nvteighen on 2011-01-03
> **hijayanth said:**
> Hi,
 
Firstly Thanks to the Library. 
 
I didn't had a chance to go through the code but I have a question - 
 
I'd give the input as 2 arguments :
1.0949B0F6F0023313C4499050DE38F34E( which isin hexa decimal and in 16 bytes) and 
2. 10(Base)
 
It guess it should output this value : 12345678901234567890123456789012345678 which is in decimal.
 
Can this is addressed?
 
Thanks in advance for any reply.
 
Regards,
Jayanth

I appreciate you liked my work. But seriously, don't use this. It's not mantained, it's not meant to be a project and it's code I wrote 3 years ago, when I was just a rookie amateur programmer (now I'm a not-so-rookie amateur :P).

> **Vox754 said:**
> 
By the way, nvteighen, you should edit the first post to clarify this, unless you want people to come after you with endless requests for support (it don't wrk!).


I edited the first post. I hope it dissuades people to use it... Wow, this is the second time this happens! Maybe I should mantain this code and gain some popularity... :P

> Also, LOL on the coding style you thought was good. You never adopted it, did you?

No, I never adopted it.

Wow, the code is horrible in some parts: using dynamic allocation for a struct that's not forwarded at all, thus allowing for stack-based allocation... or using a reversed string as a container... LOL... Now I laugh at it (, but hey, it was worth to do it. I forced myself to write a simple interface, attempted to create something that did something, etc.

But certainly I learned a lot with it. And looking at this shows me how much I've improved all these years too. This was a nice blast from the past :)

---

### Post by dribeas on 2011-01-03
As an overview, I feel that there is no real documentation on the design or the intentions. What is being stored? How is it being handled? It seems as if you are working with characters (actual values: 0-9) and growing as needed. I have seen other approaches that simplified the code by working with bigger numbers (32bit) and using only half of it for actual storage. This would also imply a better use of memory than requiring a full byte for each decimal digit. Operations can be performed straight over the contained ints and then normalized to guarantee the initial invariant (only the lower 16bits may be non-zero).

Some comments as I browse through some of the files, starting with the interface (BTW, why if there is a single header there are different translation units?):

Macros should be sprinkled with extra parenthesis:
```

#define OFFS( x, i ) x->size - i
// potential problem:
2*OFFS( ++x, n+1 );     // (2* ++(x->size)) - n + 1!!!
// solution
#define OFFS( x, i ) ((x)->size - (i))

```

I prefer providing names for all types, and not just aliases. There is no reason not to provide the struct with a name.

```

typedef struct bigint {
   // ... 
} bigint;

```

I usually provide argument names in function declarations, even if not required as a means of documenting the operation, what are the inputs and outputs. In many cases people will not look at the source code, but only headers. String literals should be `const char*` rather than `char*`. If you don't intend to modify the contents of the string then say so (I am assuming that `bigint_set` does not modify the second argument. The same with other functions, use as many `const` as fit your semantics.

On the implementation:

Your code is not *exception-safe* (ok, that is a C++ term, but it applies here): The very first function in math.c contains:

```

bigint *a_abs = bigint_new();
bigint *b_abs = bigint_new();
if ( (a_abs == NULL) || (b_abs == NULL)) 

```

If the second allocation fails (`b_abs == NULL`) then you leak the memory allocated to `a_abs`. The same goes for the second early return statement (I don't know what it is intended but what it does is leak memory if the condition is met). You need to cleanup for yourself before returning or else you leak resources. (This might be well an issue with the refactor you did, I am only looking at the second version of it.

---

### Post by worksofcraft on 2011-01-04
> **nvteighen said:**
> 
Wow, the code is horrible in some parts: using dynamic allocation for a struct that's not forwarded at all, thus allowing for stack-based allocation... or using a reversed string as a container... LOL... Now I laugh at it (, but hey, it was worth to do it. I forced myself to write a simple interface, attempted to create something that did something, etc.

But certainly I learned a lot with it. And looking at this shows me how much I've improved all these years too. This was a nice blast from the past :)

Lol, nvteighen, 2008 is not that long ago... you wanna try dropping out of the whole industry for 15 years to raise your kids and then come back to it :lolflag:

Anyway processing numbers in reverse is a good idea. They told me in primary school we should always start our sums with the least significant digit and it does make sense :P

btw. perhaps you can ask for your thread to be locked so that ppl don't post inane comments like this one ? ;)

---

### Post by nvteighen on 2011-01-05
> **dribeas said:**
> 
...


Hey, thanks for taking your time for reviewing my code. Ok, you point out stuff that I know now (but didn't back then), well... except for something I didn't know until I read your post: the need of parentheses in macros to avoid the substitution being "greedy" (in the Perl sense). Heh, you always learn something; thanks!

> **worksofcraft said:**
> Lol, nvteighen, 2008 is not that long ago... you wanna try dropping out of the whole industry for 15 years to raise your kids and then come back to it :lolflag:

Anyway processing numbers in reverse is a good idea. They told me in primary school we should always start our sums with the least significant digit and it does make sense :P

I know that 3 years isn't that much time, but I feel I've made a lot of progress. But I wasn't the usual beginner: back in 2008 I was more a "false beginner", as I had had some prior programming experience with QBASIC and VB6, but I left it. When I became interested in GNU/Linux OSs, I saw the amount of programming tools available and decided to give it a shot again. For good :)

> 
btw. perhaps you can ask for your thread to be locked so that ppl don't post inane comments like this one ? ;)

Nah, I think it's not worth to be closed.

---

### Post by ziekfiguur on 2011-01-05
Here is one i made about a year ago, it also supports multiplication, division, modulo, and all bitwise operators, but is for unsigned integers only.

It's written in 32-bits assembly (to compile you need fasm from [http://flatassembler.net/](http://flatassembler.net/)) with a C++ template as wrapper. 
The size is a template parameter, so it doesn't automatically expand to prevent an overflow.
The C++ class has all operators overloaded, so you can use it just like a normal unsigned integer, except for the istream extraction operator.

The code isn't to clean, but it was fun to make and cool to learn some assembly :)

If you want to try it on a 64bits system, you will have to install the g++-multilib and libc6-dev-i386 packages and compile with -m32

---

