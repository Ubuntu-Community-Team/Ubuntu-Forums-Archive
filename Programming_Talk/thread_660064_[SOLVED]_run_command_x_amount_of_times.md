---
title: "[SOLVED] run command x amount of times"
date: 2008-01-06
forum: Programming Talk
---

### Post by Dr Small on 2008-01-06
In bash, I want to make a while loop (I guess?) that runs a command x amount of times, until it finishes. I've been reading up on it at google, but can't find any down to earth examples (I have no idea about while).

Is there any way to do this?
I was just curious.

Dr Small

---

### Post by nhandler on 2008-01-06
In this case, a for loop would be more appropriate (however, you could also use a while loop).

Here is the code you will use:

```
#!/bin/bash
for ((i=1;i<=5;i+=1)); do
YOUR CODE HERE
done
```

---

### Post by ghostdog74 on 2008-01-06
> **Dr Small said:**
> In bash, I want to make a while loop (I guess?) that runs a command x amount of times, until it finishes. I've been reading up on it at google, but can't find any down to earth examples (I have no idea about while).

Is there any way to do this?
I was just curious.

Dr Small

```

num=0
while [ $num -lt 5 ]
do
  function
  num=$(( num+1 )) 
done


```

Read[ here ]("http://tldp.org/LDP/abs/html/")from start to end.

---

### Post by Dr Small on 2008-01-06
Ok, thanks for the info. That worked :)

Dr Small

---

