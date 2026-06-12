---
title: "Can not log as root"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by liamkincaid25 on 2008-06-14
Greetings to all. I am new to linux and decided to try Ubuntu. I use it for a couple of days and all was ok. Decided to try a double install with fedora, but all went wrong. Now I have both OS but only Ubuntu is loading. I was receiving help elsewhere on how to make the dual boot work. But I need information that can be get login as root. I have done evrything to try that  using su  and sudo but nothing seems to allow me to login as root from the terminal on desktop. This is what I get when I input the commands
 
 herbert@herbert-desktop:~$ su
Password: 
su: Authentication failure
herbert@herbert-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
herbert@herbert-desktop:~$ sudo herbert
[sudo] password for herbert: 
sudo: herbert: command not found
herbert@herbert-desktop:~$ root
bash: root: command not found
herbert@herbert-desktop:~$ su
Password: 
su: Authentication failure
herbert@herbert-desktop:~$ 
 Either says that the authentication failed or ask me for the password and when entered  send me to the same prompt herbert@herbert-desktop:~$
but not to root. If you can help me it will be appreciated ( I have other problems like screen resolution that can not be changed or message of "out of sugnal range" when booting or signing off but I can address that later) Thank you

---

### Post by dracayr on 2008-06-14
did you set a root password with ```
sudo passwd
```?

dracayr

---

### Post by sharks on 2008-06-14
its:
sudo su

---

### Post by sdowney717 on 2008-06-14
if you want to login to the gui desktop as root, then you can goto 
menu
system-admin-users and groups

setup root with the password you want

menu
system- admin - login window

click security tab
allow local system admin login

and you can login user root from the gui login boot screen

---

### Post by ukripper on 2008-06-14
You can use```
 sudo -i
``` too

---

### Post by liamkincaid25 on 2008-06-14
Waooooooooo Thank you guys this was FAST!!! I am logged as root now ( sorry elsewhere I was told to log as sudo  or su noone tolme me it was sudo su) You will see me around THANK YOU THANK YOU THANK YOU

---

### Post by ByteJuggler on 2008-06-14
Argh, please, do not enable the root account on Ubuntu, and **DO NOT recommend to newbies how to do this**.  Ubuntu deliberately locks the root account to close down a common attack vector.  Instead, use "sudo", which allows processes to run as root without enabling the root account.  

For more on root and sudo, [see here.]("https://help.ubuntu.com/community/RootSudo") (To liamkincaid25, please read this link, then lock your root account again with "sudo passwd -l root", if you've unlocked it.)

---

### Post by Joeb454 on 2008-06-14
Whenever I need root access for an extended period of time, I use ```
sudo -i
``` :) And you can mark your thread as solved from "Thread Tools" at the top of this page :)

---

### Post by spec-chum on 2008-06-14
The root password is disabled by default as a security feature on Ubuntu, as any potential attackers will know you have an account called root so they only need to crack the password.

You should be able to do anything you need root access for using sudo or gksu (sudo for terminal stuff, gksu for graphical).

The syntax is
```

sudo <command>

```

so if you needed, for example, to create a new folder somewhere other than your home folder (e.g. in /usr/local/) from the terminal you could use
```

sudo mkdir /usr/local/newfolder

```

For more information read here:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Gannon8 on 2008-06-14
If you are getting help on the boot loader GRUB, then you are probably trying to run the command grub as root right? Just type:
```
sudo grub
```
If you need a superuser terminal:
```
sudo bash
```
It is recommended, for security reasons, that you never set up a root account, and if you must, delete it after you are done with it.

---

### Post by Joeb454 on 2008-06-14
> **Gannon8 said:**
> 
If you need a superuser terminal:
```
sudo bash
```

I'd advise against that personally, and use ```
sudo -i
``` it's less likely to make things go wrong :)

---

