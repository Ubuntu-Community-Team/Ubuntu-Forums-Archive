---
title: "Bash Scripting"
date: 2013-03-19
forum: Programming Talk
---

### Post by 2001cpx on 2013-03-19
Hi!

i'm new to Linux,

i'm trying to a simple script like a batch files(ms-dos) and i have no succes and i don't understand why not work.

i.ve read all tutorial on linuxcommand.org


here is my problem


#!/bin/bash
#nothing here
echo "Hello"
Alias cls=clear
echo "world"

echo 1 and 2 work,but alias is not executed ,alias cls=clear work on command line,not in the script.

 shell permission on my files is ok

 no command "cls"  found is the result


i have read tutorial many times


thanks in advance

---

### Post by Cheesemill on 2013-03-19
When you launch a script, it runs in a new session. The alias command is being executed but it's only valid for the current session, ie during the script.

When the script finishes executing, the session it was running in is closed and you are returned to the session you were in before the script was executed, so the alias is no longer valid.

If you want to define aliases for all of your terminal sessions you have 2 options. The first is to edit your ~/.bashrc file and define the aliases there. The second option (which I use) is to create the file ~/.bash_aliases and define all of your aliases there, The default ~/.bashrc file provided with Ubuntu (and most other distros) will check for the existence of a ~/.bash_aliases file and source all of its contents if it exists. For example my ~/.bash_aliases file looks like this...
```
rob@raring:~$ cat ~/.bash_aliases 
alias sudo='sudo '
alias ipl='get_iplayer --nocopyright'
alias gipl='get_iplayer --nocopyright --output=/home/rob/Videos --tvmode=flashhd,flashvhigh,flashhigh,flashstd,flashnormal --get'
alias hist='history | grep'
alias sv='sudo vi'
alias df='df -h -t ext4'
alias du='du -h --max-depth=1 | sort -hr'
alias ls='ls -lh --color=auto'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias pg='ps -Af | grep $1'
```

---

### Post by 2001cpx on 2013-03-19
Thank you Very Much!!!!!

Now i understand!!!!

Thank you again

---

### Post by ofnuts on 2013-03-19
> **2001cpx said:**
> Thank you Very Much!!!!!

Now i understand!!!!

Thank you again
The above remarks also hold when you set environment variables. However, you can also execute a script in the context of your current session by calling it with "source" or ".", i.e.:
```

source my_settings
# or
. my_settings
```
in which case environment variables and aliases will apply to the current session.

This also lets you define functions/variables common to several scripts in a single file

---

### Post by 2001cpx on 2013-03-19
I tried your command and is very interesting!!

work like a batch files (i have 49 years old....and liked in the past MS-dos)

i like a powerfull linux command. 

Now i can start to take a control of my Machine! (need surely 5 or 10 years...)

thanks for your precious help

---

### Post by SeijiSensei on 2013-03-19
Remember that bash, like all things *nix, is case-sensitive.  "Alias" will not work because the command is named "alias."  Except in some very rare cases, almost every command in Linux and other Unix variants uses lower case.

---

