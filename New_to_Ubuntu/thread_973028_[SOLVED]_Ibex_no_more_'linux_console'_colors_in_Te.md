---
title: "[SOLVED] Ibex: no more 'linux console' colors in Terminal!"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by cisforcojo on 2008-11-06
I'm not sure why this has happened but since I installed Ibex, I can no longer see the 'linux colors' in terminal to make it a little easier for identifying executables and such. Anyone know why this might be??? Thanks!

---

### Post by philinux on 2008-11-06
Just tried the ls command and I got colours. Try looking under profile preferences. Mind you I've not changed anything.

---

### Post by cisforcojo on 2008-11-08
Yeah I have changed the settings, exactly what I used to have but no luck!
I'm wondering if this could be some remnant from my old system haunting me. I have /home on a separate partition.

---

### Post by Jeff250 on 2008-11-08
Does the prompt have color?
e.g.
```
user@host:~$
```
^^^ is that in color?

What if you say:
```
ls --color=auto
```
Is the output of that in color?

If that fixes it, then open ~/.bashrc in your favorite text editor and add the following lines:

```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
fi
```

The above will enable colorful ls only for *new* instances of the bash shell, so exit the shell, and then restart it for the fix to be permanent.

---

### Post by cisforcojo on 2008-11-08
That did it! (.bashrc addition) Thanks!

---

