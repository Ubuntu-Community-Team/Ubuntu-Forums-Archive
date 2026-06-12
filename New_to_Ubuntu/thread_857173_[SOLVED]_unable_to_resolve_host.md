---
title: "[SOLVED] unable to resolve host"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by VorlonShadow on 2008-07-12
I am getting an error "unable to resolve host scottie" at various points when I'm using the command prompt.  scottie is the name of my Linux machine which I'm logged into.  Doing some research, I believe that the resolv.conf has something to do with this.  Here is the contents of that file:

search SME
nameserver 192.168.1.1
nameserver 127.0.0.1

First, 192.168.1.1 is my router, which also runs the DHCP service.  I have made sure that the static IP address that I have assigned to scottie is listed there.

127.0.0.1 is added, just because I saw that someone suggested doing this in another area, so I tried it, and it didn't help.  I don't think I'm running DNS on this machine, so I don't know that it would help anyway??

I'm running Ubuntu 8.04 Server.

Thanks,
Jesse

---

### Post by Elfy on 2008-07-12
check your hosts file

```
cat /etc/hosts
```

> kevin@kevin-desktop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	kevin-desktop

Mine match do yours

Edit - this should help if they don't match
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by UbuntuNerd on 2008-07-12
try this go to  system > Administration > Network

> unlock the widow with your password > go to the tab Host, on the second part of the the first line ( 127.0.0.1 ) type / replace the missing host by your host name, in my case that was jp-desktop the host given during the install hope it works

---

### Post by VorlonShadow on 2008-07-12
That was it. I recently changed my machine name by editing the /etc/hostname file.  I wasn't aware that I needed to edit the /etc/hosts file as well.  Newbie mistake.  Are there any other files that I need to change the machine name in?

Thanks,
Jesse

---

### Post by Elfy on 2008-07-12
That should be it - try a sudo apt-get update - should be fine though.

Can you mark thread solved please if it is:)

---

### Post by VorlonShadow on 2008-07-12
Excellent.  I'll mark it solved now.  Thanks again for your help.

---

### Post by nuclearj on 2008-07-12
Just wanted to say that this helped me with a similar problem.  Thanks!

---

### Post by Elfy on 2008-07-12
:d

---

