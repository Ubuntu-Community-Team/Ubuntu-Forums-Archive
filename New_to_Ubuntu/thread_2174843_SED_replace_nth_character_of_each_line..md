---
title: "SED replace nth character of each line."
date: 2013-09-16
forum: New to Ubuntu
---

### Post by viddect on 2013-09-16
I am trying to replace the 3rd character of each line with a number for example

'AA' to 'A10' and 'BA' to 'B10'


i have been digging through how to's and man pages and I am not finding what I need

any help would be great.

---

### Post by Lars Noodén on 2013-09-16
Can you post a full line or two?  It would give something more concrete to work with.  But a first guess would be like this:

```

echo abcdefg | sed -e 's/^\(..\).\(.*\)$/\110\2/'

```

The manual page for sed is a little weak.  The dots represent a single character.  The escaped parenthesis group the pattern results.  In the substitution, \1 and \2 refer to the first and second groupings respectively.  And, of course, ^ and $ refer to the start and end of the line so that you are sure to get the whole line.

---

### Post by Vaphell on 2013-09-16
\2 is not necessary and with -r the expression is easier on the eyes.
```
$ echo abcdefghi | sed -r 's/^(..)./\110/'
ab10defghi
```

---

### Post by Lars Noodén on 2013-09-16
Ah yes.  The second group is entirely unnecessary.

```

echo abcdefg | sed -e 's/^\(..\)./\110/'

```

But is **-r** still POSIX?

---

