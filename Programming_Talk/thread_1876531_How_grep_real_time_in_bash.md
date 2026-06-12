---
title: "How grep real time in bash?"
date: 2011-11-06
forum: Programming Talk
---

### Post by Pithikos on 2011-11-06
I want to only get the real time it takes for a command to run and save that to a variable in bash. However I can't make sense of what is happening.

I run
```
$(time ls &> /dev/null) | grep real > test
```but file test remains empty while time is still written on screen. :confused:

---

### Post by MadCow108 on 2011-11-06
the output of the builtin time goes to stderr + it needs to go into a subshell:
```
(time ls) 2>&1 | grep real
```

---

### Post by learnbash on 2011-11-06
Brother check below code.

```


# (time ls) 1> /dev/null 2> output
[root@server1 test]# cat output

real    0m0.003s
user    0m0.001s
sys    0m0.002s


```Hope it helps

```
 (time ls) 1> /dev/null 
``` 
Above thing is ignorning output and sending it to /dev/null

```
 2>output 
``` 
Above thing is going to store error in output file, after that cat that file to see contents.

---

### Post by sanderd17 on 2011-11-06
EDIT: better explanations above

---

