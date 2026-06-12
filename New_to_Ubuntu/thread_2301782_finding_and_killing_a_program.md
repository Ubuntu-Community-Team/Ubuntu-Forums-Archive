---
title: "finding and killing a program"
date: 2015-11-05
forum: New to Ubuntu
---

### Post by c1529g on 2015-11-05
I installed the latest updates for the OS and Firefox started crashing. When i tried to restart firefox i was informed that it was already running and needed to be closed first. So after some searching i found a tutorial which showed how to find the PID of a program using ```
 pidof firefox 
``` only that didn't show nothing. So i used ```
 ps ax | grep firefox 
``` and this showed the following:

```

c1529g@my-ubuntu-mate-15:~$ ps ax | grep firefox
 3520 ?        Sl     0:54 /usr/lib/firefox/firefox
 3614 pts/1    S+     0:00 grep --color=auto firefox
c1529g@my-ubuntu-mate-15:~$

```

Could someone tell this old fool what is the PID number. Is it either 3520 or 3614?
And how i might kill the program

Thanks

---

### Post by howefield on 2015-11-05
In your terminal..

```
kill 3520
```

should do it.

---

### Post by Lars Noodén on 2015-11-05
It is 3520 as howefield says. 

If you look you can see that 3614 is the grep you are using to look for Firefox's process.  One way around that is to use a pattern with grep rather than a plain string:

```

 ps ax | grep [f]irefox

```

It means look for any letter in the set of 'f' that is followed immediately by the string 'irefox'

Or you could just use [pkill](http://manpages.ubuntu.com/manpages/trusty/en/man1/pkill.1.html)

```

pkill -x firefox

```

---

### Post by vasa1 on 2015-11-05
There's also **pgrep**:```
03:28 PM ~ $ pgrep dropbox
1607
03:30 PM ~ $ pgrep -f dropbox
1607
03:30 PM ~ $ pgrep -l dropbox
1607 dropbox
03:30 PM ~ $ pgrep -a dropbox
1607 /home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-3.10.7/dropbox
03:30 PM ~ $ 
```and you can follow that up with **pkill** as Lars pointed out.

---

### Post by c1529g on 2015-11-05
Great big thank you to each of you for all the help and advice.

---

### Post by leunam12 on 2015-11-06
I usually do ```
ps -eo pid,cmd | grep firefox
``` then kill followed by the pid number

---

### Post by HermanAB on 2015-11-06
or you can use 'htop'.

---

