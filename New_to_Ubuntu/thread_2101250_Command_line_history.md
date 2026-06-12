---
title: "Command line history"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by venkinag on 2013-01-04
I use Ubuntu 12.10.

When I open a terminal window, it allows me to navigate through the commands I typed in the past by pressing the up arrow button.

*  Does anyone know where these commands are stored for the terminal window to read and display?

*  Is there a way I can see all commands (may be stored somewhere in the system)

Thanks

---

### Post by Pjotr123 on 2013-01-04
They're in .bash_history in your home folder. Hidden file, so first unhide it by ticking the "unhide hidden files" option in the View section of the panel of your file manager. You can view and edit the contents in a text editor like Gedit or Leafpad. :)

By the way: should you wish to clear all items in the "terminal memory", then you can use this command:
```
history -c -w ~/.bash_history
```

If you want to prevent a particular command from being stored in the memory, simply precede that command by a space.

---

### Post by fdrake on 2013-01-04
> **venkinag said:**
> I use Ubuntu 12.10.

When I open a terminal window, it allows me to navigate through the commands I typed in the past by pressing the up arrow button.

*  Does anyone know where these commands are stored for the terminal window to read and display?

*  Is there a way I can see all commands (may be stored somewhere in the system)

Thanks
command
```

history

```
file ~/.bash_history

---

### Post by Fahim Abdun-Nur on 2013-01-04
Follow up question: how many items are stored in the historical list? Is this configurable?

---

### Post by howefield on 2013-01-04
Try this thread..

[http://ubuntuforums.org/showthread.php?t=1156178](http://ubuntuforums.org/showthread.php?t=1156178)

---

### Post by Fahim Abdun-Nur on 2013-01-04
thanks!

---

### Post by malspa on 2013-01-04
For distros that use su instead of sudo, there's also the file /root/.bash_history. That file doesn't exist in Ubuntu, I guess.

---

### Post by oldos2er on 2013-01-04
/root/.bash_history is there. I use "sudo -i" a lot, and that's where all its commands are logged.

---

### Post by malspa on 2013-01-05
> **oldos2er said:**
> /root/.bash_history is there. I use "sudo -i" a lot, and that's where all its commands are logged.

That file doesn't exit in either of my two Ubuntu 12.04 installations. Is it created when **sudo -i** is used?

---

### Post by oldos2er on 2013-01-05
I'm guessing it is.

---

### Post by iMac71 on 2013-01-05
> **malspa said:**
> That file doesn't exit in either of my two Ubuntu 12.04 installations. Is it created when **sudo -i** is used?Yes, it is.

---

### Post by tgalati4 on 2013-01-05
And since this is the AB subforum:

```
!!
!437

```

!! runs the last command.  !437 runs command 437 in the history list. Any other neat history tricks?

---

### Post by mc4man on 2013-01-05
> **tgalati4 said:**
> And since this is the AB subforum:
Any other neat history tricks?
For me the most useful is this, there are several variations/ways to do this or similar
I create a file in Home folder named
```
.inputrc
```
with this inside
```
"\e[5~": history-search-backward
"\e[6~": history-search-forward

```
Then in a terminal type a letter, letters, characters,  Page UP will return  commands using that letter, letters or chars. Page Dn will go back the other way (after using Page Up

(can also be placed in Root/Home if desired & will work the same

---

### Post by tgalati4 on 2013-01-05
Nice.  I just have an alias hs for history.

In my .bashrc file in my home directory:

```

# some more aliases
alias hs='history'
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'
alias cp='cp -i'
alias rm='rm -i'
alias mv='mv -i'
alias psa='ps -aux | more'


```

Also, Control-R will search your history as you start typing.  Not really useful with long history files, because it starts from the top and works down, so it brings up older commands first.  And these could be commands from weeks ago instead of a yesterday.

---

### Post by mringer on 2013-01-18
> **Pjotr123 said:**
>  
[cut]
By the way: should you wish to clear all items in the "terminal memory", then you can use this command:
```
history -c -w ~/.bash_history
```


I have L-UB 12.04. I cannot find any man page for the history command.

---

### Post by fdrake on 2013-01-18
> **mringer said:**
> I have L-UB 12.04. I cannot find any man page for the history command.

try to reinstall it:
```
sudo apt-get install --reinstall history
man history
```

---

### Post by MG&amp;TL on 2013-01-18
> **tgalati4 said:**
>  Any other neat history tricks?

You can use !! to perform sed-like operations on that command:

```
[michael@michael-desktop Documents]$ echo "foo"
foo
[michael@michael-desktop Documents]$ !!:s/foo/bar/
echo "bar"
bar
[michael@michael-desktop Documents]$ 

```

---

### Post by dodo3773 on 2013-01-18
> **venkinag said:**
> 
*  Is there a way I can see all commands (may be stored somewhere in the system)


Try this:
```

fc -l 0

```

---

### Post by mringer on 2013-01-19
> **fdrake said:**
> try to reinstall it:
```
sudo apt-get install --reinstall history
man history
```

I tried with this result:

```

sudo apt-get install --reinstall history
[password] 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package history

```

Please any ideas?

---

### Post by fdrake on 2013-01-19
> **mringer said:**
> I tried with this result:

```

sudo apt-get install --reinstall history
[password] 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package history

```

Please any ideas?
my moistake History is part of Bash so do this:
```

sudo apt-get install --reinstall bash

```
logout/ login

---

