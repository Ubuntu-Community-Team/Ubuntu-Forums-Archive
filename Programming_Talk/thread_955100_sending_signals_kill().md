---
title: "sending signals: kill()"
date: 2008-10-21
forum: Programming Talk
---

### Post by techmarks on 2008-10-21
How do I send the kill signal to a program from within another program?

I understand I can do this


```
kill (pid, SIGINT);
```

But how do I get the pid for the program I want to kill from within the program I want to issue the signal from?

Thanks for any information.

---

### Post by slavik on 2008-10-21
If you are forking, then the fork return to the parent will have the pid of the child. if this is some other proccess.

But if you need it for some other program that you didn't fork, there are 2 ways. One would be to look for the programs pid file (a simple text file where the only content is the pid of the program, most daemons store this file somewhere). The second way would be to parse ps output (or to implement your own ps) and find out the PID that way. HINT: ps piped into grep can be very useful.

---

### Post by techmarks on 2008-10-21
> **slavik said:**
> If you are forking, then the fork return to the parent will have the pid of the child. if this is some other proccess.

But if you need it for some other program that you didn't fork, there are 2 ways. One would be to look for the programs pid file (a simple text file where the only content is the pid of the program, most daemons store this file somewhere). The second way would be to parse ps output (or to implement your own ps) and find out the PID that way. HINT: ps piped into grep can be very useful.

Thanks, yes the pid for a program I didn't fork.

I'll have to see if I find the programs pid file somewhere.
(I've no idea where this file could be)

I had a feeling it might involve parsing the ps output.

---

### Post by dwhitney67 on 2008-10-21
You can try playing/experimenting with "pidof".  You would need to know the full-path name of the program running.  For example:
```

pidof /sbin/init

```
This is the first process run by the system; the return PID should be 1.

Another alternative is to develop a script that launches both applications in succession.  The second application can be given the PID of the first via the command line.  Or, without the script, just do it manually:
```

secondApp `pidof /path/of/firstApp`

```

To determine the path of the application that is running (for use with 'pidof'), run a ps -ef and determine it via the output.


P.S.  You should avoid sending an application a 'kill -9' (or SIGKILL) signal if at all possible.  This signal cannot be caught, and hence the application being terminated cannot be stopped gracefully.  Consider using another signal that the application can catch.

---

### Post by techmarks on 2008-10-21
> **dwhitney67 said:**
> You can try playing/experimenting with "pidof".  You would need to know the full-path name of the program running.  For example:
```

pidof /sbin/init

```
This is the first process run by the system; the return PID should be 1.

Another alternative is to develop a script that launches both applications in succession.  The second application can be given the PID of the first via the command line.  Or, without the script, just do it manually:
```

secondApp `pidof /path/of/firstApp`

```

To determine the path of the application that is running (for use with 'pidof'), run a ps -ef and determine it via the output.


P.S.  You should avoid sending an application a 'kill -9' (or SIGKILL) signal if at all possible.  This signal cannot be caught, and hence the application being terminated cannot be stopped gracefully.  Consider using another signal that the application can catch.




Thanks for the ideas but I tried pidof and got this;

```
$ pidof
pidof: not found

```

probably because I'm on FreeBSD.

You're right about 'kill -9'

Probably using SIGTERM is a better choice.

---

### Post by Reiger on 2008-10-22
You didn't give pidof an argument; for example:
```

prometheus@Bartix:~$ pidof opera
12086
prometheus@Bartix:~$

```

---

