---
title: "Running PDL program from terminal"
date: 2010-01-30
forum: Programming Talk
---

### Post by kcmccorm on 2010-01-30
First of all, I'm very new to programming so forgive me if any of my questions are stupid.  So my problem is this: I recently started writing a PDL program and I wanted to run it, but when I type "perl filename.pl" in the terminal, it does nothing.  Do I need to compile it? If so, how? (I tried "source filename.pl" and that didn't work).  I've run other PDL programs from the terminal, so I'm not sure what's happening.

Thank you.

---

### Post by Some Penguin on 2010-01-31
Seems likely that it's your Perl script which is the problem.  'perl foo' invokes foo as a Perl script; don't use "source" as that's for shell scripts.

---

