---
title: "BASH: How to repeat an action every 2 seconds?"
date: 2007-05-24
forum: Programming Talk
---

### Post by loathsome on 2007-05-24
Hi there,

How do I repeat something for example every 2 seconds? Let's say I'd want to echo 'lol' every two seconds, how should I do that? Thanks!

---

### Post by stee on 2007-05-24
> **loathsome said:**
> Hi there,

How do I repeat something for example every 2 seconds? Let's say I'd want to echo 'lol' every two seconds, how should I do that? Thanks!

```

while [ "true" ]
do
  echo "lol"
  sleep 2
done

```

---

### Post by ghostdog74 on 2007-05-24
man sleep

---

### Post by loathsome on 2007-05-24
Thanks a bunch.

I've got a lot of PHP experience, but bash is all new to me :)

---

### Post by loathsome on 2007-05-24
Also, how you do do something equivalent to this?

```

do
    blabla
    $variable++;
done

```

Increase a numeric variable by one each time the loop runs.

---

### Post by WW on 2007-05-24
Here is one way:
```

let x=0
while [ "true" ]
do
    echo "lol($x)"
    let ++x
    sleep 1
done

```

---

### Post by loathsome on 2007-05-24
> **WW said:**
> Here is one way:
```

let x=0
while [ "true" ]
do
    echo "lol($x)"
    let ++x
    sleep 1
done

```

Thanks, worked flawlessly!

---

### Post by ninja23 on 2008-11-05
I have a very similar question... Is there a way to do this without the sleep function?

I'm pretty much looking for this converted to code: 'if it has been 2 seconds'



Any help would be greatly appreciated =)

---

### Post by reality1011 on 2008-11-05
the only way I can think of is using date +%S to get the current second.  If you create a loop that constantly does date +%S and compared it to the last baselined second, you would find 2 seconds... I think that is unnecessary processing though...

```


sec=`date +%S`

while [1]; do 
    sec1=`date +%S`
    (( amt_slept = $sec - $sec1 ))

    if [ $amt_slept -eq 2 ]; then 
         <EXECUTE CODE>
         sec=`date +%S`
    fi


done

```

---

### Post by ninja23 on 2008-11-05
> **reality1011 said:**
> the only way I can think of is using date +%S to get the current second.  If you create a loop that constantly does date +%S and compared it to the last baselined second, you would find 2 seconds... I think that is unnecessary processing though...

```


sec=`date +%S`

while [1]; do 
    sec1=`date +%S`
    (( amt_slept = $sec - $sec1 ))

    if [ $amt_slept -eq 2 ]; then 
         <EXECUTE CODE>
         sec=`date +%S`
    fi


done

```

I can't get it to work... Could it be written as 'if it has been 2 seconds' the 'if' ?

Thanks =)

---

### Post by crazyfuturamanoob on 2008-11-05
Perhaps make a small python script?

```

import time

while 1:
    print "lol"
    time.sleep(2)

```

It's way easier.

---

### Post by ninja23 on 2008-11-05
I'm just not really sure how to explain it, I guess.

Here is an example code:

```
while : ; do

    lynx -dump http://yahoo.com
    date
    sleep 2s

done
```

Sometimes it takes longer than 2s for yahoo to load, sometimes it takes less. Is there a way to make it something like this:

```
if (current second) minus x is greater than 1

    x = (current second)
    lynx -dump http://yahoo.com
    date

done
```

---

### Post by geirha on 2008-11-05
Something like this perhaps?
```

while true; do
    mark=`date +%s`
    lynx -dump ...
    while [ $(( `date +%s`-$mark )) -lt 2 ]; do sleep 0.5; done
done

```

---

### Post by ninja23 on 2008-11-05
> **geirha said:**
> Something like this perhaps?
```

while true; do
    mark=`date +%s`
    lynx -dump ...
    while [ $(( `date +%s`-$mark )) -lt 2 ]; do sleep 0.5; done
done

```

It gives me an error?

```
[ line 4/7 (57%), col 45/64 (70%), char 116/142 (81%) ]
```

---

### Post by reality1011 on 2008-11-05
> **ninja23 said:**
> I can't get it to work... Could it be written as 'if it has been 2 seconds' the 'if' ?

Thanks =)



```


cappetta@Linux-Box:/tmp$ cat tester
#!/bin/ksh

sec=`date +%S`

while [ 1 ]; do
    sec1=`date +%S`
    (( amt_slept = $sec - $sec1 ))

    if [[  $amt_slept -eq 2  ||  $amt_slept -eq -2  ]]; then
        echo "slept 2 seconds $sec1 $sec"
        sec=`date +%S`
    fi

done
cappetta@Linux-Box:/tmp$ ./tester
slept 2 seconds 29 27
slept 2 seconds 31 29
slept 2 seconds 33 31
slept 2 seconds 35 33


```

---

### Post by sujoy on 2008-11-05
no one said anything about the watch command?

" watch - execute a program periodically, showing output fullscreen

watch runs command repeatedly, displaying its output (the first screenfull).  This allows you to watch  the  program  output
       change over time.  By default, the program is run every 2 seconds; use -n or --interval to specify a different interval."

from the manpage

---

### Post by ninja23 on 2008-11-06
reality, I can not get your script to work either. I do not have ksh, and the att link for it is broken. Please post again without using ksh?

sujoy, I have no idea what you are talking about, can you please use it in code.

reality did PERFECT, if only I had ksh, or it was available!

---

### Post by raf_kig on 2008-11-06
Could you maybe explain (as precise as possible) what exactly you are trying to achieve? Probably there are some ways to do this more easily using a different approach.

Regards

raf

---

### Post by sujoy on 2008-11-06
> **ninja23 said:**
> 
sujoy, I have no idea what you are talking about, can you please use it in code.

there is this "watch" command/program that runs a program/scripts after each specific time period. 
[http://linux.about.com/library/cmd/blcmdl1_watch.htm]("http://linux.about.com/library/cmd/blcmdl1_watch.htm")

---

### Post by reality1011 on 2008-11-06
> **ninja23 said:**
> reality, I can not get your script to work either. I do not have ksh, and the att link for it is broken. Please post again without using ksh?

sujoy, I have no idea what you are talking about, can you please use it in code.

reality did PERFECT, if only I had ksh, or it was available!


Ninja, 

ksh is a great shell.  I am not sure why you need this but I am starting to feel like it is for hw.  If you really need this functionality then you need to convert it to another shell.  I don't mind helping out but at the same time I am not going to hold your hand through every step. This is a very basic script.


> **sujoy said:**
> there is this "watch" command/program that runs a program/scripts after each specific time period. 
[http://linux.about.com/library/cmd/blcmdl1_watch.htm]("http://linux.about.com/library/cmd/blcmdl1_watch.htm")

I couldn't recall what command was just like sleep.  I would imagine that you could even use watch to execute a full function.  very useful indeed.

---

### Post by slavik on 2008-11-06
use google, there are good shell scripting guides out there.

---

