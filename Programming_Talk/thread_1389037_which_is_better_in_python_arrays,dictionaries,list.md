---
title: "which is better in python: arrays,dictionaries,lists"
date: 2010-01-23
forum: Programming Talk
---

### Post by dharanitharan on 2010-01-23
Hi friends,
            I'm new to pthon. I want to store some characters in a data structures(arrays or lists or dictionaries). then i will compare those things with certain characters obtained at run time. In this case wat data structure should i use. Im really need it... Plz help me :-)



Thanks for ur reply,
Dharanitharan.A
[http://naturefactory.wordpress.com](http://naturefactory.wordpress.com)

---

### Post by Can+~ on 2010-01-23
Uhm, a string?

---

### Post by jflaker on 2010-01-23
> **dharanitharan said:**
> Hi friends,
            I'm new to pthon. I want to store some characters in a data structures(arrays or lists or dictionaries). then i will compare those things with certain characters obtained at run time. In this case wat data structure should i use. Im really need it... Plz help me :-)



Thanks for ur reply,
Dharanitharan.A
[http://naturefactory.wordpress.com](http://naturefactory.wordpress.com)

EVERYTHING is a string unless you can confirm it is a number...

---

### Post by dharanitharan on 2010-01-23
Sorry friends. Im a beginner, im not aware of that.. Thaks for making me to understand.. Actually i wanna do this:

char a[]={'a','b','\n',';'};

How to decalre this in python

---

### Post by jeffathehutt on 2010-01-23
[PHP]a = "ab\n;"[/PHP]

That should do it :)

---

### Post by dharanitharan on 2010-01-23
> **jeffathehutt said:**
> [PHP]a = "ab\n;"[/PHP]

That should do it :)
No no. I want to know how to declare in python

---

### Post by snova on 2010-01-23
> **dharanitharan said:**
> No no. I want to know how to declare in python

That *is* how you do it in Python. jeffathehutt's suggestion is, by all means, also probably the way it *should* be done. I can't see why you would want a list of characters instead of a string, but if you insist on that:

[php]a = ["a", "b", "\n", ";"][/php]
[php]a = list("ab\n;")[/php]

---

### Post by Can+~ on 2010-01-23
Ok, let's say it in another way:

What do you want to do with said string?

For instance, if you want to compare, you don't need to do it C-style (it seems that you have C background):

[PHP]>>> "Hello World" == "Hello World"
True
>>> "orl" in "Hello World"
True
>>> "Hello World"[:4]
'Hell'
>>> "Hello World"[::-1]
'dlroW olleH'
>>> "Hello World".replace("World", "Universe")
'Hello Universe'
[/PHP]

Take a look at [string methods]("http://docs.python.org/library/stdtypes.html#string-methods") and [sequence types]("http://docs.python.org/library/stdtypes.html#sequence-types-str-unicode-list-tuple-buffer-xrange").

---

### Post by dharanitharan on 2010-01-23
> **Can+~ said:**
> Ok, let's say it in another way:

What do you want to do with said string?
Actually i want to design a C language parser using python....

If my input is lik this:

#include<stdio.h>
void main()
{
    printf("Hello World !!!");
}

then i want the output after parsing lik:
#include, <stdio.h>, void, main, (, ), {, }, printf and so on

---

### Post by Can+~ on 2010-01-23
> **dharanitharan said:**
> Actually i want to design a C language parser using python....

If my input is lik this:

#include<stdio.h>
void main()
{
    printf("Hello World !!!");
}

then i want the output after parsing lik:
#include, <stdio.h>, void, main, (, ), {, }, printf and so on

Ok, that's not "parsing", it's more like... changing the format.

But anyway, this is way out of your league. Building a "compiler" or an "interpreter" is not as simple as it seems, there's a lot of theory involved, you'd need a book like [Aho's Dragon books]("http://en.wikipedia.org/wiki/Dragon_Book_%28computer_science%29").

But whatever, first focus on learning the language, your posts suggest that you're rushing too much, assuming that you need to declare things in python, it's dynamically typed, you don't need to. Everything in python are objects and have methods and properties, it's not like C where there's memory and functions, it's another paradigm.

---

### Post by dharanitharan on 2010-01-23
> **Can+~ said:**
> Ok, that's not "parsing", it's more like... changing the format.

But anyway, this is way out of your league. Building a "compiler" or an "interpreter" is not as simple as it seems, there's a lot of theory involved, you'd need a book like [Aho's Dragon books]("http://en.wikipedia.org/wiki/Dragon_Book_%28computer_science%29").

But whatever, first focus on learning the language, your posts suggest that you're rushing too much, assuming that you need to declare things in python, it's dynamically typed, you don't need to. Everything in python are objects and have methods and properties, it's not like C where there's memory and functions, it's another paradigm.
thanks man... First i ve to come from basics.. i understood ..

---

### Post by CptPicard on 2010-01-24
> **Can+~ said:**
> Ok, that's not "parsing", it's more like... changing the format.


Well, it seems like tokenization. Perhaps a good exercise for the uninitiated... first, read a file, then, learn to split at whitespace... finally, perhaps implement finite language recognizer using a state machine :p

---

