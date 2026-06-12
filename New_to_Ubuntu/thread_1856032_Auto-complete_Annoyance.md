---
title: "Auto-complete Annoyance"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by CompBio on 2011-10-07
I'm running Ubuntu 11.04 Natty with a bash shell.  I've always liked auto-complete, but it has an awfully annoying behavior.  If I use an environment variable to point to a directory, such as:

```
MX=/home/projects/sequencing/hsapiens/data/fasta
```

Then if I try to use auto-complete:

```
cp $MX/
```

When I hit the <TAB> key, it becomes:

```
cp \$MX/
```

and from that point on, the interpreter can't understand what I'm typing.

I've seen this mentioned in a few places, but the only solution I've seen is to put up with it!  There has to be a way around this, right?

Right??  :confused:

---

### Post by CompBio on 2011-10-10
bump?

---

### Post by TeoBigusGeekus on 2011-10-10
Tried it on my system, everything's ok.
Could it be a dash thing? (I'm using bash)

---

### Post by Lisiano on 2011-10-10
```
lisiano@Lisiano-Ubuntu:/home$ bash --version
GNU bash, version 4.2.8(1)-release (x86_64-pc-linux-gnu)
Copyright (C) 2011 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
lisiano@Lisiano-Ubuntu:/home$ bash
lisiano@Lisiano-Ubuntu:/home$ export MX=/home/lisiano/Downloads
lisiano@Lisiano-Ubuntu:/home$ cp \$MX/bla .
cp: cannot stat `$MX/bla': No such file or directory
lisiano@Lisiano-Ubuntu:/home$ export MX=/home/lisiano/Downloads/
lisiano@Lisiano-Ubuntu:/home$ cp \$MX/bla .
cp: cannot stat `$MX/bla': No such file or directory
lisiano@Lisiano-Ubuntu:/home$ 
```Same with cd but it doesn't add the backslash. I'll try it on a server I admin and see if it's the same there, I remember using variables as path names.

EDIT: Server
```
GNU bash, version 3.2.25(1)-release (i686-redhat-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.
```
It resolved perfectly, even expanded the variable into the full string. Probably something in the shells. The servers .bashrc for my user only contains ls aliases and a few variables I set. The servers /etc/bashrc does look different than my Ubuntus /etc/bash.bashrc```
# /etc/bashrc

# System wide functions and aliases
# Environment stuff goes in /etc/profile

# By default, we want this to get set.
# Even for non-interactive, non-login shells.
if [ $UID -gt 99 ] && [ "`id -gn`" = "`id -un`" ]; then
        umask 002
else
        umask 022
fi

# are we an interactive shell?
if [ "$PS1" ]; then
    case $TERM in
        xterm*)
                if [ -e /etc/sysconfig/bash-prompt-xterm ]; then
                        PROMPT_COMMAND=/etc/sysconfig/bash-prompt-xterm
                else
                PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME%%.*}:${PWD/#$HOME/~}"; echo -ne "\007"'
                fi
                ;;
        screen)
                if [ -e /etc/sysconfig/bash-prompt-screen ]; then
                        PROMPT_COMMAND=/etc/sysconfig/bash-prompt-screen
                else
                PROMPT_COMMAND='echo -ne "\033_${USER}@${HOSTNAME%%.*}:${PWD/#$HOME/~}"; echo -ne "\033\\"'
                fi
                ;;
        *)
                [ -e /etc/sysconfig/bash-prompt-default ] && PROMPT_COMMAND=/etc/sysconfig/bash-prompt-default
            ;;
    esac
    # Turn on checkwinsize
    shopt -s checkwinsize
    [ "$PS1" = "\\s-\\v\\\$ " ] && PS1="[\u@\h \W]\\$ "
fi

if ! shopt -q login_shell ; then # We're not a login shell
        # Need to redefine pathmunge, it get's undefined at the end of /etc/profile
    pathmunge () {
                if ! echo $PATH | /bin/egrep -q "(^|:)$1($|:)" ; then
                        if [ "$2" = "after" ] ; then
                                PATH=$PATH:$1
                        else
                                PATH=$1:$PATH
                        fi
                fi
        }

        # Only display echos from profile.d scripts if we are no login shell
    # and interactive - otherwise just process them to set envvars
    for i in /etc/profile.d/*.sh; do
        if [ -r "$i" ]; then
            if [ "$PS1" ]; then
                . $i
            else
                . $i >/dev/null 2>&1
            fi
        fi
    done

        unset i
        unset pathmunge
fi
# vim:ts=4:sw=4
```It's running CentOS 5, so I'm not sure blindly copy-pasting the servers bashrc instead of Ubuntus will be a good idea, although worth a shot, note you must have a LiveCD or test it with a VM.

---

### Post by CompBio on 2011-10-11
Thanks!  I'll give that a shot.  It would be nice if there were a switch somewhere in the bashrc that I can toggle.

---

