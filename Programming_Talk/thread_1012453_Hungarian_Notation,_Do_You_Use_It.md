---
title: "Hungarian Notation, Do You Use It?"
date: 2008-12-15
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-12-15
as the title says...

i dont like it...i just would do something like

```

int turns;
int *turnNumber;
void foo();

```

---

### Post by u-slayer on 2008-12-15
On a related note: I think underscore_notation is much easier to use than CamelCase. 

I type on the dvorak keyboard where the underscore is typed by pressing shift and the key under your right pinky which is on the Home_Row. Compare this to standard qwerty where the underscore is out of reach. This makes my variables much easier to read while minimizing errors in case sensitive languages like C.

---

### Post by jimi_hendrix on 2008-12-15
> **u-slayer said:**
> I type on the dvorak keyboard where the underscore is typed by pressing shift and the semi-colon key. Compare this to standard qwerty where the underscore is out of reach. This makes my variables much easier to read while minimizing errors in case sensitive languages like C.

yes but most of use dont have dvorak keyboards...

---

### Post by Cracauer on 2008-12-15
I prefer languages that allow "-" in symbols and then write (with-temporary-file (....))

I put spaces around binary math operators anyway, and I think the compiler can as well force everybody else to do it, too :)

---

### Post by jimi_hendrix on 2008-12-15
> **Cracauer said:**
> I put spaces around binary math operators anyway, and I think the compiler can as well force everybody else to do it, too :)

that i normally do to...

x * foo * bar / baz

does anyone put spaces between the ( ) and parameters like...

foo( bar );

?

i never liked that...too much white space

---

### Post by u-slayer on 2008-12-15
> **jimi_hendrix said:**
> yes but most of use dont have dvorak keyboards...

Just go to Systems->Preferences->Keyboard->Layouts:wink:

---

### Post by kavon89 on 2008-12-15
I'll go ahead and clarify what it is, from Wikipedia:

> In Systems Hungarian notation, the prefix encodes the actual data type of the variable. For example:

    * lAccountNum : variable is a long integer ("l");
    * arru8NumberList : variable is an array of unsigned 8-bit integers ("arru8");
    * szName : variable is a zero-terminated string ("sz"); this was one of Simonyi's original suggested prefixes.

Apps Hungarian notation doesn't encode the actual data type, but rather, it gives a hint as to what the variable's purpose is, or what it represents.

    * rwPosition : variable represents a row ("rw");
    * usName : variable represents an unsafe string ("us"), which needs to be "sanitized" before it is used (e.g. see code injection and cross-site scripting for examples of attacks that can be caused by using raw user input)
    * strName : Variable represents a string ("str") containing the name, but does not specify how that string is implemented.

Most, but not all, of the prefixes Simonyi suggested are semantic in nature. The following are examples from the original paper: [1]

    * pX is a pointer to another type X; this contains very little semantic information.
    * d is a prefix meaning difference between two values; for instance, dY might represent a distance along the Y-axis of a graph, while a variable just called y might be an absolute position. This is entirely semantic in nature.
    * sz is a null- or zero-terminated string. In C, this contains some semantic information because it's not clear whether a variable of type char* is a pointer to a single character, an array of characters or a zero-terminated string.
    * w marks a variable that is a word. This contains essentially no semantic information at all, and would probably be considered Systems Hungarian.
    * b marks a byte, which in contrast to w might have semantic information, because in C the only byte-sized data type is the char, so these are sometimes used to hold numeric values. This prefix might clear ambiguity between whether the variable is holding a value that should be treated as a letter (or more generally a character) or a number.


I personally don't use it, however I can see how it is useful when you've got lots of variables of similar "data".

---

### Post by monkeyking on 2008-12-15
It depends on the nastyness of the program.
If the program is complex and other people is going to look at the code I tend to use it.

When I look at other people's code,
I find it easier to understand, when I can do type checking on the var names.


btw, how about a poll about reverse polish notation calculators.

---

### Post by mssever on 2008-12-16
If you find Hungarian Notation necessary, your program probably needs to be broken into smaller chunks and/or you're using too many globals and/or you aren't doing a very good job of choosing names.

> **u-slayer said:**
> On a related note: I think underscore_notation is much easier to use than CamelCase.I agree. Even though it's a little tougher to type when you're using QWERTY, it's a whole lot easier to read. When I started programming, I preferred to use CamelCase. However, when I started to learn Ruby, I was essentially forced to change styles (underscores are a strong convention in Ruby and Ruby is big on making everyone follow conventions). Now, I dislike it when I need to use CamelCase in order to follow some style guide.

---

### Post by lisati on 2008-12-16
Surely the context, along with things like the constraints imposed your chosen language, "corporate" standards (if you're part of a team), and ultimately, program clarity, should be the guide.....

---

### Post by jimi_hendrix on 2008-12-16
i personally find Hungarian Notation to just make a mess...

---

### Post by tjandracom on 2008-12-16
[QUOTE="monkeyking"]It depends on the nastyness of the program.
If the program is complex and other people is going to look at the code I tend to use it.

When I look at other people's code,
I find it easier to understand, when I can do type checking on the var names.

[/QUOTE]

i agree with that. it doesn't matter if you are using underscore or CamelCase, but it always a good idea to give a hint of variable type in the variable name.

---

### Post by myrtle1908 on 2008-12-16
Many moons ago I found it very useful (especially in large projects) however with the recent prevalence of IDEs and the like, I find it less important.  With today's IDEs one can simply hover over a variable to check its type.

---

### Post by dribeas on 2008-12-16
> **kavon89 said:**
> I'll go ahead and clarify what it is, from Wikipedia:

I personally don't use it, however I can see how it is useful when you've got lots of variables of similar "data".

+1.

I do use (in the few cases where it makes sense) Apps Hungarian Notation. I never use and clearly dislike System Hungarian Notation. It is another example of a good idea ruined by wrong understanding.

The clearer example is where the Apps Hungarian Notation was born: Microsoft Office. They had lots of x and y coordinates, and they represented different locations as they referred to different coordinate systems. The standard there was prepending the coordinate system to the variable similar to:

paper_x: x coordinate referred to the paper corner

page_x: x coordinate referred to printing margin

screen_x: x coordinate referred to the first pixel of the document shown on screen

block_x: x coordinate referred to the current block (paragraph/figure)

That is, in all cases the variable is x (horizontal coordinate), but in each case the variable has a different meaning. Hungarian notation help defining the real meaning of the variable.

---

### Post by jespdj on 2008-12-16
camelCase (starting with a lower-case letter) is the defacto standard for variable names in Java; almost all Java programmers everywhere do it like that (because it's the way it's done in the standard Java API).

For C or C++, I would use lower_case_with_underscores. Isn't that the preferred style for GNU software?

Long ago, when I was a Microsoft C++ programmer, I used Hungarian notation, because that was the defacto standard for C++ programs on Windows at the time.

---

### Post by pmasiar on 2008-12-16
I don't use it anymore, but for big project, notation and naming conventions is a must.

Also, in Python and java I use plural for collections, singular for item, ...sz for a length/size of the collection, and ...i for iterating index.

Conventions are good, they make your code more consistent. Hungarian notation is just a quite nasty one ;-)

---

### Post by Mickeysofine1972 on 2008-12-16
Well I have to agree with some of the points in that I use App but not System as I really only ever found App useful.

My reason for this is only so that I can keep track of scope really, although i never use globals except in special cases.

I dont object to using the variable_name type stuff, but unless you can be cool enough to hold programming context in your head at the same time as trying to be creative in variable naming, I suggest you stop making it needlessly hard on yourself and find a style that lets you name variables easily and with very little fuss, which for me, Apps does.

The point here really is that we are trying to have a set of approaches to coding that make us perform well, reduce errors & reduce the amount of effort required to perform a programming task. For me its Apps for another whos comfortable, it may not be.

Occams razor says that given two solutions to a task the best choice is always the most simple one.

Mike

---

