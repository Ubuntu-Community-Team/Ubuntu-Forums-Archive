---
title: "Writing custom scripting language"
date: 2008-05-05
forum: Programming Talk
---

### Post by Touch.Code on 2008-05-05
Hi all,

I was wandering if anyone had any tips (not ones saying don't do it), resources or snippets towards creating my own scripting language in C++.

While I was in Windows I looked around LUA, Lex and Yacc, but never got any further.

Even if my language was (for the moment) only able to open a script file, perform some mathematics and maybe even beep or display a message box, I would be happy.

Some resources for opening a file and then parsing what is inside would be nice :)

Before any of you doubt me, here is a small list of things I have programmed (in):
[LIST]
[*]16-Bit ASM Operating System
[*]AutoIt
[*]VB6
[*]PHP
[*]SQL
[*]MySQL
[*]Javascript
[/LIST]
I know some aren't exactly difficult, however I have experience in programming, C++ is the next level for me.

Thankyou,
James

---

### Post by RIchard James13 on 2008-05-05
Use [RPN]("http://en.wikipedia.org/wiki/Reverse_Polish_notation") for maths because it easier to parse than standard mathematical notation. I once wrote a FORTH interpreter in BASIC and FORTH uses RPN so there was no problem with equations like y = ( 2 + 3 ) / 4

---

### Post by CptPicard on 2008-05-05
Figure out a grammar and implement it in Lisp. It's a very good language for creating languages. I mean, what's with all this C++ these days? :)

Well.. if you insist on C or C++... figure out a grammar and then use yacc or bison to generate a parser. Then when you have an expression tree, all you need is to walk it and evaluate it.

---

### Post by Touch.Code on 2008-05-05
Richard, the Wiki page doesn't exist. Although it sounds like a good idea.

Picard, I shall have a look at Lisp now :)

Thanks for the quick replies!

---

### Post by tseliot on 2008-05-05
> **CptPicard said:**
> Figure out a grammar and implement it in Lisp. It's a very good language for creating languages. I mean, what's with all this C++ these days? :)

Well.. if you insist on C or C++... figure out a grammar and then use yacc or bison to generate a parser. Then when you have an expression tree, all you need is to walk it and evaluate it.
CptPicard I have the solution to your problem ;) :
[PHP]from Tolerance import tolerateCPlusPlusFans
tolerateCPlusPlusFans()[/PHP]

---

### Post by Wybiral on 2008-05-05
> **tseliot said:**
> CptPicard I have the solution to your problem ;) :
[PHP]from Tolerance import tolerateCPlusPlusFans
tolerateCPlusPlusFans()[/PHP]

tseliot, I have a solution to your problem:

```

new_tolerance = filter((lambda x: x != "c++"), old_tolerance)

```

Or, maybe this one:

```

(remove-if (lambda (x) (string= x "c++")) '("c" "c++" "python" "lisp"))

```

---

### Post by Lau_of_DK on 2008-05-05
Hey,


If you have no demands of the language being very fast, you would probably do yourself a favor by abadoning C++ as you will inevitable spend alot of time on pointers, typecasting and the likes.

A way that would be intersting (but not very fast I think), would be to compose your new scripting language of Lisp macros and thereby extending the Lisp language itself.

You could have a setup that read every line of a text file like myscript.mylanguage, and directly executed the command. Besides for some error checking your entire scripting engine could look like this:

```

(defun run-script (filename)
  (with-open-file (in filename)
    (with-standard-io-syntax (progn (read in))))

```

So if the first line in your file said "(say hello world)", that line would be directly executed. And given that you have a macro called "say" which accepts any number of strings as arguments, you would also have a working function. 

/Lau

---

### Post by WW on 2008-05-05
You might find some ideas in [Chapter 8 Minilanguages](http://www.faqs.org/docs/artu/minilanguageschapter.html) of [*The Art of Unix Programming*](http://www.faqs.org/docs/artu/index.html).

---

### Post by pmasiar on 2008-05-05
Forth is excellent tool to develop new languages, and is incredibly fast.

---

