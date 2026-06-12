---
title: "help, cant update or install...?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by NeoEIRE on 2008-09-22
for some reason i get this message #1 when i try updating or installing stuff, and when i cut and paste the command into terminal it says #2..


#1--- E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


#2--- switch@switch-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
switch@switch-desktop:~$ 



i am the admin of this PC, i checked all the boxes, so i have no idea why this is comming up?

thanks
neoeire

---

### Post by echo314 on 2008-09-22
Try running ```
sudo dpkg --configure -a
```

It should elevate your privileges temporarily. With Linux (in most cases) you only elevate your privileges when you need to.

---

### Post by Mornedhel on 2008-09-22
> **NeoEIRE said:**
> i am the admin of this PC

Nope, you're not. root is. Unless you specified otherwise after the installation.

You need to prefix your command with sudo, as in "sudo dpkg --configure -a". This will prompt for your user password.

More information on sudoing is available somewhere in the stickies, but it boils down to this : regular users can be granted temporary administration privileges for most commands if they are in the sudoers file. (You most certainly are.)

---

### Post by NeoEIRE on 2008-09-22
> **echo314 said:**
> Try running ```
sudo dpkg --configure -a
```

It should elevate your privileges temporarily. With Linux (in most cases) you only elevate your privileges when you need to.

this worked, but i have one broken packet?

----You have 1 broken package on your system!
----Use the "Broken" filter to locate it


what is this and how do i fix it please... now this is stopping me for updating...

---

### Post by NeoEIRE on 2008-09-22
> **Mornedhel said:**
> Nope, you're not. root is. Unless you specified otherwise after the installation.

You need to prefix your command with sudo, as in "sudo dpkg --configure -a". This will prompt for your user password.

More information on sudoing is available somewhere in the stickies, but it boils down to this : regular users can be granted temporary administration privileges for most commands if they are in the sudoers file. (You most certainly are.)

i tried to log into the "root" before but no luck, i never put a password on it so i have no odea how to access it...?

i am curious how to do that, but my problem was fixed...

---

### Post by jpoRS on 2008-09-22
You can't "log into" root.  By putting "sudo" in the beginning of commands you are temporarily giving your user root privileges.  

There are a few ways you can make your user have root privileges all the time, but it compromises the security of your system, and thus nearly everyone advises against it.

Good luck,
jim

---

### Post by Mornedhel on 2008-09-22
The root account is not enabled by default. You can enable it, but it's not recommended (for security purposes). For your needs, sudo should be enough.

---

### Post by eeeandrew on 2008-09-22
A good common trick for running commands in terminal.

If you need to run a large number of commands all with root privelages instead of typing sudo command1, sudo command2. you can instead type

> sudo -s

you will notice that the prompt changes from user@computer to root@computer.

you can then enter all commands with root access without sudoing every time.

hope you find that useful,
Andrew

---

### Post by hyper_ch on 2008-09-22
have a read here:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by NeoEIRE on 2008-09-25
> **NeoEIRE said:**
> this worked, but i have one broken packet?

----You have 1 broken package on your system!
----Use the "Broken" filter to locate it


what is this and how do i fix it please... now this is stopping me for updating...

need help with this as its stopping me from updating.... whats broken package and how do i fix it please????

---

### Post by zvacet on 2008-09-25
```
sudo apt-get -f install
```

---

