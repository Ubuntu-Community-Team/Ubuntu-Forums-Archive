---
title: "update window title"
date: 2009-08-18
forum: Programming Talk
---

### Post by lavinog on 2009-08-18
I am trying to reproduce an issue with my taskbar flickering, but I need a simple script that will change a window title repeatability

I tried to do it by changing $PS1 a couple of times, but it only shows the last change.
```

PS1='\[\e]0;\u@\h:1 \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$'
sleep 1

PS1='\[\e]0;\u@\h:2 \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$'
sleep 1

PS1='\[\e]0;\u@\h:3 \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$'
sleep 1

PS1='\[\e]0;\u@\h:4 \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$'


```
tried executing it with ```
. scriptname
```

I don't have alot of gui experience so if someone knows of a quick way to do something like this it would be appreciated.

---

### Post by stroyan on 2009-08-18
You can just echo an escape sequence to set a gnome-terminal title.
These title changes will go by too quickly to see them all.
You could add a sleep command if you want to slow them down.
```

title () 
{ 
    echo -en "\033]2;$1\007"
}
for (( i=1; i<20000; i++ ))
do
  title $i
done

```

---

### Post by lavinog on 2009-08-18
That will work. Thank you

Where do I find documentation on the escape codes for future ref?

---

### Post by stroyan on 2009-08-18
> **lavinog said:**
> Where do I find documentation on the escape codes for future ref?

The gnome-terminal documentation is very weak at covering escape sequences.
The best approach is to look at the xterm escape sequences.
gnome-terminal attempts to match xterm (unless a feature has a security problem like getting a terminal to echo back arbitrary strings.)
Look here for a long list of xterm escape sequences-
[http://www.xfree86.org/current/ctlseqs.html](http://www.xfree86.org/current/ctlseqs.html)

---

### Post by lavinog on 2009-08-19
Thank you

---

