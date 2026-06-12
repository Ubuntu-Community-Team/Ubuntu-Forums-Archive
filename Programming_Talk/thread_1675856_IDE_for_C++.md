---
title: "IDE for C++"
date: 2011-01-26
forum: Programming Talk
---

### Post by tommy1987 on 2011-01-26
Hi,

I'm doing more and more C++ these days and wanted an IDE that might provide me auto-code completion. Wondered what you people are using and like??

---

### Post by fct on 2011-01-26
My favorite: Codeblocks: [http://www.codeblocks.org/](http://www.codeblocks.org/)
Codelite is nice too: [http://www.codelite.org](http://www.codelite.org)

You could also look into Anjuta and KDevelop. But they aren't as portable as the two I've mentioned, so developing with them in other OS (like Windows or Mac) will be harder.

---

### Post by Simian Man on 2011-01-26
Eclipse with the CDT is my favorite.

---

### Post by fct on 2011-01-26
> **Simian Man said:**
> Eclipse with the CDT is my favorite.

Now that's one I always forget to try despite using Eclipse for Java professionally.

---

### Post by matthew.ball on 2011-01-26
I don't know if you would really call it an IDE, but emacs can go above and beyond the call of what is often considered an IDE (at least here on UF).

For example, emacs with [CEDET]("http://cedet.sourceforge.net/") is *very* good. CEDET basically "transforms" emacs into a full-blown development environment. You could get away without using CEDET, but it handles some things like project management which can be quite tedious (there are some screenshots available [here]("http://sourceforge.net/project/screenshots.php?group_id=17886")).

Apologies for the terrible music, but [this]("http://www.youtube.com/watch?v=C0qblk1BQrI") YouTube video shows how you can set-up a new C++ file fairly easily. There's also some really nice integration with [FONT="Courier New"]gdb[/FONT] (as shown [here]("http://www.youtube.com/watch?v=vHOzMOzzxDA")).

Unfortunately, it's one of the very few editors which *requires* the user to go through an interactive tutorial to use the editor. This tutorial takes roughly 10 minutes, but it's important the user actually engages with the editor (i.e. types in the keys as they are presented). There are really only a handful of commands (or key-bindings) a user need commit to memory, everything interactive is accessible to a user through the [FONT="Courier New"]M-x[/FONT] minibuffer. There are *many* extensions available for emacs which improve it's default behaviour.

If you've spent any time using emacs, you'll eventually want to add your own customisations. This isn't entirely necessary (I know a few senior researchers who have been using *vanilla* emacs for years for instance). To extend emacs, you write some [emacs lisp]("http://en.wikipedia.org/wiki/Emacs_Lisp") code in an init file for emacs (usually this is just [FONT="Courier New"]~/.emacs[/FONT] but it's possible to have a config file in the range of 10,000 lines of code, and managing a single file for something so large becomes tedious, so typically you would extend it over to a handful of files each serving a specific purpose).

If you're interested, check out [emacs wiki]("http://www.emacswiki.org/"), ask questions in the IRC channel [FONT="Courier New"]#emacs[/FONT] on [FONT="Courier New"]irc.freenode.net[/FONT] and search google for example [FONT="Courier New"].emacs[/FONT] configuration files for possible extensions.

---

### Post by rich1939 on 2011-01-26
> **fct said:**
> My favorite: Codeblocks: [http://www.codeblocks.org/](http://www.codeblocks.org/)
Codelite is nice too: [http://www.codelite.org](http://www.codelite.org)

You could also look into Anjuta and KDevelop. But they aren't as portable as the two I've mentioned, so developing with them in other OS (like Windows or Mac) will be harder.

I also prefer CodeBlocks for C & C++.

---

### Post by Miyavix3 on 2011-01-26
If you haven't tried Geany yet, give it a try. It supports code snippets which I find to be super useful. It makes doing homework in Java much more bearable. :p

---

### Post by slooksterpsv on 2011-01-26
I vote for Eclipse - I use it for C++, Python, Java (Android), etc. it's perfect =D. Just install Eclipse then get the CDT here:

[http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)

It's amazing. I never got Codeblocks to work for me very well... I'll try it again, what the heck.

---

### Post by krazyd on 2011-01-26
I like vim with the [OmniCppComplete]("http://www.vim.org/scripts/script.php?script_id=1520") plugin.

---

### Post by comprar piso on 2011-01-26
helo every 1 i wany to learn this C++ how i can i dont have any idea about programing

---

### Post by Zugzwang on 2011-01-27
> **comprar piso said:**
> helo every 1 i wany to learn this C++ how i can i dont have any idea about programing

Get a good book and start learning. Make sure that the book is not too old and deals only with standard-compliant code.

Also consider that starting with C++ as your first programming language is not necessarily a good idea, as it has some technicalities which you typically don't want to deal with in the beginning, and often also not afterwards. Someone here wrote (I think) that the MIT Python introductory courses are available at iTunes university. That might also be an alternative to the book thing and there might also be classes for other programming languages as first programming language there as well, in case you don't like Python.

---

### Post by cgroza on 2011-01-27
> **comprar piso said:**
> helo every 1 i wany to learn this C++ how i can i dont have any idea about programing

I would start learning the basic with a language like Ruby or Python and then buy a book and start learning.

---

### Post by dozy on 2011-01-29
I use QT Creator as the IDE for my normal C++ programming; it is the best environment I have used so far.
It may be intended for QT but can be configured for general C++ use.

See this post:
[http://ubuntuforums.org/showthread.php?t=1120632](http://ubuntuforums.org/showthread.php?t=1120632)

---

