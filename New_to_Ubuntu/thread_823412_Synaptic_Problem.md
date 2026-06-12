---
title: "Synaptic Problem"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by bern1939 on 2008-06-09
Using 8.04 and unable to open Synaptic.
Yes I have checked the posts on this without success.
Using the terminal route I get the following:

bernard@bernard-desktop:~$ update-manager

current dist not found in meta-release file


When I insert 'synaptic' at the terminal I am told in a dialog box that it will start without administrative privileges...............which of course is useless.

Any suggestions as to how I can get this vital component to work?

Thanks


Bern

---

### Post by SunnyRabbiera on 2008-06-09
try sudo apt-get update?

---

### Post by bern1939 on 2008-06-09
Thanks....did that and it ran through a list.
The update manager says ....yes it is up-to-date!

However I still cannot open Synaptic to install pkgs.
Yes I can use sudo apt-get install prog from the terminal but would like to be able to use the graphical Synaptic.

Thanks


Bern

---

### Post by SunnyRabbiera on 2008-06-09
try to reinstall synaptic?
if you need a more graphical tool you can try aptitude, its a terminal application but has a gui like interface.

---

### Post by ukripper on 2008-06-09
in terminal type this:
```
sudo dpkg --configure -a
```

if package is broken it will fix it for you.

---

### Post by bern1939 on 2008-06-09
bernard@bernard-desktop:~$ sudo dpkg --configure -a
sudo: unable to resolve host bernard-desktop
bernard@bernard-desktop:~$ 

I wonder what's going on here?

Bern

---

### Post by SunnyRabbiera on 2008-06-09
Hmm, well you can also try adept too for a graphic front end...
Are you sure you didnt mess with your permissions or anything?

---

### Post by ukripper on 2008-06-09
Can you post your hosts file here do following:

```
gedit /etc/hosts
```

---

### Post by bern1939 on 2008-06-09
THis is the result of your suggestion:

127.0.0.1 localhost
127.0.1.1 bernard-desktop.Eircom

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Bern

---

### Post by bern1939 on 2008-06-09
Just an addition to this:

When I do the following this is the result......however Synaptic does open and I am able to install from it!!!

bernard@bernard-desktop:~$ sudo synaptic
sudo: unable to resolve host bernard-desktop
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
bernard@bernard-desktop:~$ sudo synaptic
sudo: unable to resolve host bernard-desktop

What could be wrong here?

Bern

---

