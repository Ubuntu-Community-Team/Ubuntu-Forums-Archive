---
title: "Desktop or Server version for Samba?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by davoutuk on 2008-09-10
I'm a Linux newbie...

I am looking to install Samba on a Linux desktop to act as file server for a collection of XP and Vista PC's.

For this purpose does it matter whether I install the Ubuntu 'Desktop' or 'Server' version?

---

### Post by hyper_ch on 2008-09-10
Desktop

a server is typically a machine that does nothing else but "server". Mostly they don't have a monitor or keyboard or mouse attached.

---

### Post by halitech on 2008-09-10
are you planning on sitting it in a closet somewhere and not using it? then go server. If it will also ask as a desktop, then go desktop

---

### Post by superprash2003 on 2008-09-10
since you are new to linux better stick with desktop version and configure samba.. in your case it shouldnt make much of a difference..

---

### Post by davoutuk on 2008-09-10
Yes - the idea is to have it sitting in acorner and act as a file server. Then to use something like VNC to manage it if required.

Why would installing the server option be more difficult?

---

### Post by Kinetic_lord on 2008-09-10
i don't think you know what a server is... so, just get the desktop edition.

---

### Post by halitech on 2008-09-10
> **davoutuk said:**
> Yes - the idea is to have it sitting in acorner and act as a file server. Then to use something like VNC to manage it if required.

Why would installing the server option be more difficult?

the server install is all command line (no gui and vnc won't work on it) so you would have to administer it via ssh from the command line. Now, don't take it that I'm saying not to do the server install but where you are saying you are new to Linux, you may want to install the desktop version, get everything set up and move it into place but keep a spare monitor, mouse and keyboard around for when you run into troubles.

---

### Post by stevenroose on 2011-08-05
But when you setup a Desktop and unplug monitor/keyboard/mouse and all, won't the CPU still be bothered by the fact that a desktop environment is still running?
Can you exit the desktop environment and go command line in a dekstop setup?
How? I think it is, you can do so from booting but can you close gnome (of unity) from within itself? (or a terminal window..)

Thanks

---

### Post by maverickaddicted on 2011-08-05
Hello,

Can you help me with this - 

[http://ubuntuforums.org/showthread.php?t=1813689](http://ubuntuforums.org/showthread.php?t=1813689)

---

### Post by 3rdalbum on 2011-08-05
> **stevenroose said:**
> But when you setup a Desktop and unplug monitor/keyboard/mouse and all, won't the CPU still be bothered by the fact that a desktop environment is still running?

It won't even notice. I used to use the desktop edition on my headless server and it didn't miss a beat when I unplugged mouse, keyboard and monitor, nor when I plugged them back in again if I needed to do some admin.

> Can you exit the desktop environment and go command line in a dekstop setup?

Log out. Press Control-Alt-F1. Type:

```
sudo service gdm stop
```

Congratulations, you're command-line only without having to reboot. If you want the GUI back, type:

```
sudo service gdm start
```

Note that these commands don't stop the GUI coming back up if you reboot.

---

