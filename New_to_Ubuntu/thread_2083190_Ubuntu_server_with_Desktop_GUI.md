---
title: "Ubuntu server with Desktop GUI"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by samkwak on 2012-11-11
Hello out there.
 
I am new to Ubuntu/Linux/Unix in general and want to use the GUI to start, BUT, need to use Ubuntu as a server platform for Asterisk ( An open source PBX)
 
From what I read, the use of the GUI is discouraged with the server.
 
Question #1. Does the GUI from the desktop version a functional means of controlling the server functions?
 
Q2. If so, and if I intended to use the GUI that comes with the desktop version, Should I install the desktop version with the GUI and upgrade the additional packages for the server functions or the other way around or does it matter at all???
 
Thank you
Sam Kwak

---

### Post by jerome1232 on 2012-11-11
> **samkwak said:**
> Hello out there.
 
Question #1. Does the GUI from the desktop version a functional means of controlling the server functions?

That depends on the specific service you run, for the most part you just edit text based configuration files, so the answer is yes.
 
> 
Q2. If so, and if I intended to use the GUI that comes with the desktop version, Should I install the desktop version with the GUI and upgrade the additional packages for the server functions or the other way around or does it matter at all???
 
Thank you
Sam Kwak

Doesn't matter at all, personally I would go with something lighter than Unity, maybe xfce (xubuntu) or lxde (lubuntu).

---

### Post by papibe on 2012-11-11
Hi samkwak. Welcome to the forums ):P

You can run any service from a server on a desktop edition. If you don't feel comfortable running a headless server or text-only server edition, by all means install a Desktop Edition.

Another consideration would be what you will be running. For instance, I run over night video conversions on a headless server using ffmpeg. If you prefer the GUI Handbrake, you would need to install a GUI to supports it.

When neither of the above consideration are issues, it all comes down to resources. The server will use considerable less RAM, and a less hard drive space.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by samkwak on 2012-11-11
Thank you.

---

### Post by PinkFloyd102489 on 2012-11-11
Best way to do it is run the server install then install the GUI over top of that.

Simply:
```
sudo apt-get install Xubuntu-desktop
```

Replace (or remove) the X depending on which "flavor" you wish to installed. As mentioned previously, xubuntu or lubuntu are good lightweight choices.

---

### Post by mastablasta on 2012-11-12
there are other even lightre GUI's such as IceWM for exmaple.
 
however for server it would make more sense to just install server version and then log to it and operate it via webmin GUI and a few other tools.

---

