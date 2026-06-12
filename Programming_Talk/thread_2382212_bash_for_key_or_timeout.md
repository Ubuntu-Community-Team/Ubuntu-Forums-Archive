---
title: "bash for key or timeout"
date: 2018-01-10
forum: Programming Talk
---

### Post by cazz on 2018-01-10
If it possible in a bash script make a if with timeout so if I don't push a button on the keyboard and the 5 sec have gone it going to do run a command, and if I do press a key it does not run the command.

---

### Post by TheFu on 2018-01-10
I think 'read' has a timeout option in bash. It is a built-in.  It is NOT POSIX.

---

### Post by cazz on 2018-01-10
hmm thanks :)

---

### Post by sudodus on 2018-01-10
```
help read|less
```

tells us to use **read** with the option **-t**

```
     -t timeout        time out and return failure if a complete line of input is
                not read within TIMEOUT seconds.  The value of the TMOUT
                variable is the default timeout.  TIMEOUT may be a
                fractional number.  If TIMEOUT is 0, read returns immediately,
                without trying to read any data, returning success only if
                input is available on the specified file descriptor.  The
                exit status is greater than 128 if the timeout is exceeded

```

---

### Post by cazz on 2018-01-10
mm yes I did find that and now I know what to search for then it easy to find the information I need.

Thanks alot :)

---

### Post by TheFu on 2018-01-10
BTW, I didn't know about the 'help' command until sudodus wrote it above.  ;) there is always something new to learn.

The trick for finding help is to know if the command is 'built-in' or external.  External commands should have manpages or info-pages.  man / info. info documented commands normally have a manpage stub, which points to the info-page. Built-in commands, like 'read', are part of the bash help, so only those built-in commands are covered.

Other built-in examples are 'for' and 'while', which are good for looping in bash scripts.
Other shells might not have a help command.

---

