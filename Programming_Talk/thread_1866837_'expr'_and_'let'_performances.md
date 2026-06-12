---
title: "'expr' and 'let' performances"
date: 2011-10-22
forum: Programming Talk
---

### Post by hakermania on 2011-10-22
Hehehe, here you are:
```

alex@MaD-pc:~$ a=0; time while [ $a -lt 10000 ]; do let a=$a+1; done

real    0m0.217s
user    0m0.208s
sys    0m0.008s
alex@MaD-pc:~$ echo $a
10000
alex@MaD-pc:~$ a=0; time while [ $a -lt 10000 ]; do a=$(expr $a + 1); done

real    0m30.448s
user    0m1.540s
sys    0m5.088s

```When I first started bash scripting I was told to use 'expr' so as to do a small addition to a variable but now I can see that it's much slower than 'let'.

From the above executions you can see that expr is 172 times slower (!) ;)

---

### Post by Lars Noodén on 2011-10-22
Nice tip and an excellent test.

---

### Post by sisco311 on 2011-10-22
> **hakermania said:**
> Hehehe, here you are:
```

alex@MaD-pc:~$ a=0; time while [ $a -lt 10000 ]; do let a=$a+1; done

real    0m0.217s
user    0m0.208s
sys    0m0.008s
alex@MaD-pc:~$ echo $a
10000
alex@MaD-pc:~$ a=0; time while [ $a -lt 10000 ]; do a=$(expr $a + 1); done

real    0m30.448s
user    0m1.540s
sys    0m5.088s

```When I first started bash scripting I was told to use 'expr' so as to do a small addition to a variable but now I can see that it's much slower than 'let'.

From the above executions you can see that expr is 172 times slower (!) ;)

It's because let and (( are BASH builtin commands. Builtins are faster than external commands. 

let and (( aren't standard. The POSIX equivalent would be:
```
a=0; time while [ $a -lt 10000 ]; do a=$(($a+1)); done
```

[http://mywiki.wooledge.org/BashGuide/CompoundCommands#Arithmetic_Evaluation](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Arithmetic_Evaluation)

---

### Post by Lars Noodén on 2011-10-22
> **sisco311 said:**
> 
let and (( aren't standard.

Which means that they won't run in [dash](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dash.1.html) which is where /bin/sh links to in Ubuntu.

---

