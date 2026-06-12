---
title: "Executing symbolic link"
date: 2015-01-28
forum: New to Ubuntu
---

### Post by Aphexlog on 2015-01-28
Hello everyone ):P

I have a path that I have created a symbolic link for quick access.
The path is as follows:
"/home/awest/VirtualBox/Loki"

however when I attempt to execute this link I receive this error:
"bash: ./Loki.vbox: No such file or directory"

I am attempting to execute via "./Loki.vbox" command while in the appropriate directory.

- Thank you it advance

---

### Post by Bucky Ball on 2015-01-28
How did you create the symlink? [This]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html?showComment=1275427925979") gives a good explanation of the syntax.

Basically, the thinking is:

ln -s 'location to link to' 'name of symlink'

If you provide the path of both the target directory and the symlink you are looking to create, we'll have a better idea of how the command should look.

Are you trying to create a symlink in the host to a directory in a virtual machine?

---

### Post by Aphexlog on 2015-01-28
From the directory that I wanted the link in, I use: ln -s [I]pathoffile
Path of file:
[/I]/home/awest/VirtualBoxVMs/Loki/Loki.vbox

Path of link:
/home/awest/Virtual

Yes, this is a symbolic link for a VM

---

### Post by Aphexlog on 2015-01-28
Okay, I found an issue.
it was a link to a file that did not exist due to a typo
I fixed the path, however I now get this error:
"sudo: .Loki.vbox: command not found"

---

### Post by deadflowr on 2015-01-28
The actual command you used would be a little more helpful.
You could look through your bash-history by using the up arrow in while in the terminal until you get to the command, then copy and paste it.

Also, I sort of understand what you are trying(Or at least I think I do), but why not use Virtualbox's built-in function vboxmanage to startup the vm?
It's dead easy to do Simply "vboxmanage startvm name-of-vm-here"

You could even make it easier by adding a quick bash_alias, something like
alias loki='vboxmanage startvm Loki'
and add it to your .bashrc file.
Restart the terminal and from then on to start the vm just type loki.

I don't know, just thinkin'.

---

### Post by Aphexlog on 2015-01-28
I will need to be able to start up the vm remotely through a terminal session. That's why I am going this rout.
However, setting up an alias would make like easier. the only file that I see similar, is /etc/bash.bashrc. Is that the file that I am looking for to add the alias?
Additionally, the command that I am using is "ln -s ../VirtualBoxVMs/Loki/Loki.vbox"

---

### Post by Bucky Ball on 2015-01-28
```
ln -s /home/awest/VirtualBox VMs/Loki/Loki.vbox /home/awest/Virtual
```

... is how it should look where '/home/awest/VirtualBox VMs/Loki/Loki.vbox' is the target and '/home/awest/Virtual' is the symlink you are trying to create.

Also notice you have a blank space in the target you're wanting to link to. Wonder if that is causing issues?

Perhaps change 'VirtualBox VMs' to 'VirtualBox_VMs' or remove the space completely and try again. deadflowr may have some alternative solutions without using a symlink by the looks.

PS: What I mean is, because of the syntax used when creating a symlink, the system may be reading this much:

```
ln -s /home/awest/VirtualBox VMs/Loki/Loki.vbox
```

... and seeing an error because it's expecting this:

```
ln -s /home/awest/VirtualBox /VMs/Loki/Loki.vbox
```

... if you follow me. Once it sees a space it would be expecting the second part of the command, the symlink. Therefore, once it gets the error, it will ignore the rest of your command which actually creates the symlink:

```
/home/awest/Virtual
```

---

### Post by Aphexlog on 2015-01-28
Yes, I initially had that issue. I changed the name to VirtualboxVMs and there arived the new error message:
[COLOR=#000000]"sudo: .Loki.vbox: command not found"[/COLOR]

But at this point, I am thinking that my best bet is to create a alias for the VM
I am in the ~/.bashrc file but unsure where to drop the "alias lokivm='vboxmanage startvm Loki.vbox'" line within that file.

this is the text from the ~/.bashrc file:

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
fi


# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'




# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\$


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

### Post by deadflowr on 2015-01-28
I usually put stuff in the .bashrc in the top area in the space after the first entries, # for examples line.
Simply because I can be positive it is not in the middle of something.

That said, another even easier option is to make a file called .bash_aliases and add the aliases to that.
Simple as that, just make the file add the alias and save. No need to make it a #!/bin/bash or anything.
the path would be ~/.bash_aliases

Also the VirtualBox VMs folder has a space so in the terminal it should output with a \,  like VirtualBox\ VMs
which tells the system that those two words are actually connected, even though they are spaced apart.
When you don't add that \ after the VirtualBox then the system thinks those are two different things, and acts accordingly.
If that makes sense.

Also the name of the vm is whatever the name of the containing folder is, so in this case just Loki in the vboxmanage command.
No need to add the .vbox at the end...

---

### Post by ajgreeny on 2015-01-28
I think your problem results from the path you used, ie, **/home/awest/VirtualBox VMs/Loki/Loki.vbox** containing a space, so I think you may need
```
ln -s "/home/awest/VirtualBox VMs/Loki/Loki" /home/awest/Virtual
```
Note the quotation marks around the source pathway and no .vbox at the end; you need the actual file name.

I always think it a great pity that VB added that space to the default folder name for VMs, as it always needs a bit of extra thought to any processes in command-line involving those; thank goodness for autocomplete!

---

### Post by Aphexlog on 2015-01-28
So, I added the ~/.bash_aliases then I edit it to reflect this:
alias lokivm='vboxmanage startvm Loki'
[Side note - I chose not to use alias loki because it appears that there is a package named loki]
I reboot the terminal and now it is working
- thank you

---

