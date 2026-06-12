---
title: "Regular expressions"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by skyline131313 on 2011-09-26
I was wondering if there is an easier way to do a command like this:

```
ls [aA][bB]*[abcd] [cC][hH]*[abcd] [sS][uU]*[abcd]
```

There doesn't seem to be an OR operator for this (usually it is '|' but that is used by temrinal.

just to shorten what I need to type, I would want some like this:

```
ls ([cC][hH] | [sS][uU] | [aA][bB])*[abcd]
```

---

### Post by sisco311 on 2011-09-26
Brace expansion:
```
echo {[aA][bB],[cC][hH],[sS][uU]}*[abcd]
```

Or if extglob is enabled:
```
echo @([aA][bB]|[cC][hH]|[sS][uU])*[abcd]
``` 

See:
[http://mywiki.wooledge.org/BashGuide/Patterns](http://mywiki.wooledge.org/BashGuide/Patterns)

---

### Post by Lisiano on 2011-09-26
It seems in Bash you need to backslash a metacharacter to get OR, so something in the lines of this ```
ls \([cC][hH] \| [sS][uU] \| [aA][bB]\)*[abcd]
```
More on Bash Regex.
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_01.html#sect_04_01_02](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_01.html#sect_04_01_02)

---

