---
title: "bash completion after upgrade to 17.04"
date: 2017-08-03
forum: New to Ubuntu
---

### Post by twh270 on 2017-08-03
I've just upgraded to 17.04 from 16.04 and directory completion now prints out what looks like a broken ANSI escape sequence. For example typing "ls w<tab>" gives me:

ls ^[\(B^[\[mworkspace

I've done a fair bit of Googling but have come up empty. The following lines in my ~/.bashrc appear to be the symptom (I've commented them out to work around the problem):

### if ! shopt -oq posix; then
###   if [ -f /usr/share/bash-completion/bash_completion ]; then
###     . /usr/share/bash-completion/bash_completion
###   elif [ -f /etc/bash_completion ]; then
###     . /etc/bash_completion
###   fi
### fi

It's surely something simple but I'm at a loss, any help appreciated.

---

### Post by vocx on 2017-08-03
> **twh270 said:**
> I've just upgraded to 17.04 from 16.04 and directory completion now prints out what looks like a broken ANSI escape sequence. For example typing "ls w<tab>" gives me:

ls ^[\(B^[\[mworkspace

I've done a fair bit of Googling but have come up empty. The following lines in my ~/.bashrc appear to be the symptom (I've commented them out to work around the problem):

### if ! shopt -oq posix; then
###   if [ -f /usr/share/bash-completion/bash_completion ]; then
###     . /usr/share/bash-completion/bash_completion
###   elif [ -f /etc/bash_completion ]; then
###     . /etc/bash_completion
###   fi
### fi

It's surely something simple but I'm at a loss, any help appreciated.
It may not be necessarily a permanent problem with the system. Sometimes the terminal gets corrupted, so the way to fix it is simply to run "reset" in the terminal.
```

reset

```

---

### Post by twh270 on 2017-08-03
Thanks vocx but that doesn't do it. (However, I'd forgotten that 'reset' is a thing, so thanks for the reminder.)

---

### Post by Bashing-om on 2017-08-03
twh270; Hey:

Just another thought:
> **twh270 said:**
> Thanks vocx but that doesn't do it. (However, I'd forgotten that 'reset' is a thing, so thanks for the reminder.)

Do the target files exist ?
> 
sysop@x1604:~$ ls -al /usr/share/bash-completion/bash_completion 
-rw-r--r-- 1 root root 67661 May 18  2016 /usr/share/bash-completion/bash_completion

sysop@x1604:~$ ls -al /etc/bash_completion
-rw-r--r-- 1 root root 45 Aug 12  2015 /etc/bash_completion
sysop@x1604:~$ 


[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by twh270 on 2017-08-03
Problem resolved. Turned out I had the following code in my ~/.bashrc:

```

# http://unix.stackexchange.com/questions/20803/customizing-bash-shell-bold-color-the-command
shopt -s extdebug
trap "tput sgr0" DEBUG

```

Found it by putting a `return` in the middle of my ~/.bashrc and then walking it to the above lines via binary search. Each time opening a new shell and running `. /usr/share/bash-completion/bash_completion` to see if the tab completion worked.

---

### Post by sisco311 on 2017-08-03
Cool! 

Please mark this thread as solved.

---

