---
title: "What would be a good beginner programming language?"
date: 2008-06-12
forum: Programming Talk
---

### Post by Tsurugi13 on 2008-06-12
I'm looking to start programming, but I'm a total newbie. I messed around a tiny bit with python, but I've also been told to start with BASIC. What does the Ubuntu community think? Also, how would I get started with the language I choose?

---

### Post by gr4nf on 2008-06-12
If you start with basic, be Absolutely Sure not to use on with line numbers. this was messing me up alot when i first switched from BASIC to C.

---

### Post by sam_delta on 2008-06-12
id say stick with python, its simple, powerful and alot of support in ubuntu.

python has lots of support in ubuntu, so if you like ubuntu, go for it
and you can make programs and ejoy the language much faster than most other languages
heres a good tutorial
[http://www.python.org/doc/current/tut/tut.html](http://www.python.org/doc/current/tut/tut.html)


sam

---

### Post by the_doc on 2008-06-12
It depends on what it is you intend to do with it in the end.

I started with pascal to learn the basics then moved quickly on to C and C++.  I would prpobably start with C as it isn't Object Oriented which can confuse new programmers, although some people turn their nose up at C because it's too 'old school'.

---

### Post by gr4nf on 2008-06-12
Also, BASIC tends to be very proprietary to micrasoft (being written by gates, and all). I would keep pushing through with python. Its in some ways easier than basic.

---

### Post by Tsurugi13 on 2008-06-12
I'm just looking for a good general starting point to learn the basics of programming.

---

### Post by sdennie on 2008-06-12
Perl!!!

---

### Post by the_doc on 2008-06-12
If you're looking for the basics then you can't go wrong with C, not to mention the ease of running it in *nix and the wealth of material on the web.

---

### Post by Biggy on 2008-06-12
> **Tsurugi13 said:**
>  I've also been told to start with BASIC. What does the Ubuntu community think? Also, how would I get started with the language I choose?

For Basic language use [Gambas]("http://gambas.sourceforge.net/")

---

### Post by the_doc on 2008-06-12
Fact of the matter is, all programming languages have sequence, selection and iteration etc, so just find one you like the look of I guess.  As I said earlier it may be wise to choose an non OO language to start with, but you don't have to.

---

### Post by kdcoetzee on 2008-06-12
> **the_doc said:**
> If you're looking for the basics then you can't go wrong with C, not to mention the ease of running it in *nix and the wealth of material on the web.

i agree C/C++ 2 is the best language to start with.

---

### Post by gr4nf on 2008-06-12
Here we go:

Most things you will use in programming are functions. In most, they have the following syntax:

function_name(argument, argument)

A function is just a value, basically. You could even pass a function to another function.

add(1, add(1, 2))

that would output 4. Some functions actually do things, besides just returning a value, like the python "print()".

print("hi")

this would return nothing, but would output the word "hi" to the shell.

some functions return less obvios things. Lets take, for example, a function that took a number, and made it into a string. Numbers and Strings are two different data types, so you couldn't say, for example:

print(4)

or at least not in most languages. Python in smart, so it would allow you to do so, but you couldn't in C. Here's another example:

print(number_to_string(add(1, 2)))

this would add 1 and 2, making 3, and would then turn it into a string, a data type that "print()" can understand.
</makeshift tutorial>

Good Luck!

---

### Post by raul_ on 2008-06-12
A lot of code is still written in C/C++ (look at our mighty kernel).

I like C, it's really low level. If you like to know what you're doing, start with C, so you learn how memory is managed, how pointers work, etc, etc.

I think starting with a high-level language isn't good. If you start with java, for example, you'll learn java but you won't learn how to program.

IMO anyway :P

You could also see Scheme for some basic programming. You'll get familiar with recursion and some important programming paradigms. It's not only how you make it work, it's with how much style you do it ;) (this was really geek)

To get started just go to [www.google.com](www.google.com) and search for "getting started with <insert language here>" or "<language here> tutorial"

You could also search for LaRoza here in the forums and check the links in his/hers signature

---

### Post by decoherence on 2008-06-12
I second the vote for Python.

Also, check out Ruby if only for this [fantastic ongoing tutorial]("http://poignantguide.net/ruby/"). There's also a very good interactive Ruby tutorial [here]("http://tryruby.hobix.com/") which will get you started very quickly.

---

### Post by LaRoza on 2008-06-12
See the sticky. I can't believe the advise in this thread...

I guess that is what is bound to happen with random people.

---

