---
title: "what really happens when type exit"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by hookitup on 2012-10-21
when you type in the command exit in the terminal . what exactly does it do. does it run a script that kills process, does it run a file. is it just backed into the OS, what exactly does it do?

is there a file associated with this command? that you are able to edit?


please dont give me the obvious answer that it exits the terminal.

---

### Post by bab1 on 2012-10-21
> **hookitup said:**
> when you type in the command exit in the terminal . what exactly does it do. does it run a script that kills process, does it run a file. is it just backed into the OS, what exactly does it do?

is there a file associated with this command? that you are able to edit?


please dont give me the obvious answer that it exits the terminal.
The command *exit* is a function and is part of the standard libraries that the OS uses.  It terminates the calling process immediately.  It is not a script.  It is written in C. If you wanted, you could look at the source code to see how it works.

For more basic information see```
man exit

man 3 exit
```

---

### Post by Starcruiser322 on 2012-10-21
I would say that it is an uneditable command that calls a halt to running processes in the current session and ends the session if there are no more processes. (each terminal window would be a session)
This is evidenced by typing "sudo su", entering the password, and then typing "exit". It does not exit the terminal, because sudo su starts a new session within the session.

---

### Post by Frogs Hair on 2012-10-21
This should give you a start . [http://linux.about.com/library/cmd/blcmdl3_exit.htm](http://linux.about.com/library/cmd/blcmdl3_exit.htm)

---

### Post by dniMretsaM on 2012-10-21
It runs the [FONT=Courier New]exit[/FONT] program located at [FONT=Courier New]/usr/bin/exit[/FONT]. Information about what exactly it does can be found by reading the exit man page (run [FONT=Courier New]man exit[/FONT] or you can read it [online](http://linux.die.net/man/3/exit)).

---

### Post by hookitup on 2012-10-22
perfect great answer from everyone.

---

