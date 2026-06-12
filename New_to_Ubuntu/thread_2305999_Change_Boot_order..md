---
title: "Change Boot order."
date: 2015-12-11
forum: New to Ubuntu
---

### Post by stephen-maxwing on 2015-12-11
and of course the first question is how to change boot order.  i start up normally, but if i don't stay near computer it boot into U, and i want to start in Windows. So how to reorder the grub file. oh i have searched and it appears everyone has a problem, i just have an inconvenience.

---

### Post by howefield on 2015-12-11
Post moved to its own thread and titled accordingly.

---

### Post by slickymaster on 2015-12-11
Moved to a thread of its own.

---

### Post by grahammechanical on 2015-12-11
The person who started this thread wants to do a similar thing. You can learn from the mistakes of others. Note the information provided by efflandt in post #7

[http://ubuntuforums.org/showthread.php?t=2305787&p=13405120#post13405120](http://ubuntuforums.org/showthread.php?t=2305787&p=13405120#post13405120)

You will need to make the edits using a text editor that has been loaded with administrator privileges. When I edit system configuration files I use Gedit and I start it with this command

```
sudo -H gedit
```

We can load Gedit and load a document at the same time with something like this.

```
sudo -H gedit /etc/default/grub
```

You will need to add the lines

> GRUB_DEFAULT=saved
GRUB_SAVEDFAULT=true

to this

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


the # symbol tells grub to ignore that instruction 

and then run

```
sudo update-grub
```

Regards.

---

