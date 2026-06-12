---
title: "Secure way for programs without focus to read keyboard?"
date: 2009-09-25
forum: Programming Talk
---

### Post by shinobitux on 2009-09-25
Recently, I came across a piece of C code that monitors and redirects keyboard input to a different program.

This code makes use of the /dev/input/eventX files. The code didn't originally work since the event files didn't have read access for the user. I believe that this is the right thing to do, since keyloggers could easily take advantage of event files with read access.

If you need a background process to monitor user input what is the right and correct way to do this? Or is this practice taboo in general?

~shinobitux

---

