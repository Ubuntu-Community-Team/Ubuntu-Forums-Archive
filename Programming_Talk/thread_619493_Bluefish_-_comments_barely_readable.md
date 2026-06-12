---
title: "Bluefish - comments barely readable"
date: 2007-11-21
forum: Programming Talk
---

### Post by TimGS on 2007-11-21
How do I change the color that Bluefish uses for comments in my code?

At the moment its the default light grey on the white background, which is insanely difficult to read.

- Tim.

---

### Post by ghostz00 on 2008-04-18
I had the same problem and I couldn't figure out how to edit them in the preferences window. So this is how I fixed it.

Make sure Bluefish is closed and open:
[B]
~/.bluefish/highlighting[/B]

in your favorite editor.  And look for a line like this:

patterns: javascript:Comment (C++):0://.*?$::2::**#cccccc**::1:1:

and change the hex code to a color easier to read.

---

