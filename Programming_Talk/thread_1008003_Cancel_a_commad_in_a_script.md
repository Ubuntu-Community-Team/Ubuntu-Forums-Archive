---
title: "Cancel a commad in a script"
date: 2008-12-11
forum: Programming Talk
---

### Post by b-boy on 2008-12-11
Hi

Is there a way to Cancel a command in a running script without ending the script itself?

---

### Post by tdrusk on 2008-12-11
> **b-boy said:**
> Hi

Is there a way to Cancel a command in a running script without ending the script itself?
I am not very experienced in scripting, but you could ask a question before you execute that part, then throw in an if statement for that command.

---

### Post by davidbilla on 2008-12-11
> Is there a way to Cancel a command in a running script without ending the script itself?


If the command is already running, you can check for the process id (pid) of the command and kill it.

You can do something like this.

```
procid=`ps -C <prg-name> -o pid=`
if test -z $procid
then
#Process not running
else
kill -9 $procid

```
To do that outside the script
```

$ procid=`ps -C <prg-name> -o pid=`
$ kill -9 $procid

```

---

### Post by b-boy on 2008-12-11
> **tdrusk said:**
> I am not very experienced in scripting, but you could ask a question before you execute that part, then throw in an if statement for that command.

I dont think that will work

let me give more info 

my script has a for loop with once command inside so when the command is executed ok it goes to  the next one but if there is a problem it just hangs as it is waiting for a response no when this happens i just want to cancel this command and let the loop go to the next command

---

### Post by dwhitney67 on 2008-12-11
If you have a script that hangs, then perhaps you should focus your attention on that script so that your second script would not need a workaround.

The suggestion offered by davidbilla would work, however it does not solve the root of the problem that you are having.

Also, using a '.' to terminate a sentence is golden.  You should consider using it sometimes!

---

### Post by b-boy on 2008-12-12
> **dwhitney67 said:**
> If you have a script that hangs, then perhaps you should focus your attention on that script so that your second script would not need a workaround.

The suggestion offered by davidbilla would work, however it does not solve the root of the problem that you are having.

Also, using a '.' to terminate a sentence is golden.  You should consider using it sometimes!

ok i will try

---

