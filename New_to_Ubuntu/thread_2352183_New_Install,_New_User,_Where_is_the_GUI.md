---
title: "New Install, New User, Where is the GUI?"
date: 2017-02-10
forum: New to Ubuntu
---

### Post by rdabate on 2017-02-10
Hi,

I've successfully installed Ubuntu Server 16.10.  Downloaded from [https://www.ubuntu.com/download/server](https://www.ubuntu.com/download/server)
Also installed Webmin, and that seems to be working as well.

I'm new to Ubuntu, and Linux for the most part.  I thought there was a GUI with Ubuntu Server?  I'm not seeing that?  Does it need to be installed?

---

### Post by Perfect Storm on 2017-02-10
Ubuntu Server Edition comes without gui. You have use commands if you like or install a DE to it.

---

### Post by Bucky Ball on 2017-02-10
Welcome. Is there a particular reason you've installed the server? If you're going for a desktop, may as well install one of the other flavours. If it's lightweight you're after, Xubuntu or Lubuntu might do it.

FYI: An interim release like 16.10 is not recommended for a server. Generally people do not want to, or it is not possible to, upgrade their server every six months.

Interim releases have nine months support. LTS releases, 16.04 LTS for instance, has five years support. Anything ending with LTS is long-term support and those releases come out every two years, next one April 2018 (18.04 LTS, the release number giving the years and month of the year). ;)

PS: To answer your original question, yes, a desktop environment does need to be installed, but there are a heap to choose from and that is another matter ...

---

### Post by QIII on 2017-02-10
"Needs to be installed" only if you "need" a GUI.

But if you plan to use it as a server, you don't need a GUI.  If using it as a server is your goal, then you really should use it as a server.  In the Linux world that means sans GUI.

---

### Post by HermanAB on 2017-02-10
A server usually sits on a rack in a dark corner of a dank data centre, with no screen, keyboard or rodent attached to it and is managed remotely over SSH.  The desktop machine that you SSH from, usually has a screen, keyboard and rodent with a GUI.  So that is why your server doesn't need one.

However, if your 'server' sits on your desktop and has all the accoutrements, then do "apt-get install xfce" to give you something less frustrating to work with.

---

### Post by Bucky Ball on 2017-02-10
> **HermanAB said:**
> However, if your 'server' sits on your desktop and has all the accoutrements, then do "apt-get install xfce" to give you something less frustrating to work with.

Do you mean 'apt install **xfce4**'? ;)

---

### Post by HermanAB on 2017-02-11
Ayup - I'm so old skool, I am several Ubuntu versions behind.

Actually, the last few weeks I've been fixing problems with OpenBSD and Windows 7 - It feels like time travel, going 10 years back.

---

