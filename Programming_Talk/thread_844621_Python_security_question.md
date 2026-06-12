---
title: "Python security question"
date: 2008-06-29
forum: Programming Talk
---

### Post by snova on 2008-06-29
I've had an idea for a game buzzing around in my head for a while, but it requires stringent security measures.

To my dismay, rexec and Bastion are disabled due to security holes. I've thought up a partially functional replacement for my purposes; but though it appears sufficient, I wouldn't like to see it fail.

Hence this post: I would like public review of my system, so as to point out weaknesses that I have not found. If you can include a fix, even better.

The problem is thus: my application, written in Python, requires a way to safely execute arbitrary code (also Python) downloaded from the Internet. It is also quite possible that the source will not be included, but only the bytecode.

Fortunately, only the math module is likely to be needed by these scripts, so the entirety of the standard library can be closed off for simplicity.

In short, I need a sandbox.

My solution consists of executing each untrusted script in a separate thread. The __import__ function within sys is replaced with a version that only allows imports from a dummy library (including only math, for now) and from the package that the script resides in. It works the way it always does from the sole trusted thread.

Since it doesn't allow imp to be imported, a fully functional import statement cannot be constructed to get around it; or so I think.

I can't see a flaw here, but a determined cracker might. Can anybody see a problem with this?

---

### Post by LaRoza on 2008-06-29
> **snova said:**
> 
The problem is thus: my application, written in Python, requires a way to safely execute arbitrary code (also Python) downloaded from the Internet. It is also quite possible that the source will not be included, but only the bytecode.


The byte code of Python is easy to follow and disassemble (in fact, Python has a standard module for that)

I don't see any safe way of doing this. The only thing I could think of would be a Java applet, but that wouldn't work the same way.

You might want to redesign this.

---

### Post by snova on 2008-06-29
> The byte code of Python is easy to follow and disassemble (in fact, Python has a standard module for that)

Python source is hard to keep secret, sure. But that isn't the point, it's to prevent it from being able to run certain things in __builtin__ and in other places.

A key to this is the patched import statement. It doesn't *allow* most things to be imported. __builtins__ is reduced to safer levels (specifically, exit() is removed, among others) by deleting things, and sys and imp aren't available at all. That way a new import statement can't even be constructed, much less used in place of the new one.

Since I can't audit the entire standard library, I decided it's not useful anyway, and added it to the List Of Unavailable Packages.

The only thing *I* can see is that the Python interpreter might bypass the __import__ function for built in modules. If this is the case, there really is no way to do this. But I don't think so.

But, like I said, my opinion won't matter much. Python is so dynamic there probably *is* a way through. But I'd like to know what it is before I give up.

> The only thing I could think of would be a Java applet, but that wouldn't work the same way.

The reason this is in Python is that I don't like Java much, despite apparently having quite a suite of security modules.

>  You might want to redesign this.

I already have. This is part of my fourth attempt at a well-written design document.

I suppose some test code would be handy... I should try out my own claims. :grin:

And before anybody says something about uncooperative threads not being killable in Python, I'm using the Qt toolkit for this.

---

### Post by pmasiar on 2008-06-29
Google App Engine (GAE) has exactly the same problem - and they did not found any decent solution, even having some smartest Python hackers on payroll, so I don't think it is possible.

Guido is aware that having secure sandbox (like Java applet is) would be boost for Python, and Mozilla would like to use Python for plugins - but technology is not here yet. Maybe Python4 will solve it ... :-)

---

