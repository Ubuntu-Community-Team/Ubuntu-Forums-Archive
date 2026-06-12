---
title: "Require help with script"
date: 2007-06-24
forum: Programming Talk
---

### Post by supersonicdarky on 2007-06-24
i thought i'd try shell scripting, and decided to start off with a script that shortens the command in [here](http://ubuntuforums.org/showthread.php?t=472090) into **history10**


so far i got this put all it produces is a blank line
```
#!/bin/bash

history | sed -e 's/  / /g' | cut -d " " -f3 | sort | uniq -c | sort -n | tail | sort -nr | echo

```

also, | means output of previous command as input of next command, right?

---

### Post by McNils on 2007-06-24
The last echo produces a blank line. Skip it and it will work. 
echo does not read from stdin.

---

### Post by Mr. C. on 2007-06-24
Here's a variant that is a bit shorter.  See if you can figure out what it is doing:

fc -nl -1000 | sed 's/\t */ /g' | sort | uniq -c | sort -n -r| head

Also, your command (without the trailing echo) is producing a series of blank lines that are counted.

MrC

---

