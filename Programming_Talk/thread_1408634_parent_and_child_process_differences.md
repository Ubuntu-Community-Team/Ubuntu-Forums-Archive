---
title: "parent and child process differences"
date: 2010-02-16
forum: Programming Talk
---

### Post by Mahngiel on 2010-02-16
Reading Mendel Cooper's "Advanced Bash-Scripting Guide" I came across something that may be my problem.

> A script can export variables only to child processes, that is, only to commands or
processes which that particular script initiates. A script invoked from the
command-line cannot export variables back to the command-line environment.
Child processes cannot export variables back to the parent processes that spawned
them.
What prompted my reading into this is my attempt at implementing piped output of 'top' and 'free'.  While with 'free' I am successful in defining the regex inside a variable, and depending on situations, outputting an image. (yes, inside conky)

However, with 'top' i had to run a batch (-b) tag behind the grep pipe, and although the variable i assigned it to will indeed return a digit, I have been unsuccessful in calling even text when that digit meets certain target points.


So, it leads me to be curious if 'top' and 'free' are different in a way that such different measures are taken.  Thanks for any input you have in this topic.

FYI: my pipes are as follows
```
totalram=$(free | grep "Mem:" | awk '{print $2}')
usedram=$(free | grep "Mem:" | awk '{print $3}')
ram=$[ 100 * $usedram / $totalram ]
``````
cpu=$(top -b|grep -m1 'Cpu(s):'|awk '{print $2}'|grep -m1 -o '[0-9]\.[0-9]')
```

---

### Post by pbrane on 2010-02-16
I think the difference is that **free** runs once and outputs information while **top** will normally run continuously. I tried your code on the command line, I'm not sure that that last *grep* is for. Got some funny output. I got the user CPU time when I dropped that last *grep*. I also added the *-n 1* option to have *top* only run one iteration. and Dropped the *-b* option.
```

top -n 1 | grep -m1 'Cpu(s):' | awk '{print $2}'

```

---

### Post by Mahngiel on 2010-02-16
Thanks for the reply.  I'll have a go at this when I get home and let you know.
 
With that last *grep* I was able to pull the cpu % used in it's decimal form, versus only getting the digits parsed.

---

### Post by Mahngiel on 2010-02-17
You questioned the third pipe before...

Your pipe:
mahngiel@studio:~$ top -n 1 | grep -m1 'Cpu(s):' | awk '{print $2}'
[COLOR=Red]1.2%us,[/COLOR] 

The second grep drops the "&us,":
mahngiel@studio:~$ top | grep -m1 'Cpu(s):'|awk '{print $2}'|grep -m1 -o '[0-9]\.[0-9]'
[COLOR=Red]1.2[/COLOR]

Thank you though.  I spent about 2 minutes thinking about this as I was replying again, and realized I was approaching this all wrong.  I don't even need the decimal point!

mahngiel@studio:~$ top | grep -m1 'Cpu(s):'|awk '{print $2}'|cut -c1
[COLOR=Red]1[/COLOR]

Drop the decimal, and viola!  You know, through the manuals i've read these past 3 months on how to bash, I've read repeatedly that BaSH doesn't like decimals.  The sooner you learn to fudge them by either multiplying the variable by exp's of 10, or in this case, cut them completely, the easier your scripting days will be.

Thanks all.

---

### Post by Mahngiel on 2010-02-21
So a thought came to me this afternoon.  Regarding the post above this, I used a cut pipe to grab the first number.  The point was to drop the decimal, which IS what happens, but if that number reaches above 9.9, I will only pipe out the first digit.

Ex: 10 will still only be 1, and 25 only 2 due to the cut.  

Is there a better way to cut out the decimal in a live event where the number is constantly changing?

---

### Post by Mahngiel on 2010-02-22
bumpity pls

---

### Post by Mahngiel on 2010-02-23
Bump again.  

There's got to be a way to cut a decimal out of a number that could be 1.4 at one time, and 15.4 at another.

---

