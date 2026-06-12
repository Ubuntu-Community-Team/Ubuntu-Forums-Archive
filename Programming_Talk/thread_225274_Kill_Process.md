---
title: "Kill Process"
date: 2006-07-29
forum: Programming Talk
---

### Post by cosmo1983 on 2006-07-29
Hi,

How would I kill a process from with bash? Do I always need to end the process using PID? I have tried "Killall Firefox" and it doesn't seem to work, is there way to read the current processes from within bash?

---

### Post by Swab on 2006-07-29
killall firefox-bin

---

### Post by Swab on 2006-07-29
"ps -e" will show you running processes.

---

### Post by cosmo1983 on 2006-07-29
Awesome, thanks.

---

### Post by gruepig on 2006-07-29
Also try pkill, which is a bit cleaner than parsing the output of ps yourself.

---

### Post by manqueller on 2009-04-03
Isn't there a command that you can type in the terminal that will turn the cursor into a skull and cross bones, and then you can kill any application by clicking on it with that?

I forget what that one is.

---

### Post by johnl on 2009-04-03
The command you're thinking of is 'xkill'.

Generally I do something like this:

```

kill -TERM `pidof firefox`

```

---

### Post by spupy on 2009-04-03
Some additional info regarding the topic. The purpose of the **kill** command is to send signals to a process. The default signal sent is 15 - SIGTERM - termination signal. 9 (SIGKILL) is a more hard and sure way to kill a process - a process can ignore sigterm, but sigkill is the "finger of death". There are several more signals: [http://linux.die.net/man/7/signal](http://linux.die.net/man/7/signal)

Two signals I find interesting are SIGSTOP and SIGCONT. With sigstop you can "freeze" a process. Use sigcont to unfreeze it. Beware that this can lead to problems, for example with files used by the frozen process.

---

### Post by credobyte on 2009-06-22
Take a look at this reply : [http://ubuntuforums.org/showpost.php?p=7008718&postcount=8](http://ubuntuforums.org/showpost.php?p=7008718&postcount=8)

---

### Post by simeon87 on 2009-06-22
> **credobyte said:**
> Take a look at this reply : [http://ubuntuforums.org/showpost.php?p=7008718&postcount=8](http://ubuntuforums.org/showpost.php?p=7008718&postcount=8)

Yes, it's one post above your post in this thread..?

---

### Post by credobyte on 2009-06-22
> **simeon87 said:**
> Yes, it's one post above your post in this thread..?

Sorry, something have been messed up with my clipboard - I was trying to copy something else, not this one ( in my previous reply ).
Anyway, here's the link : [http://ubuntuforums.org/showpost.php?p=2846394&postcount=6](http://ubuntuforums.org/showpost.php?p=2846394&postcount=6)

---

### Post by soltanis on 2009-06-22
T OP, use killall, or if that isn't working, use pkill, or if that isn't working, use this command (never fails me):

```

ps -e | grep <name> | awk "{ print $1; }" | xargs kill -9

```

---

### Post by therendus on 2009-10-25
What if the process in question doesn't respond to anything.

I have a nautilus process halted on a dnd operation.
sys monitor says it's in running state (and consuming 100 % of two cpu cores)

I tried all signals on it from 1 to 30 with root permissions.
To no effect at all !!

---

### Post by anand2308 on 2012-08-27
> **manqueller said:**
> Isn't there a command that you can type in the terminal that will turn the cursor into a skull and cross bones, and then you can kill any application by clicking on it with that?

I forget what that one is.


it is xkill

---

### Post by nothingspecial on 2012-08-27
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

