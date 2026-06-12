---
title: "added useradd/adduser - hostname doesn't show on this user's command prompt."
date: 2013-03-03
forum: New to Ubuntu
---

### Post by HalfNote5 on 2013-03-03
I added a new user and set their password and all that good stuff, but for some reason this particular user, when logged in, just gets /  as a prompt (sometimes username /   instead of the usual username@hostname / 

Why?  And can I fix it? It doesn't appear to be hurting anything, but it's bugging me.

---

### Post by Cheesemill on 2013-03-03
It sounds like your new users ~/.bashrc file isn't being sourced properly.
Can you post the ouput of the following commands please...
```
ls -l ~/.bashrc
ls -l ~/.profile
cat ~/.bashrc
cat ~/.profile
```

---

### Post by HalfNote5 on 2013-03-03
> **Cheesemill said:**
> It sounds like your new users ~/.bashrc file isn't being sourced properly.
Can you post the ouput of the following commands please...
```
ls -l ~/.bashrc
ls -l ~/.profile
cat ~/.bashrc
cat ~/.profile
```



Thanks! I take it you mean while logged in as the user in question. (If I'm mistaken, let me know. These results are while logged in as the new user):



**ls -l ~/.bashrc** is:
-rw-r--r-- 1 dirk dirk 3486 May 21  2012 /home/testuser/.bashrc





**cat ~/.bashrc** is:

# ~/.bashrc: executed by bash(1) for non-login shells.
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
fi




**cat ~/.profile** is:

$ cat ~/.profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

---

### Post by CaptainMark on 2013-03-04
Did you create the new user with the command line utility? If so then I believe Ubuntu will create a new user with the /bin/sh shell instead of the /bin/bash shell, you can test by typing "echo $SHELL" into a terminal and if this is the problem you can easily correct it with this command```
chsh -s /bin/bash NEWUSER
``` just replace NEWUSER with the problematic user's name, and prepend the sudo command if you are not already logged in as this user

---

### Post by schragge on 2013-03-04
> **HalfNote5 said:**
> **ls -l ~/.bashrc** is:
-rw-r--r-- 1 [COLOR=#ff0000]dirk dirk[/COLOR] 3486 May 21  2012 /home/[COLOR=#ff0000]testuser[/COLOR]/.bashrcI wonder why the new user's name is *dirk* if his home directory is */home/testuser*. Did you explicitly specify the home directory while creating that user? Something like
```
sudo adduser --home /home/testuser dirk
``` or ```
sudo useradd -d /home/testuser dirk
```

---

### Post by schragge on 2013-03-04
> **CaptainMark said:**
> Did you create the new user with the command line utility? If so then I believe Ubuntu will create a new user with the /bin/sh shell instead of the /bin/bash shellCannot say for Ubuntu as I don't use it, but at least in Debian users created with *sudo adduser* will get */bin/bash* as their default login shell:
```

[COLOR=green]$[/COLOR] grep ^DSHELL /etc/adduser.conf
DSHELL=/bin/bash

```
[highlight]Update.[/highlight]
You are right about *sudo useradd* however:
```

[COLOR=green]$[/COLOR] grep ^SHELL /etc/default/useradd
SHELL=/bin/sh

```

---

### Post by HalfNote5 on 2013-03-04
> **schragge said:**
> I wonder why the new user's name is *dirk* if his home directory is */home/testuser*. Did you explicitly specify the home directory while creating that user? Something like
```
sudo adduser --home /home/testuser dirk
``` or ```
sudo useradd -d /home/testuser dirk
```


I didn't, and I thought that was really, really weird, too. I don't even HAVE a user named "Testuser"

---

### Post by HalfNote5 on 2013-03-04
> **CaptainMark said:**
> Did you create the new user with the command line utility? If so then I believe Ubuntu will create a new user with the /bin/sh shell instead of the /bin/bash shell, you can test by typing "echo $SHELL" into a terminal and if this is the problem you can easily correct it with this command```
chsh -s /bin/bash NEWUSER
``` just replace NEWUSER with the problematic user's name, and prepend the sudo command if you are not already logged in as this user


There's the ticket! Thanks!

---

