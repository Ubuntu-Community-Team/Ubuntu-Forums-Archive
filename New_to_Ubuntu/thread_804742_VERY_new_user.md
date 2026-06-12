---
title: "VERY new user"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by DannyDKing on 2008-05-23
I just purchased a new Dell server, SC-440. I installed Fedora as the operating system. 

I know someone is going to laugh, :lolflag: but when I went and installed Ubuntu all I got was a black screen with my name as a Cursor.

:confused: Is this normal? Remember I have only used Windows and DOS my entire life. This is VERY new to me.

Thank you for your time and your patience

Danny

---

### Post by bwhite82 on 2008-05-23
Which version of Ubuntu did you install? Was it the server version?

---

### Post by SlappyPappy on 2008-05-23
Try downloading the LiveCD version of Ubuntu and running the OS off of the disk to check compatibility with your hardware. It's a nice way to do a general test.  :)

---

### Post by DannyDKing on 2008-05-23
Yes it was the server version 8.04

> **Soldierboy said:**
> Which version of Ubuntu did you install? Was it the server version?

---

### Post by DannyDKing on 2008-05-23
Well this is a very new server. It didnt have any software on it when I got it. I installed Fedora but can go with anything.

I want to do a home web server with email, MySQL, perl, php, ASP, etc.

> **SlappyPappy said:**
> Try downloading the LiveCD version of Ubuntu and running the OS off of the disk to check compatibility with your hardware. It's a nice way to do a general test.  :)

---

### Post by bwhite82 on 2008-05-23
I've never used the server version, however, I'm pretty sure that it comes with no graphical desktop environment. Most veteran server administrators prefer the command line for maintenance tasks. I could be wrong on that however. (As I've never used Ubuntu's server version). If you have a black screen and a command prompt, everything is probably working fine.

---

### Post by Barrucadu on 2008-05-23
If you have never used Linux before, install the desktop edition. The server edition is more for people who know what they're doing. All software for the server edition will work on the desktop edition - just possibly not as well, as the server edition is, well, optimized for servers.

---

### Post by roe_polak on 2008-05-23
What you're seeing is the command line. If you're not comfortable with the command line you can install the default ubuntu graphic environment (using Gnome) by entering

```
sudo aptitude install ubuntu-desktop
```

This will offer you a good dekstop environment from which you can run your server.

---

### Post by DannyDKing on 2008-05-23
Then can I use the desktop version for what I am wanting to do?
Does it have a graphical interface?

Thanks for the help so far
Danny

> **Soldierboy said:**
> I've never used the server version, however, I'm pretty sure that it comes with no graphical desktop environment. Most veteran server administrators prefer the command line for maintenance tasks. I could be wrong on that however. (As I've never used Ubuntu's server version). If you have a black screen and a command prompt, everything is probably working fine.

---

### Post by Barrucadu on 2008-05-23
You can use the desktop edition, and it will do what you want to with a GUI. Unless you're constantly requesting things from this server, you won't notice a difference in performance.

---

### Post by bwhite82 on 2008-05-23
> **DannyDKing said:**
> Then can I use the desktop version for what I am wanting to do?
Does it have a graphical interface?

Thanks for the help so far
Danny

You have so many options with Linux. :) You can either install the package "ubuntu-desktop" onto your server installation (recommended). Or, you can download the desktop installation CD and install with that, then install all of the needed server packages and make the server optimizations (not recommended).

So, assuming you have a working internet connection on your server, simply issue the following command from the command prompt:
> sudo aptitude install ubuntu-desktop

If you have no working internet connection, well you've got some work to do.

---

