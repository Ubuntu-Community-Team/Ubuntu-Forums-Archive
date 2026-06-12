---
title: "Altering the Control-C behaviour in bash scripts??"
date: 2007-01-11
forum: Programming Talk
---

### Post by ssalman on 2007-01-11
Hi,
  I'm running a time/CPU consuming/intensive set of programs in series using a bash script. Some may not finish at all!! and I would like to hit control-C and stop that one program and move on to the next after few hours/days, how can I do that in bash scripting? Alternatively (really a better option) I would like to set a time limit for each program after which it will stop and move to the next... currently I don't have control over the run time of each program.

Thanks in advance.

---

### Post by ghostdog74 on 2007-01-11
you could use [traps]("http://tille.xalasys.com/training/bash/ch12.html")?

---

### Post by ssalman on 2007-01-11
> **ghostdog74 said:**
> you could use [traps]("http://tille.xalasys.com/training/bash/ch12.html")?

How would I trap the INT signal and then make it resume the next statement in the script?

---

### Post by supirman on 2007-01-11
a short example doing a trap on Ctrl-C.

```

#!/bin/bash
trap 'echo Control-C trap caught; exit 1' 2 #traps Ctrl-C (signal 2)

while true
do
  echo infinite loop
  sleep 2
done

```

Perhaps you could put a custom function call in the trap handler to keep track of which task you're currently on, and which to go to next...

---

### Post by ssalman on 2007-01-11
> **supirman said:**
> a short example doing a trap on Ctrl-C.

```

#!/bin/bash
trap 'echo Control-C trap caught; exit 1' 2 #traps Ctrl-C (signal 2)

while true
do
  echo infinite loop
  sleep 2
done

```Perhaps you could put a custom function call in the trap handler to keep track of which task you're currently on, and which to go to next...



Thanks for posting the sample code, but the above code will exit as soon as I press Control-C, the behavior I'm looking for is to break out of the command (sleep in this case) but continue with the bash script (the loop in this case). is that possible?

Alternatively, can I set an upper limit for a command to run after which it will be terminated if it did not finish earlier.

Thanks for all the help.

---

### Post by haelters on 2007-12-11
I know it a late answer, but you might be interessed in ulimit...

Manfred

---

