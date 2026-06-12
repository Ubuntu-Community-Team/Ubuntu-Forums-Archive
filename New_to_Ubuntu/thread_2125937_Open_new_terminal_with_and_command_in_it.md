---
title: "Open new terminal with and command in it"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-03-15
Hi, I have a program, that can be only launched from terminal, but I want this thing in menu list. I know how to add commands in menu list, but the program have to be launched from terminal. So.. I need a command, that will launch a new terminal and in the new terminal run command.
Specifically the program I need to launch is "fp" and I have Xubuntu 12.10 using Terminal Emulator.
Thank you for any help..

---

### Post by sisco311 on 2013-03-15
The name of the terminal emulator used in Xubuntu is xfce4-terminal. You can use its -x option to run a command in it:```
xfce4-terminal -x "fp"
```

---

### Post by schragge on 2013-03-15
```
xfce4-terminal -x fp
```

---

### Post by ViliX64 on 2013-03-15
Thank you very much :) You have been very helpfull..

---

### Post by sudodus on 2013-03-15
You can run it in a terminal like this
```
xterm -e command [options] [parameters]
```
If you want it to stay after completion, use the ***hold*** option (otherwise you might not see the output of the command).
```
xterm -hold -e fp
```
See ```
man xterm
``` for all options.

You can also use xfce4-terminal as described in the previous posts, but it has fewer options.
```
xfce4-terminal -e fp
```

---

### Post by ViliX64 on 2013-03-15
By the way, what is the difference in those commands:
```
xfce4-terminal -x "fp"
```
and
```
xfce4-terminal -x fp
```
They look similar, but still different and it seems that both of them works.
So why this?
```
" "
```

---

### Post by sudodus on 2013-03-15
The double quotes (") can be used to make the command see a file name with spaces as one single parameter, and the shell will expand wild cards and interpret shell variables. If you enclose a string in single quotes ('), it works in the same way for spaces, and the shell will not expand or interpret anything.

I think that in this case the quoting will make no difference.

---

### Post by ViliX64 on 2013-03-15
Thank you for explaining sudodus..

---

