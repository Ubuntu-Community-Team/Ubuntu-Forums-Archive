---
title: "Need help to fix this problem with VNC"
date: 2024-06-06
forum: New to Ubuntu
---

### Post by cilssp on 2024-06-06
Hi everyone!

When I connect from a Windows computer to my Ubuntu computer with tightvnc and I start typing a command in the terminal, there comes a time when the keyboard breaks and I start writing all capital letters without having it activated, it writes symbols and my keyboard breaks my ubuntu computer. To fix it I have to restart my computer.


I wanted to know if there is any other program that I can use in Ubuntu for VNC connections or if there is a way to solve this error other than restarting.

---

### Post by currentshaft on 2024-06-06
Does it only happen in Terminal? Try the "reset" command next time.

---

### Post by TheFu on 2024-06-06
a) Don't use Wayland.  Use Xorg (X11) for the display manager.
b) If you want better performance AND 1000x better security, use an NX-based tool.  x2go is that tool.
c) The DE cannot be KDE or Gnome, use any other DE say Mate, XFCE, or just a straight WM like openbox or fvwm instead of a DE.

Do those things and you'll have secure, fast, access to the remote computer. Setup ssh-keys between the two systems and not only will it be more secure, but much more convenient.  With MS-Windows as the client, the trick is to get the complete font package from the x2go download along with the setup.exe installer.  I use x2go from MS-Windows for a few years. It is rock solid.  I'd leave it connected for over a week at a time. If it did disconnection, I could reconnect and find my desktop exactly like it was before.  Additionally, x2go uses a virtual session, so nobody needs to physically login on the remote computer.  This is different from VNC.  

Tuning the performance based on your available connection speed isn't hard either.  I setup the x2go session connection to be 1 lower than the actual speed and set the image compression to be 4K-png for my 1080p screens.  For typical uses like working on documents or handling email, it is like being on the physical system. I've used it from 5 continents and connections from 100Mbps fibre to shared 64Kb ISDN connections in very remote places. Obviously, the ISDN connection was slower, but thanks to the ability to tune the compression and set the connection speed, I let the image quality be less, so the performance would be acceptable.

I really wish VNC and RDP would just die out.  Those methods have had many security problems for about 20 yrs.  RDP security was a complete joke until after Win7.  Using VNC is begging to be hacked.

1. Setup ssh between the 2 systems.  This is less for MS-Windows since most Windows people use PuTTY and that tool uses a non-standard ssh, but if you cannot connect from Windows via ssh into the remote x2go server, it won't work. That is required.  ```
sudo apt install ssh fail2ban
``` should be sufficient on any Ubuntu system - client or server.  Of course, you'll need to allow ssh access to the remote server, whatever that entails. If you run a firewall, allowing ssh in isn't hard and you'll still be protected against brute force attacks by the default fail2ban settings.
2. [https://wiki.x2go.org/doku.php/doc:installation:x2goserver](https://wiki.x2go.org/doku.php/doc:installation:x2goserver) - add the PPA, from then on the x2goserver will be updated with your normal patching (hopefully, weekly). 
```
sudo add-apt-repository ppa:x2go/stable
sudo apt-get update
sudo apt-get install x2goserver x2goserver-xsession
```
3. [https://wiki.x2go.org/doku.php/doc:installation:x2goclient](https://wiki.x2go.org/doku.php/doc:installation:x2goclient) - Use the Windows instructions for the client. Should be 2 installs - the x2goclient and the font packages.

that's it.

Find the x2go client in the menu of your Windows computer, fill out the username/remote host, choose the DE to be used and connect. If performance isn't what you hoped, do what I've suggested above and it will be like night and day.

12.04 - 24.04 are supported by the PPA, so this should "just work" provided you aren't trying to use Wayland or Gnome or KDE-Plasma.

I think you'll be impressed.

---

### Post by ActionParsnip on 2024-06-07
What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by cilssp on 2024-06-07
Yes only in Terminal but then when I disconnect the Window PC or Ubuntu PC from the VNC the other computer can't use the keyboard and need to restart the PC

---

### Post by cilssp on 2024-06-07
> **ActionParsnip said:**
> What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

I need the full remote system because I work as a IT Technical Support and sometimes people need to do something and they don't know how so instead of going to the office I ask for the IP and do everything from my office.

---

### Post by ActionParsnip on 2024-06-07
> **cilssp said:**
> I need the full remote system because I work as a IT Technical Support and sometimes people need to do something and they don't know how so instead of going to the office I ask for the IP and do everything from my office.

Ah so remote user support. Makes sense

---

### Post by TheFu on 2024-06-09
> **cilssp said:**
> I need the full remote system because I work as a IT Technical Support and sometimes people need to do something and they don't know how so instead of going to the office I ask for the IP and do everything from my office.

Use MS-SMS. It does remote support. Have the company buy it.

With Linux, use x2go if you must, but ssh for 99% of the things.  And when you solve it, create an **ansible** script/task so it can be used for all other systems, if needed.

---

