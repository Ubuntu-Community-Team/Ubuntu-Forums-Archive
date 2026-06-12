---
title: "I'd like to learn how to code plugins/modules (C)"
date: 2009-06-11
forum: Programming Talk
---

### Post by tuggy on 2009-06-11
Hi
I've been searching for tutorials and manuals, but I cant find out anything that helps me.
I'm looking for something that teaches me how to code a plugin-capable program.

That is, how can I make a program check for some specific files in a folder (plugins), load them, and make more features available?

I was thinking of starting with something very simple. Imagine a calculator app with only one function "sum". Now I want to code 3 plugins for "sub" "mult" and "div", and be able to load them at runtime.

Any helpful pointers, tips, links? :)
thanks

---

### Post by nvteighen on 2009-06-11
What you need is dynamic linking (**dlopen()** and friends... look at the manpages) to load shared libraries at runtime (these shared libraries will be your plugins.

Of course, your plugins will have to emulate a normal application's main() method. That will force you to create some rule for your plugin developers... e.g. that the plugin entry points should be a function **int plugin_main(int, char *)** or whatever.

Also, you'll have to provide a Plugin API. This means, your program should provide pulgin developers a decent library of functions and data structures that are common for the tasks related to your application, so they don't have to reinvent the wheel every time and start building from a certain common base.

---

### Post by tuggy on 2009-06-11
thanks a ton!
that was exactly what I needed. the man page will show me the rest of the way ;)

---

### Post by nvteighen on 2009-06-11
> **tuggy said:**
> thanks a ton!
that was exactly what I needed. the man page will show me the rest of the way ;)
Well, if you don't know how to compile shared libraries, take a look at: [http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html)

---

