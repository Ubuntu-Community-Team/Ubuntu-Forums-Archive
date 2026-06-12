---
title: "Questions regarding big projects (C)"
date: 2011-01-24
forum: Programming Talk
---

### Post by cguy on 2011-01-24
1. Since you can compile multiple files at once (gcc a.c b.c -o x), aren't header files obsolete? I mean you could use them if you wanted to, but you could avoid them completely if you desired so, right?

2. f(int, int) is called inside X.c, but it is declared somewhere else, in the myriad of other files.
How can one find out where f(int, int) is declared?

---

### Post by Lootbox on 2011-01-24
Having header files would save you the effort of declaring every single external function/variable you use in a particular module as extern at the beginning of the .c file. It also provides a clean way to expose the interface of a module without unnecessary implementation details.

As for your second suggestion, you could get that functionality with an IDE like Code::Blocks or Eclipse. Personally, using grep seems to work pretty well for me.

---

### Post by Arndt on 2011-01-24
> **Lootbox said:**
> 
As for your second suggestion, you could get that functionality with an IDE like Code::Blocks or Eclipse. Personally, using grep seems to work pretty well for me.

Look at etags.

---

### Post by trent.josephsen on 2011-01-24
So every time you change
```
/* a.c */
#define ROWS 10
/* ... 10 line main() function calling stuff in b.c */

```

to
```
/* a.c */
#define ROWS 20

```

you have to recompile all 30,000 lines of code in b.c ?  Great idea, there.  I wonder why it hasn't caught on.

---

### Post by worksofcraft on 2011-01-24
> **cguy said:**
> 1. Since you can compile multiple files at once (gcc a.c b.c -o x), aren't header files obsolete? I mean you could use them if you wanted to, but you could avoid them completely if you desired so, right?


Common header files are necessary for practical reasons, to tell one module what is inside the other module.

See here is a.cpp
[php]
// g++ a.cpp b.cpp
// note: aString is a constant text string that resides in file b.cpp
// but the premiss is that we don't need header files...

// Definitely need this one for the C standard I/O library!
#include <cstdio> 
int main(int argc, char *argv[], char *envp[]) {
	return !printf(aString);
}
[/php]
and here is b.cpp
[php]
// g++ a.cpp b.cpp
const char aString[] = "Hello, I am a string!\n";
[/php]

Then I compile them together...
```

cjs@cjs-ubuntu:~/Desktop/examples$ g++ a.cpp b.cpp
a.cpp: In function ‘int main(int, char**, char**)’:
a.cpp:8: error: ‘aString’ was not declared in this scope

```

see one module just doesn't know about what is in the other even when we compile them in the same command!

---

### Post by nvteighen on 2011-01-25
The only way for the C compiler to know what's in another module is by using a header file. Don't think of a multifile project; think of a shared library that's already compiled... how would you inspect its contents?

I know there are better ways, Java's for instance (I like having the .class file both as implementation and interface), but this is the way C, C++ and Objective-C work.

---

### Post by wmcbrine on 2011-01-26
> **cguy said:**
> 1. Since you can compile multiple files at once (gcc a.c b.c -o x), aren't header files obsolete?No. (I don't even know what compiling multiple files at once has to do with header files at all.)

> *I mean you could use them if you wanted to, but you could avoid them completely if you desired so, right?*You could, but it wouldn't make sense to do so.

> [i]2. f(int, int) is called inside X.c, but it is declared somewhere else, in the myriad of other files.
How can one find out where f(int, int) is declared?[/i]grep

Well, hopefully you gave the function a more descriptive name than "f", because that's gonna be hard to grep for.

[quote=nvteighen]The only way for the C compiler to know what's in another module is by using a header file.[/quote]Technically, there is no difference between a .h and .c file; you can just copy all those "extern" lines directly into your .c file, and you never have to use a header file. Like I say, it would make no sense to do that. But you *could*.

Rarely, when I've only wanted a few functions from a library, I have actually just embedded a couple of "extern" declarations rather than #include a big header file, to save on compile time. This is less of an issue nowadays.

---

### Post by nvteighen on 2011-01-26
> **wmcbrine said:**
> 
Technically, there is no difference between a .h and .c file; you can just copy all those "extern" lines directly into your .c file, and you never have to use a header file. Like I say, it would make no sense to do that. But you *could*.

Rarely, when I've only wanted a few functions from a library, I have actually just embedded a couple of "extern" declarations rather than #include a big header file, to save on compile time. This is less of an issue nowadays.

Of course... maybe I sacrificed too much accuracy to make my point better understood and ended up writing something that's not true.

So, rephrasing: what the compiler needs is to know the signatures of the functions that are being used in the module... and that's usually done with a header file for convenience reasons.

---

### Post by ibuclaw on 2011-01-26
> **cguy said:**
> 1. Since you can compile multiple files at once (gcc a.c b.c -o x), aren't header files obsolete? I mean you could use them if you wanted to, but you could avoid them completely if you desired so, right?


You need the -combine switch to compile multiple files at once, and that's only if the frontend language supports it (C I think does, D too).

```
gcc a.c b.c -combine -o x
```
Has it's gains and pitfalls though...

---

### Post by worksofcraft on 2011-01-26
> **ibuclaw said:**
> You need the -combine switch to compile multiple files at once, and that's only if the frontend language supports it (C I think does, D too).

```
gcc a.c b.c -combine -o x
```
Has it's gains and pitfalls though...

Oh learn something new everyday :)
```

$ g++ -combine b.cpp a.cpp -o x
a.cpp: In function &#8216;int main(int, char**, char**)&#8217;:
a.cpp:8: error: &#8216;aString&#8217; was not declared in this scope

```
```

$ gcc -combine b.c a.c -o x
a.c: In function &#8216;main&#8217;:
a.c:8: error: &#8216;aString&#8217; undeclared (first use in this function)
a.c:8: error: (Each undeclared identifier is reported only once
a.c:8: error: for each function it appears in.)

```
I tried it but failed :(

---

### Post by ibuclaw on 2011-01-27
> **worksofcraft said:**
> Oh learn something new everyday :)

I tried it but failed :(

I said compile multiple files at once, I didn't say all files share the same scope if you do so. ;)

---

