---
title: "sudo: unable to resolve host"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by MFelkins on 2008-04-28
I am trying to install some software and one of the steps is to edit the source.list file. I keep getting this error;

mfelkins@mfelkins-desktop:~$ sudo
sudo: unable to resolve host mfelkins-desktop
mfelkins@mfelkins-desktop:~$ 


Note my machine is named mfelkins-desktop. So what is up with this? It can't find itself? The last thing I need is 20 something angst.

By the way. Brand new install of the Hardy Heron 8.04

---

### Post by Oldsoldier2003 on 2008-04-28
> **MFelkins said:**
> I am trying to install some software and one of the steps is to edit the source.list file. I keep getting this error;

mfelkins@mfelkins-desktop:~$ sudo
sudo: unable to resolve host mfelkins-desktop
mfelkins@mfelkins-desktop:~$ 


Note my machine is named mfelkins-desktop. So what is up with this? It can't find itself? The last thing I need is 20 something angst.

By the way. Brand new install of the Hardy Heron 8.04
check your /etc/hosts and make sure the host name matches /etc/hostname

---

### Post by Rocket2DMn on 2008-04-28
You can post the hosts file for us, too
```
cat /etc/hosts
```
I had this problem after upgrading and Oldsoldier's suggestion got me back on track.  My computer name had changed in /etc/hosts to something a little different, but it was a quick fix.

---

### Post by MFelkins on 2008-04-28
It taged my AD domain after the machine name. So how do I change it or add another line? sudo does not work

---

### Post by MFelkins on 2008-04-28
mfelkins@mfelkins-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 mfelkins-desktop.ad-ent

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
mfelkins@mfelkins-desktop:~$

---

### Post by MFelkins on 2008-04-28
mfelkins@mfelkins-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 mfelkins-desktop.ad-ent

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
mfelkins@mfelkins-desktop:~$

---

### Post by Oldsoldier2003 on 2008-04-28
change:
```
127.0.1.1 mfelkins-desktop.ad-ent
```
to:
```
127.0.1.1 mfelkins-desktop
```

---

### Post by Rocket2DMn on 2008-04-28
> **MFelkins said:**
> mfelkins@mfelkins-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 mfelkins-desktop.ad-ent

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
mfelkins@mfelkins-desktop:~$

Yeah looks like it got messed up.  Since sudo isn't working, we will try gksudo
```
gksudo gedit /etc/hosts
```
Change the line
```
127.0.1.1 mfelkins-desktop.ad-ent
```
to
```
127.0.1.1 mfelkins-desktop
```
Save and close and you should be good.  If it won't let you run gksudo, you need to reboot, enter the recovery kernel from GRUB (second option) and run
```
nano /etc/hosts
```
Move around with the cursor using the arrow keys and change the line, then do CTRL+X to close, and tell it to save when prompted, then reboot normally with
```
reboot
```

---

### Post by Oldsoldier2003 on 2008-04-28
> **Oldsoldier2003 said:**
> change:
```
127.0.1.1 mfelkins-desktop.ad-ent
```
to:
```
127.0.1.1 mfelkins-desktop
```

since you can't sudo and you probably don't have SU available unless you enabled root login, you'll need to reboot to recovery mode to edit the file as root

---

