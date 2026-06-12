---
title: "multiple definitions not found"
date: 2010-10-11
forum: Programming Talk
---

### Post by JakeFrederix on 2010-10-11
I have a piece of c code which has been driving me up the wall.
It basically does string-matching.
And to store the results I made a small struct arraylist.

If I include arraylist.h, I get "undefined reference" errors
when including arraylist.c I get "multiple definition" errors.

Somehow I can't manage this.

Thanks in advance,
Jake

---

### Post by worksofcraft on 2010-10-11
Ok I made it compile for you. revised archive attached...

It compiles as follows: g++ *.cpp *.c
then run as ./a.out

I'm not quite sure what was going wrong for you, but it is best to only have declarations in header files and that means **any file that you specify with #include** even if it doesn't have .h suffix.

So I put declarations for the functions you call from main into your arraylist.h header file and then included that in all the c and cpp files. I removed their inclusion from main.cpp and now they can all be compiled independently... and that was about all that was needed :)

---

### Post by JakeFrederix on 2010-10-11
I'm afraid that when I apply your strategy to all files (because I didn't include file_util.c for instance), it again fails to compile.

I made an additional header for file_util.c and for boyer_moore_horspool.c

Am I making the same mistake again?

---

### Post by worksofcraft on 2010-10-11
> **JakeFrederix said:**
> I'm afraid that when I apply your strategy to all files (because I didn't include file_util.c for instance), it again fails to compile.

I made an additional header for file_util.c and for boyer_moore_horspool.c

Am I making the same mistake again?

Well no... see it works just fine on my computer here:
```

$>ls
a.out	     boyer_moore_horspool.c  file_util.h
arraylist.c  boyer_moore_horspool.h  main.cpp
arraylist.h  file_util.c	     Makefile
$>g++ *.cpp *.c
$>./a.out
NAME
	search1

SYNOPSIS
	./search1 <patroonbestand> <tekstbestand> ... <tekstbestand>

DESCRIPTION
	Doorzoekt een reeks tekstbestanden naar een patroon met behulp van het Boyer-Moore-Horspool algoritme.

$>

```
Mind you... IDK what is supposed to do though :shock:

---

### Post by dwhitney67 on 2010-10-11
If you are developing in C, then stick to it.  There's no need to mix in C++.  Your main.cpp should be renamed main.c, and the cstdlib should be renamed to stdlib.h; also the using namespace directive should be removed.

Other than those issues, the following two warnings popped up when I compiled the app:
```

gcc -Wall -pedantic -std=c99 *.c
arraylist.c: In function ‘list* arraylist_create()’:
arraylist.c:9: warning: no return statement in function returning non-void
main.c: In function ‘int main(int, char**)’:
main.c:33: warning: unused variable ‘j’

```

---

### Post by Reiger on 2010-10-11
> Mind you... IDK what is supposed to do though

It's a text search algorithm. You feed it a pattern in a file (first argument) then any number of text files to search through for that pattern. 

See also: [http://en.wikipedia.org/wiki/Boyer–Moore–Horspool_algorithm](http://en.wikipedia.org/wiki/Boyer–Moore–Horspool_algorithm)

---

### Post by JakeFrederix on 2010-10-11
Thanks everyone!
Works like a charm now.

Jake

---

