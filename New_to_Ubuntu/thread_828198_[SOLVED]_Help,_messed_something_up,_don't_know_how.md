---
title: "[SOLVED] Help, messed something up, don't know how to fix"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by ebeckhusen on 2008-06-13
Okay, so I know just about enough to be dangerous:)

I had my system working when I shut down yesterday, but today when I restarted it was messed up.

I can't get my bars to show up, some programs won't start (firefox, most of the other stuff on the start menu) but some do (thunderbird, a couple of others).  Compiz works, Awn works.  When I start in failsafe mode everything works.

So I think I must have messed up a script somewhere, I just have no idea which one or how to fix it.  Any ideas on what I can look at?

---

### Post by gr4nf on 2008-06-13
Would you post:
```

ls /etc/rc3.d/
cat ~/.bashrc

```

---

### Post by ebeckhusen on 2008-06-13
> **gr4nf said:**
> Would you post:
```

ls /etc/rc3.d/
cat ~/.bashrc

```

```
becky@becky-laptop:~$ ls /etc/rc3.d/
README                       S13kdm            S20rsync       S89atd
S01policykit                 S18avahi-daemon   S20samba       S89cron
S05vbesave                   S20apmd           S24dhcdbd      S90binfmt-support
S10acpid                     S20apport         S24hal         S98usplash
S10sysklogd                  S20cupsys         S25bluetooth   S99acpi-support
S10xserver-xorg-input-wacom  S20hotkey-setup   S25pulseaudio  S99laptop-mode
S11klogd                     S20nvidia-kernel  S30gdm         S99rc.local
S12dbus                      S20powernowd      S89anacron     S99rmnologin

```

```
becky@becky-laptop:~$ cat ~/.bashrc
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

---

### Post by beren.olvar on 2008-06-13
Try running a terminal... if that works try launching firefox and other 
messed apps from there and post what happens.

also, if you hadnt installed emerald you could try
metacity --replace

in case you did install emerald try 
emerald --replace

and look for errors in the output (post them too)

cheers

---

### Post by ebeckhusen on 2008-06-13
I could not open a terminal or Firefox from the regular Gnome session, only from the failsafe session.

Any other ideas?

---

### Post by beren.olvar on 2008-06-13
uhm... try Alt+F2 (run dialog) to run gnome-terminal
if nothing happens then you could do this:

-press Ctrl+Alt+F2 
this will take you to a console, pretty much like the DOS one.

-log in
-once logged in execute:
```

nick@nick_pc:~$DISPLAY=:0 gnome-terminal

```
that should spawn a terminal window at your current X session, to see if that worked

-press Alt+F7
to get back to your X window enviroment.

If you have a terminal open, congratulations, you can post error mesages again :)
else...
we will need to think harder.

hope it works

cheers.

---

### Post by ebeckhusen on 2008-06-13
> **beren.olvar said:**
> uhm... try Alt+F2 (run dialog) to run gnome-terminal
if nothing happens then you could do this:

-press Ctrl+Alt+F2 
this will take you to a console, pretty much like the DOS one.

-log in
-once logged in execute:
```

nick@nick_pc:~$DISPLAY=:0 gnome-terminal

```
that should spawn a terminal window at your current X session, to see if that worked

-press Alt+F7
to get back to your X window enviroment.

If you have a terminal open, congratulations, you can post error mesages again :)
else...
we will need to think harder.

hope it works

cheers.

Okay, I did what you said above, but when the terminal opened it was not responding.  I could not get Firefox to start from the console.  Where do I get the error messages so I can post them.

---

### Post by sdowney717 on 2008-06-13
can you create a new user and log in with that new user ID.
Then see if it all works.

system-admin-users and groups

I did this one time when my home directory got botched up. I had lost all my panels. I then went about deleting everything in my home directory and somehow it all got regenerated. But I was pleased when I found out another login user had no problems.

If you can login with another user or even root, then just gksudo nautilus and you can move your files around from one user to another.

---

### Post by kansasnoob on 2008-06-13
"Okay, so I know just about enough to be dangerous"

That makes two of us!

I have a list of three things to try when somethings "breaks". It has about a 10% success rate.

1. I open synaptic and click reload and then I look at the bottom of the screen where it shows xxxxxx# of packages installed, broken, etc. Hey I'm a nOOb, I'm old, not that smart, and I break things ........ so once in a while it'll show a broken package.

2. To resolve any possible unmet dependencies I might have created I execute one of the few commands I've memorized: sudo apt-get -f install.

3. I restart in "recovery mode" and watch for any "failures" and I come here to the forums and ask what the heck to do next (I quite often don't even know what the final lines of recovery mode text are telling me to do).

---

### Post by ebeckhusen on 2008-06-14
> **sdowney717 said:**
> can you create a new user and log in with that new user ID
Then see if it all works.

system-admin-users and groups

I did this one time when my home directory got botched up. I had lost all my panels. I then went about deleting everything in my home directory and somehow it all got regenerated. But I was pleased when I found out another login user had no problems.

If you can login with another user or even root, then just gksudo nautilus and you can move your files around from one user to another.
Thanks, I ended up doing this and it worked for me.  Lost a few settings while doing it, and I need to fix permissions on a few files, but at least I'm running again without having to use failsafe mode.

---

### Post by ebeckhusen on 2008-06-14
> **kansasnoob said:**
> "Okay, so I know just about enough to be dangerous"

That makes two of us!

I have a list of three things to try when somethings "breaks". It has about a 10% success rate.

1. I open synaptic and click reload and then I look at the bottom of the screen where it shows xxxxxx# of packages installed, broken, etc. Hey I'm a nOOb, I'm old, not that smart, and I break things ........ so once in a while it'll show a broken package.

2. To resolve any possible unmet dependencies I might have created I execute one of the few commands I've memorized: sudo apt-get -f install.

3. I restart in "recovery mode" and watch for any "failures" and I come here to the forums and ask what the heck to do next (I quite often don't even know what the final lines of recovery mode text are telling me to do).

Thanks for trying to help.  It didn't fix the problem, but I did find one broken package in the process, and thanks to you I was able to fix it.

---

### Post by sdowney717 on 2008-06-14
One of the advantages of linux is keeping the user space separate from the filesystem, as user configurations mostly are in their own user space. Create a new user and you can get going again when you find you totally messed up your user space and cant find a way out.
Once I did that for myself, I played around with my old user space. I found that I could delete everything and the system would regenerate certain needed files and I got it working again.
Linux is superior!
It is a good idea to have a backup user ready to go to get back into your system, just in case you break it. If you dont know this you might be tempted to do an unnecessary complete reinstall. Also give that user the same privileges as your regular current user.

---

