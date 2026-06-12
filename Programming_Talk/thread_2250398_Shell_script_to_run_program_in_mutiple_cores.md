---
title: "Shell script to run program in mutiple cores"
date: 2014-10-28
forum: Programming Talk
---

### Post by achuthpnr on 2014-10-28
I want to run a program N times, with an incremented variable as input each time. The for loop in bash script seems a good option here. So I have like

```
#!/bin/bash
for i in {1..10}
do
   ./my_prog $i
done
```

Imagine one run takes about 10minutes to finish. The above code obviously runs on one processor at a time until it finishes and then starts the next one. 
I have multiple processors and I want to use them all together to save time
Is there any way other than doing n separate scripts of
```
for i in {1..10..1}...
```. to have the same effect in a single script such that all cores are used together? 

just curious...

---

### Post by ofnuts on 2014-10-28
Originally written for ksh, will likely work in bash... Needs some improvement if you want to cath errors in subprocess

```

#!/bin/ksh

set -a pids
for # with whatever adequate loop you have 
do
  your_program_invocation_here &
  pids[${#pids
[*]}]=$!
done

for pid in ${pids
[*]}
do
  wait $pid
  print "Sensed end of $pid"
done
# continues here when all launched subprocess have ended

```

---

### Post by Vaphell on 2014-10-28
you may want to look at gnu parallel

[http://www.gnu.org/software/parallel/parallel_tutorial.html#Number-of-simultaneous-jobs](http://www.gnu.org/software/parallel/parallel_tutorial.html#Number-of-simultaneous-jobs)


> ```
for pid in ${pids[*]}
```

unless things are different in ksh this is bad. You don't create array to merge elems into a single string (which is what * does using first IFS char as a glue) and then let it split on whitespace. Just go for elems directly with "${pids[@]}"
There are almost no legitimate uses of *, especially when loops are concerned.

---

### Post by achuthpnr on 2014-10-29
Thanks Vaphell. GNU-parallel seems an interesting choice.

---

