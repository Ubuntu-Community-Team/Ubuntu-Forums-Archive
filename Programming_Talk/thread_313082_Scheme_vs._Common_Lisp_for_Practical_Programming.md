---
title: "Scheme vs. Common Lisp for Practical Programming"
date: 2006-12-05
forum: Programming Talk
---

### Post by Ubuntist on 2006-12-05
After having played with MIT Scheme, I've decided I want to get a little deeper into Lisp as a potential real-world programming language.  My first thought was that this meant Common Lisp, since Scheme, although very elegant, seemed to lack some things very useful in solving real-life problems.  Recently, though, I've started to get the impression that at least some Schemes are more fully kitted out for everyday work than I had thought.  MzScheme, for example, apparently has an object system built in and I gather some Schemes can be compiled and some allow macros.

My general question is, how do the various Scheme implementations, especially those readily available under Ubuntu, compare with Common Lisp for practical programming?  Which Scheme implementations are best for this purpose?  In using practical features, is one likely to encounter a great deal of implementation dependence?

---

### Post by hernan43 on 2006-12-05
I know that this doesn't answer your question, but I know people that swear by sbcl(Steel Bank Common Lisp):

[http://www.sbcl.org/](http://www.sbcl.org/)

They write all kinds of programs in it. Including ones that perform real world tasks and run on production machines.

---

### Post by pmasiar on 2006-12-06
MIT is replacing Scheme with Python: [http://www.google.com/search?q=mit+python+scheme](http://www.google.com/search?q=mit+python+scheme)

For **practical **programming, python is it! Can you guess I am a pythonista? :-)

---

### Post by tomchuk on 2006-12-06
[This](http://community.schemewiki.org/?scheme-vs-common-lisp) might help.

---

### Post by Ubuntist on 2007-01-20
> **tomchuk said:**
> [This]("http://community.schemewiki.org/?scheme-vs-common-lisp") might help.

Thanks much -- that is *very *helpful.  I think it's CL for me, but I'll still admire Scheme.

---

### Post by Ubuntist on 2007-01-20
[quote=pmasiar;1853172]MIT is replacing Scheme with Python: [http://www.google.com/search?q=mit+python+scheme](http://www.google.com/search?q=mit+python+scheme)

That is something!  I can see how Python's wide acceptance is a major practical advantage.  My own code, however, is only likely to be run by me.  As much as I like Python, I prefer Ruby and Lisp.

---

### Post by anc2020 on 2008-08-17
Practical programming eh?
Recently I've been using clisp instead of bash as my login shell.

Step one: add /usr/bin/clisp to /etc/shells.
Step two: change /bin/bash to /usr/bin/clisp in /etc/passwd.

That's it. You can do most things you want with (shell "myshellcommand"), but will need to use the builtin (cd) function for change directory.

After thoughts:

a) You may* need to explicitly set your window manager path in ~/.xinitrc for it to run at startup, eg.
exec /path/to/your/ (kde or gnome)

* That's how I run KDE on my Gentoo box, haven't tested yet on Ubuntu.

b) Clisp is quite verbose at start-up. I've created a small shell script called /usr/bin/clisp-silent with one line:
/usr/bin/clisp -q -q
and use this as my shell instead.

c) Clisp allows you to change your prompt text, see [http://clisp.cons.org/impnotes/prompt.html](http://clisp.cons.org/impnotes/prompt.html) and have fun.

Already I've got some quite useful bits of code in my /home/ali/.clisprc
that I'll post some here if requested.

And no, I don't type (shell "blah blah") every time I do a command.

I type something like
(s nano -w "file.txt")

or if I use nano enough, I add (defshell nano) to my .clisprc and just use:

(nano -w "file.txt")

To remove those extra two parens, either:

a) put "\ec": "()\C-b" into ~/.inputrc and type control-c before the command
or
b) port [http://srfi.schemers.org/srfi-49/srfi-49.html](http://srfi.schemers.org/srfi-49/srfi-49.html) better-than-python-indentation to Common Lisp (may require some guru-ness)

hth, thrill seekers

---

### Post by CptPicard on 2008-08-17
This is a tough issue. Common Lisp has so much more "pragmatic" stuff in it, and CLOS is just a wonderful object system. Its compilers and other tools are much more mature. Emacs+SLIME+SBCL is the coolest programming environment I have ever used. Anything for Scheme does not come close.

I like Scheme *as a language* more... it's simpler and more elegant. I like having lazy evaluation right in the language and not having the value/function slot distinction. Scheme's lack of namespaces is nasty in bigger projects though. Scheme's macros are supposedly safer, but I must admit I am not a macro god and don't use them much yet so I shouldn't comment.

If I had to actually do something "real" I guess Common Lisp still easily wins. There's just more stuff ready to use, too. In Scheme you must hack a lot by hand which is not conductive to actual productivity.

There is actually an interesting alternative which I prefer over both CL and Scheme, and that is Clojure, a Lisp that runs on the JVM. It really does most of the stuff right that either Scheme or CL do wrong, and as an added bonus, you can easily call Java code from it. You really have all the already-written Java stuff at your fingertips.

Tools are a little patchy still at the moment, but once the Netbeans plugin (Enclojure) matures, I really won't look back.

---

### Post by anc2020 on 2008-08-17
You're not wrong about + sbcl emacs slime

Unfortunately using SBCL's version of (run-program "blah"), I wasn't able to do some of the shell things I wanted to.

Speaking of which, if you're planning on using clisp (or any other interpreter) instead of bash, you can easily test that it does everything you want before changing any /etc files.

---

