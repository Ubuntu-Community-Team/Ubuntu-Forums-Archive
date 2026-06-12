---
title: "Shell scripting"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by Bomoshell on 2012-09-04
Hello!

Given the following script I have to solve the next task:
Modify the script so that you only display the words that start with a consonant and end with a figure.

#!/bin/bash
i=1
for arg in $@; do
             if test ${#arg} -gt 2; then
                             if test ${#arg} -lt 7; then
                                                   echo "$i   $arg"
                             fi
            fi
((i++))
done


So what command should I use?

---

### Post by coffeecat on 2012-09-04
This sounds very much like a homework assignment. From the forum [Code of Conduct](http://ubuntuforums.org/index.php?page=policy):

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. 

Thread closed. If you feel this has been closed unfairly, please post in the [Resolution Center](http://ubuntuforums.org/forumdisplay.php?f=123) and we'll take it from there.

---

