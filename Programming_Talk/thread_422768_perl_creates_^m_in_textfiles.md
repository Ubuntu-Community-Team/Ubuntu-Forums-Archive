---
title: "perl creates ^m in textfiles"
date: 2007-04-25
forum: Programming Talk
---

### Post by monkeyking on 2007-04-25
Hi I'm using perl on ubuntu,
and when I create textfiles, it sometimes inputs ^M

any idea why?

---

### Post by Ramses de Norre on 2007-04-25
Do they come from windows? Windows' newlines translate to ^M\n on linux (so that "^M" followed by a real newline).

---

### Post by yaaarrrgg on 2007-04-25
yes, check your end of line character, if you are writing the text to a file.  

In windows, your perl script should use "\r\n" and in linix just "\n".

The windows end of line is a throwback to the old days when the printer had a carriage that had to physically return to beginning of the line, before the paper would advance.

---

