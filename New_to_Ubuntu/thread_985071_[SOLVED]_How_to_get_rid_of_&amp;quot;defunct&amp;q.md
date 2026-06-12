---
title: "[SOLVED] How to get rid of &amp;quot;defunct&amp;quot; processes?"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Blofeld on 2008-11-17
Hi, Abiword always leaves behind several processes which are marked "defunct" (I detect those by running the *ps -e | grep abi* command), and which can't be killed with the *kill* command.

How do I get rid of those processes? 

And what exactly does "defunct" mean in this context -- are those processes still using up system resources?

Thanks.

---

### Post by redseventyseven on 2008-11-17
Have you used "killall" instead of kill?

e.g.:
```
killall defunct
```

---

### Post by Keith Hedger on 2008-11-17
> killall defunct
will try to kill all processes NAMED defunct not marked as defunct!
does ```
sudo kill -9 PROCNUM
``` not work? (where PROCNUM is the process number)

---

### Post by scorp123 on 2008-11-17
> **Blofeld said:**
>  And what exactly does "defunct" mean in this context  "defunct" processes are 'dead' programs. Something crashed them somehow and now they're hanging forever. Hard to tell why and how this happens; usually it happens if programs are (still too) buggy (e.g. bleeding-edge "Beta" software) and not (yet) properly written and/or tested. In UNIX lingo you might also hear the term "zombie processes" which is quite a good description IMHO :D ... the process is dead, and yet it's still walking around your system's memory .... :D

> **Blofeld said:**
>  are those processes still using up system resources? That depends. Usually they shouldn't. They're dead, so they shouldn't be doing anything anymore except for being in a "zombie" state where they still show up in the process tables. They're more of a cosmetic annoyance and different than the zombies in horror movies no real threat, e.g. they usually can't "bite" other processes in any way and turn them into process-zombies too. But processes that are somehow related and connected to each other can make each other crash, e.g. if one process dies and the other process is waiting forever for something to happen then it can happen that the one process that died turns the other process into a "zombie". Typical example is Firefox, e.g. when you try to play a video on YouTube and the Flash player component all of a sudden decides to die it will likely crash Firefox too .... or leave it in an "undead" state which will force you to kill it manually.

**_How to get rid of them:_**

Check your process table, e.g. with this command:
```
ps -efH
``` .... this will give you your running processes in a tree-like fashion, eg. you will see which process spawned which other processes. Sometimes if a process goes "defunct" and it simply refuses to die it might help to kill the parent process that spawned it too. If an ordinary "**kill *processnumber***" command does not work, you might try the "no more asking nicely method" with "**kill -9 *processnumber***" ... The difference here being that an ordinary **"kill"** tries to "talk" to the process and asks it nicely to quit gracefully and cleanly whereas a **"kill -9"** doesn't bother to ask, it tells the OS kernel to get rid of that process no matter what.

Other related programs you might want to try:
[LIST]
[*]killall
[*]pkill
[/LIST] ... I especially like **"pkill"** because it is able to work with patterns and not just precise names. So this command ...
```
pkill 'firefox*'
``` should go and kill everything that starts with "firefox*..." in its name, e.g. "firefox-bin", "firefox-2", "firefox-3.0.3" and whatever other names the binary in question might have.

---

### Post by psusi on 2008-11-17
Yes, a defunct zombie process is just hanging around waiting for the parent process to read its exit status, so you want to kill the parent if it is hung and not reaping its children.

---

### Post by Blofeld on 2008-11-18
Thanks to all for your very helpful comments.
Of course, now since I've asked, there are suddenly no more "defunct" / zombie processes.  But when they should once more raise their ugly heads, I'll stone cold "kill -9" the bastards.

---

### Post by scorp123 on 2008-11-18
Please mark this thread as being "SOLVED" ;)

---

### Post by Blofeld on 2008-11-18
@scorp:  Done, thanks for the hint.

---

