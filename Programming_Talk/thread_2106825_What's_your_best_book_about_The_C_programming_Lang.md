---
title: "What's your best book about The C programming Language?"
date: 2013-01-20
forum: Programming Talk
---

### Post by honeybear on 2013-01-20
Hello,

I would like to ask you what is the best ever book you have read about Language C or that you might recommend reading? 

Please one single book per post (to be the best ever in your opinion)?

Regards

/* EDIT: we talk about C for compilers such as GCC, Borland C, ... (we do NOT talk about C++, C#...) */

---

### Post by Bachstelze on 2013-01-20
The only book I have ever read about C is K&R, and I haven't even read all of it. C is a small language and IMO a book is not at all necessary to learn it. And I am a very bookish person in general.

---

### Post by ofnuts on 2013-01-20
K&R too...  but I read all of it.

---

### Post by KdotJ on 2013-01-20
Another one here for K&R... but was more of a reference.

I book at I used a little bit while ar university was a (prior edition) of [this book]("http://www.amazon.com/How-Program-7th-Deital/dp/013299044X"), which I found fairly helpful and it used good examples.

---

### Post by slickymaster on 2013-01-20
> **KdotJ said:**
> Another one here for K&R... but was more of a reference.

Exactly. +1

---

### Post by MG&amp;TL on 2013-01-20
Uhuh. K&R too. It's not exactly up-to-date, but it's the best one I've found and anything you need clarification on you can google.

---

### Post by ehrt74 on 2013-01-21
C has some overloaded syntax which makes life difficult, and a book can help get a grasp of it.

For example, the asterisk has at least 3 distinct meanings. It either means "I'm defining something to be a pointer" or "I'm following a pointer to where it points to" or "I'm multiplying 2 numbers". The word 'static' is another example.

What I like about C is that if you understand a bit about how a computer physically works then C isn't a great stretch. It's usually quite simple to understand "what's going on". For this reason, it was the first language that made sense to me (after having spent months trying to understand Java and getting nowhere).

One day I started working on a book I downloaded somewhere online. I tried recently to find the book for a friend and couldn't find it anywhere, I'm afraid. The book didn't follow best practices anyway (it suggested casting mallocs, for example), but it was perfect for me to get into programming.

---

### Post by Warren Hill on 2013-01-21
The only book I still use is 

The C Programming language 

by Kernighan and Ritchie

---

### Post by trent.josephsen on 2013-01-21
> **ehrt74 said:**
> C has some overloaded syntax which makes life difficult, and a book can help get a grasp of it.

For example, the asterisk has at least 3 distinct meanings. It either means "I'm defining something to be a pointer" or "I'm following a pointer to where it points to" or "I'm multiplying 2 numbers". The word 'static' is another example.

The first two "meanings" are the same, syntactically. That's what "declaration mimics use" means. One of the things I hate about most languages that attempt to "improve" C is that they all introduce new and mutually incompatible declaration syntax. 

```
int *ip; // *ip is an int; therefore ip is a pointer-to-int
f(*ip);  // f is a function that takes an int
```

You're right about "static", though. "extern", too.

---

### Post by honeybear on 2013-01-21
I must say even the use of :

char *variable;
char *variable;
char variable[] = "bla";
char variable[254]; 

is pretty confusing since they all are closely same but havent same purposes. 

As the thing with your '*' that does many things


To me, one good boot that I read stuffed with lot of examples and details of the commands is this one:
[http://www.bookeo.fr/Turbo-C_a79.html](http://www.bookeo.fr/Turbo-C_a79.html)

you can't find it anymore

---

### Post by JDShu on 2013-01-21
As an alternative to K&R, you can also check out Learn C the Hard Way by Zed Shaw. It's [free]("http://c.learncodethehardway.org/book/") so no harm in doing so. There's even a [URL="http://c.learncodethehardway.org/book/krcritique.html"]critique of K&R.
[/URL]
As a disclaimer, I haven't actually read either book, but Learn Python the Hard Way is pretty good and Shaw seems like he knows what he's talking about even if he's opinionated.

---

### Post by Gyokuro on 2013-01-21
At university K&R is standard lecture but here another one: The C Book ([http://publications.gbdirect.co.uk/c_book/](http://publications.gbdirect.co.uk/c_book/)), you can even download it.

---

### Post by honeybear on 2013-01-24
In some other forms. I must say that this tutorial is pretty cool: 
[http://www.iu.hio.no/~mark/CTutorial/C-Tut-4.02.pdf](http://www.iu.hio.no/~mark/CTutorial/C-Tut-4.02.pdf)

---

### Post by Bachstelze on 2013-01-24
> **honeybear said:**
> In some other forms. I must say that this tutorial is pretty cool: 
[http://www.iu.hio.no/~mark/CTutorial/C-Tut-4.02.pdf](http://www.iu.hio.no/~mark/CTutorial/C-Tut-4.02.pdf)

Really? It doesn't seem to provide anything more than others, and its code is written in very old (and bad) style.

---

### Post by honeybear on 2013-01-24
> **Bachstelze said:**
> Really? It doesn't seem to provide anything more than others, and its code is written in very old (and bad) style.

 Thanks for your comments.

---

### Post by dwhitney67 on 2013-01-25
In the 4 days that this thread has been open, I could've learned C (if I did not already know it).

Gaining good programming experience, on the other hand, will take much longer... years in fact.

---

### Post by Bachstelze on 2013-01-25
> **dwhitney67 said:**
> Gaining good programming experience, on the other hand, will take much longer... years in fact.

It also takes a willingness to learn how to code *well*, after having learned how to code.

---

### Post by ofnuts on 2013-01-25
> **Bachstelze said:**
> It also takes a willingness to learn how to code *well*, after having learned how to code.

I don't think it's a problem of willingness. My experience with numerous programmers is that they all code decently according to their own standards. The problem is that some have fairly low standards. It's a bit like the lady who did the ["potato Jesus"](http://en.wikipedia.org/wiki/Potato_Jesus) :)

---

### Post by Bachstelze on 2013-01-25
> **ofnuts said:**
> I don't think it's a problem of willingness. My experience with numerous programmers is that they all code decently according to their own standards. The problem is that some have fairly low standards. It's a bit like the lady who did the ["potato Jesus"](http://en.wikipedia.org/wiki/Potato_Jesus) :)

If you don't code well, at some point someone will tell you. I define "willingness to learn" by whether you listen to them, no matter how rude they are.

---

