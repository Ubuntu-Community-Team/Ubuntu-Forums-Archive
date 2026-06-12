---
title: "Detection of a command in shell"
date: 2010-04-02
forum: Programming Talk
---

### Post by kapmsd on 2010-04-02
Guys,I would like to know if there is any way to detect a command if it going to be executed in the shell?
Eg:
Cmd: sudo apt-get clean
I want a C program to be called before this cmd is executed.

---

### Post by lostinxlation on 2010-04-02
alias command ?

---

### Post by Bachstelze on 2010-04-02
With zsh, you can define a precmd() function (in e.g. your ~/.zshrc) and it will be executed before every command. Bash might have something similar, I don't know much about it.

---

### Post by geirha on 2010-04-02
You can use the DEBUG trap. See «help trap».
```

$ trap 'echo this happens before' DEBUG
$ echo an echo
this happens before
an echo

```

---

### Post by kapmsd on 2010-04-02
How would I use alias to call my program when a command like "sudo apt-get autoclean" is gonna be executed??
Using alias ,i can create only some shortcuts only for commands,right??

---

### Post by lostinxlation on 2010-04-03
> **kapmsd said:**
> How would I use alias to call my program when a command like "sudo apt-get autoclean" is gonna be executed??
Using alias ,i can create only some shortcuts only for commands,right??

For example,  see below.
You maynot be able to alias whole line including options/arguments, but a simple script can do it.

```

TPX30:~/tmp> cat foo
#!/bin/csh

if ($1 == "zzz" && $2 == "xxx") then
  \echo "Inserted line"
endif
\echo $*

TPX30:~/tmp> alias echo foo
TPX30:~/tmp> echo zzz xxx
Inserted line
zzz xxx
TPX30:~/tmp> echo zzz xx
zzz xx

```
So it should be like,

```

TPX30:~/tmp> cat foo
#!/bin/csh

if ($1 == "apt-get" && $2 == "autoclean") then
  Call your script
endif
\sudo $*

```

and alias sudo to foo.

---

