---
title: "Memory Snapshot"
date: 2010-01-24
forum: Programming Talk
---

### Post by n00bi3 on 2010-01-24
Hi everyone,

I am trying to dump an executables image on the memory to a file.I tried /proc/PID/mem but no luck.File exists but gives this :

cat: mem: No such process

Is there an Ubuntu related trick ? Because on other distros I can do it.

Thanks

---

### Post by n00bi3 on 2010-01-25
No one has any idea ?

I guess ubuntu sucks at low-level development things and I need to change my distro immediately.

I recommend you all Slackware, it is way too much better than Ubuntu.

---

### Post by napsy on 2010-01-25
Care to share why slackware is better?

---

### Post by MadCow108 on 2010-01-25
it has nothing to do with the distribution, just with the installed programs
a developer should be able to install what he needs and not be dependent on default installations...


one way of doing it needs gdb (gnu debugger) installed.
set ulimit -c to whatever you need
attach gdb to the process (gdb --pid=number)
>gcore filename
>detach

voila a coredump has been saved
you can automate that with a gdb script

---

### Post by n00bi3 on 2010-01-25
Because it conserves default linux architecture, if you are familiar with unix and derivations you will be just fine working with Slack, for ubuntu it has diiferent characteristics than other distros you need to specifically have know-how knowledge for it.

Correct if I am wrong but when I try to some system stuff (like cat /proc/PID/mem) it behaves different than general linux behaviour.

I might be wrong thought, just observation.

---

### Post by MadCow108 on 2010-01-25
as far is I know its normal to not be able to "cat" the memory
you need to attach to it with ptrace first
thats something cat does not do => use another program (like gdb, see above)

maybe slackware changes this behavior, but then your argument would be wrong way round

but what I suspect is that you have an very outdated source.
"catting" any process memory is a security problem which was fixed ages ago.

---

### Post by n00bi3 on 2010-01-25
well, I am not planning to use the catted version of mem, I am just trying to access to the file and it seems that I can not do it in anyway.

my ulimit is already large to dump the core but gdb will dump the entire image of the executable or some parts ?

I mean when I dump the executable after that I will put it as a binary to somewhere on the disk and call that location from rawfs driver (direct disk access)

I am about to try it know I hope it works.

---

### Post by napsy on 2010-01-25
You can't just access the memory region belonging to another process with every program. You could try to run the program under gdb and then use some gdb command to get the contents of the RAM.

---

