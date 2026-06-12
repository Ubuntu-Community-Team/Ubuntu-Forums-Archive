---
title: "[SOLVED] What is the difference between these 2 commands that allow you to string tog"
date: 2006-10-26
forum: Programming Talk
---

### Post by bswilson on 2006-10-26
I have seen in various places where folks share commands to run for various purposes.  Some of these posts show you how to use a double ampersand to string 2 commands together.  I am not familiar with this syntax, but know well the use of a semi-colon.

Is there any difference between these 2 commands?  Where can I find more documentation on the double ampersand?

**Command 1**
```
sudo apt-get update && sudo apt-get install <package>
```
**Command 2**
```
sudo apt-get update; sudo apt-get install <package>
```

---

### Post by shining on 2006-10-26
The answer is in "man bash", also available there:
[http://www.gnu.org/software/bash/manual/bashref.html#SEC18](http://www.gnu.org/software/bash/manual/bashref.html#SEC18)

---

### Post by eeGhoong0ais on 2006-10-26
```
command1; command2
``` means "do command1, then when it's finished do command2". ```
command1 && command2
``` means "do command1, and if it finishes without reporting any errors, do command2".

You can also use ```
command1 || command2
``` - that one means "do command1, and if it reports an error, do command2".

You can even go wild with ```
command1 && command2 || command3
``` if you're feeling really adventurous - something like ```
sudo apt-get update && sudo apt-get install <package> || echo "dammit!"
``` for example.

---

