---
title: "Are these really the same in C++ ??"
date: 2008-02-05
forum: Programming Talk
---

### Post by BuffaloX on 2008-02-05
I was going through a tutorial on C++,
When I got confused by the use of syntax I hadnt seen explained previously.
Then I tried fiddling a bit and it seems that 

int* p; 
int * p;
int *p;
int*p;

Means exactly the same...
Is this really true, or is it just me that misunderstands something.

---

### Post by CptPicard on 2008-02-05
Yes... they are the same. "int* p" and "int *p" are the most common variants, I'd discourage the use of the others, they sort of "tokenize" * separately and it looks too much like multiplication... personally I use "int *p".

---

### Post by BuffaloX on 2008-02-05
Thanks for confirming, It  really confused me.
But now I can read C code a little better.
I think I prefer int *P too, since it most looks like whats really being done.

---

### Post by CptPicard on 2008-02-05
There's a bit of a philosophical difference there that we had a thread of some time ago... they are the same thing but you can think of them slightly differently. If you prefer to read the thing from right to left as "p is a pointer to int" you actually might want to see it as (int*) p, where the * is part of the type of the pointer.

If you prefer to see things from the dereferencing point of view -- considering what *p is when you evaluate it -- you can think of it as "*p is an int", so "int *p" may make more sense then.

---

### Post by Lster on 2008-02-05
[QUOTE=CptPicard]If you prefer to see things from the dereferencing point of view -- considering what *p is when you evaluate it -- you can think of it as "*p is an int", so "int *p" may make more sense then.[/QUOTE]

That is brilliant - I've never visualized it like that before! Somehow I just never thought along that path. Thanks.

---

### Post by CptPicard on 2008-02-05
I think it was aks44 who first explained that to *me* in that thread a few months ago. It was a bit of a revelation to me too, although I've always used int *p myself -- while always reading it the first way I mentioned -- thinking of it primarily as a type declaration for "p", not "*p" :)

---

### Post by public_void on 2008-02-05
You have to remember your code goes through a lexical analyser and it doesn't care too much how you write it just sees lexemes that map to a token. In each case it reads "i" "n" "t" (int), "*", "p" and ";" and disregards the whitespace. So in each case you have <type><*><variable name><semi-colon> which is syntactically correct so the parser is happy.

---

### Post by c174 on 2008-02-05
Many people prefer "int *p", because when you create multiple variables in a single statement like this

int *p1, *p2

then both "p1" and "p2" will be pointers - as expected. If you do like this

int* p1, p2

then "p1" is a pointer, but "p2" is an int. However, personally I prefer "int* p" and also "int& p" e.g. when passing arguments to a function. It emphasizes the *type* of the variable :)

---

### Post by aks44 on 2008-02-05
> **c174 said:**
> Many people prefer "int *p", because when you create multiple variables in a single statement like this

int *p1, *p2

then both "p1" and "p2" will be pointers - as expected. If you do like this

int* p1, p2

then "p1" is a pointer, but "p2" is an int.

What those very people often forget, is that a pointer (like any other variable) should be initialized *_as soon as_* it is declared, which doesn't mix well with multiple declarations per line (unless one loves messy unreadable code, of course). ;)


I for one prefer to emphasize on the actual type of the variable too. This brings orthogonality to the whole source code, especially when dealing with templates (as any half competent C++ programmer has to).

---

### Post by BuffaloX on 2008-02-09
> **c174 said:**
> Many people prefer "int *p", because when you create multiple variables in a single statement like this

int *p1, *p2

then both "p1" and "p2" will be pointers - as expected. If you do like this

int* p1, p2

then "p1" is a pointer, but "p2" is an int. However, personally I prefer "int* p" and also "int& p" e.g. when passing arguments to a function. It emphasizes the *type* of the variable :)

This is really bad in C / C++ syntax, it's so bad I'd call it a bug.
This is good to know, before attempting to read other peoples code.

---

