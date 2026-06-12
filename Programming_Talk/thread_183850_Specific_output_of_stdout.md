---
title: "Specific output of stdout"
date: 2006-05-28
forum: Programming Talk
---

### Post by mucha on 2006-05-28
How can I print out a specific text of a stdout (by a program)? Like with regexp or something?

---

### Post by glinsvad on 2006-05-28
If you want to filter the stdout from a program, pipe it through grep like this:
```

grep -E REGEXP

```

To try it out, here's an example:
```

top -b -n 1
top -b -n 1 | grep -E "[ \t]+x[a-z]+[ \t]*$"

```
Translation: Only show lines containing one-or-more whitespace, then the character x, then one-or-more lowercase letter, then possibly more whitespace and finally end of line. The candidates would be xscreenserver etc.

---

### Post by mucha on 2006-05-29
Thanks, but I also want to print a specific text on each line. Like with your line "top -b -n 1 | grep -E "[ \t]+x[a-z]+[ \t]*$"" it prints out:
> 12426 simon      0   0  4208  608  536 S  0.0  0.1   0:02.08 xbindkeys
30789 simon      0   0 80440  12m 7988 S  0.0  1.2   1:09.27 xchat

But if I just want to print out the names of the applications, like:
> xbindkeys
xchat

In php/perl you can use the () chars, think its called back references.

---

### Post by glinsvad on 2006-05-29
Then use a stream editor like sed also:
```

top -b -n 1 | grep -E '[ \t]+x[a-z]+[ \t]*$' | sed -r 's%^.*[ \t]+(x[a-z]+)[ \t]*$%\1%g'

```

You might want to look into sed-commands. If you know Perl or Python, these will do just fine as well.
[http://sed.sourceforge.net/sed1line.txt]("http://sed.sourceforge.net/sed1line.txt")

EDIT:
Looking more into sed really makes grep obsolete, since the whole thing can be done like this:
```

top -b -n 1 | sed -r '/^.*[ \t]+(x[a-z]+)[ \t]*$/!d;s%^.*[ \t]+(x[a-z]+)[ \t]*$%\1%g'

```
Translation: If regexp does not match, delete line (/regexp/ matches, ! means not, d deletes line).  Then, if regexp matches, substitute the line with the text inside the first parenthesis (s%regexp%replace%g replaces regexp with replace, \1 referes to the text inside the first parenthesis in regexp).

---

### Post by glinsvad on 2006-05-29
By the way, the coolest thing about sed is that you can make scripts for automatically editing files!

Just make a file with the postfix .sed. Here's an example I call mainrepos.sed, that can uncomment main and restricted repositories in your sources.list:
```

#!/bin/sed -rf

s%^[ \t#]*(deb[ \t]+http://[A-Za-z0-9.]*archive.ubuntu.com/ubuntu[ \t]+breezy+[ \t]+main[ \t]+restricted)[ \t]*$%\1%g

```

To test it, comment out the repositories and run it in terminal like this (naturally sed-scripts are executable):
```

sudo ./mainrepos.sed -i /etc/apt/sources.list

```

---

### Post by mucha on 2006-05-29
Thanks for your help! :) Really appreciated

---

