---
title: "General Query Root User"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by awatkins1971 on 2013-04-14
I'm following the course activities given by the Open University covering Linux. They tell you how to become a root user etc. with sudo su. But how do you come out off the root ? Can anyone help?  Plus can anyone recommend a book that I can read and learn more about Linux? Thank you in advance

---

### Post by Cheesehead on 2013-04-14
> **awatkins1971 said:**
> But how do you come out off the root ?

Use the command 'exit' to return to a non-root shell prompt ($).

However, I have used Ubuntu for seven years, and use sudo very frequently. I use root regularly in Debian and other distros.
I have *never* needed to use root in Ubuntu, and strongly discourage it.

---

### Post by sisco311 on 2013-04-14
Just to make it clear. If you have sudo rights to start a root shell, then you should use```
sudo -i
```to start one. Iif not, but (there is and) you know the root password, then you should use ```
su -
```

Please read [uhelp]community/RootSudo[/uhelp]

 You can log out from a root (or any other) shell with the `exit' command or by pressing Ctrl+d (assuming that your shell dandles them).

  In Ubuntu, the `admin' users (like the first user created during installation) have full sudo rights, which means that they can use sudo to run any command as root or any other user. So, most of the time you don't need to start a root shell, because you are able to run a single command as root with sudo.

BTW, Welcome to the forums!

HTH

---

### Post by zrdc28 on 2013-04-14
If you are root all you have to do is "su username" will take you back to user!

---

### Post by bab1 on 2013-04-14
> **zrdc28 said:**
> If you are root all you have to do is "su username" will take you back to user!

Not true.  The original shell is still open. When you su username, you open  a new shell.  So now you have 3 shells open (username, root, username).  Exit is the proper way to close an open shell.

---

### Post by wickedpuppy on 2013-04-15
> **bab1 said:**
> Not true.  The original shell is still open. When you su username, you open  a new shell.  So now you have 3 shells open (username, root, username).  Exit is the proper way to close an open shell.

Agreed. In fact , doing that is very dangerous for production servers because the next person who uses the console might log out of the shell to find out that he/she automatically landed in a root shell! Best would be to exit or ctrl-d.

---

