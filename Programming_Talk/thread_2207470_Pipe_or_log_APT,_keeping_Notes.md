---
title: "Pipe or log APT, keeping Notes"
date: 2014-02-23
forum: Programming Talk
---

### Post by wolfgentleman on 2014-02-23
I am making a script that installs a dynamic list of packages and I need to know if a package is 'redirected' to another packages such as rpm-dbg -> librpm-dbg. The way I was going to do that was as follows:

```
apt-get --no-install-recommends --no-remove -y --simulate install $file >ptmp 2>&1
if [[ `cat ptmp` == *Note,\ selecting ]]
then
    file=`cat ptmp|grep Note,|awk -F\' '{ print $2; }'`
fi
```

However I found out that by using '>' to dump the output into a file it acts like it had -q passed to it. I also tried '&>' and '|cat>' with the same results. So what I am I missing/doing wrong?

BTW: I posted this question on [askubuntu.com 3 days ago]("http://askubuntu.com/questions/423443/pipe-or-log-apt-keeping-notes") with no response, so I was hoping that I might get an answer, or even a response in general, to my question here.

---

### Post by steeldriver on 2014-02-23
Are you sure the behaviour of > is the problem? it's hard to see how 

```
if [[ `cat ptmp` == *Note,\ selecting ]]
```

can possibly work. Can you explain a bit more exactly what you are trying to do?

---

### Post by wolfgentleman on 2014-02-23
> **steeldriver said:**
> Are you sure the behaviour of > is the problem?
Here is what I have tried (using rpm-dbg as example):

```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get --no-install-recommends --no-remove -y --simulate install rpm-dbg[/FONT][/COLOR]
```
Shows "Note, selecting 'librpm-dbg' instead of 'rpm-dbg'" in the output
```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get --no-install-recommends --no-remove -y --simulate install rpm-dbg|grep -i "notes,"[/FONT][/COLOR]
```
Doesn't show output at all
```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get --no-install-recommends --no-remove -y --simulate install rpm-dbg|cat[/FONT][/COLOR]
```
Doesn't show the "notes"
```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get --no-install-recommends --no-remove -y --simulate install rpm-dbg&[/FONT][/COLOR]
```
Shows output, but not the "notes"
```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get --no-install-recommends --no-remove -y --simulate install rpm-dbg>ptmp;cat ptmp[/FONT][/COLOR]
```
Doesn't show the "notes"
```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get --no-install-recommends --no-remove -y --simulate install rpm-dbg&>ptmp;cat ptmp[/FONT][/COLOR]
```
Doesn't show the "notes"
```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get --no-install-recommends --no-remove -y --simulate install rpm-dbg&>ptmp[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] 2>&1[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono];cat ptmp[/FONT][/COLOR]
```
Doesn't show the "notes"

Which leads me to think that anything that causes apt to be in the background or async essentially passes the -q option.

> **steeldriver said:**
> Can you explain a bit more exactly what you are trying to do?
I am trying to make a script that looks for, installs, marks as auto, and generates a meta package for the *-dbg packages based on your currently installed packages. I can't post what I have so far, as I am booted into Windows ATM, but I will post it by tomorrow if it is needed.

P.S.: I hadn't realized that I forgot an * in my if statement it should be:
```
[COLOR=#000000][FONT=Ubuntu Mono]if [[ `cat ptmp` == *Note,\ selecting* ]]
```[/FONT][/COLOR]

---

### Post by steeldriver on 2014-02-23
Try adding an explicit -q=0

```
$ apt-get --no-install-recommends --no-remove -y --simulate **-q=0** install rpm-dbg 2>&1 | grep 'Note'
Note, selecting 'librpm-dbg' instead of 'rpm-dbg'

```

---

### Post by wolfgentleman on 2014-02-24
> **steeldriver said:**
> Try adding an explicit -q=0

```
$ apt-get --no-install-recommends --no-remove -y --simulate **-q=0** install rpm-dbg 2>&1 | grep 'Note'
Note, selecting 'librpm-dbg' instead of 'rpm-dbg'

```
Just got a chance to test it and it worked magnificently! Thank you so much!

---

### Post by steeldriver on 2014-02-24
Glad to help - tbh it was a lucky guess!

---

