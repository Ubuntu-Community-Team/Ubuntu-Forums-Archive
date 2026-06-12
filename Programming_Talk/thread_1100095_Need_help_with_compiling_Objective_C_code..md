---
title: "Need help with compiling Objective C code."
date: 2009-03-18
forum: Programming Talk
---

### Post by MR.UNOWEN on 2009-03-18
Hello,
So I'm learning how to program in Objective C. Anyway, I'm having trouble compiling some code. I used the example in a book with no luck. Can someone help me set up things so I can start compiling code. 

Also I'm eventually going to start writing code for the iphone, so could the set up also closely mimic compiling code on the mac, that would be great.

Here's what happened the first few times...

~/Desktop$ gcc fun.m -o prog1 -l objc
gcc: error trying to exec 'cc1obj': execvp: No such file or directory
~/Desktop$ gcc -x objective-c fun.m -o happy
gcc: error trying to exec 'cc1obj': execvp: No such file or directory
~/Desktop$ gcc -x objective-c fun.m
gcc: error trying to exec 'cc1obj': execvp: No such file or directory

---

### Post by lloyd_b on 2009-03-18
Compiling Objective C requires a package that isn't part of the standard install (or part of the "build-essential" package):
```
sudo apt-get install gobjc-4.3
``` (or install the package "gobjc-4.3" via the package manager of your choice).

Once you've done that, your first attempt ("gcc fun.m -o prog1 -l objc") should work.

Lloyd B.

---

### Post by MR.UNOWEN on 2009-03-18
Thanks, that did the job.

Also, I'm having trouble running executables. I always have to provide the full path for some reason or I'll get "command not found". Also this seems to be just the case with my computer. Other computers don't have this problem. Is there something under terminal I have to do?

---

### Post by lloyd_b on 2009-03-18
Exactly what executables?  Are we talking about system binaries ("ls", "find", etc), or just programs that you've compiled?

You *always* have to provide a path to a command, unless the directory the executable is in is defined in your PATH environment variable.  If you're just trying to run programs in your current directory, "./programname" is sufficient.

Note that while you *can* modify the PATH to include "." (the current directory), this is NOT recommended - on multiuser systems it used to be common to exploit this to trick a person into running a malicious program.

Lloyd B.

---

### Post by MR.UNOWEN on 2009-03-18
The executable i'm talking about is the one I just compiled. So i'm at Desktop in terminal and the executable is on my Desktop so I type "prog1" in and it wont work, but if i do ".../Desktop/prog1" it does.

---

### Post by snova on 2009-03-18
> **MR.UNOWEN said:**
> The executable i'm talking about is the one I just compiled. So i'm at Desktop in terminal and the executable is on my Desktop so I type "prog1" in and it wont work, but if i do ".../Desktop/prog1" it does.

You've come quite close to solving it by yourself. Bash does not search the current directory for programs, as lloyd_b said.

However, rather than going up a directory and then back down, remember that '.' is always equivalent to the current directory.

---

### Post by MR.UNOWEN on 2009-03-18
./prog1 did the job, but how come on some computers I can just do prog1 and it'll work, where as on my computer i have to do ./prog1?

---

### Post by snova on 2009-03-18
> **MR.UNOWEN said:**
> ./prog1 did the job, but how come on some computers I can just do prog1 and it'll work, where as on my computer i have to do ./prog1?

Possibly because they put '.' in the $PATH variable. Try printing it out on one of those computers.

which may also help explain it:

```
which prog1
```

---

### Post by MR.UNOWEN on 2009-03-19
Ok...   i think I'm starting to understand things....

So how do I add the dot into the PATH?

What file and what line do I need to edit to do this?

---

### Post by sujoy on 2009-03-19
edit the PATH variable in your ~/.bashrc or ~/.bash_profile

PATH=.:${PATH}

---

### Post by MR.UNOWEN on 2009-03-19
Where should that be placed. I'm not seeing that particular line.

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# don't overwrite GNU Midnight Commander's setting of `ignorespace'.
export HISTCONTROL=$HISTCONTROL${HISTCONTROL+,}ignoredups
# ... or force ignoredups and ignorespace
export HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)

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

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

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

---

### Post by nvteighen on 2009-03-19
Just place it at the end and it will work.

---

### Post by MR.UNOWEN on 2009-03-19
Thanks, that did the job.

---

### Post by lloyd_b on 2009-03-19
Just a comment - if you're going to add "." to the PATH, you should really add it at the *end* of the PATH, rather than the beginning.

The reason - a malicious user could put an executable with a common name ("ls" was commonly used for this purpose in the old days) in a given directory, and if you have "." at the beginning of your PATH, and you run "ls" in the directory that file is in, then you wind up running the exploit code from that directory, rather than the system binary.  The exploit code would typically do its dirty work, and then call "/bin/ls" so that you'd see exactly what you'd expect to see.

This isn't as much of an issue as it used to be, since on most home systems there isn't a malicious user to begin with.  But it's good general practice to put the "." last (if you have it at all).

Lloyd B.

(In case you don't understand what I mean by "beginning" and "end" - "PATH:$PATH:.", rather than "PATH=.:$PATH")

---

### Post by MR.UNOWEN on 2009-03-20
Thanks again and yes, I didn't understand what you were saying at first until I read the last line.

---

### Post by iansane on 2011-12-06
well it's 2011 now but this post helped solve the same issue for me.

Need to install two packages now. gobjc-4.4 and gobjc-4.4-multilib to get past the error message if anyone has this issue on 10.04.

---

### Post by jweinraub on 2012-07-18
You should be made aware while putting the dot in the end of the path would help with malicious people replacing ls with an alias that will say rm -rf / the computer, it is recommended to never ever put the dot in the path.

It isn't standard on most systems I ever encountered, and getting into the habit of ./a.out really isn't that hard.

Many many years ago when I first started doing Linux development as in using Debian w/o any GUI and just running gcc, yes it was convenient to do a.out rather than ./a.out but it is a very good practice to keep doing it that way.  It can be very dangerous.

---

