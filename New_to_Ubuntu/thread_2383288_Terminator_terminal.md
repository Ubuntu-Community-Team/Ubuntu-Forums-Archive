---
title: "Terminator terminal"
date: 2018-01-23
forum: New to Ubuntu
---

### Post by mac187 on 2018-01-23
I just downloaded terminator, i needed it because of im using a lot of windows, but one disturbing thing.. My root name is grey .. How to make it green like the default terminal in Ubuntu?

Thanx

---

### Post by again? on 2018-01-23
Edit /root/.bashrc
Uncomment the line...
```
force_color_prompt=yes
```
In my file it's line #39.

---

### Post by mac187 on 2018-01-23
In my bashrc file is this :

```
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
```



dont understand exactly which one to unmark :/

---

### Post by again? on 2018-01-23
There's only 1 line with "#force_color_prompt=yes".
Remove the "#" at the beginning of that line.

---

### Post by mac187 on 2018-01-23
nothing changed :/ root name is still gray :/

---

### Post by again? on 2018-01-23
When logged into a terminal as root, run
```
source /root/.bashrc
```
or just close all terminals and restart terminator.

You do mean when logged into terminator as root don't you?

---

