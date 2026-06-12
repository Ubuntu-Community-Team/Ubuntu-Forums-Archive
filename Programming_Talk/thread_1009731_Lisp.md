---
title: "Lisp"
date: 2008-12-12
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-12-12
I have been in denial about LISPS greatness, but I have been forced to see the light. But ...

How do you write a function that prints a value without returning it

such as

args = X
set A = 2*X
print A
set B = 4*X
print B
return X

---

### Post by Wybiral on 2008-12-12
Depends on the dialect of Lisp, but it would look something like this

```

(define (some-function x)
  (let ((a (* 2 x))
        (b (* 4 x)))
    (display a)
    (display b))
  x)

```

---

### Post by Mr.Macdonald on 2008-12-13
why doen't this do the same thing

[PHP](defun s (x)
	((print (* x 2))
	(print (* x 4)))
	x)[/PHP]

or even work

---

### Post by CptPicard on 2008-12-13
Because ... "that's not right... it's not even wrong" :)

There is no function called "print" unless you've defined one, and you're invoking a function that is not being returned from this "print", and even if it were, you're doing it Scheme-style, not common-lisp style (that is, using funcall or apply). Plus, you've got mismatched parenthesis...

---

### Post by Mr.Macdonald on 2008-12-13
this is the lisp version I am using
> CMU Common Lisp CVS release-19a 19a-release-20040728 + minimal debian patches, running on aidan-desktop
With core: /usr/lib/cmucl/lisp.core
Dumped on: Fri, 2008-12-12 20:11:01-08:00 on aidan-desktop
For support see [http://www.cons.org/cmucl/support.html](http://www.cons.org/cmucl/support.html) Send bug reports to the debian BTS.
or to [email]pvaneynd@debian.org[/email]
type (help) for help, (quit) to exit, and (demo) to see the demos

Loaded subsystems:
    Python 1.1, target Intel x86
    CLOS based on Gerd's PCL 2004/04/14 03:32:47


Is there a different common lisp I should use

---

### Post by CptPicard on 2008-12-13
No, but you should just learn the language ;)

---

### Post by Mr.Macdonald on 2008-12-13
Lisp is great, but there was a different version I should use,

clisp, you can pass files to execute into it and it has the up arrow history reading thing. MUCH BETTER!!!

---

### Post by CptPicard on 2008-12-13
> **Mr.Macdonald said:**
> 
clisp, you can pass files to execute into it and it has the up arrow history reading thing. MUCH BETTER!!!

You're doing it wrong... you're totally missing the Lisp environment which is like half the fun of coding Lisp if you're using it like a regular interpreter, passing files to it... and using the raw REPL to write anything substantial is painful.

Try using a proper environment like SLIME, or if you're not into Emacs, the cusp plugin for Eclipse...

---

### Post by Cracauer on 2008-12-14
> **Mr.Macdonald said:**
> I have been in denial about LISPS greatness, but I have been forced to see the light. But ...

How do you write a function that prints a value without returning it

such as

args = X
set A = 2*X
print A
set B = 4*X
print B
return X

Why don't you want to return it? There's no harm in that. In general you always want to return a value that might turn out useful, if you have it floating around anyway.

Here's how to return nil instead:

```

(defun blah (moo)
  (print moo)
  nil)

```

If for whatever correctness aspect you really don't want a value returned:

```

(defun blah (moo)
  (print moo)
  (values))

```

CMUCL 19a is more for the software archaeologist. We are at 19e now.

You want SLIME or ilisp in Emacs on top. At the very least edit in Emacs for another Lisp indentation aware editor.

---

### Post by nvteighen on 2008-12-14
Just a note: in functional programming you usually return something. You're still using an imperative mindset where the "result" is just having a function "do" something. In functional programming the "result" is having resolved relations between functions (not data, that'd be logical programming), so you almost always need something to be returned in order to not stop that resolving process (aka "Eval-Apply Loop" in Lisp lingo).

Of course, Common Lisp is not a pure-functional programming language, but most part of the Lisp code I've seen is functional.

Lisp development is absolutely different to anything else... if you take a look at my FreeTruco project (see sig), you'll see a program written in Scheme where the difference between usage and development is zero... Usually, you develop languages that solve some problem rather than an application in the traditional sense...

For an interesting Common Lisp project, take a look at SymbolicWeb:
[http://groups.google.com/group/symbolicweb](http://groups.google.com/group/symbolicweb)

---

