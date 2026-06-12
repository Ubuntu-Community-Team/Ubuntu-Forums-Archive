---
title: "cant switch sessions"
date: 2015-10-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2015-10-08
i am running ubuntu 14.04 which is my default and i just installed xfce and xubuntu. when i get to the login screen and select either xubuntu or xfce session the computer just reboots. selecting ubuntu 14.04 still works fine. any ideas/tks

---

### Post by v3.xx on 2015-10-09
Will startx work?  startx /path/to/bin/desktop file

---

### Post by Geoffrey_Arndt on 2015-10-09
Your post seems confusing (maybe it's just me) . . did you add a partition and then install the Xubuntu distro . . . ?  Or did you just install the XFCE desktop inside your Ubuntu partition?    If you did the first option, you should see the Grub menu and select the Xubuntu distro.

---

### Post by rburkartjo on 2015-10-09
after i enter my password screen just goes back to the login screen.any ideas/tks.

---

### Post by Bashing-om on 2015-10-09
rburkartjo; Hey ...

> 
.any ideas/tks.

Several possibilities that it "might" be .
1) Ya been sudo'n where you  should not and now 'root' owns /home ?
2) Permission issues ?? Very likely. Is the variable XAUTHORITY set ?
3) Proprietary driver broke in a update ?
4) GUI broke > What results when booting to terminal and attempting to start the GUI from terminal ?

Presently not enough info to even hazard a viable guess. But the good thing is
[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bapoumba on 2015-10-09
Threads merged.

---

### Post by rburkartjo on 2015-10-09
bash i booted up in recovery and deleted xauthority did not fix. virtual just takes my user name and password but cant get pass text mode. how would i check for ownership and if not correct.tks/rayj

---

### Post by Bashing-om on 2015-10-09
rburkartjo; Welp;

As you have removed .Xauthority, is it re-created upon rebooting ?
Do you own:
```

ls -al .Xauthority
ls -al .ICEauthority

```

Do you have a login manager ? Is it lightdm ? Do you have access ?
```

ls -al /var/run/lightdm/root/

```

What returns:
```

echo $XAUTHORITY

```

If all these are in order, I think then it is time to start reading the log files, see what the system reports for problems.

[INDENT][INDENT]the process
[INDENT][INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]to effect restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bobuntu2 on 2015-10-09
Had a similar problem a few days ago after I'd been messing with lighm-gtk-greeter and it's settings tool.  When I couldn't get them to do what I wanted I switched back to unity-greeter, to face the same issue as you...log in and the screen goes back to the Log-in greeter.
I fixed it by reconfiguring both lightdm and unity-greeter.
sudo dpkg-reconfigure unity-greeter  (or whatever greeter you're using).
sudo dpkg-reconfigure lightdm

All was well after that.

---

### Post by rburkartjo on 2015-10-09
bash as you request in order

1-3 no such file
4 just returned to prompt

---

### Post by Bashing-om on 2015-10-09
rburkartjo; Well !

That ain't good .
The question now is why ?
What have you got set ?
```

cat ~/.profile
cat ~/.bashrc
cat ~/.bash_logout

```

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by rburkartjo on 2015-10-09
bash in order

1 - if ["bash"] then if [-f ~/bashrc] ; then if [~/.bashrc]; then ,~/bashrc
2 and 3-files dont exist
4- no output

---

### Post by rburkartjo on 2015-10-09
bob didnt work tks

---

### Post by rburkartjo on 2015-10-09
i have been using ubuntu for years and know there is fix. just dont know what it is

---

### Post by Bashing-om on 2015-10-09
rburkartjo; Like ;

If you do not have these file:
```

sysop@1404mini:~$ cat ~/.profile
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
sysop@1404mini:~$


sysop@1404mini:~$ cat ~/.bashrc
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

if[ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34]\w\[\033[00m\]\$ '
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
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
    alias xterm='xterm -rv' ##added 18may2014 to change the xterm background from white.
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)"$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

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
#PATH="$HOME/bin:$PATH" ##this path is now set by default and is not required to be set plicitly 07jun2015
sysop@1404mini:~


sysop@1404mini:~$ cat ~/.bash_logout
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy
#deactivated 08jul13 so I can see everything.

#if [ "$SHLVL" = 1 ]; then
#    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
#fi
echo "Logging out, Gone and done" >&2
#
sysop@1404mini:~$

```
I can not see how anything would work. But maybe your DeskTop Environment is such that they are not required ??
----------------------
I would think that XAUTHORITY must be set .
```

sysop@1404mini:~$ echo $XAUTHORITY
/home/sysop/.Xauthority
sysop@1404mini:~$

``` where I am sysop.


[INDENT][INDENT]If I know better I would say better
[/INDENT][/INDENT]

---

