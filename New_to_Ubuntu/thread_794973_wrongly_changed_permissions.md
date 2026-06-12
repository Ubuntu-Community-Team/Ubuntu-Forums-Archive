---
title: "wrongly changed permissions"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by ene_dene on 2008-05-15
I've done a real mess. I wanted to change permission for my home dir as a root user and for some reason I've lost access to /. After that I've opened nautilus as root, went to / and changed permission to all directories except /home to be readable to all and acessed by root user. After restart x would not start because wrong permissions, for example:
```
startx
...
> Error: Canot open "/var/tmp/server-0.xkm" to write keyboard discrition

```
and similar errors.
Is there any way to return all the directories to default state of permissions? I don't know who to do it from command line.

---

### Post by sdennie on 2008-05-15
That sounds pretty lethal.  Files throughout / have varying permissions and doing any sort of blanket chmod or chown will almost certainly break the system.  As far as I know, after doing a massive permission change, it's probably going to be much faster to re-install rather than attempt to fix the permissions.  I believe the 8.04 installer can detect a /home directory and install the OS without destroying your data (that was an scheduled feature of the live disk but, I don't know if it made it in).

---

### Post by ZabiGG on 2008-05-15
Ooh, baby.

There's a way but it's gonna cost ya... are you willing to sweat blood and tears, and read ??? 

I won't agree to point you to it if you're not a thorough reader.

There are dangerous root commands in there only experienced users should rely on.

PM me (send me a private message) if you want the link

---

### Post by ene_dene on 2008-05-15
I've went to repair mode. There I've managed to start x as root user, changed the permissions to all files that are not /home to root can do it all and the rest can read all files and directories. After restart I can login as any user and I don't see and huge problems, but still need to be solved:
1. my sudo doesn't work, I get:
```
sudo something
sudo: /etc/sudoers is mode 0664, should be 0440
```
2. One of the users can't see buttons that minimise (_) and shut down windows (x).
Does someone know where should I change permissions to fix these problems?

---

### Post by sdennie on 2008-05-15
I really do think you are going to have to re-install.  Stuff like you've just described will happen frequently with wrong permissions and, although you may be able to cure the acute symptoms temporarily, the machine will never be the same.  A good example is your sudo problem.  You can't edit the file because you can't get root permissions via sudo because of permission problems.  So: *You can't edit the sudoers file because sudo can't read that file to see if you are allowed to...*

---

### Post by ene_dene on 2008-05-15
I will reinstall. I can't understand how this has happened. What I did was started nautilus with sudo nautilus command, then I went to user directory and changed permission for one user and after that I couldn't see the / directory that's when I had to try to change permissions of / dir... and now this problem.
Thanks all for your help.

---

### Post by Keith Hedger on 2008-08-03
This wont be of help now but I have done similar things so I created a small app to record/repair permissions so checkout: [http://code.google.com/p/perms/](http://code.google.com/p/perms/) for future use.

---

