---
title: "Questions about inconsitencies with the PS1 in the default ~/.bashrc"
date: 2019-02-25
forum: Programming Talk
---

### Post by connectingmedia on 2019-02-25
Hi there!

I came across a inconsistency that made wonder if it is intentional and I am misunderstanding something.
In the default [FONT=courier new]~/.bashrc[/FONT] in my Ubuntu installation is the line
```
PS1='${debian_chroot:+($debian_chroot)}...'
```
And a bit further down I can see
```
PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
```
Now I do understand what the `${debian_chroot:+($debian_chroot)}` stands for and what the different quotes mean ([FONT=courier new]'[/FONT]-Quotes keep the variable literally, meaning it gets extended when the [FONT=courier new]PS1[/FONT] is being expanded/rendered and [FONT=courier new]"[/FONT] expand it right there, meaning it the expanded result is directly in the [FONT=courier new]PS1[/FONT]).
But what I am wondering about is why it is added as a string in the first one and as a variable expansion in the second.
From my (possibly limited) understanding it would make more sense to have the variables expanded late, so the second snippet should be
```
PS1='\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]'"$PS1"
```
Or am I missing something here?

If it's relevant I'm using Ubuntu 18.04.2 LTS.

---

### Post by connectingmedia on 2019-03-15
Bump

---

