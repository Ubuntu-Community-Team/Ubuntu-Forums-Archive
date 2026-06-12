---
title: "How to let external program (called from Java) print to display too?"
date: 2007-02-03
forum: Programming Talk
---

### Post by Dislimit on 2007-02-03
How to let external program (called from Java) print to display too?
I use Runtime.exec(cmd) to invoke a Perl script. It works but does not print to screen.
How to do it?

---

### Post by Ramses de Norre on 2007-02-03
By catching it in a string, that method will return stdout as a string. So if you assign the method's return value to a string you can output that string to the display.

---

