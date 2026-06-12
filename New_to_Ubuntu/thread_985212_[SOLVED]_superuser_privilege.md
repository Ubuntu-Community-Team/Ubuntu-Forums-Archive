---
title: "[SOLVED] superuser privilege"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Scunnered on 2008-11-17
I attempted to remove Opera from the system as I had made too many changes and intended to re-install.

Following an advice on an earlier post I entered dpkg -r opera in the terminal only to be told that superuser privilege was required.

Looking at the help section left me more confused. Can someone offer guidance on where I am going wrong.

Many thanks

---

### Post by morphos on 2008-11-17
sudo apt-get remove ?

---

### Post by Peter09 on 2008-11-17
to gain superuser privileges you need to enter sudo in front of your command.
```
sudo dpkg -r opera
```

---

### Post by LowSky on 2008-11-17
The command you should use is 

```
sudo apt-get remove opera
```

but the command you were looking to run was

```
sudo dpkg -r opera
```

---

### Post by jpoRS on 2008-11-17
Some background information:

sudo (short for Super User DO) is the command you put before any command that requires superuser or root access to preform.  It grants you temporary superuser powers, allowing you to preform superuser tasks without the danger of a superuser account.  It is one of the reasons that Linux is safe from viruses and other malware.

However that does not mean that sudo is "safe".  You have complete power over your system when you use sudo, and that means you can do anything, including deleting your entire hard drive.  Be very careful with what you do with sudo, and when in doubt seek a second opinion.  For more info on the dangers of sudo, check out [this.]("http://ubuntuforums.org/announcement.php?f=326")

Good luck!
jim

---

### Post by bodhi.zazen on 2008-11-17
See also [uwiki]RootSudo[/uwiki]

---

### Post by Scunnered on 2008-11-18
Many thanks to everyone for the code.

**jpoRS and bodhi.zazen**

My particular thanks for the explanations.  This will assist in furthering my understanding of Linux.  It is at times confusing when posts are made expecting the questioner to be fully aware of the different levels of control

---

