---
title: "aliased commands doesn't work in bashscripts"
date: 2009-01-20
forum: Programming Talk
---

### Post by monkeyking on 2009-01-20
Hey, I've added som huge alias commands in my .bashrc, these work!

But I've made a bash script that uses these alias' but the script complains that it doesn't know them.

Doesn't a script "inherit" all sys vars from .bashrc 
Does anyone know how to bypass this,
do I need to do source .bashrc

thanks in advance

---

### Post by stylishpants on 2009-01-20
It's possible that this is your problem:

```

fhanson@fhanson:~$ head -6 /etc/skel/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

```

The non-interactive shell that is started to run your shell script is likely reading .bashrc only up to the last line shown above.

If your aliases are defined in .bashrc below that line, then they would not be read.

---

### Post by skoorbevad on 2009-01-24
Try adding '. ~/.bashrc' near the beginning of your script.  Or, '. ~/.bash_profile' if you use .bash_profile.

Or, redefine the aliases inside your script if you only want a couple of them, but I'd suggest calling the actual command that's aliases instead of the alias itself within the script.

---

