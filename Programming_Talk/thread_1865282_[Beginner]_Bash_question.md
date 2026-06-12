---
title: "[Beginner] Bash question"
date: 2011-10-19
forum: Programming Talk
---

### Post by Jabrick on 2011-10-19
So I am trying to configure my ~.bashrc file, with an if statement.

```

#
# ~/.bashrc
#

#If not running interactively, don't do anything#
[[ $- != *i* ]] && return

#Aliases#
alias ls='ls --color=auto'
alias grep='grep --color=auto'
alias mplayerx='mplayer -heartbeat-cmd "xscreensaver-command -deactivate"'
alias wireless='wicd-curses'
alias background='feh --bg-scale'

#Customizing PS1#
export PS1='\[\e[1;35m\][reza]\W>\[\033[0m\] '

directory=$(pwd)
if [$directory == /home/bob]; then
     echo "You are in home directory"
fi

```

And when I start the terminal I get this message.
bash: [/home/bob: No such file or directory

In the end my ultimate goal is for
PS1 to show my working directory (\W) only when I'm not in home.

P.S
Do I have a second problem, because this bash script only runs when you start the terminal? If so what can I do to solve my problem.

~

---

### Post by Vaphell on 2011-10-20
change
```
if [$directory == /home/bob]
```
to
```
if [ $directory == /home/bob ]
```

[] need to be separated from condition arguments.

---

### Post by dethorpe on 2011-10-20
If you want PS1 to include a dynamic part that is recalculated each time the prompt is displayed i.e to show or not show the working directory like you want, then include a call to a script in it to provide that bit.
 
e.g. to include the current date/time rather than the time the terminal opened and .bashrc was run you can do this:
 
```
export PS1='\[\e[1;35m\][reza]\W>\[\033[0m\] `date` >'

```
 
Key bit is as your string is inside single quotes the command (date) dosn't run when you export PS1, but does each time PS1 is used instead. (if it was inside double quotes you could then quote the backticks to get the same effect) 
 
Replace date above with your own script to decide if you are in home or not and return the path to display.
 
e.g.
```
 
 
directory=$(pwd)
if [$directory != /home/bob]; then
     echo $directory
fi
 

```

---

### Post by Jabrick on 2011-10-22
Thank you Vaphell for the advice helping me fix my syntax.
Also thank you dethorpe by advising me how to add a dynamic part to my PS1.

I have it working how I want it now. Feels good :)

Great support!

---

