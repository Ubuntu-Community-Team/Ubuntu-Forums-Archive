---
title: "kill zombie process's"
date: 2007-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by kerry_s on 2007-09-25
just needed a place to put this script so i can find it easier, should i need to.
it kills zombie process's. :)

```

#!/bin/sh
 kill -HUP `ps -A -ostat,ppid,pid,cmd | grep -e '^[Zz]' | awk '{print $2}'` 

```

---

### Post by hyper_ch on 2007-09-30
It doesn't kill them all ;(

---

### Post by kerry_s on 2007-10-07
1

---

### Post by G4slight$ on 2008-05-07
Ubuntu 8.04 sucks!!! Way too CPU intensive --
and what the hell is a zombie shell doing on install?
BUSTED!!!!!
no real answers on this one - --

---

### Post by hyper_ch on 2008-05-08
G4:
I'm looking forward to your improved Ubuntu release/derivate

---

### Post by GhettoYhetti on 2011-05-31
> **kerry_s said:**
> just needed a place to put this script so i can find it easier, should i need to.
it kills zombie process's. :)

```

#!/bin/sh
 kill -HUP `ps -A -ostat,ppid,pid,cmd | grep -e '^[Zz]' | awk '{print $2}'` 

```
Nice . . . . maybe add a couple of echo statement so everyone can see how the scripts works.  Just a thought.

You never know when a script will harm rather than hurt.

---

### Post by kerry_s on 2011-06-01
> **GhettoYhetti said:**
> Nice . . . . maybe add a couple of echo statement so everyone can see how the scripts works.  Just a thought.

You never know when a script will harm rather than hurt.

you did notice the date? that was from way back 2007.
i don't really come across any zombie process's these days.

---

### Post by leonbravo on 2011-06-22
> **kerry_s said:**
> you did notice the date? that was from way back 2007.
i don't really come across any zombie process's these days.


Yes, it does. 
 Ubuntu 11.04 has reported at least 3  zombie processes.  Reported in here :
 [https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/753984](https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/753984)
and  [https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/739780](https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/739780)

---

### Post by leonbravo on 2011-06-22
It seems that the problem with the script is the column in which awk works (I think the only thing it's done with awk is print though)

Coming to my point you can first find the parent of the zombie process.  Like this :  

  ps -fe | grep defunct      

that will show you the zombie processes without the header: UID        PID  PPID  C STIME TTY          TIME CMD. So that the third column is the parent. 

Now you can check the children of the process with:   

ps -fe | awk '$3==2372 { print $0}'

Where 2372 was the parent of the zombie process, or change to column $2 to check the parent name. 

If you still decide to go on you will have to kill the parent.... (also  mix all the command in one line)

---

### Post by GhettoYhetti on 2011-07-09
Didn't mean to stir up trouble.  Yes I did notice the date.  I just make it a habit of placing echoes in scripts.  Especially anything that does kills, removing, etc.

I agree that zombies are a rare thing nowadays, but I came across 2 in 10.10 that I wanted to research different removal methods.

Again I meant nothing negative in my comment.  I actually used it.

---

