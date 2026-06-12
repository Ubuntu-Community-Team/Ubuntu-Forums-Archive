---
title: "[SOLVED] making a shortform for a command"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-08-31
Can i make a short form for a command
like
instead of typing sudo apt-get install all the time can i simply type 'agi'

something like that

---

### Post by original_jamingrit on 2008-08-31
Yes you can!

in your home directory there should a file called .bashrc which is hidden by default.  Open it with gedit or another text editor, and then add this line to it:
```
alias NEWCOMMAND='OLDCOMMAND'
```and replace the capitalized parts.

you would probably want:
```
alias agi='sudo apt-get install'
```
and then you could use 'agi firefox' to install firefox, for example.

You can also use this to 'replace' commands:
```
alias ls='echo "April Fool's Day"'
```

Your .bashrc may already contain some examples of other aliases that you are already using!

There's lots of neat tricks you can use the .bashrc for, check out this thread: [http://ubuntuforums.org/showthread.php?t=679762&highlight=.bashrc](http://ubuntuforums.org/showthread.php?t=679762&highlight=.bashrc)

---

### Post by lovinglinux on 2008-08-31
Coooool! Thanks **i.mehrzad** for creating the thread and **original_jamingrit** for explaining how to. 

Linux is so freaking cool. Now I have "agi" and "agr" commands. Maybe I should call them "lazyi" and "lazyr" :)

---

### Post by 7raTEYdCql on 2008-08-31
I made the changes to the .bashrc file.
Now when i open terminal i get the following error.
```
bash: alias: agi: not found
bash: alias: =sudo apt-get install: not found

```


when i use agi firefox. I get the following prompt:
mehrzad@mehrzad-laptop:~$ agi firefox
bash: agi: command not found
mehrzad@mehrzad-laptop:~$ 'agi firefox'
bash: agi firefox: command not found
[/code]

---

### Post by 7raTEYdCql on 2008-08-31
thanks i got it to work.

---

### Post by billgoldberg on 2008-08-31
Mark your thread as solved please.

---

