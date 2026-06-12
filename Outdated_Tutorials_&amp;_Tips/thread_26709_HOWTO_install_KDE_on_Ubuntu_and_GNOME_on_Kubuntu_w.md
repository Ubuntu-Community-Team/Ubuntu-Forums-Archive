---
title: "HOWTO install KDE on Ubuntu and GNOME on Kubuntu without internet connection"
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by mrbass on 2005-04-13
With an internet connection you can install:
kubuntu-desktop 67MB/108MB download, uses 312MB additional hd space
ubuntu-desktop 115MB download, uses 542MB additional hd space

So people who would want to do this might include:
-no internet connection available who had cd's mailed to them or burned by a friend
-who plan on installing either one more than a couple times before next release
-rolling it out on multiple desktops in a corporate environment

**To install kubuntu-desktop KDE 3.4 on existing Ubuntu 5.04**
insert Kubuntu 5.04 CD
[b]sudo apt-cdrom add
sudo apt-get install kubuntu-desktop[/b]
logout | end session
Session or Session Type choose KDE, then login.

**To install ubuntu-desktop GNOME 2.10 on existing Kubuntu 5.04**
insert Ubuntu 5.04 CD
Ubuntu CD detected choose Cancel
**sudo apt-cdrom add**
Ubuntu CD detected choose Cancel
**sudo apt-get install ubuntu-desktop**
logout | end session
Session or Session Type choose GNOME, then login.


btw I know you can do it the graphical way from ubuntu --- insert kbuntu cd, start package manager, search kubuntu-desktop, mark, apply, apply, choose kdm or gdm but I think the terminal way is quicker.

Sidenote:
How to install **XFCE 4.2.1 Desktop Environment** (like KDE/GNOME but super light weight) 14MB download
but requires internet connection though.

**sudo apt-get install xfce4 xfmedia xterminal xfce4-theme-brushedchrome**

---

### Post by jfdill_2 on 2005-04-20
Is there any difference whether you start with Ubuntu and add KDE or start with Kubuntu and add GNOME, or should the results be almost identical?

I want to be able to set up systems where users have a choice to login to GNOME or KDE.

---

### Post by ykpaiha on 2005-04-20
I stil have a Great question:
What's the best 
kde over Ubuntu
Or Gnome over Kubuntu ?
For me the 1st worked very well rather than with the second sounds, candies, and some bugs issues.

And for you ?

---

### Post by jfdill_2 on 2005-04-25
[QUOTE=ykpaiha]I stil have a Great question:
What's the best 
kde over Ubuntu
Or Gnome over Kubuntu ?
For me the 1st worked very well rather than with the second sounds, candies, and some bugs issues.

And for you ?[/QUOTE]
I've tried both, had to set up software mixing per this thread for games:
[http://www.ubuntuforums.org/showthread.php?t=8882&page=2&pp=10&highlight=multiple+sounds](http://www.ubuntuforums.org/showthread.php?t=8882&page=2&pp=10&highlight=multiple+sounds)

On one computer (an old Dell GX1 with Ubuntu + KDE) esound works for sound, and on the other (Averatec laptop with Kubuntu + GNOME) I had to use ALSA, but my guess is that's a function of the soundcard hardware and what is or isn't supported.  On both computers, when I launch games from the command line, sound works, but when I launch games from the menu, sound doesn't work.  I haven't found any differences yet.

---

### Post by uberlube on 2008-02-21
I find that KDE is the best and makes things more stable. Plus the default software and file manager are awesome.

---

### Post by kool_kat_os on 2008-02-21
i hope u guys know that this thread is from 2005.....its 2008:)

---

### Post by uberlube on 2008-02-21
.............wow that was embarrassing:lolflag:

---

### Post by Board1 on 2008-02-25
I have just installed Ubuntu 7.10 Server version for the first time, from a CD. When it boots it goes to the command-line-prompt. Please, how could I get a GUI installed? I have not yet configured an internet connection because I figure that I would need a GUI to setup the network connection.

---

### Post by whit on 2008-03-09
> **Board1 said:**
> I have just installed Ubuntu 7.10 Server .... When it boots it goes to the command-line-prompt. Please, how could I get a GUI installed? I have not yet configured an internet connection.

If you're on dhcp and plugged into your LAN, you should have an Internet connection working. If you don't have dhcp, but you have a permanent (DSL or cable) connection, you need to do a simple edit on the values in the file /etc/network/interfaces. Enter "man interfaces" for the man page. All you really need is the address and the netmask. For example (with random values):

```
auto eth0
iface eth0 inet static
        address 206.22.236.77
        netmask 255.255.255.240

```

Then "ifup eth0" should connect you (if the address and netmask are right).

Once your net connection is up, you can use apt-get to install the GUI you desire.

---

### Post by kavoura on 2008-12-05
The instructions given for an older Ubuntu:
```
To install kubuntu-desktop KDE 3.4 on existing Ubuntu 5.04
insert Kubuntu 5.04 CD
sudo apt-cdrom add
sudo apt-get install kubuntu-desktop
logout | end session
Session or Session Type choose KDE, then login.

```

-- should they work with Ubuntu 8.04 or should I use something different?

I tried the first line given, and got the following output:
```
E: Sub-process gpgv returned an error code (2)
E: Read error - read (5 Input/output error)

W: Signature verification failed for: /cdrom/dists/hardy/Release.gpg
```

The CD I used for Kubuntu to get KDE is for Kubuntu 8.04.

---

