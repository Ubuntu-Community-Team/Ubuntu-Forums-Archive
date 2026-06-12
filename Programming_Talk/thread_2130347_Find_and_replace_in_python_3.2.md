---
title: "Find and replace in python 3.2?"
date: 2013-03-29
forum: Programming Talk
---

### Post by sudo san on 2013-03-29
Hi, I am quite new to python and was just recently writing a python 3.2 script for installing all my favourite programs on a fresh install of ubuntu. I have only just learned about if statements and wondered if there was a way I can use them to write a script to upgrade from earlier versions of ubuntu, e.g upgrade from precise to quantal.

For example, I want the script to take input from the user about which version they are using and the version they are going to upgrade to. Then look for the first input in the ```
/etc/apt/sources.list
``` and replace it with the second input. I am guessing that if statements would be used. I cannot find how to do this even with a quick google.

Any help would me much appreciated.

Thanks very much in advance.

---

### Post by MadCow108 on 2013-03-29
python is a little overkill for that, a simple sed -e "s/old/new/" file would do that too, also you should use update-manager -d or do-release-update for that

but if you want to do it in python the things you need is:
raw_input
some string comparisons
open
.read method of files
.replace method of strings
.write method of files

---

### Post by Vaphell on 2013-03-29
agreed about python being an overkill and that using upgrade paths provided by the system is how it's supposed to be done.

also asking user about his release doesn't make much sense, what if the answer is wrong? you can probe the system directly, eg if you want to get codename
```
lsb_release -sc
```

---

### Post by sudo san on 2013-03-29
Ok, I will just write myself a simple bash script then. Thanks for the help.
:)

---

