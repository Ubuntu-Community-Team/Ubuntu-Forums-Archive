---
title: "Python Xlib - Any way to change the cursor?"
date: 2011-08-27
forum: Programming Talk
---

### Post by Senesence on 2011-08-27
I'm using a code snippet found in this thread: [http://ubuntuforums.org/showthread.php?t=1398201](http://ubuntuforums.org/showthread.php?t=1398201)

That's my test base, and it works fine ( I can draw on the root window ).

What I would like to do now, is to actually change the cursor to a cross, and then back to a normal mouse pointer when the program exits.

I'm hoping that someone here would know how to do that, since the [python-xlib documentation]("http://python-xlib.sourceforge.net/doc/html/python-xlib_toc.html") is pretty horrible.

I mean, I would understand if python-xlib was a direct mirror of the C api, in which case that documentation would serve fine, but it's not, so it doesn't.

Any help would be appreciated.

---

### Post by cgroza on 2011-08-27
I found this maillist post that seems to give you 2 functions:
[http://archives.seul.org/linuxgames/Feb-2000/msg00033.html](http://archives.seul.org/linuxgames/Feb-2000/msg00033.html)

---

### Post by Senesence on 2011-08-27
> **cgroza said:**
> I found this maillist post that seems to give you 2 functions:
[http://archives.seul.org/linuxgames/Feb-2000/msg00033.html](http://archives.seul.org/linuxgames/Feb-2000/msg00033.html)

Well, I think this is referring to the C api - I'm using python-xlib.

Is there an equivalent function in python-xlib?

I can't find it.

---

### Post by cgroza on 2011-08-27
> **Senesence said:**
> Well, I think this is referring to the C api - I'm using python-xlib.

Is there an equivalent function in python-xlib?

I can't find it.
Those functions should be available in the Python API too. It is the same library, just a different binding.
I may be wrong though.

---

### Post by Senesence on 2011-08-28
> **cgroza said:**
> Those functions should be available in the Python API too. It is the same library, just a different binding.
I may be wrong though.

Did you actually find equivalent functions in python-xlib docs, or are you just guessing?

As I said, I can't seem to find it.

So, if you could either give me a link to where these python-xlib functions are documented, or, even better, a small python-xlib example that changes the cursor, I would really appreciate it.

Thanks.

---

