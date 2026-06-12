---
title: "Extra &quot;stuff&quot; in compiled binary - why?"
date: 2009-04-07
forum: Programming Talk
---

### Post by Krupski on 2009-04-07
Hi all,

I noticed that some text gets inserted into the binary files which result from compiling my C source.

Unless I'm debugging, I want the smallest possible binary possible. The stuff I see appears to be useless (code-wise) as I can zero-overwrite it and the executable still works.

Here's a screenshot of the text as seen in "hexedit":


[CENTER][IMG]http://home.roadrunner.com/~krupski/images/screen.jpg[/IMG][/CENTER]


I've seen programs (pre-compiled binaries) from other sources that had no "advertising" in them.

Is this unique to the Ubuntu release of GCC and G++?

What does it mean? Why is it in there?

And, is there a way to remove it?

Thanks!

-- Roger

---

### Post by movieman on 2009-04-07
It's probably debugging info: run 'strip' on the file and see if it goes away.

Note that debug info shouldn't be loaded into memory unless you need it, so it only really increases the size of the executable on disk, not in RAM.

---

### Post by Krupski on 2009-04-07
> **movieman said:**
> It's probably debugging info: run 'strip' on the file and see if it goes away.

Note that debug info shouldn't be loaded into memory unless you need it, so it only really increases the size of the executable on disk, not in RAM.

No, it's not debug info. The file HAS debug info in it (and I know what it looks like).

That "Ubuntu" stuff is even present in non debug, stripped "release" versions of a binary.

---

### Post by NathanB on 2009-04-07
To eliminate all of the "extra stuff", you will want to generate the ELF header by hand.  This tutorial will walk you through the details:

[http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html](http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html)

---

### Post by Krupski on 2009-04-07
> **NathanB said:**
> To eliminate all of the "extra stuff", you will want to generate the ELF header by hand.  This tutorial will walk you through the details:

[http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html](http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html)

That's really interesting info... but not really the answer to the question.

---

### Post by Frank Kotler on 2009-04-08
Try "strip -R.comment myfile". (but if you *really* want a small file, follow Nathan's advice!)

Best,
Frank

---

### Post by dwhitney67 on 2009-04-08
> **movieman said:**
> It's probably debugging info: run 'strip' on the file and see if it goes away.

Note that debug info shouldn't be loaded into memory unless you need it, so it only really increases the size of the executable on disk, not in RAM.
Unless of course, the RAM is your "disk".  Not all systems have a HDD.

---

### Post by nvteighen on 2009-04-08
It's just compiler information. Not "adverstising" and not particular to Ubuntu either... :)

---

### Post by Krupski on 2009-04-08
> **nvteighen said:**
> It's just compiler information. Not "adverstising" and not particular to Ubuntu either... :)

Well, in a roundabout way, I got my answer. The utility "strip" is what removes unnecessary things from executables.

And, to remove the "advertising" (compiler information), "strip" is used like this:

```

    strip -s -R .comment -R .gnu.version executable

```

So, thanks everyone for the help and comments!

-- Roger

---

### Post by Krupski on 2009-04-08
> **Frank Kotler said:**
> Try "strip -R.comment myfile". (but if you *really* want a small file, follow Nathan's advice!)

Best,
Frank

At first I thought that was a GCC command line argument!  :)

It wasn't until later that I found out that "strip" is a separate program!

-- Roger

---

