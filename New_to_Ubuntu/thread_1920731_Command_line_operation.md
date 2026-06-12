---
title: "Command line operation"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by Old Hickory on 2012-02-05
How do I launch a program from the command line in Ubuntu 10-11? I have searched several books on basics and Googled the subject, but have found no help,

---

### Post by Carborundum on 2012-02-05
You invoke the command associated with the program in question in a terminal. For example, to launch Firefox from the command line, simply enter the command "firefox" in a terminal emulator of your choice.

---

### Post by ajgreeny on 2012-02-05
> **Old Hickory said:**
> How do I launch a program from the command line in Ubuntu 10-11? I have searched several books on basics and Googled the subject, but have found no help,
That depends on exactly what you mean.
You can open a gnome-terminal in Ubuntu or konsole in Kubuntu and type into that the name of the program executable, eg "firefox" or "alsamixer".  Try it out and you will see what I mean.

From the command line proper, ie a tty login, you can not launch a GUI application in that way, as that needs a graphical xsession running, so you will not be able to run any gnome or kde applications, etc etc,  however you will still be able to run some ncurses graphical applications such as "alsamixer".

I hope that helps you but come back again if that is all too difficult to understand.

---

### Post by josephmills on 2012-02-05
lets make a program called "hello_world"
1) open terminal and type in ```
gedit &
```   the & sign makes it so it is running in the background aka you can type more code into the terminal. 

2) in gedit paste this code in 
```

#!/use/bin/env bash 
clear 
echo "HELLO World"
sleep 12 
clear

```


save and close 

3) in terminal change directions into the same place that you saved to hello_world program ex-sample ```
cd ~/where/ever/you/saved/hello_world 
```


4) make program be able to run 
```
chmod +x hello_world
```

5) run the program 
```
./hello_world
```


hope that this helps

---

### Post by oklokl on 2012-02-05
test.sh
sh file > Mouse Right Click P
Action

#!/bin/bash
gnome-terminal -e "bash -c \"~/downloads/file.sh; exec bash\""


## or
# ex>

#!/bin/bash
xterm -hold -e "sudo im-switch -c"

---

