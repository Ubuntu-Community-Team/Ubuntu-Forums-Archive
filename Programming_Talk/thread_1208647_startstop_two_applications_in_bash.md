---
title: "start/stop two applications in bash"
date: 2009-07-09
forum: Programming Talk
---

### Post by MadsRH on 2009-07-09
Hi
Can anyone tell me how I can launch two applications (CoverGloobus and Banshee) with one scrip (this already works) and quit both when I quit Banshee?

This is my current file:
```
#!/bin/bash
# My first script

/home/mads/.CoverGloobus/CoverGloobus.py &
banshee-1 --redirect-log --play-enqueued %U


```

I'm very much a newbie regarding both Linux and coding, so please don't write too geeky replies ;-)



Thanks for reading

---

### Post by stroyan on 2009-07-09
When bash starts a process in the background the PID is available as $!.
You can remember that PID in a shell variable and then use kill to stop it.
Using kill without options sends the default signal SIGTERM.
That is probably what you want for this situation.
```
#!/bin/bash
# My first script

/home/mads/.CoverGloobus/CoverGloobus.py &
CoverGloobusPID=$!
banshee-1 --redirect-log --play-enqueued %U
kill $CoverGloobusPID

```

---

### Post by MadCow108 on 2009-07-09
add that to a text file and make it executable with chmod u+x file
```

#!/bin/bash
/home/mads/.CoverGloobus/CoverGloobus.py &
COVERPID=$!
banshee-1 --redirect-log --play-enqueued %U &
BANSHEEPID=$!
wait $BANSHEEPID
kill $COVERPID

```
edit: fixed error

---

### Post by MadsRH on 2009-07-09
**stroyan** and **MadCow108** thanks for the fast reply.

I have no idea why, but only **stroyan**'s code seems to work.

Thanks to both of you for helping :-)

---

### Post by smartbei on 2009-07-09
It's probably because of "kill $CONKYPID". It should be "kill $COVERPID".

@MadCow108: I don't think the wait is necessary, after all it will only return when banshee closes, which is the same thing as wait.

---

### Post by MadCow108 on 2009-07-09
> **smartbei said:**
> It's probably because of "kill $CONKYPID". It should be "kill $COVERPID".

@MadCow108: I don't think the wait is necessary, after all it will only return when banshee closes, which is the same thing as wait.

fixed the copy past error.
yes the wait is unecessary in this case.
But you need it if you want to do something after banshee has started

---

### Post by joey-elijah on 2009-07-11
Hey y'all. 

could i substitute Banshee for Rhythmbox and get it to work fine?

---

### Post by maslic68 on 2010-04-11
this doesn't work for me. Is it possible it's because i run CvoerGloobus simply by "covergoobus" command?

EDIT: Oh, yeah... maybe I should've googled a little more BEFOR i aked the question

anyway this works with the package install of CoverGloobus:

```
#!/bin/bash
python /usr/share/covergloobus/covergloobus.py &
COVERPID=$!
banshee-1 --redirect-log --play-enqueued %U &
BANSHEEPID=$!
wait $BANSHEEPID
kill $COVERPID
```

---

### Post by Cracauer on 2010-04-11
You should put this into an EXIT trap handler. That way it will always be executed when the shell exits. Namely, if you control-C or kill -TERM this script you will have the cleanup happen anyway. If you code it straight, then aborting the script will not run your cleanup.

```

#! /bin/sh

onexit ()
{
	if [ -n "$diediedie" ] ; then
		echo killing background $diediedie # race condition
		kill "$diediedie"
	fi
}
trap onexit EXIT

sleep 5 &
diediedie=$! # race condition
sleep 3
echo ended forground

```

Note that the thing is full of race conditions which could be tightened up somewhat but not entirely in bourne shell.

---

### Post by tiznom on 2010-09-30
Total noob question here, but I'll ask anyway.

What exactly do I do with the above script to apply it? To have it begin functioning, and opening & closing CoverGloobus whenever I open & close Banshee? I read the beginner's guide to Bash[ here]("https://help.ubuntu.com/community/Beginners/BashScripting") [help.ubuntu.com] but I don't see how to get it to begin working. I'm okay with making it executable, copying it, etc. I just don't know where to put the script, or how to activate this functionality. Thanks in advance...

---

