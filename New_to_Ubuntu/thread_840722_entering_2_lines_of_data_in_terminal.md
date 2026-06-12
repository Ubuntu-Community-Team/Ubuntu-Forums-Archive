---
title: "entering 2 lines of data in terminal"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by bu2971x on 2008-06-25
how do you enter 2 lines in terminal without hitting enter
ex...
sudo tar -jxvf  firefox-3.0.tar.bz2 -c /opt
rm firefox-3.0.tar.bz2

---

### Post by Eisenwinter on 2008-06-25
command1 && command2 && command3 && etc...

```
sudo tar -jxvf firefox.tar.bz -c /opt && rm firefox
```

---

### Post by Dr Small on 2008-06-25
The && operator waits for the previous command to complete with an exit status of 0 before executing the next command.

The ; operator waits until the previous command completes, regardless of exit status.

---

### Post by Christmas on 2008-06-25
Not exactly: it's better to have it like this
```
command1; command2; command3;
```

The problem with the && operator is that it executes the second command only if the first one was successful. So if command1 fails, command2 won't be executed.

Example:
```
$ pwd
/usr
$ mkdir bla; ls
mkdir: cannot create directory `bla': Permission denied
bin  games  include  lib  local  sbin  share  src  X11R6
$

```

And:
```
$ pwd
/usr
$ mkdir bla && ls
mkdir: cannot create directory `bla': Permission denied
$

```
Notice 'ls' doesn't get executed anymore.

Edit: Dr Small cleared this up already, just a sec faster.

---

