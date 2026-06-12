---
title: "wildcards in quotes?"
date: 2009-08-04
forum: Programming Talk
---

### Post by akimatsu123 on 2009-08-04
hi, 

i am writing a shell script, and I need to use

```
gnome-terminal -e "<command>"/CODE]

to start a new terminal. 

however, in the command, I need to use a wild card. The command that goes in <command> is:

[CODE]cp filename*.sh ~/.scripts
```

However, the terminal just returns that it cannot find filename*.sh (ie. it's escaped the *). How do i unescape the * inside a quote?

---

### Post by Hobgoblin on 2009-08-04
Why start a new terminal which will close when the command completes?

Why not simply run the command in the background?

i.e
```
cp filename*.sh ~/.scripts &
```

---

### Post by akimatsu123 on 2009-08-05
because although that may work for the particular cp command i need to do this several times and some of the commands i need to see their output live

thanks

---

### Post by Dill on 2009-08-05
You could try assigning your command to a variable...

```
COMMAND="cp filename*.sh ~/.scripts"
```

And then opening a new terminal like so...

gnome-terminal -e $COMMAND.

I'm not sure if it'll work, but I did notice that by assigning a statement with wildcards in such a manner, the shell automatically expands the wildcard in your variable... which makes sense, but didn't seem immediately apparent...

```
atherdy@lamp:~/test$ ls
jk.html  test  test2
satherdy@lamp:~/test$ COMMAND="ls *"
satherdy@lamp:~/test$ echo $COMMAND
ls jk.html test test2
satherdy@lamp:~/test$
```

Cheers,
Dill

---

### Post by geirha on 2009-08-08
```
gnome-terminal -x bash -c 'cp -vi filename*.sh ~/.scripts; read'
```

gnome-terminal will close as soon as the command has completed. That's why I put a read at the end. It will wait for the user to hit enter before closing.

---

### Post by kaibob on 2009-08-08
> **geirha said:**
> gnome-terminal will close as soon as the command has completed. That's why I put a read at the end. It will wait for the user to hit enter before closing.

An alternative that keeps the terminal window open:

```
gnome-terminal -x bash -c 'cp -vi filename*.sh ~/.scripts; bash'
```

---

