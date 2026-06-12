---
title: "bashrc"
date: 2010-12-26
forum: Philippine Team
---

### Post by stjohnmedrano on 2010-12-26
i did some tweaking in my bashrc file. ang nang yari i change my orignal prompt to ">".
pag mag type naako ng commands tapos press ko yung home key yung cursor babalik yun dapat sa first line ng commands pero ang nangyari mag stop lang siya in between the commands.

```

> cat .bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

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

color_prompt=yes

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir 
# Edit your prompt
case "$TERM" in
xterm*|rxvt*)
    
    export PS1="\e[01;32m> \e[0m" 
    #PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto -l --group-directories-first'
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

# Some personal aliases and functions.
# My personal choice you can delete this portion if you want
    
    #alias date='date +"%A, %B %-d, %Y"'
    #alias bc='bc -q'
    
    function update 
        {
            echo "Updating $HOSTNAME..."
            sudo aptitude update
            echo "$HOSTNAME Is Updated!"
        }

    
> 



```

---

### Post by loell on 2010-12-27
the '>' at the end is an incorrect syntax.

---

### Post by Script Warlock on 2010-12-27
@stjohn, ahahhaa tanaw man gud ka tron legacy...

---

### Post by dsdeiz on 2010-12-28
I'm no bash expert but try doing:

```
PS1="\[\e[01;32m\]> \[\e[0m\]"
```

:D

---

### Post by (&amp;*4h*)#$ on 2010-12-28
If > is a special character, you might want to prepend it with an escape character like so: \>
I haven't tried that yet so I am not sure if this is helping. :P

---

### Post by stjohnmedrano on 2010-12-28
> **Script Warlock said:**
> @stjohn, ahahhaa tanaw man gud ka tron legacy...

hahaha... lagi, experiment lang, hehehe...

---

### Post by stjohnmedrano on 2010-12-28
thank you po, but still the same, kahit na binalik ko yung dollar sign na prompt "$ ", ganon parin.

---

### Post by stjohnmedrano on 2010-12-28
i agree with loell talagang incorrect yung ">" ganon na syntax, i figure it how.

```

export PS1="\[\033[01;32m\] >\[\033[0m\] "

```this one works fine with me, hehehe....

its same with dsdeiz code
```

PS1="\[\e[01;32m\]> \[\e[0m\]"
``` i just add a space before " > ".

thanks everyone....

OT:
@warlock: grabe hangover bai, hehehe...

---

### Post by enhu on 2010-12-30
ano pala ang gusto mong ma-accomplish?

---

