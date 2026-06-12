---
title: "Ok, I've installed NMap, now  how do I launch it?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by KevinD_Atl on 2008-04-23
[FONT="Trebuchet MS"]I just installed the Nmap 4.11 I believe, but I thought it was graphical and put itself into the Applications list. Where can I find it to launch it manually from the terminal? I really need the GUI also, if ther is any steps to get that added in[/FONT]

---

### Post by aeiah on 2008-04-23
to launch it from the terminal, open a terminal and type 
```
nmap
```

there are several gui front ends for nmap. i havent tried any of them but perhaps this one is worth a look:[http://sourceforge.net/projects/nmapgui/](http://sourceforge.net/projects/nmapgui/)

---

### Post by Seisen on 2008-04-23
> **KevinD_Atl said:**
> [FONT="Trebuchet MS"]I just installed the Nmap 4.11 I believe, but I thought it was graphical and put itself into the Applications list. Where can I find it to launch it manually from the terminal? I really need the GUI also, if ther is any steps to get that added in[/FONT]

From the terminal try ```
sudo zenmap
``` and it should bring up the gui version of nmap.

---

### Post by spiderbatdad on 2008-04-23
nmap also has a graphical frontend: nmapFE

---

### Post by aaronhall555 on 2008-04-23
> **KevinD_Atl said:**
> [FONT="Trebuchet MS"]I just installed the Nmap 4.11 I believe, but I thought it was graphical and put itself into the Applications list. Where can I find it to launch it manually from the terminal? I really need the GUI also, if ther is any steps to get that added in[/FONT]

nmap is a command line application, and you can install the graphical counter part called nmapfe (stands for nmap front end).

To install this you just need to run these commands:
```
sudo apt-get install nmap
sudo apt-get install nmapfe
```

Those commands should automatically place a application icon in the Applications>Internet menu as NmapFE, also if you want to launch NmapFE from the command line you just have to enter:
```
nmapfe
```

You have to be super user (sudo or be root user) to use some of the more descriptive features of nmap/nmapfe.

```
sudo nmapfe
```
or
```
sudo -s
nmapfe
```

---

### Post by KevinD_Atl on 2008-04-23
HA, and the obvious always prevails~  Where is that nmap launcher located? Just have to create a shortcut and good to go.

---

### Post by bubbabeernuts on 2008-11-30
> **KevinD_Atl said:**
> HA, and the obvious always prevails~  Where is that nmap launcher located? Just have to create a shortcut and good to go.

I have a similar issue.

I'd also like to know how to create a Zenmap icon for my desktop.  I don't see any Zenmap icons in the Applications submenus.

but I'm also dealing with another issue.

I'm running Ubuntu Linux version 8.04(Hardy Heron).

I just installed nmap, along with the Zenmap frontend GUI.  The install only allowed for Zenmap to be installed; the command sequence said Zenmap is now being used instead of nmapFE.

I can run Zenmap from the Alt+F2 run dialog box, but I receive a dialog box which says "Non-root user - You are trying to run Zenmap with a non-root user.  Some Nmap options need root priviliges to work."  I then tried to run an Operating System Detection scan on myself to see how the app works, and I received the following error: "TCP/IP fingerprinting (for OS scan) requires root privileges. QUITTING!"

So, what can I do to run Zenmap scans from my user profile without these errors?  Do I need to change privileges for my profile?  Thanks in advance.

---

