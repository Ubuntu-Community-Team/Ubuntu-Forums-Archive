---
title: "SU Login"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by donaldshelton on 2008-10-19
When I try to go to the root directory, I get a authentication failure message:

don@don-laptop:~$ su
Password: 
su: Authentication failure
don@don-laptop:~$ 

I use the same password as the one I use to login, which is also the same as the one I use for administrative functions.

What to do?

Don:guitar:

---

### Post by anjilslaire on 2008-10-19
```

sudo su

```

Be careful ;)

---

### Post by NorthernLights on 2008-10-19
Hi,

"su" command is disabled on a fresh Ubuntu installation. But since you got "sudo", type in "sudo -s" to achieve the same reseult.

See you!

---

### Post by SunnyRabbiera on 2008-10-19
Right, to preform administration tasks use sudo if prompted to use su in a tutorial.

---

### Post by bodhi.zazen on 2008-10-19
> **NorthernLights said:**
> Hi,

"su" command is disabled on a fresh Ubuntu installation. But since you got "sudo", type in "sudo -s" to achieve the same reseult.

See you!

Well, not exactly. su works just fine, but without an argurement it defaults to root and the root account is locked.

Ubuntu uses sudo.

For a root shell use :

```
sudo -i
```

For graphical applications (nautilus) use gksu.

See also : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Gone fishing on 2008-10-19
Thanks bodhi.zazen

However, I've always used sudo bash for a root shell can you give us a link or explain the differences between 

sudo -i
sudo -s
sudo bash

Thanks

---

### Post by bodhi.zazen on 2008-10-19
> **Gone fishing said:**
> Thanks bodhi.zazen

However, I've always used sudo bash for a root shell can you give us a link or explain the differences between 

sudo -i
sudo -s
sudo bash

Thanks

sudo -i is a log in shell and will use root's environmental variables.

sudo -s will give you a shell with your users environmental variables.

I think an example is best :

Try these commands :

```
sudo -s # enter password
echo $HOME #enter this command as root
exit #exit the root shell

sudo -i
echo $HOME
exit

sudo bash
echo $HOME
exit
```sudo bash starts a bash shell as root , but again does not change the environmental variables.

It is when you are writing files to your user's $HOME rather then /root that you can have problems.

For reference you need to read through the sudo man pages and configuration

[http://linux.die.net/man/8/sudo](http://linux.die.net/man/8/sudo)

---

### Post by bodhi.zazen on 2008-10-19
I am going to close this thread now as people keep posting information on how to set a root password. 

Ubuntu uses sudo and setting a root password is very rarely necessary. Setting a root password can break Ubuntu and is only supported when all else fails.

        [uwiki]RootSudo[/uwiki]

---

