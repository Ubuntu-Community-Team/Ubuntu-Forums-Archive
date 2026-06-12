---
title: "[SOLVED] i broke the terminal"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by hellomoto on 2008-07-13
I broke the terminal!

well at least I was fiddling with they way it looked and then ... i rebooted and when i tried to open it... it wouldn't! it flashes up then closes itself instantly.

I have tried reinstalling via synaptic but had no luck.

I wouldn't mind but I find the terminal pity useful! lol

any ideas? -- no not to why I am so incompetent but as to how I fix the terminal! :P

---

### Post by dldseneviratne on 2008-07-13
Try this and see if it works: :)

```
sudo apt-get remove terminal
```

and then:

```
sudo apt-get install terminal
```

Cheers,

---

### Post by ghost_ryder35 on 2008-07-13
boot up normally and then hit
ctrl + alt + f1
then login and go to your home directory
/home/username/
```

vi .bashrc

```see if you can see anything out of the norm.. here is mine for a comparison
```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

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
#force_colored_prompt=yes

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
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

another thing to point out is removing it via synaptic wont remove the config file... u can remove it via synaptic and then manually remove
**.bashrc **
from your home directory and then reinstall and u should be good to go.

---

### Post by hellomoto on 2008-07-13
i have tried completely removing synaptic selecting -incl configuration files

I have tried changing my .bashrc with the contents of your one. 

and still no luck?#

seams really strange

---

### Post by LaRoza on 2008-07-13
Exactly what did you do?

You can press "Atl + F2", type "xterm", and try to run "gnome-terminal" from that. Post any errors you get.

---

### Post by hellomoto on 2008-07-13
> **LaRoza said:**
> Exactly what did you do?

You can press "Atl + F2", type "xterm", and try to run "gnome-terminal" from that. Post any errors you get.

I did this... it returns no errors.

again the gnome-terminal opens for about 1-2 seconds then closes. 

I really don't understand. Even after reinstalling Including installation file?!


I just changed a couple of settings via the edit profile option on the terminal - i wanted to change the way it looked.
Then I added gnome-terminal to sessions to run on startup. AS I wanted it to load automatically. I have since removed this to see if it was the problem but it still doesnt load.

---

### Post by PmDematagoda on 2008-07-13
When you open xterm, try executing gnome-terminal with:-
```
strace gnome-terminal
```
and see if that coughs up any errors.

---

### Post by LaRoza on 2008-07-13
> **hellomoto said:**
> 
I just changed a couple of settings via the edit profile option on the terminal - i wanted to change the way it looked.
Then I added gnome-terminal to sessions to run on startup. AS I wanted it to load automatically. I have since removed this to see if it was the problem but it still doesnt load.

Remove it from sessions then! It is probably running in the background.

---

### Post by hellomoto on 2008-07-13
fixed it....

I managed to open a gnome-terminal via htop. From there I could access the gnome-terminal settings.

On the "title and command" tab there is an option called run a "custom command instead of my shell" I had selected this (i was trying to get the terminal to run a command when it loaded). 

Then in my messing I had the option "when command exits - exit the terminal"

So when I tried to open a terminal it would open run a command then exit...

so stupid me! But at least its fixed now.

Thankyou everyone for your help!

---

### Post by Bodsda on 2008-07-13
Damn, wrote this too late...

---

