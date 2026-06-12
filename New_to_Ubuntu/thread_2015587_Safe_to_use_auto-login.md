---
title: "Safe to use auto-login?"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by jickerson on 2012-07-03
Hi, I'm new to linux and had a security question. I'm an academic researcher and created a liveCD to turn unused machines at my university into computational nodes. However, in order to speed up the process, when i made the .iso file, i changed the settings so that it would auto-login into my account. I am just concerned about the security of this setup. The account still has a strong password on it, it just has auto-login enabled. My concern is that this leaves the computer vulnerable over the network, and that someone would be able to compromise the running system and mount & read/write to the hard drive installed. 

Also, I don't know if this matters, but once the system starts up, two python scripts are executed from rc.local (the second one being ppserver.py).

Does this compromise my system and leave it open to a network attack?

Thanks!

---

### Post by cbanakis on 2012-07-03
As far as I know, the only added security risk from having auto-login enabled, is that someone can sit down at the computer as use it without a password.

And even then, most settings and system files are still locked down.

You can't even install an app from the software center without a password.

In short, as far as I know, enabling auto-login does just that.
You still need a password for everything you do without auto-login, except for logging in locally.

---

### Post by Paqman on 2012-07-03
> **jickerson said:**
> 
Does this compromise my system and leave it open to a network attack?


Nope. Just because you're logging in automatically it's not like everything in your session has elevated privileges, and it certainly isn't going to open any gaping holes to the outside world.

---

### Post by sudodus on 2012-07-03
But they can run as servers for number-crunching without anybody logged in at all. Then nobody could fill the hard drives with personal files or use them for web browsing.

On the other hand, maybe you would be happy to keep them available for temporary users as well as using them for number-crunching.

---

### Post by jickerson on 2012-07-03
> **sudodus said:**
> But they can run as servers for number-crunching without anybody logged in at all. Then nobody could fill the hard drives with personal files or use them for web browsing.

On the other hand, maybe you would be happy to keep them available for temporary users as well as using them for number-crunching.
 
By this, do you mean that if I execute the python scripts via rc.local that they will run without even having to log in at all? In other words, the machines could sit at the login screen and still run the two processes in the background?

---

### Post by sudodus on 2012-07-03
> **jickerson said:**
> By this, do you mean that if I execute the python scripts via rc.local that they will run without even having to log in at all? In other words, the machines could sit at the login screen and still run the two processes in the background?
There are several ways to run programs (or scripts) without logging in. It is also possible to run cron jobs as root or as a user. Think of a server, that has no graphical user interface. You can also configure a headless server without monitor, keyboard and mouse.

You can log in locally or via the network, and a master computer can control slave computers.

---

### Post by Paqman on 2012-07-03
> **jickerson said:**
> the machines could sit at the login screen

Have you installed the desktop version, or the server version?

The most efficient thing to do would be use the server version to set the machines up headless and log in remotely to control them.

If you really wanted to get max cycles out of them you could start with the [minimal system]("https://help.ubuntu.com/community/Installation/MinimalCD/") and only install the actual packages you needed to execute your tasks and communicate.

---

### Post by jickerson on 2012-07-03
> **Paqman said:**
> Have you installed the desktop version, or the server version?

The most efficient thing to do would be use the server version to set the machines up headless and log in remotely to control them.

If you really wanted to get max cycles out of them you could start with the [minimal system]("https://help.ubuntu.com/community/Installation/MinimalCD/") and only install the actual packages you needed to execute your tasks and communicate.

Desktop version. The problem that I run into as far as controlling remotely is that I won't know the IP addresses of the nodes at startup (and more than likely, my master node won't be on the same set of addresses as the slave nodes, like 192.168.4.xxx and 192.168.8.xxx) That is what the first python script is for. Its job is to identify the ip address of the slave and report it to a message queue (of sorts) that my master node will read from once all the slaves have been started.

---

