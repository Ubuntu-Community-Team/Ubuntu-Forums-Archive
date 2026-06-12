---
title: "Default Directory in Terminal Problem"
date: 2023-12-20
forum: Programming Talk
---

### Post by drumone on 2023-12-20
Somehow during one of my classes I changed the terminal directory (I think). When I open up the terminal in Ubuntu, this is what I see:

~(Test) >

It used to read Home or my username, if I recall correctly. How do I change this back to the default name and/or directory?

---

### Post by Bashing-om on 2023-12-20
Hello drumone -

Where you are when in terminal is where you start when booting back up.

try this
```

cd

```
to change the Present Working Directory back to /home >
reboot

what shows now ?

-some things are simple-

---

### Post by drumone on 2023-12-20
I tried that. It still shows: 

~(Test) >

I think it got changed during the project for my class on Git. Any other ideas?

---

### Post by #&amp;thj^% on 2023-12-20
> **drumone said:**
> I tried that. It still shows: 

~(Test) >

I think it got changed during the project for my class on Git. Any other ideas?

I'll take a stab can you show us this:
```
tac /home/$USER/.profile

```
and this as well:
```
tac /home/$USER/.bashrc 
```
Well we might as well get this while we are here:
```
tac /etc/environment

```

---

### Post by drumone on 2023-12-20
In order as requested:

```

fi
    PATH="$HOME/.local/bin:$PATH"
if [ -d "$HOME/.local/bin" ] ; then
# set PATH so it includes user's private bin if it exists

fi
    PATH="$HOME/bin:$PATH"
if [ -d "$HOME/bin" ] ; then
# set PATH so it includes user's private bin if it exists

fi
    fi
	. "$HOME/.bashrc"
    if [ -f "$HOME/.bashrc" ]; then
    # include .bashrc if it exists
if [ -n "$BASH_VERSION" ]; then
# if running bash

#umask 022
# for ssh logins, install and configure the libpam-umask package.
# the default umask is set in /etc/profile; for setting the umask

# the files are located in the bash-doc package.
# see /usr/share/doc/bash/examples/startup-files for examples.
# exists.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# ~/.profile: executed by the command interpreter for login shells.
```
```

fi
    PATH="$HOME/.local/bin:$PATH"
if [ -d "$HOME/.local/bin" ] ; then
# set PATH so it includes user's private bin if it exists

fi
    PATH="$HOME/bin:$PATH"
if [ -d "$HOME/bin" ] ; then
# set PATH so it includes user's private bin if it exists

fi
    fi
	. "$HOME/.bashrc"
    if [ -f "$HOME/.bashrc" ]; then
    # include .bashrc if it exists
if [ -n "$BASH_VERSION" ]; then
# if running bash

#umask 022
# for ssh logins, install and configure the libpam-umask package.
# the default umask is set in /etc/profile; for setting the umask

# the files are located in the bash-doc package.
# see /usr/share/doc/bash/examples/startup-files for examples.
# exists.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# ~/.profile: executed by the command interpreter for login shells.
~(Test) > ^C
~(Test) > tac /home/$USER/.bashrc
fi
	export PS1='\W$(__git_ps1 "(%s)") > '
	source ~/.git-prompt.bash
if [ -f ~/.git-prompt.bash ]; then

fi
  source ~/.git-completion.bash
if [ -f ~/.git-completion.bash ]; then

fi
  fi
    . /etc/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  if [ -f /usr/share/bash-completion/bash_completion ]; then
if ! shopt -oq posix; then
# sources /etc/bash.bashrc).
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# enable programmable completion features (you don't need to enable

fi
    . ~/.bash_aliases
if [ -f ~/.bash_aliases ]; then

# See /usr/share/doc/bash-doc/examples in the bash-doc package.
# ~/.bash_aliases, instead of adding them here directly.
# You may want to put all your additions into a separate file like
# Alias definitions.

alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
#   sleep 10; alert
# Add an "alert" alias for long running commands.  Use like so:

alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
# some more ls aliases

#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'
# colored GCC warnings and errors

fi
    alias egrep='egrep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias grep='grep --color=auto'

    #alias vdir='vdir --color=auto'
    #alias dir='dir --color=auto'
    alias ls='ls --color=auto'
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
if [ -x /usr/bin/dircolors ]; then
# enable color support of ls and also add handy aliases

esac
    ;;
*)
    ;;
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
xterm*|rxvt*)
case "$TERM" in
# If this is an xterm set the title to user@host:dir

unset color_prompt force_color_prompt
fi
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
if [ "$color_prompt" = yes ]; then

fi
    fi
	color_prompt=
    else
	color_prompt=yes
	# a case would tend to support setf rather than setaf.)
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# We have color support; assume it's compliant with Ecma-48
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
if [ -n "$force_color_prompt" ]; then

#force_color_prompt=yes
# should be on the output of commands, not on the prompt
# off by default to not distract the user: the focus in a terminal window
# uncomment for a colored prompt, if the terminal has the capability; turned

esac
    xterm-color|*-256color) color_prompt=yes;;
case "$TERM" in
# set a fancy prompt (non-color, unless we know we "want" color)

fi
    debian_chroot=$(cat /etc/debian_chroot)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
# set variable identifying the chroot you work in (used in the prompt below)

[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"
# make less more friendly for non-text input files, see lesspipe(1)

#shopt -s globstar
# match all files and zero or more directories and subdirectories.
# If set, the pattern "**" used in a pathname expansion context will

shopt -s checkwinsize
# update the values of LINES and COLUMNS.
# check the window size after each command and, if necessary,

HISTFILESIZE=2000
HISTSIZE=1000
# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

shopt -s histappend
# append to the history file, don't overwrite it

HISTCONTROL=ignoreboth
# See bash(1) for more options
# don't put duplicate lines or lines starting with space in the history.

esac
      *) return;;
    *i*) ;;
case $- in
# If not running interactively, don't do anything

# for examples
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# ~/.bashrc: executed by bash(1) for non-login shells.
```

```

CLUTTER_PAINT=disable-dynamic-max-render-time
MUTTER_DEBUG_ENABLE_ATOMIC_KMS=0
MOZ_ENABLE_WAYLAND=1
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
```

---

### Post by TheFu on 2023-12-20
Were you screwing with PS1 or PS2 environment variables or did you change your shell?

The defaults for a prompt in bash (the default shell) are
{username}@{hostname}:{relative directory}$

Or you could have started a new shell, so type 'exit' to leave it.
If you logout and login again, that would have the same impact.

I'm confuse why 1fallen asked for **tac** to be used.  I'd like to think it was brilliant, but I suspect it was a 3 typos.

The following commands will take you to the same place:

```
cd 
cd $HOME
cd ~
cd ~/
cd ~{username}

```
~ says to look up the username in the password entry DB (which could be /etc/passwd (or a networked LDAP, NIS, NIS+ or some other delegated password setup).
Without a {username},  ~ it assumes the current username.  These shortcuts are very handy to know.

git has 20M projects, so saying you may have used 1 isn't exactly helpful.  It is like saying a saw a car somewhere, help me figure out which radio station it was playing.  You may have seen the car on TV or a few days ago or at a sports stadium with 100K other people.  See the issue?

---

### Post by Bashing-om on 2023-12-20
However --

Tells the tale:
"~(Test) > tac /home/$USER/.bashrc"
> 
fi
	export PS1='\W$(__git_ps1 "(%s)") > '
	source ~/.git-prompt.bash
if [ -f ~/.git-prompt.bash ]; then

fi
  source ~/.git-completion.bash
if [ -f ~/.git-completion.bash ]; then

where and how the prompt is changed.

-not a mystery any longer-

---

### Post by drumone on 2023-12-20
Except that I'm just starting to learn all of this... which means it's still a mystery. LOL

@Bashing-om - Could you kindly give the English translation for dummies (namely ME)? I'm unclear as to what I need to change exactly. 

I'm just trying to figure out how to change things back to the standard default directory for Ubuntu terminal. I've checked for remote branches, local branches, file lists, and everything else I could think of after going through my notes again. It all comes up empty. It's like I changed the default name to Test, after it was "main" or "master. I know the change occurred during my project for class, but I have no idea what I did or how I did it at this point.

---

### Post by TheFu on 2023-12-20
Remove these lines:
```
export PS1='\W$(__git_ps1 "(%s)") > '
source ~/.git-prompt.bash
```

that's a start.
Get a book on Linux - here's one I used to teach beginning linux: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)

---

### Post by drumone on 2023-12-20
Thanks @TheFu. That did the trick!

I'm so bogged down just trying to learn Java and my other classes that learning Linux is going to have to wait. However, I've saved it and will definitely give it a read in the future. Thanks for the info!

---

### Post by TheFu on 2023-12-21
Java. Yuck.  You want to be a corporate drone programmer?

---

### Post by #&amp;thj^% on 2023-12-21
> **TheFu said:**
> Remove these lines:
```
export PS1='\W$(__git_ps1 "(%s)") > '
source ~/.git-prompt.bash
```

that's a start.

I couldn't hang around waiting for the OP to reply, so +1 on the removal on those lines.

> **TheFu said:**
> Java. Yuck.  You want to be a corporate drone programmer?
LOL the Old (J)ust (A)nother (V)irus (A)way, double Yuck.
Happy to hear this is solved now.

---

