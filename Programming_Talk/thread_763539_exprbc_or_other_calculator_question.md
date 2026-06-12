---
title: "expr/bc or other calculator question"
date: 2008-04-23
forum: Programming Talk
---

### Post by Noggenfogger on 2008-04-23
Hi

I'm looking for a way to round off numbers upwards using shell script.

examples:

1400/512 using bc or expr will return 2. 
I want it to always roundoff upwards not down, so in this case i need it to return 3.

1024/512 must generate 2, that don't need to be rounded off since it's divided into 2 exactly.
 

hope you understand what I'm looking for

Anyone know how to do this?
(sorry for my poor english)

---

### Post by ghostdog74 on 2008-04-23
```

# echo "scale=2;2.3433/2" | bc
1.17

```

---

### Post by croto on 2008-04-23
Here is a little hacky bash-bc funtion, and it seems to do the job. 
```

darkstar:~$ f () { echo "scale=20; a=($1); scale=0; b=a/1; if (a==b) b else b+1" | bc -l; }

```
I'm getting this results
```

darkstar:~$ f 10.1
11
darkstar:~$ f 1040/512
3
darkstar:~$ f 1024/512
2

```

However, if you run it like " f expression ", where the expression would give a number x such that x-[x]<10^-20 ([x] means integer part of x), you may not get the result you want. Anyway, I don't think that's gonna be a problem for most practical cases. If you need more precision, you could always increase scale from 20 to whatever you want.

EDIT: It doesn't work fine with negative numbers.

---

### Post by Noggenfogger on 2008-04-23
Thanks both, the last one was exactly what I was after the first one I will use in another script.
Salute!

---

