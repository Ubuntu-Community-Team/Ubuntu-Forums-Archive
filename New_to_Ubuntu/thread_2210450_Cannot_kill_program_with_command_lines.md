---
title: "Cannot kill program with command lines"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-03-10
Sometimes a program stops responding but I can't kill it on the the terminal with either killall foo or kill pid. But open the system monitor and click "kill process" always works. I am wondering what is the command used by system monitor.

---

### Post by DogMatix on 2014-03-10
Have you tried

```
pkill foo
```

---

### Post by monkeybrain20122 on 2014-03-10
No, will see if that works if this happens next time. Since it happens rarely I don't know when it will be. :)

---

### Post by 3rdalbum on 2014-03-11
The default setting for 'kill' merely tells the program that it would be nice if it could please shut down. If the program is completely hung up, the normal kill won't do anything.

There are different levels of kill but most of them rely on the program listening for the signal and reacting. The only sure-fire way to absolutely kill a program that is not responding is:

> kill -9 <pid>

With the -9 option, kill actually tells the kernel to "end this program NOW", which always works. Obviously the program won't ask you if you want to save open documents, finish writing config files or complete a printing operation, so only use it when you have to.

---

### Post by tgalati4 on 2014-03-11
I think the default settings for the previous methods tried by the OP are -15, which is the Terminate signal.  This works in most cases when the program is still running and not in a "crashed" state.  "Terminate" is good to use because any open files get closed properly.  -9 (Kill with prejudice) signal is effective, but you do run the risk of unfinished business.

From the *killall* man page:

> DESCRIPTION
       killall sends a signal to all processes running any of the specified commands. If no signal name is specified, SIGTERM is sent.

SIGTERM is flag -15, which is the polite termination flag.

From the *kill* man page:

> DESCRIPTION
       The default signal for kill is TERM.

TERM is another name for the polite termination signal (-15).

To see the process flags available, try killing a process with *htop*:

```
sudo apt-get install htop
```

---

### Post by OrangeCrate on 2014-03-11
> **monkeybrain20122 said:**
> Sometimes a program stops responding but I can't kill it on the the terminal with either killall foo or kill pid. But open the system monitor and click "kill process" always works. I am wondering what is the command used by system monitor.

For that it's worth, I've always used:

```
xkill
```

which turns the cursor into an "X", which, if you click on the misbehaving program, instantly shuts it down. It's never failed me, that I can remember.

---

### Post by raja.genupula on 2014-03-11
> **3rdalbum said:**
> The default setting for 'kill' merely tells the program that it would be nice if it could please shut down. If the program is completely hung up, the normal kill won't do anything.

There are different levels of kill but most of them rely on the program listening for the signal and reacting. The only sure-fire way to absolutely kill a program that is not responding is:



With the -9 option, kill actually tells the kernel to "end this program NOW", which always works. Obviously the program won't ask you if you want to save open documents, finish writing config files or complete a printing operation, so only use it when you have to.


+1 to kill -9

---

### Post by monkeybrain20122 on 2014-03-11
Thanks for all the reponses. I think I get the explanation  now so I will mark this thread as solved.

---

### Post by whitesmith on 2014-03-11
> **monkeybrain20122 said:**
> Sometimes a program stops responding but I can't kill it on the the terminal with either killall foo or kill pid. But open the system monitor and click "kill process" always works. I am wondering what is the command used by system monitor.One possible approach is to open a terminal (Ctrl-Alt-T) and enter```
top
```Then find the pid (xyz) of the process you want to kill. Now, remaining in top, enter```
k xyz
```Top always works for me. Of course, this isn't exactly the solution you were seeking.

---

