---
title: "[SOLVED] What does 'S99' mean in the name of an init script?"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Peter Frank on 2008-09-19
The title is my question. I'm trying to learn about the basics of runlevels but after a few minutes of googling failed to find an explanation of the number.

---

### Post by ptn107 on 2008-09-19
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-boot-init-shutdown-sysv.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-boot-init-shutdown-sysv.html)

---

### Post by MegaJim on 2008-09-19
The number is the priority in which the script is executed; lower number = higher priority

---

### Post by unutbu on 2008-09-19
When the machine enters a runlevel, the scripts are executed in lexical order. 
If the scripts starts with a 'K' then the script is called with a 'stop' argument.
If the scripts starts with a 'S' then the script is called with a 'start' argument.
(All 'K' scripts are executed before any 'S' script).

S99 means the script is started, but only after scripts of the form Snn* are started, where nn < 99.

See [http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

---

### Post by andrewc6l on 2008-09-19
The scripts are started in order. S99 means it will start after S98, S97, 96... etc. In other words, if you have service yyy which requires service xxx to be running, then life is better if you have:

   S26xxx
   S27yyy

or some other Snn greater than S26 (such as S99, which would mean more or less "after everything else that is less than 99") :-)

Incidentally, Snn scripts start services, and Knn scripts stop services. Usually they're links to the same thing in /etc/init.d; S  is the equivalent of "service xxx start" and K is the equivalent of "service xxx stop".

---

### Post by iansane on 2008-09-19
something else of interest. Was reading about a autocad script.

It starts with S99. In the script is a line that tells the system the run level.

```

id:3:initdefault:

```

I looked and see they don't all have a line like this but I think if it is run level three, the symbolic link used to run it will be in the /etc/rc3.d folder and if it runs at run level 5, its link is in the rc5.d folder. 

Also when telling the system to run at a certain run level such as is required for installing nvidia drivers with the nvidia.sh script you use the command "telinit 3" to tell init to run in level 3.

Check out the links in the rcX.d folders and see how they point to the scripts in init.d that should help to understand them too.

---

