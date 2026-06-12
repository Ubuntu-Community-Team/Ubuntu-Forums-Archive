---
title: "man page for eval?"
date: 2012-08-20
forum: Programming Talk
---

### Post by conradin on 2012-08-20
Hi all,
I am working on a Ubuntu port of some scientific equipment scripts aimed at RHEL. There seems to be some different command line functions that I'm not exactly familiar with, such as $eval
how can I find out more about the eval command? 
My usual source:
[http://linux.die.net/man/1/eval](http://linux.die.net/man/1/eval)
seems useless in this case. 

the specific is a variable assignment. where findproc is a previous line 
Actualy, while I am at it, Im not exactly sure what grep $1 is either. 
```
 
... 
findproc="ps -e  | grep $1 | awk '{ printf(\"%d \",\$1) }'"
 npids=`eval $findproc`
```

as
usual any insight would be greatly appreciated.

---

### Post by steeldriver on 2012-08-20
iirc it's a shell builtin

[http://tldp.org/LDP/abs/html/internal.html](http://tldp.org/LDP/abs/html/internal.html)

AFAIK in newer versions of bash, it is better practice to replace that kind of thing with the $(...) syntax which allows you to assign the result of a command e.g.

```
var=$(ps -ef | grep *whatever*)
```Regarding your second question, $1 in the grep command would conventionally be the 1st command line argument to the script (assuming this is part of a shell script); however inside the awk command it's the first field in the input - in other words, any lines matched by grepping for the 1st shell argument get piped to awk, which prints the 1st field (column) of those lines.

---

### Post by Vaphell on 2012-08-21
eval should be avoided if possible. Executing arbitrary strings at runtime is a dirty hack, not to mention dubious security, especially when the string depends on user input in any way - allowing to eval "rm -rf /" would not be a great idea. It's not unlike the sql injection attacks which are the bane of the poorly constructed websites on the internet.

---

### Post by conradin on 2012-08-21
Thanks Guys, 
I found this web-page helpful as well.
[http://wiki.bash-hackers.org/rcwatson](http://wiki.bash-hackers.org/rcwatson)

the set -vx command was also a great thing to learn about. 
Thanks again!

---

