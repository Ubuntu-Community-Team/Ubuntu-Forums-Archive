---
title: "translating one language to another"
date: 2007-12-27
forum: Programming Talk
---

### Post by DouglasAWh on 2007-12-27
I am on a handheld, so my apologies if my research is woefully inadequate.  Are there programs that will translate PHP to Python or any such types of things?  I do know some of them exist at an enterprise level, but I don't know if there are any that are free (as in price).  I suppose it could be of interest to others if there were cheap offerings or ones with trial versions.  THANKS!

As a side note, the site seems to work pretty well from the Blackberry.  Good job guys and gals!

---

### Post by Wybiral on 2007-12-27
I started a project to convert Python to Javascript [here]("http://code.google.com/p/epy/") (shameless self promotion). The same principle (of using Python's AST) could be used to convert Python to PHP relatively painlessly (aside from Python and PHP's massive standard libraries). I haven't heard of any projects to do so though. I've also never heard of any projects to convert PHP to Python either.

I can see the use in a Python-to-PHP converter since there are so many free PHP hosts, but what do you need a PHP-to-Python converter? Porting existing code, or just for the heck of it?

---

### Post by pmasiar on 2007-12-27
I assume your PHP is a web application, right? 

There are far better ways to write web apps in Python than blindly translate PHP to Python. Python has namespaces, and Python has MVC-based web app frameworks, like Django or TurboGears, which will guide you to far more clean and maintanable code.

---

### Post by Majorix on 2007-12-27
I had never heard of any such tools. And my search in google didn't bring back any useful results. So I am asking to you, are you sure that there are apps that can do this in enterprise level, now that you spoke of it?

Actually I haven't seen any single successful converter between any language, including very similar ones.

---

### Post by DouglasAWh on 2007-12-27
PHP to Python was just an example.   The enterprise application some of my friends worked on translated from COBOL to C, if I remember correctly.  They work for a consulting firm.  I don't know if the company they worked for released it or if they did or what.  I can try to get some more information if people are really interested.

---

### Post by samjh on 2007-12-27
There are quite a few automated porting tools from one programming language to another.  Most of them are limited though, and you need to manually edit the resulting code to ensure there are no important flaws.  Even the relatively simple business of translating VB6 to VB.NET is fraught with dangers.

For any that will work on large-scale projects, I haven't come across anything free of charge or FOSS.

COBTOC is a COBOL to C translator which does straight-forward file-to-file translation of COBOL source files to C source files.

For .NET languages, you have [http://www.remotesoft.com/octopus/](http://www.remotesoft.com/octopus/)

What source and target languages are you thinking about?

---

### Post by DouglasAWh on 2007-12-27
My friend said it was APS-COBOL to C that they worked with.  The guy that they worked with was on the original APS-COBOL team, so he was definitely a veteran.  It wasn't their intellectual property though, so he can't really say much else about it.

---

### Post by pmasiar on 2007-12-28
> **samjh said:**
> COBTOC is a COBOL to C translator which does straight-forward file-to-file translation of COBOL source files to C source files.


COBOL to C is rather different: COBOL is higher level (and much older), and it's compiler most likely just generates C. I do not think there are significant conceptual differences between COBOL and C, which would prevent straightforward translation. Web application in PHP has rather different structure from a (properly MVC structured) Python web app, and creating tool to automate refactoring would be quite a challenge.

---

