---
title: "Gdm will not start"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Alex R on 2008-08-31
Hi,
I have had Xubuntu 8.04 on my laptop for a few months, but now gdm has suddenly stopped working. When I switch the computer on it loads to the console (tty1), and it has the following lines written at the top of the screen:

```
Starting up...
Loading, please wait...
Kinit: name_to_dev_t(/dev/disk/by-uuid/4ce5ec2f-c3fd-4a37-96d8-302912b2b80b) = Sda3(8,3)
Kinit: trying to resume from /dev/disk/by-uuid/4ce5ec2f-c3fd-4a37-96d8-302912b2b80b
Kinit: No resume image, doing normal boot.
```

Once I log in I try starting gdm using:

```
sudo /etc/init.d/gdm start
```

But that fails. I also tried:

```
sudo gdm
```

And that gave me the message:

```
gdm: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_hash_table_ref
```

I tried sudo dpkg-reconfigure gdm, but that also gave me an error message (I can't remember exactly what), I also tried uninstalling gdm then installing it again using gdm, but this does not solve the problem. Also, I think I accidentally removed xubuntu-desktop when I removed gdm - I tried reinstalling it with apt-get, but it says that it failed to fetch something, and it "could not resolve gb.archive.ubuntu.com". Running sudo apt-get update gave me this same message for a long list of websites. I also tried installing xdm, which I believe is an alternative to gdm, but apt-get gave me the same error as for xubuntu-desktop.

Can anyone suggest how I can get gdm to work again (or at least an alternative like xdm)?

I think someone posted a similar problem on the forums a few days ago, but I couldn't find their thread again, so I had to start a new one (I don't think they solved the problem either).

---

### Post by jemate18 on 2008-08-31
type
> startx

Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by gmxgeek on 2008-08-31
It is possible that X is not set up correctly, given
```

gdm: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_hash_table_ref

```

it could either be your gtk, or your X that is bad

try reinstalling gtk first, and if that doesn't work, X11, but be very careful.

---

### Post by Alex R on 2008-08-31
I tried using startx, but after a few seconds it went back to the console - I couldn't see all of the message it gave me though because I don't know how to scroll up on the console.

I'll now try to reinstall gtk.

---

### Post by jemate18 on 2008-08-31
> **Alex R said:**
> I tried using startx, but after a few seconds it went back to the console - I couldn't see all of the message it gave me though because I don't know how to scroll up on the console.

I'll now try to reinstall gtk.

ok try this,

type```
sudo dexconf [password]
```
This will try to generate a new X server configuration based from debconf data.
Dont forget to have a backup of your current xorg.conf before trying to edit it or executing dexconf. so that if it messes things up, you can restore it.

_______________________
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by Alex R on 2008-08-31
I tried dexconf, but it hasn't solved the problem.

How do I reinstall gtk? I tried using:

```
sudo apt-get install --reinstall gtk
```

but it said that it could not find the package gtk - have I just got the name of the package wrong, or do I need to do something else?

---

### Post by jemate18 on 2008-08-31
> **Alex R said:**
> I tried dexconf, but it hasn't solved the problem.

How do I reinstall gtk? I tried using:

```
sudo apt-get install --reinstall gtk
```

but it said that it could not find the package gtk - have I just got the name of the package wrong, or do I need to do something else?


The command is to remove first, 
apt-get remove [whateEverToREmove]

and then install
apt-get install [whatEverToInstall]

---

### Post by GepettoBR on 2008-08-31
before trying to reinstall the X server, you can run ```
sudo dpkg reconfigure -phigh xserver-xorg
```Don't forget to backup your xorg.conf before trying this.

---

### Post by Alex R on 2008-08-31
Using sudo dpkg reconfigure -phigh xserver-xorg didn't solve the problem.

I tried sudo apt-get remove gtk, but it said it couldn't find the package gtk, so I think I've got the package name wrong - do you know what it is?

---

### Post by Alex R on 2008-08-31
I found the package, its called libgtk2.0-dev, however when I try to reinstall it apt-get cannot fetch the packages because it 'could not resolve gb.archive.ubuntu.com'. How can I fix this?

---

### Post by GepettoBR on 2008-08-31
> **Alex R said:**
> I found the package, its called libgtk2.0-dev, however when I try to reinstall it apt-get cannot fetch the packages because it 'could not resolve gb.archive.ubuntu.com'. How can I fix this?

This means apt cannot connect to the download server.. How is your computer connected to the internet?

---

### Post by Alex R on 2008-08-31
It is using a wired ethernet connection - it is working fine when I use the live cd, but I don't know how to check if its working from the console, when I'm not using the live cd.

---

### Post by GepettoBR on 2008-08-31
To see if it is working properly, try to ping any network address, like [www.google.com](www.google.com) or your modem/router's IP (usually 192.168.x.1, where x can be 1, 0 or 100 - usually). Just type "ping <adress-or-IP>" and see if it succeeds. If not, you don't have a working internet conection. Also, please post the output of "ifconfig" for me to take a look.

---

### Post by Alex R on 2008-08-31
I tried to ping [www.google.com](www.google.com), but it said "unknown host".

The output of ifconfig is:

```
lo    Link encap:Local Loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      IP LOOPBACK RUNNING MTU16436 Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
```

---

### Post by GepettoBR on 2008-08-31
ifconfig is supposed to display all your network interfaces. lo is the Loopback interface, and the fact that no other interfaces are shown means that you have no network connection, probably due to a missing module somewhere. Is reinstalling the OS an option? It would probably be less trouble than fixing this, though we can try if you rpefer.

---

### Post by Alex R on 2008-08-31
I think it will be easier to just reinstall the OS. 

Thank you for all your help!

---

### Post by GepettoBR on 2008-08-31
> **Alex R said:**
> I think it will be easier to just reinstall the OS. 

Thank you for all your help!

I'm sorry we couldn't fix it, but I guess this was a learning experience :)


Good luck!

---

