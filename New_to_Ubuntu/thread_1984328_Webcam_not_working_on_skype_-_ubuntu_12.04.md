---
title: "Webcam not working on skype - ubuntu 12.04"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by Apanta on 2012-05-21
**Webcam is not working on skype with Ubuntu 12.04** 			
 			 			 		   		 		 		I have a Creative Instant webcam not working on Skype,   in  Ubuntu 12.04.
If I use the Skype icon  the program runs, but the webcam is non running.

By opening a terminal and using:

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype
```

Skype runs and the webcan is ok.

Closing the terminal, Skype closes regularly.

How can I launch Skype from the dafault icon?
Any help to solve my problem will be well accepted.

Thank you.   :-(
Apanta

---

### Post by papibe on 2012-05-21
Hi Apanta.

You need to set the variable LD_PRELOAD permanent in your environment. You have 2 options:

1. For personal use (just your user) add this line to your ~/.bashrc
```
export LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
```

2. For system-wide, add this line to your /etc/environment
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so
```

Then restart your machine.

If you want to read more about this, take a look at this [tutorial]("https://help.ubuntu.com/community/EnvironmentVariables"). Specially the section called 'Persistent environment variables'.


I hope that helps, and tell us how it goes.
Regards.

---

### Post by Apanta on 2012-05-22
Thanks.
I'll try to solve.
Regards 

Apanta

---

### Post by Apanta on 2012-05-22
Sorry,
How can I find:    ~/.bashrc  :confused:

If I type :

```
~/.bashrc
```the output is:

```
apanta@apanta-desktop:~$ sudo ~/.bashrc
sudo: /home/apanta/.bashrc: command not found
apanta@apanta-desktop:

```how can I make the change?  

Waiting for step by step instructions  ( open a terminal, type this ....)
thanks.
sorry for my bad english.

Apanta

---

### Post by Toporagno on 2012-05-22
Hi Apanta,
I think that .bashrc is a hidden file that you can find in your home. I'm a newbie myself so don't take what I say as something you should do it's just a suggestion, but I think that you have to edit the .bashrc file so I think you should open a terminal and type
```
sudo nano /.bashrc
``` or ```
sudo gedit /.bashrc
```and then add the line Papibe wrote in his post.

---

### Post by Apanta on 2012-05-22
> **Toporagno said:**
> Hi Apanta,
I think that .bashrc is a hidden file that you can find in your home. I'm a newbie myself so don't take what I say as something you should do it's just a suggestion, but I think that you have to edit the .bashrc file so I think you should open a terminal and type
```
sudo nano /.bashrc
``` or ```
sudo gedit /.bashrc
```and then add the line Papibe wrote in his post.

Hi.
from terminal, giving the command:

```
sudo gedit ~/.bashrc
```I see the ~/.bashrc file.

Inside this file,  there is:

> # ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fiWhere can I add the line Papibe wrote in his post  (at the last line... after the last fi ...before fi ... or where?

Take note that I am an absolute beginner in Ubuntu. :p:p

Thanks
Apanta

---

### Post by papibe on 2012-05-22
At the very end will be just fine.

Regards.

---

### Post by whitethorn on 2012-05-22
Um,

Why are you using the sudo command?  The sudo command is there when you want superuser priviledges. As in you want to edit system files. By using it on a file in your home folder and saving that file as sudo you won't be able to access it as your normal user anymore.

If you are working in your home folder don't use sudo. So a simple
```
gedit ~/.bashrc
```
or if you prefer
```
nano ~/.bashrc
```

Just in case you might want to check and see if you did change the permissions. Just to make sure

```
cd  #to get to your home folder
ls -l  # list everything and see the proper permissions
ls -l |grep .bashrc   #see the permissions on your .bashrc

```

---

### Post by madjr on 2012-05-22
another way  (if you're using unity) is to drag the icon from the dash to the desktop, right click and add the command in properties.

---

### Post by Apanta on 2012-05-22
> **papibe said:**
> At the very end will be just fine.

Regards.

I added the line at the end (after the last fi) and now the end of the file is:

[QUOTE . /etc/bash_completion
fi
export LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so][/QUOTE] 

I saved the file and close all.

Sorry, Skipe still runnig without webcam.

other suggestions?.
Apanta

---

### Post by papibe on 2012-05-22
Did you restart your machine?

Regards.

---

### Post by Apanta on 2012-05-22
Yes.
I created a new file on my desktop, named it Skype.
inside there are the lines  you wrote. I saved file and closed it.

In properties/permission  I signed it executable.

Now launching by double click on the file Skype works and the webcam runs ok.

wich is the next step?.
thanks
Apanta

---

### Post by Apanta on 2012-05-22
> **Apanta said:**
> Yes.
I created a new file on my desktop, named it Skype.
inside there are the lines  you wrote ad I saved file and closed it.

In properties/permission  I signed it executable.

Now launching by double click on the file Skype works and the webcam runs ok.

wich is the next step?.
thanks
Apanta


Ok... I solved in this way:

1 - Cut and paste the file Skype from the desktop to my home.

2 - Opening System Tools/Preferences/ Main Menu/Internet/Skype and select  "Skype properties"

3 - in the command space I wrote : /home/apanta/Skype

4 - Closed all

Now by cliking  on the default skype icon  all is working perfectly (audio e webcam).

Thanks  for precious help.  ):P

Apanta

---

