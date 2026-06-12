---
title: "Question on using resource files"
date: 2010-02-21
forum: Programming Talk
---

### Post by nvteighen on 2010-02-21
I'm a bit confused on which is the best approach to handle the following situation. Consider I'm coding a program, say, in Python, which needs to use an external file for something; ok, I can code that by using the relative path and it'll work... until I happen to install it system-wide and following the usual filesystem conventions of having resource data placed at /usr/share/app_name or configuration files at /etc/app_name or whatever. By using a relative path approach, though, I'm able to test the thing quickly, not having to install it by myself... and it makes tarball distribution much easier.

So, my question is the following: While developing, what do you do? These are the alternatives I can think of are:

1. You code thinking in how it works when effectively installed, so that to test it you actually install the files into system-wide places.
2. You code a way that somehow allows you to detect whether the code is installed system-widely or not. If it is, code will search in standard places; if not, it defaults to relative paths.
3. You use a config file somewhere that tells the location the program has to look at in order to find the needed resources.

I like the 3rd option more than anything, as it sounds more flexible and easier to mantain... but I have really almost no experience in deployment issues, so any advice from someone more experienced is welcome...

Thanks!

---

### Post by CptPicard on 2010-02-21
2? Coding a function that does a "locate-this-file" by guessing the alternatives shouldn't be too hard.

---

