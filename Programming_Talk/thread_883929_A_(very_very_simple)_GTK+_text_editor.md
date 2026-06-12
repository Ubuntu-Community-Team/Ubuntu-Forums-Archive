---
title: "A (very very simple) GTK+ text editor"
date: 2008-08-08
forum: Programming Talk
---

### Post by nvteighen on 2008-08-08
Hi there!
Some time ago, I asked for some help regarding a text editor in [this thread]("http://ubuntuforums.org/showthread.php?t=877245"). Well, I attach you the finished (?) program. Don't expect something good, it just opens and saves files without breaking them (but it's GPL, so modify it if you want).

The structure is simple: the main.c module takes care of the GUI and file.c does the low-level part (which is trivial). Most interesting part was the kind of "wrapper" (the callback functions) I was required to write in order to connect both parts.

To compile, use the 'make' command. Also, you need to have libgtk2.0-dev installed (GTK+ development files).

So, I wanted to share it and hear your comments, if any.

EDIT: I forgot, the whole thing is written in C.

---

### Post by raul_ on 2008-08-08
Maybe a couple of screenies? :popcorn:

---

### Post by Kadrus on 2008-08-08
Download it and:make
then run ./texedit
if you're fearing that it might be harmful its not

---

### Post by raul_ on 2008-08-08
Not really, it's just that it's always nice to have some screenshots when 'selling' our program

---

### Post by nvteighen on 2008-08-08
> **raul_ said:**
> Maybe a couple of screenies? :popcorn:

See below. I forgot about them... But it's a good thing Kadrus sent one, because Text-ed makes use of the locale language (and your icon theme!). In my screenies text appears in Spanish, but in his, in English. I send you also a screenie with a "Permission denied" error.

> **Kadrus said:**
> Download it and:make
then run ./texedit
if you're fearing that it might be harmful its not

It won't be harmful unless you run it with (gk)sudo and mess a system file with it :) If you're still afraid, look at the source!

---

### Post by nvteighen on 2008-08-08
> **raul_ said:**
> Not really, it's just that it's always nice to have some screenshots when 'selling' our program
If this was a sellable product...

---

### Post by raul_ on 2008-08-08
> **nvteighen said:**
> If this was a sellable product...

That's why I put it between '' :)

---

