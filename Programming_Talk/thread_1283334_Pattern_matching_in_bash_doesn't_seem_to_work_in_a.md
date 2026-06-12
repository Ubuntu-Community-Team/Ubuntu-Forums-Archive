---
title: "Pattern matching in bash doesn't seem to work in a script"
date: 2009-10-05
forum: Programming Talk
---

### Post by Paddy Landau on 2009-10-05
I'm having a big problem with pattern matching in Bash.

Consider the following two lines, which I type into a terminal.
```
zn='2560x1024'
echo ${zn//+([[:digit:]])/}  # Remove all digits
```The output is a single 'x', which is what I expect.

However, if I copy those exact lines into a script, as follows...
```
#!/bin/bash
zn='2560x1024'
echo ${zn//+([[:digit:]])/}  # Remove all digits
```Then the output from the script is '2560x1024'.

Why the difference?

---

### Post by MadCow108 on 2009-10-05
extglob (extended pattern matching) is probably disabled in the subshell started by the script and is enabled in your regular shell:
enable it with:
shopt -s extglob

[http://www.gnu.org/software/bash/manual/html_node/The-Shopt-Builtin.html](http://www.gnu.org/software/bash/manual/html_node/The-Shopt-Builtin.html)

you can also use your regular shell by starting the script with source or .

---

### Post by Paddy Landau on 2009-10-05
+1 -- Thank you! I would never have worked that out myself.

---

