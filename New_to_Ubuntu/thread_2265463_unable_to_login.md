---
title: "unable to login"
date: 2015-02-15
forum: New to Ubuntu
---

### Post by madhu4 on 2015-02-15
I have installed ubuntu 12. I am trying to login in ubuntu server but  no luck.  Ican able to log snd through the putty.

please let me know how to resolve th issue.

---

### Post by TheFu on 2015-02-15
Welcome to the forums.

Putty is an ssh client. That requires and ssh-server be installed and secured. Do this on the ubuntu server:
```
sudo apt-get install openssh-server fail2ban
```

During the server install, you could have selected "ssh server" from the options. That is the only one of those checkboxes I check for every install.

You probably want to set a static IP for the server too - otherwise your putty won't be able to find the server from boot to boot.

At your level, it will save you time to work through a server setup book for the next 6 weeks or so. I cannot recommend one, but there must be many out there.  Don't forget about help.ubuntu.com

---

### Post by bill19 on 2015-02-18
If you can't even log in to Ubuntu, how can you install an open ssh-server and run something on the ubuntu server?

---

### Post by bill19 on 2015-02-18
can any of this be done through the guest login?

---

### Post by Frogs Hair on 2015-02-18
The guest account doesn't allow the use of sudo commands. Ctrl + Alt + F1 will open the tty terminal and after login ,password, and the installation command / instructions in The Fu's post you can enter the following.```
 sudo reboot
```

---

### Post by TheFu on 2015-02-18
> **bill19 said:**
> If you can't even log in to Ubuntu, how can you install an open ssh-server and run something on the ubuntu server?

You need "console" access as the original userid that installed the OS from the same method you installed it.  You didn't mention any VPS, remote server or virtualization, so you probably loaded it on a physical machine.  Login using the same account that was setup during the install, then install the ssh server as said above.

Guests cannot do anything ... well, guests shouldn't be able to anything system-wide and we mostly trust that as true.  Ubuntu is a multi-user system with different levels of access.

---

