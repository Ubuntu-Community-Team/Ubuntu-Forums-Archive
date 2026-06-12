---
title: "[SOLVED] Backround processes and semicolons"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Sbroad on 2008-06-13
Hi everyone.  I'm writing a script to interact with some remote machines.  For the purposes of the script, I need to send all the commands in a single line, but some of these commands need to run in the background.

Here's an example of what I'm trying to do:
```

RNAfold < test_fasta.txt > output.txt &; (more commands)
```

The problem is I get a syntax error with the & next to the semicolon.  Is there any way to run a process in the background and still use a ";"?

Thanks,
Sam

---

### Post by sdennie on 2008-06-13
Did you try:

```

(RNAfold < test_fasta.txt > output.txt &) ; (more commands)

```

---

### Post by Sbroad on 2008-06-13
Nope, but that does it.  Thanks for the quick reply. :)

---

