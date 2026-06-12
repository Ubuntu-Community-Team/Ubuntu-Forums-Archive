---
title: "Simple Regular Expression Question"
date: 2010-11-23
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-11-23
I am trying to write a couple regular expressions in Java for matching lines that appear in a file which look like this:

nocon(0:4) = 0110
nocon(5) = 0
mtd_cntrl = 1

What regular expressions would I need to match these?  It would be something like:

(\w+)\((\d+):(\d+)\)\s*=\s*(\d+) - 1st Line
(\w+)\((\d+)\)\s*=\s*(\d+) - 2nd Line
(\w+)\s*=\s*(\d+) - 3rd Line

I put in parenthesis to indicate what I want to match, but not sure how to handle the literal parenthesis.  I plan to write this in Java using Pattern / Match classes.  I think those expressions are close to what I need.  Can someone fix?

---

### Post by Some Penguin on 2010-11-23
Backslash is an escape character.  Of course, it's also an escape in a string constant, so you need to use "\\(" instead of "\(" (since "\(" is *not* a legal escape sequence in a Java string constant).  For longer sequences, "\Q...\E" quotes whatever the ... is, and "quoted = Pattern.quote(unquoted)" gets you an escaped form, too.

---

### Post by SNYP40A1 on 2010-11-24
> **Some Penguin said:**
> Backslash is an escape character.  Of course, it's also an escape in a string constant, so you need to use "\\(" instead of "\(" (since "\(" is *not* a legal escape sequence in a Java string constant).  For longer sequences, "\Q...\E" quotes whatever the ... is, and "quoted = Pattern.quote(unquoted)" gets you an escaped form, too.

Cool, thanks Penguin.  I'll try the double slashes later tonight.

---

