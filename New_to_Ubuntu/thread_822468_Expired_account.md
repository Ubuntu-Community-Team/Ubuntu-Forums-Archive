---
title: "Expired account?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by MarcDam on 2008-06-08
when i create an account (or try to) the terminal comes up with the following ```
Your account has expired; please contact your system administrator
chfn: PAM authentication failed
adduser: `/usr/bin/chfn test' returned error code 1. Exiting.

```
and it doesn't let me type in real name and the other personal stuff.
This happened after i by accident unlocked the root account and then locked it again.
Another thing disturbing me is that i can use the "sudo" command without typing my password after it sometimes.
So my actual question is how do i get my account back like it used to be without reinstalling Xubuntu.
I installed Xubuntu  days ago so i am a complete noob and need everything step by step.
I have read [this]("http://ubuntuforums.org/showthread.php?t=787373&highlight=Expired+account%3F") and it didn't help me.

---

### Post by MarcDam on 2008-06-09
Anyone?

---

### Post by SunnyRabbiera on 2008-06-09
sudo has a timeout, so you will have to make sure you type in your password every so often... If i remember right sudo has a 5 to 10 minute countdown

---

### Post by MarcDam on 2008-06-09
Where can i change my countdown?
And i don't think that is the problem because even when i acquire root by typing sudo -i then the same account creating problem is there.
Any other suggestions?

---

### Post by zwilrich on 2008-09-09
I was having the same problem and this fixed it.

From [https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755)

This seems to be related to the use of "passwd -l root".
Until the Debian fix shows up in hardy, here is a workaround, thanks to Nicolas François:

sudo passwd --unlock root
sudo usermod --lock root

---

