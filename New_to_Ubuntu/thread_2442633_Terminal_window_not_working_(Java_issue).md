---
title: "Terminal window not working (Java issue?)"
date: 2020-05-05
forum: New to Ubuntu
---

### Post by acrosome2 on 2020-05-05
Hi, all. I'm stumped. I opened the terminal window to try to update GIMP on my machine running 18.04 LTS, and every time I do it opens VASSAL, and then the terminal window opens with a message:

```
(java:5032): GLib-GObject-WARNING **: 16:50:00.109: invalid cast from 'GtkToplevelAccessible' to 'JawToplevel'
```

The cursor is there, but no prompt and I can't do anything.  I can't even kill the process to get the terminal back. I had previously written a little script to start VASSAL, with the icon on my desktop:

```
[Desktop Entry]
Encoding=UTF-8
Name=VASSAL
Comment=Launch VASSAL.sh
Exec=/home/dean/VASSAL/VASSAL.sh
Icon=/home/dean/VASSAL/doc/images/VASSALicon.png
Type=Application
```


But I don't see why opening a terminal window should run it. If I close the window that VASSAL opened in, it also closes the terminal. I tried moving the VASSAL icon I made off the desktop and into another folder, but this still all happens when I try to open a terminal. (Clicking on the VASSAL icon still works as intended, opening VASSAL, with no issues.) I can't even try to update Java without a terminal, to see if that corrects the problem.

Then, there's something really odd.  I moved the folder that VASSAL is stalled in, and changed the script for the icon so that it still works, but now I can't open a terminal window AT ALL.  If I either ctrl-alt-T or right-click the desktop and choose it from the drop down menu NOTHING HAPPENS.

---

### Post by Impavidus on 2020-05-06
I'm not familiar with VASSAL. My guess is that whatever you did to install it, added something to either your .profile or your .bashrc. Those files are read whenever you open a shell, which is the thing running in a terminal. Whatever is now in that .profile or .bashrc causes the shell to open VASSAL immediately and and terminate as soon as VASSAL terminates. If VASSAL fails to start, the shell is terminated too. When the shell terminates, the terminal closes.

The solution is to investigate your .profile and .bashrc files and fix them.

Unfortunately, it's not uncommon for install scripts to butcher your .profile or .bashrc.

---

### Post by acrosome2 on 2020-05-06
I don't *think* that's the issue.  I'm pretty sure I've used the terminal since installing VASSAL.  In fact, before I made the desktop icon I had to use the terminal to launch it.  This is new behavior.

Still, it's worth looking into, if you can tell me where those are.  I'm googling now.

EDIT-- Oh, they're in my home directory.

I don't see anything odd in .profile:

```
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


# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.local/bin" ] ; then
    PATH="$HOME/.local/bin:$PATH"
fi
```

And .bashrc looks pretty understandable, too:

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

```

---

### Post by acrosome2 on 2020-05-06
I tried opening gnome-terminal using the HUD, it still doesn't work.  I tried opening xterm using the HUD, but apparently that's not installed.  The only way I can get a terminal is Ctrl-Alt-F3.

From my googling, in 16.04 a lot of people had something like this happen after a python update, since gnome-terminal requires it.  I didn't mess with python, but could it somehow be the issue?

I found this as a possible fix:
```
sudo apt install dconf-cli
dconf reset -f gnome-terminal
sudo apt-get remove gnome-terminal
sudo apt-get install gnome-terminal
sudo locale-gen --purge
sudo dpkg reconfigure locales
reboot
```
But it didn't work.

I also just tried to sudo apt-get install xterm but it says that it's already installed.  So why won't it launch from the HUD?

EDIT-- Well, at least I figured out that I can launch xterm from the applications menu.  That makes life a little simpler.  So I guess that the problem is gnome-terminal in some way.

If I try to run gnome-terminal in xterm nothing happens, but at least I get my prompt back.[/FONT]

---

### Post by acrosome2 on 2020-05-06
I'm now wondering if it may be a python problem, like in the many hits I get googling terminals that won't open.
If I gedit /usr/bin/gnome-terminal the first line is:
```
#! /usr/bin/python3
```
But if I run python in xterm it says that my version is 2.7.17 so could that be the issue?  I'm not sure how a comment in gnome-terminal would really affect this, but I found answers saying to change it when people updated to python3.6 for instance.
I'm also not sure what would have caused this, since I haven't been messing around with python.

---

### Post by Impavidus on 2020-05-06
There could be a million reasons why your terminal doesn't start, but the fact that it attempted to run VASSAL was a hint. Now that you moved VASSAL, the terminal doesn't start at all. Or it starts and immediately exits, before it even opens a window.

That you can run an xterm is an interesting hint too. It means that your shell runs fine. I assume at least that your gnome-terminal and your xterm are supposed to run the same shell (bash, unless you changed that). You can't run gnome-terminal from your xterm, so the problem is not with the launcher of gnome-terminal. So I'm quite sure too that the problem is with gnome-terminal. When you attempt to start gnome-terminal, it doesn't open a window with a shell, but does something weird. You already reinstalled it, so it's not a problem with the executable itself.

gnome-terminal is actually a wrapper script, written in python, that launches gnome-terminal.real. The first line of that script, like all scripts, tells the system which interpreter must be called to run it, so that's Python 3. On your system you should have both Python 2.7 and Python 3.6. Nothing suspicious going on there.

It might be interesting to know the command line arguments used to start gnome-terminal. With the VASSAL directory back where it was, so that gnome-terminal at least opens a window and keeps it open for a while, can you open a gnome-terminal and run in your xterm```
ps -ef | grep term
```It might give a hint.

Another thing to look at are the configuration files for gnome, in particular gnome-terminal. They should be somewhere in ~/.config, I hope with a rather obvious name. Any reference to VASSAL would be a red flag. I don't use gnome-terminal myself.

---

### Post by slickymaster on 2020-05-06
@acrosome2:

Please don't use quote tags when posting terminal output, use code tags instead.

---

### Post by acrosome2 on 2020-05-07
No, I didn't change the default shell in any way. 

No luck finding anything that mentions gnome-terminal in ~/.config. There's a gnome-initial-setup-done text file that just contains the single word "yes". And there's a folder called gnome-session which contains a folder named saved-session which is empty. 

 In my home directory I see a .bashrc and a .profile file, but neither mentions gnome-terminal.

ps -ef | grep term in xterm while the gnome terminal is open and frozen as described above gets me:

```

gdm 1693 1528 0 19:50 tty1 00:00:00 /usr/bin/Xwayland :1024 -rootless -terminate -accessx -core -listen 4 -listen 5 -displayfd 6
dean 5206 3315 0 20:01 ? 00:00:00 /usr/lib/gnome-terminal/gnome-terminal-server
dean 5295 3487 0 20:01 tty2 00:00:00 xterm
dean 5325 5297 0 20:01 pts/1 00:00:00 grep --color=auto term
```

---

### Post by ActionParsnip on 2020-05-08
If you install guake does it run OK (guake is very good)

---

### Post by acrosome2 on 2020-05-13
It probably would.  But I'm trying to fix gnome-terminal.

EDIT--
Wow, it comes as *source code* and you have to compile it?  No.  Not bothering.

---

