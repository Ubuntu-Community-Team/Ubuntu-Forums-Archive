---
title: "Error using sudo"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Wantingtolearn on 2008-10-22
kmichaellong@kmichaellong-laptop:~$ sudo
sudo: unable to resolve host kmichaellong-laptop
kmichaellong@kmichaellong-laptop:~$ 

Every time I try to use superuser in terminal, I get this message.  What am I doing wrong and how can I fix this?  Thank you for you help!!!

---

### Post by stephanvaningen on 2008-10-22
Hey! Try this:
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)
Hope it helps,

---

### Post by fooman on 2008-10-22
please post the output of:

```
cat /etc/hosts
```

---

### Post by Wantingtolearn on 2008-10-22
I was looking at that thread, but this is what I saw when I did that

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Should I follow the same guidelines?

Thank you!

---

### Post by fooman on 2008-10-22
i think you may have missed a few lines above "# The following lines are desirable for IPv6 capable hosts"

if they are there...please post.

---

### Post by blazercist on 2008-10-22
its caused by /etc/hosts your hostname will probably have a .WORKGROUP suffix whihc needs to be removed.

---

### Post by Sarmacid on 2008-10-22
Run

```
sudo gedit /etc/hosts
```

And add this lines at the top of the file

```
127.0.0.1 localhost
127.0.1.1 kmichaellong-laptop

```

---

### Post by Wantingtolearn on 2008-10-22
Sorry, I did miss the top part, I am still very new to this and everyone is very helpful

127.0.0.1 localhost
127.0.1.1 kmichaellong-laptop.domain.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Thank you

---

### Post by fooman on 2008-10-22
well like Sarmacid posted above...try this:

```
gksudo gedit /etc/hosts
```

when it opens,  change 

127.0.1.1 kmichaellong-laptop.domain.com

to:

127.0.1.1 kmichaellong-laptop

save and close the file. that should work.

---

### Post by Sarmacid on 2008-10-22
Forget my last post. Run

```
sudo gedit /etc/hosts
```

And change 
```
kmichaellong-laptop.domain.com
```
to
```
kmichaellong-laptop
```

Bah, fooman beat me to it >_<

---

### Post by Wantingtolearn on 2008-10-22
I went ahead and did that, but nothing seems to be coming up.  I see something that pops up outside of terminal saying, "starting administr..." but terminal just shows a blinking "|" and the tab that pops up saying, "starting administr..." goes away.

---

### Post by No-Neck on 2008-10-22
```
sudo nano /etc/hosts
```?

---

### Post by bodhi.zazen on 2008-10-22
Well, if the OP has not root access they will need to either boot to recovery mode and use nano or boot a live CD and mount the ubutnu partition from there.

In recovery mode

```
nano -w /etc/hosts
```

Add in your changes, Ctrl-X to exit, type Y to save changes

then
```
telinit 2
```

---

### Post by Wantingtolearn on 2008-10-22
I tried that and when I put in the code I see a tab show up that says "starting administr..." then it disappears, and terminal goes to a blinking "|"

---

### Post by bodhi.zazen on 2008-10-22
What did you try exactly ? Did you boot to recovery mode and edit your /etc/hosts with nano ?

---

### Post by Wantingtolearn on 2008-10-22
Sorry, I am not sure how to reboot in recovery, I really am a beginner.

---

### Post by bodhi.zazen on 2008-10-22
> **Wantingtolearn said:**
> Sorry, I am not sure how to reboot in recovery, I really am a beginner.

Reboot Ubuntu. At the boot (grub) screen hit escape. One of the options will be recovery mode. This will boot you to a menu with a list of options. Select I think boot to command line (sorry I forget). This will boot to a command line only, thus nano ;)

---

### Post by tonymoloney on 2008-10-22
I get the same message, but it doesn't stop me using sudo, so I've just ignored it.

---

