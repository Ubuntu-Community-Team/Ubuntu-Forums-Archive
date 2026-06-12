---
title: "Su and Sudo question"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by moose4204l on 2008-06-02
Is there a way to give privilages just to su instead of sharing it with sudo. basically i have a file that i run, its a chmod and chown script i run as su user for a folder. su has its own password. sudo is obviously my password for my login but sudo obviously can run the script. is there away to make these privileges different so you have to enter the su password in order to run it?

---

### Post by SunnyRabbiera on 2008-06-02
In ubuntu the root account is disabled but its possible to get one, but its not advised.
I would just stick to sudo, it does its job just as well and in some places its better then su.

---

### Post by kerry_s on 2008-06-02
since you've already cut your security in half by activating root, just remove the user from sudoers.

sudo is safer and is the default for a reason, having a root user, only the password needs to be cracked. with sudo you need to find the name of the user, then crack the password.

---

### Post by dracayr on 2008-06-02
> Is there a way to give privilages just to su instead of sharing it with sudo

you don't have to give *privileges* to su (the root user). he's the "god" of your system. He can do everything

dracayr

---

### Post by moose4204l on 2008-06-02
i dont have a root user, i dont think. i just have my account and i gave a script root priviliges to somewhat password protect it. so to r/w/e you need to either sudo it or su then execute. is that the same thing as activating root?

---

### Post by SunnyRabbiera on 2008-06-02
yes using sudo is practically root, if you are worried about security then dont worry... this isnt windows :D

---

### Post by dracayr on 2008-06-02
no it isn't. Just understood you wrong. But as you are talking aubout *su*, I guess you have activated it... But as as the name of *sudo* indicates, it's only purpose is to execute commands as root. so no to your question. But I guess you could (I'm not sure if It'll work) create another user with the user-ID 0

dracayr

---

### Post by ByteJuggler on 2008-06-02
> **moose4204l said:**
> i dont have a root user, i dont think. i just have my account and i gave a script root priviliges to somewhat password protect it. so to r/w/e you need to either sudo it or su then execute. is that the same thing as activating root?

su with no parameters, changes the logged on user to the root user, requesting the root password.  Normally however, the root user account is **locked** on Ubuntu.  Thus rendering su unusable, except for changing to other normal accounts. (Think "su joeuser".) Thus, if you're using su to get root access, then you must've unlocked the root account and given it a passwd somewhere along the line.  This is what is not advised on Ubuntu as explained above. 

If you want to have the script run as root even when started by an arbitrary user, then you can set the "setuid" bit on the file permissions, and make sure the script is owned by root.  Then the script will always start under the root account regardless of who starts it.  (It can then use the su command to change to another user's context if it wants to of course.)  Needless to say, such a script can potentially be a huge security hole so be careful.

To set the setuid bit on a file and make it world executable, do e.g.

```
chmod 4755 executablefilename
```

Then do 

```
chown root.root executablefilename
```

You may need to prepend sudo in front of the commands. After this, the script will be "setuid root", as explained above.

---

### Post by moose4204l on 2008-06-02
is there away to undo my su from before, you said i unlocked it. is there away to re lock it or only from a fresh install?

---

### Post by kerry_s on 2008-06-02
you can lock it with->

**sudo passwd -l root**

---

