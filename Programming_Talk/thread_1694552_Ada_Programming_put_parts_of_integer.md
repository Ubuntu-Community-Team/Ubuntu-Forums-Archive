---
title: "Ada Programming put parts of integer"
date: 2011-02-24
forum: Programming Talk
---

### Post by clever233 on 2011-02-24
Hello i'm new to this forum.
I'm trying to learn ada at home.

I created a program which saves 10 dates to integer sorts them and then puts them on the screen.
When i put the dates on the screen i want them to be put like this
1921-12-23 but because they are integer i dont know how to put parts of the integer so they get put
19211223.

Help is much appreciated.
I tried to search the forum but didnt find any answer to this question.

regards Woo

---

### Post by Tony Flury on 2011-02-24
> **clever233 said:**
> Hello i'm new to this forum.
I'm trying to learn ada at home.

I created a program which saves 10 dates to integer sorts them and then puts them on the screen.
When i put the dates on the screen i want them to be put like this
1921-12-23 but because they are integer i dont know how to put parts of the integer so they get put
19211223.

Help is much appreciated.
I tried to search the forum but didnt find any answer to this question.

regards Woo

are the date part always 2 digit - for instance : 19300901 - 1st September 1933 - if so then : 

the date part is always your integer Mod 100
the month is always (Integer Div 100) Mod 100
The year is always Integer Div 10000

MOD is the modulus operator
DIV is integer division
I don't know Ada to know how they translate.

---

### Post by clever233 on 2011-02-24
> **Tony Flury said:**
> are the date part always 2 digit - for instance : 19300901 - 1st September 1933 - if so then : 

the date part is always your integer Mod 100
the month is always (Integer Div 100) Mod 100
The year is always Integer Div 10000

MOD is the modulus operator
DIV is integer division
I don't know Ada to know how they translate.

Thank you Tony Flury your answer was very helpful.
Been searching for the solution for quite a while.
Works like a charm.
Regards clever233

---

