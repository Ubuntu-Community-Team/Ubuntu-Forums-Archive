---
title: "Top command show only specified outputs"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by benas2 on 2014-05-20
Hello,

I have command

```
top -b -n 1 -u xxx | awk 'NR>7 { sum += $9; } END { print sum; }'
```

It's running quite long till i get resposne, i need to make it run low to get cpu usage for that user. So my idea is only show cpu usage by top command. Can any1 explain is it possible to limit columns via argument line for example top -columns cpu ?

---

### Post by Frogs Hair on 2014-05-20
Hello and Welcome

The man page may help . ```
man top
```

---

### Post by benas2 on 2014-05-21
Yes i checked man of top command, however it seems that they dont give to choose collumns output via command line arguments. Maybe there is some faster way to determine linux user cpu usage ?

---

### Post by Frogs Hair on 2014-05-21
You may want to check this site which I have found useful. The packages specified are usually available in Ubuntu and there is further reading link at the bottom of the page. Bump the thread every 24 hrs as need until a user more familiar with using the syntax comes along. 

[http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html](http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html)

---

### Post by steeldriver on 2014-05-21
Can you explain more what you mean by "It's running quite long till i get resposne, i need to make it run low to get cpu usage for that user."? 

What is the actual problem you are trying to solve here? 

Perhaps the 'ps' command can be made to do what you want? e.g.

```

ps -u $USER -o %cpu= --sort -%cpu

```

As far as I know, the only way to control the column selection for 'top' in batch mode is via a ~/.toprc file.

---

### Post by benas2 on 2014-05-22
Ok, i need to get specific linux user current cpu speed. If i run command
```
time top -b -n 1 -u 2205 | awk 'NR>7 { sum += $9; } END { print sum; }'
```
I get response
```

2#This is current user cpu speed

real    0m0.518s
user    0m0.006s
sys     0m0.009s

```
As you can see it runs ~0.5s. Which is too much for me.

Running

```
time ps -u 2205 -o %cpu --sort -%cpu
```
```
%CPU
 3.3
 0.0


real    0m0.008s
user    0m0.004s
sys     0m0.004s

```

Ps command is returning same cpu value all the time, while top is changing regulary..
```

_ps:%CPU
 3.3
 0.0
_top:
2
_ps:
%CPU
 3.3
 0.0
_top:
4
_ps:
%CPU
 3.3
 0.0
_top:
2

```

---

### Post by Vaphell on 2014-05-22
afaik ps cpu% reports avg value which sucks to say the least.

Either way why 0.5s is too slow? What do you need it for?

---

### Post by benas2 on 2014-05-22
> **Vaphell said:**
> afaik ps cpu% reports avg value which sucks to say the least.

Either way why 0.5s is too slow? What do you need it for?

I'm monitoring my linux user in php application. I'm getting hdd, ram, cpu values, but cpu uses too much time, because for instance hdd calculations takes less than 0.1s

---

### Post by Vaphell on 2014-05-22
you didn't answered why 0.5s is too much time. Maybe system doesn't have that data lying around and needs to probe processes to establish the temporary avg?

---

### Post by benas2 on 2014-05-22
> **Vaphell said:**
> you didn't answered why 0.5s is too much time. Maybe system doesn't have that data lying around and needs to probe processes to establish the temporary avg?
Yeah, sorry. 0.5s is too much for me. I don't blame my system.. I'm just searching for faster current cpu average finding.

---

