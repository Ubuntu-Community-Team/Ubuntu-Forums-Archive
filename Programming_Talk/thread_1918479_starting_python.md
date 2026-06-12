---
title: "starting python"
date: 2012-02-01
forum: Programming Talk
---

### Post by conradin on 2012-02-01
Hi all,
 Im just starting python, coming from the bash scripting perspective. 
How do I use command line programs like:
clear, seq, date, echo, >> << >, exit, nslookup, grep, and so on from the a python script? Any hints or good reading I should checkout?

---

### Post by ofnuts on 2012-02-01
> **conradin said:**
> Hi all,
 Im just starting python, coming from the bash scripting perspective. 
How do I use command line programs like:
clear, seq, date, echo, >> << >, exit, nslookup, grep, and so on from the a python script? Any hints or good reading I should checkout?
These commands are useless in Python which has its own built-in functions for this (print, range()...); Python isn't a drop-in replacement for bash. In Bash you try to have most things done by commands, you own code being mostly glue. In Python your code includes a lot more logic and in most case you'll deal with files directly (otherwise use Bash).

---

### Post by JDShu on 2012-02-01
Here's a free book to work through:

[http://learnpythonthehardway.org/book/](http://learnpythonthehardway.org/book/)

Zed Shaw is highly respected (if abrasive) in the python community.

---

### Post by MadCow108 on 2012-02-01
if you want to use python as a bash shell replacement, there are better shells than the default one available which give direct access to installed executables and their output.
e.g. ipython or bpython

to use it in script there are wrappers to the subprocess module to simplify some things, e.g. pbs:
[https://github.com/amoffat/pbs](https://github.com/amoffat/pbs)

---

