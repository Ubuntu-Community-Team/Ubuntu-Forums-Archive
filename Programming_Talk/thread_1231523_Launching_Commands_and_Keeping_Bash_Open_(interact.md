---
title: "Launching Commands and Keeping Bash Open (interactive)"
date: 2009-08-04
forum: Programming Talk
---

### Post by terminator14 on 2009-08-04
I'm trying to launch bash with a few commands, and keep it open (from what I understand that's called interactive mode).

Ex:

If you run:

```
bash
```

you get a new bash console you can run commands in, and type:

```
exit
```

when you are done to return to your previous environment.

If you run:

```
bash -c 'cd /; pwd'
```

though, you get the output of the two commands, or of the last one in this case since the first doesn't give you output, and the bash environment exits as soon as the commands finish running, so in this case you will be back to the folder you started out in, and not /. How would I launch these commands and keep the new bash environment from closing?

I tried:

```
bash -ic 'cd /; pwd'
```

but that didn't work either.

---

### Post by unutbu on 2009-08-04
I think we need a little more context. Are you writing a script, and just want to run a collection of commands in a bash shell?

Or are you trying to launch, say, a gnome-terminal, and want the gnome-terminal to stay open?

---

### Post by soltanis on 2009-08-04
From the manpage:

> 
       When an interactive shell that is not a login shell  is  started,  bash reads  and  executes  commands  from /etc/bash.bashrc and ~/.bashrc, if these files exist.  This may be inhibited by using the  --norc  option. The  --rcfile  file option will force bash to read and execute commands
from file instead of /etc/bash.bashrc and ~/.bashrc.


You might consider this action?

---

### Post by terminator14 on 2009-08-04
I'm following [this]("https://help.ubuntu.com/community/LiveCDCustomization") link to write a small script for cusomizing a live cd of jaunty, but when i get to the step that says

```
sudo chroot edit
```

the script can't launch any commands in the chroot edit environment. To do so, I would need to run something like:

```
chroot edit /bin/bash -c "mount -t proc none /proc && mount -t sysfs none /sys && export HOME=/root && export LC_ALL=C && alias finish='rm -rf /tmp/* ~/.bash_history && rm /etc/resolv.conf 2>/dev/null && umount -lf /proc && umount /sys && exit'"
```

but as soon as those commands run, the chroot environment exits since bash exists. I need bash to stay open until I tell it to exit.

I tried:

```
bash -ic --norc 'cd /; pwd'
```

but it just shows some usage info on bash indicating I'm using the command wrong. Would this command help in my case? Or is it meant for something else? It sounds like if used properly, it will cause bash to run commands from a file, but I need it to run commands that are input by the user through the terminal window (stdin).

Edit: Ok I figured out I should have ran the command this way instead for it not to show errors:

```
bash --norc -ic 'cd /; pwd'
```

but that still does exactly the same thing as before.

---

### Post by unutbu on 2009-08-04
Have you tried running the commands enclosed by parentheses so that the group of commands run in a subshell?
```

(
sudo chroot edit
... more commands ...
mkinitramfs -o /initrd.gz 2.6.15-26-k7
)
```

See [http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/subshells.html](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/subshells.html)

---

### Post by stroyan on 2009-08-04
It may be practical to use the BASH_ENV environment variable instead of -c to give a file with a list of steps to perform before waiting for user input.

It would be simpler to just add an invocation of a bash shell as one of the many commands in your -c argument.  The second bash shell would run and interact with the user until it was exited interactively.  Then the first bash shell would finish.

You should have a look at the schroot package.
It could make much of what you are doing with chroot much easier.

---

### Post by terminator14 on 2009-08-04
> **unutbu said:**
> Have you tried running the commands enclosed by parentheses so that the group of commands run in a subshell?
```

(
sudo chroot edit
... more commands ...
mkinitramfs -o /initrd.gz 2.6.15-26-k7
)
```

See [http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/subshells.html](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/subshells.html)

I tried running my commands as 

```
(
chroot edit
mount -t proc none /proc
mount -t sysfs none /sys
export HOME=/root
export LC_ALL=C 
alias finish='rm -rf /tmp/* ~/.bash_history && rm /etc/resolv.conf 2>/dev/null && umount -lf /proc && umount /sys && exit'
)
```

but all that does is run chroot edit, wait for me to exit the chroot environment, and run all those commands afterwards. Upon messing around a little more with running commands in a subshell, it looks like this outcome is exactly what it should be, but not exactly what I'm looking for. I need the commands to run inside the chroot environment. 

As for using either BASH_ENV, or the schroot package, I'm looking into it now. Thanks.

---

