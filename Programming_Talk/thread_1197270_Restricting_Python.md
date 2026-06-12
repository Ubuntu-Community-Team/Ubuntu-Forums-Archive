---
title: "Restricting Python"
date: 2009-06-25
forum: Programming Talk
---

### Post by Gannon8 on 2009-06-25
Hello all

I am going to try embedding python into a game as a system for writing client-side modules for the game. I want to restrict python from opening files, importing os, sys, and a few others, and other similar lockdown techniques, so that malicious servers cannot delete the entire drive.
Is there a way to do this, or do I have to look at the code being sent?

In C by the way

---

### Post by Reiger on 2009-06-25
That depends mostly on how you embed it. In a language like Java embedding Jython-with-strings-attached is fairly easy. (You could simply load your interpreter through a custom Classloader which has a non-trivial SecurityManager attached to it.)

---

### Post by Paul Miller on 2009-06-26
The short answer is: if you're embedding it in a C or C++ app, you can't really do that efficiently.

A slightly longer answer is: You really either need to trust your users or not allow third-party scripting at all.  

In theory, it is, of course, possible to limit a script's access to (say) the os and sys modules, which would limit a lot of the potential damage that could be done.  It's even possible to modify the file() and open() builtins to restrict which files they can open (but it's somewhat involved).  

[This]("http://code.activestate.com/recipes/496746/") is a start, but I'm not entirely convinced it's completely secure, as I haven't audited the entire Python codebase.  At a glance, it doesn't seem to prevent you from exhausting all of memory by evaluating an expression like "10**10**10", for instance.

All in all, if you must use Python and you must have complete sandboxing, I would say either using Jython (as a previous poster mentioned) or carefully auditing and patching the interpreter source are your best bets.  I wouldn't try to secure the interpreter with Python code (for one thing, Python doesn't have a good builtin way to measure the amount of memory an object takes up, among other things).

---

