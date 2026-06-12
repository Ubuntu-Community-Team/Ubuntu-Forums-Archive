---
title: "[SOLVED] how to recover root password.??"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by mozartvn on 2008-06-11
hi all.
i have just installed ubuntu 8.04 live with windows XP. Plz help me, recover root password.
in boot screen,I had run "recover mode"-->"drop root shell"-->passwd to change pass, but it not work.
plz correct me. :confused::(
Thanks u.

---

### Post by wolfen69 on 2008-06-11
[THIS]("http://www.ubuntu-unleashed.com/2007/09/recover-forgotten-ubuntu-password.html") may help.

---

### Post by stchman on 2008-06-11
> **mozartvn said:**
> hi all.
i have just installed ubuntu 8.04 live with windows XP. Plz help me, recover root password.
in boot screen,I had run "recover mode"-->"drop root shell"-->passwd to change pass, but it not work.
plz correct me. :confused::(
Thanks u.

You just installed Ubuntu and already forgot your password????!!!!!!

In Ubuntu root does not have a password.  Your account by default administers the system with the use of sudo.  There is NEVER a need to login as root, EVER.

---

### Post by Joeb454 on 2008-06-11
If you want to use root in a terminal, run ```
sudo -i
``` if you want Nautilus to run as root (I don't recommend it, but hey :)) Hit Alt+F2 and type ```
gksudo nautilus
```

---

### Post by Sef on 2008-06-11
Moved to Absolute Beginners.

Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

Sudo gives you temporary root privleges, if you need root.  Otherwise, you work in a limited mode.  If you use it and have a secure password, then your chance of being hacked is greatly lessened.

---

### Post by aysiu on 2008-06-11
> **mozartvn said:**
> 
in boot screen,I had run "recover mode"-->"drop root shell"-->passwd to change pass, but it not work. What do you mean *it not work*? What happened exactly when you tried to change it? What error message did you get?

You know that when you type your password, [there will be no visual feedback, right? Your password change is still be accepted.](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by mozartvn on 2008-06-12
Thank all, I forgot the username, that is the main reason. My trouble was processed. :guitar:

---

### Post by kevdog on 2008-06-12
> **stchman said:**
> There is NEVER a need to login as root, EVER.

Hmmm, this seems like a overblown blanket statement.  While I agree in theory, I wouldn't say there is never a need to login as root!

---

### Post by stchman on 2008-06-12
> **kevdog said:**
> Hmmm, this seems like a overblown blanket statement.  While I agree in theory, I wouldn't say there is never a need to login as root!

All the years I have been using Linux I have never had to log in as root.

If I need root privileges I simply use sudo or gksudo.  I think you will find this opinion shared by many.

Also never run Firefox using sudo as this is a very bad thing.

---

