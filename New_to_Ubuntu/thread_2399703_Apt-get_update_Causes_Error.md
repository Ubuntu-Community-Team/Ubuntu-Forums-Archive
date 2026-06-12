---
title: "Apt-get update Causes Error"
date: 2018-08-28
forum: New to Ubuntu
---

### Post by austincibulka on 2018-08-28
Hi,

I actually have two issues running with Ubuntu.

1. Whenever I run apt-get update in the terminal, the following error shows:

```
E: Malformed entry 55 in list file /etc/apt/sources.list (Component)E: The list of sources could not be read.
```


2. Whenever I open any terminal, the following error automatically populates:

```
The program 'mpicc' can be found in the following packages:
 * lam4-dev
 * libmpich-dev
 * libopenmpi-dev
Try: sudo apt install <selected package>
No completion added for /home/austincibulka/OpenFOAM/OpenFOAM-v1806/platforms/linux64GccDPInt32Opt/bin
... incorrect platform, or not yet compiled?
```


It is apparent to me that number two is related to my most recent installation of OpenFOAM, but I am not too sure how to remove that error.

Thank you for any help.

Austin

---

### Post by logix2 on 2018-08-29
1. Open the /etc/apt/sources.list file with a text editor and look at line 55. What does it say? For example you can use gedit to open that file (without permissions to modify it, that requires root):

```
gedit /etc/apt/sources.list
```

To view the line number, enable the display of line numbers in Gedit (Preferences > VIew tab).

2. It sounds like something in your ~/.bashrc file is triggering that. Can you post the contents of your ~/.bashrc file? You can open it in Gedit using this command:

```
gedit ~/.bashrc
```

---

### Post by austincibulka on 2018-08-29
> **logix2 said:**
> 1. Open the /etc/apt/sources.list file with a text editor and look at line 55. What does it say? For example you can use gedit to open that file (without permissions to modify it, that requires root):

```
gedit /etc/apt/sources.list
```

To view the line number, enable the display of line numbers in Gedit (Preferences > VIew tab).

2. It sounds like something in your ~/.bashrc file is triggering that. Can you post the contents of your ~/.bashrc file? You can open it in Gedit using this command:

```
gedit ~/.bashrc
```


1. See attached for line 55 (highlighted):
[ATTACH=CONFIG]280902[/ATTACH]

2. Contents of ~/.baschrc file:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples


# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac


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
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi


# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
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


# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'


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
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi


source /home/austincibulka/OpenFOAM/OpenFOAM-v1806/etc/bashrc
```

---

### Post by DuckHook on 2018-08-29
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by aysiu on 2018-08-30
Your line 55:
```
deb [arch=amd64] https://download.docker.com/linux/ubuntu stable
```

What it should look like:
```
deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable
```

Reference:
[https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository](https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository)
```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

*lsb_release* would be *xenial*, in your case.

---

### Post by austincibulka on 2018-08-30
Problem number 1 on my original post has been solved. Are there any suggestions solve problem number 2?

Thank you.

---

### Post by oldos2er on 2018-08-30
For problem 2 you might try commenting out the "source /home/austincibulka/OpenFOAM/OpenFOAM-v1806/etc/bashrc" line, so that it appears as ```
# source /home/austincibulka/OpenFOAM/OpenFOAM-v1806/etc/bashrc
``` However I have no knowledge of OpenFOAM and I can't say whether or not this will cause any issues. After making the change restart your terminal to check.

---

### Post by monkeybrain20122 on 2018-08-30
> **oldos2er said:**
> For problem 2 you might try commenting out the "source /home/austincibulka/OpenFOAM/OpenFOAM-v1806/etc/bashrc" line, so that it appears as ```
# source /home/austincibulka/OpenFOAM/OpenFOAM-v1806/etc/bashrc
``` However I have no knowledge of OpenFOAM and I can't say whether or not this will cause any issues. After making the change restart your terminal to check.

That is the problem. the script loads OpenFoam's environmental variables which shadow the system's default and may lead to unexpected errors (it is a computional Fuid mechanics program) I think depending on how it is installed openfoam may ask if you want to put that line in .bashrc (or may tell you to do it yourself) 

@OP, I would as oldos2er says remove that line and run it in the terminal every time you use openfoam

I would create an alias in .basrc like 

```
alias load_OF="source /home/austincibulka/OpenFOAM/OpenFOAM-v1806/etc/bashrc"
```

Then run openfoam with
```

load_OF 
openfoam
```

---

