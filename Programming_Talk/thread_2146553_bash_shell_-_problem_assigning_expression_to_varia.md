---
title: "bash shell - problem assigning expression to variable"
date: 2013-05-18
forum: Programming Talk
---

### Post by stou on 2013-05-18
Hi guys

I am having some troubles to get my bash script working. Process assigned to that script stop as soon as I start it. 
After some tests, I identify that something wrong is happening into following lines :
```
 USR=$(top -d1 -n2 | grep 'Cpu(s)' | tail -1 | sed -e 's/\s\+/ /g' | cut -d' ' -f 2 | cut -d'%' -f 1 | cut -d'.' -f 1)
 SYS=$(top -d1 -n2 | grep 'Cpu(s)' | tail -1 | sed -e 's/\s\+/ /g' | cut -d' ' -f 3 | cut -d'%' -f 1 | cut -d'.' -f 1)


 ALL=$(($USR+$SYS))
 echo $ALL | tr '[ \n]' '-' >> stat.log

```

I try to assign to variables USR and SYS some expressions. I think that my syntax is correct but at the end it is not working. 

It tried that way too :
```
 USR=`top -d1 -n2 | grep 'Cpu(s)' | tail -1 | sed -e 's/\s\+/ /g' | cut -d' ' -f 2 | cut -d'%' -f 1 | cut -d'.' -f 1`
 SYS=`top -d1 -n2 | grep 'Cpu(s)' | tail -1 | sed -e 's/\s\+/ /g' | cut -d' ' -f 3 | cut -d'%' -f 1 | cut -d'.' -f 1`

```

But result is the same.

Does somebody have an idea what I am doing wrong here? :confused:
I suspect an issue with some wrong quotes used but after some search I don't find any solution...



**UPDATE 19/05 :** 
The script is basically running when I start it on the current thread :
```
 
stou@laptop:~/$ sh read_stats.sh 

```
But my problem is when I start it on another thread to let it work in background. It stops as soon as I tip another command (or just press ENTER) in shell :
```
 
stou@laptop:~/$ sh read_stats.sh &
[1] 4473
stou@laptop:~/$
[1]+  Stopped          sh read_stats.sh
stou@laptop:~/$

```

---

### Post by cortman on 2013-05-18
One problem you have is with using the variable $USER. That it is a system reserved variable, for printing the name of the current (you guessed it) user. Rename the variable $USR or something else.
Might be a good idea to check with printenv to make sure you're not trying to overwrite any environment variables.

---

### Post by stou on 2013-05-19
Hi cortman,

Thanks for your tip O:)
It's kind of a stupid issue... So I changed USER variable to USR (and checked with printenv for other potentially reserved variable names I maybe override).  

Unfortunately the result is the same with this new variable name...

Does anyone has another idea?

(I updated my initial message as I got some others informations during my tests)

---

### Post by steeldriver on 2013-05-19
It's difficult to tell from just the fragment you provided, but I think the problem is possibly not the variable assignment, but that 'top' doesn't like running without an interactive shell e.g.

```
$ top > top.out &
[3] 16383
$ 

[COLOR=#ff0000][3]+  Stopped                 top > top.out[/COLOR]
$ kill 16383 
$ ls -l top.out
-rw-rw-r-- 1 steeldriver steeldriver [COLOR=#ff0000]**0**[/COLOR] May 19 07:30 top.out

```

You can try giving the -b (batch mode) flag to top e.g.
```

$ top **[COLOR=#0000ff]-b[/COLOR]** > top.out &
[4] 16391
$ 
$ kill 16391
$ 
[4]-  Exit 143                top -b > top.out
$ ls -l top.out
-rw-rw-r-- 1 steeldriver steeldriver [COLOR=#0000ff]**62071**[/COLOR] May 19 07:32 top.out
$ 

```

---

### Post by prodigy_ on 2013-05-19
> **stou said:**
> ```
 USR=$(top -d1 -n2 | grep 'Cpu(s)' | tail -1 | sed -e 's/\s\+/ /g' | cut -d' ' -f 2 | cut -d'%' -f 1 | cut -d'.' -f 1)
 SYS=$(top -d1 -n2 | grep 'Cpu(s)' | tail -1 | sed -e 's/\s\+/ /g' | cut -d' ' -f 3 | cut -d'%' -f 1 | cut -d'.' -f 1)
 ALL=$(($USR+$SYS))
```

^ Are you trying to get the integer part of **us** and **sy** here? Well, how about: ```
cpu_usage=$(top -d1 -n2 | grep 'Cpu(s)' | tail -1)
cpu_sys_usr=$(echo ${cpu_usage#* } | awk -F'[,. ]' '{ print $1, "+", $4 }')
cpu_all=$(expr $cpu_sys_usr)
``` then?

Re. your script as a whole, I have a gut feeling that you're trying to reinvent **nice** or **time**. And you probably shouldn't do that. :)

---

### Post by schragge on 2013-05-19
> **stou said:**
> ```

SYS=$(top -d1 -n2 | grep 'Cpu(s)' | tail -1 | sed -e 's/\s\+/ /g' | cut -d' ' -f [COLOR=red]3[/COLOR] | cut -d'%' -f 1 | cut -d'.' -f 1)

```
The [COLOR=#FF0000]3[/COLOR] there most probably should be [COLOR=#FF0000]4[/COLOR].

But I'd rather parse the output of [vmstat]("http://manpages.ubuntu.com/manpages/raring/en/man8/vmstat.8.html")
```
cpu_all=$(vmstat 1 2|awk 'NR>3{print $13+$14}')
```

---

### Post by Vaphell on 2013-05-19
as for all-caps names - simply don't use them. There is a boatload of env variables that are all-caps by convention. I've seen someone override PATH, long story short the results were not pretty (all commands stopped to work because shell couldn't locate them anymore). Have at least 1 lowercase char and you won't risk overriding them ever again.

---

### Post by cortman on 2013-05-19
It is also often useful to run a script in debugging mode, with the -x option.

---

### Post by stou on 2013-05-20
Hi guys

Thanks a lot for your answers!
My original problem here was what @steeldriver pointed out : I used *top* command not in batch mode.
Then I tried with -d option. It is working but it seems not very proper in my case as I want to launch a shell script and let it run for a long period (logging some statistics over cpu, memory and network use). *Top* outputs seems not very stable to parse. 

I will rather use the *vmstat* command outputs like @schragge advised. I didn't know that command ;-)

Unfortunately to run the script in debugging mode was not useful in my case because that was not a syntax or logic problem but an execution issue (*top* not working normally when I started the script in background). Is it possible to start a background process in debugging mode?

@Vaphell I am already following your advice -> no more all-caps variable names in my shell scripts!

You can turn that thread as solved, thanks guys! 8-)

---

