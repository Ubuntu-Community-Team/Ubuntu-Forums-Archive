---
title: "options for time in the command line do not work"
date: 2007-03-30
forum: Programming Talk
---

### Post by name7ess on 2007-03-30
Hi all,

This question is not directly related to programming, but i think it still fits here somehow:

Time seems to think that the options are the actual command, but i could not figure out how to tell time that they are not.  Man just says that they should be placed before the command.

```

name7ess@T60:/tmp$ time -o
bash: -o: command not found

real    0m0.001s
user    0m0.000s
sys     0m0.000s
name7ess@T60:/tmp$ time -o /dev/stdout ls
bash: -o: command not found

real    0m0.001s
user    0m0.000s
sys     0m0.000s
name7ess@T60:/tmp$ time -h
bash: -h: command not found

real    0m0.001s
user    0m0.000s
sys     0m0.004s
name7ess@T60:/tmp$

```

---

### Post by WW on 2007-03-30
Interesting... there appear to be two **time** commands.  Try giving the full path to the command, i.e.
> /usr/bin/time -o /dev/stdout ls
That worked on my computer (running dapper).

Compare
> $ man 1 time
and
> $ man 1posix time
(You may have to install some additional manpage packages to view these.)

---

### Post by WW on 2007-03-30
> **WW said:**
> Interesting... there appear to be two **time** commands. 
There *are* two time commands.  One is a bash shell command; take a look here: [http://tldp.org/LDP/abs/html/timedate.htmlhttp://ubuntuforums.org/newreply.php?do=newreply&p=2376589](http://tldp.org/LDP/abs/html/timedate.htmlhttp://ubuntuforums.org/newreply.php?do=newreply&p=2376589)
Scroll down to the short section about **time**; note the comment about **time** being a reserved word.  The shell time command is the one that will be used if you just type **time** in a terminal.

The other is the command in /usr/bin/time.  This is the command that you will read about if you enter **man time** in a terminal.

The bash gurus can explain why this command
```
$ time time
```
actually runs both versions!

---

### Post by Mr. C. on 2007-03-30
Since the dawn of time...!

There have always been two time commands, one builtin, and /bin/time.  Each were slightly different.

```
time time
```

will use the built-in to call the program located in your PATH (/usr/bin/time).  Built-in shell commands are always attempted first.  To avoid built-in's, use \ to escape:
```

$ time ls
$ \time ls
```

MrC

---

### Post by drunken_sapo on 2008-07-30
> **Mr. C. said:**
> Since the dawn of time...!

There have always been two time commands, one builtin, and /bin/time.  Each were slightly different.

```
time time
```

will use the built-in to call the program located in your PATH (/usr/bin/time).  Built-in shell commands are always attempted first.  To avoid built-in's, use \ to escape:
```

$ time ls
$ \time ls
```

MrC

pity i wasn't there in the dawn of time (or \time) :D
this drove me insane until i've read your messages. 
thank you guys.

---

