---
title: "Noob Question"
date: 2007-05-21
forum: Programming Talk
---

### Post by Naralas on 2007-05-21
I like C/C++, and a lot of the time I prefer C, and I know it's merits as the language I should be comfortable with first.

So my question is, how do you get used to strings in C? Coming from Q-BASIC/Java/web programming (javascript, php, ruby etc.) I am very used to strings being childs play. I only turn strings into character arrays (yes I know they always are) when I need to apply an algorithm to them. I don't WANT them to be always in that format.

Just try try try? and get used to it?

I am currently working on a project and using C++ simply because it requires reading and writing a lot of files and I want simplicity.

---

### Post by Psicolonia on 2007-05-21
try erics robert's libraries on strings.

you can declare them like this:

string str = strCpy("hello");

or like this

string str;
strCpy("hello", str);


can't really remember witch...

---

### Post by std on 2007-05-21
> **Naralas said:**
> I am currently working on a project and using C++ simply because it requires reading and writing a lot of files and I want simplicity.

If you're using C++, you could try to use STL, there's a fairly good string library there.

---

### Post by pmasiar on 2007-05-21
> **Naralas said:**
> I am currently working on a project and using C++ simply because it requires reading and writing a lot of files and I want simplicity.

Simplicity processing text files and text handling?

It smells like so called "scripting" language is best tool for the job. Try Python.

---

### Post by destructchaos on 2007-05-21
i agree with pmasiar, though i prefer Perl for such flavors of fun.

---

### Post by joe_bruin on 2007-05-22
> **Naralas said:**
> I like C/C++, and a lot of the time I prefer C, and I know it's merits as the language I should be comfortable with first.

So my question is, how do you get used to strings in C? Coming from Q-BASIC/Java/web programming (javascript, php, ruby etc.) I am very used to strings being childs play. I only turn strings into character arrays (yes I know they always are) when I need to apply an algorithm to them. I don't WANT them to be always in that format.

Just try try try? and get used to it?

I am currently working on a project and using C++ simply because it requires reading and writing a lot of files and I want simplicity.

C has beautiful simplicity in that it gives you only the most basic tools for getting things done.  And that includes only the most basic string and memory handling routines (as the former depends so much on the latter).  Memory is yours to use or abuse.  In C, strings are character arrays.  Don't be afraid of them, it's part of understanding how to work with memory.  There is no easy way around it.  You'll make mistakes, you'll crash a few programs.  But after a while it's not that bad, and you'll be able to deal with memory with confidence, instead of relying on objects and templates that do it all for you.

And remember the motto of the C programmer: "don't screw up"

---

