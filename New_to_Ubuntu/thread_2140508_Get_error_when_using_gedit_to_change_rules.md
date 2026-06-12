---
title: "Get error when using gedit to change rules"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by kneedalz on 2013-04-29
Keep getting this error when I'm trying to add this rule so I can root my Nexus 4
```
jesse@HP-Mini:~$ sudo gedit /ect/udev/rules.d/99-android.rules
[sudo] password for jesse: 

(gedit:4639): IBUS-WARNING **: The owner of /home/jesse/.config/ibus/bus is not root!

```

I just loaded Ubuntu a week ago on this HP mini. It is the only operating system on here and I completely wiped the hd before I installed.

---

### Post by lykwydchykyn on 2013-04-30
So, iBus is an input service which gedit presumably utilizes.  

When you "sudo" a command, you are running the command as root, and root owns the process.  You don't, however, completely become root, because your environment remains yours.  Which means "$HOME" or "~" is not root's home, but yours; and thus, when an application or service invoked by sudo looks for config files in "$HOME/.someconfig", it's looking in your home directory, not root's.

The upshot, then, is that when you run "sudo gedit", root is running gedit with your config files, and this ibus service is saying "wait, you're accessing jesse's ibus configs, but you're not jesse -- you're root", and it's warning you because this could be a potential problem at some point.

Presumably, using "gksudo" instead of "sudo" might fix this issue, or perhaps running "sudo -i gedit", which will use root's environment instead of yours.  I can't test this, since I haven't got gedit installed.

---

### Post by kneedalz on 2013-04-30
Thank you! Both worked actually. Is gksudo an administrative command for the whole system as opposed to individual log ins? What is the -i command doing?

---

### Post by lykwydchykyn on 2013-04-30
> **kneedalz said:**
> Thank you! Both worked actually. Is gksudo an administrative command for the whole system as opposed to individual log ins? What is the -i command doing?

sudo is just a straightforward "do the following as root" command.  Graphical environments have a lot of things going on, services that applications talk to, interprocess communication, special environemnt variables, etc.  gksudo is just an add-on to sudo that (1) presents a GUI login screen and (2) takes care of some of those extra considerations for working as another user in a graphical environment.  

Like I said, the '-i' switch sets up root's environment for the command to be run; without that switch the command runs in your environment. 

An "environment" in this instance is just a set of variables that are set up for your login session.  You can view your environment by running the "env" command.  That might make things a little clearer.

---

