---
title: "Ssh help"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by jabema on 2011-11-08
I have a computer dual booted with windows xp and Kubuntu 11.10 and a laptop running Kubuntu 11.10.  I set up ssh-server on both Kubuntu machines and everything works fine.  I set up putty and winSCP on my windows boot and that also works fine.  It allows me to access my laptop perfectly.  My problem and question is how do I access my windows boot from my laptop?

Is there some other program I need to install or am I missing something with the software I'm already using?  I try to google "connect to windows from ubuntu" and I get a lot of results with "vnc, tunneling, and virtual boxes".  I am very new to the world of file sharing so these terms mean very little to me.

The computers are only on my home network so security isn't a huge issue, I would just like to be able to access files from my desktop even if someone is running the machine in Windows.

---

### Post by alphacrucis2 on 2011-11-08
> **jabema said:**
> I have a computer dual booted with windows xp and Kubuntu 11.10 and a laptop running Kubuntu 11.10.  I set up ssh-server on both Kubuntu machines and everything works fine.  I set up putty and winSCP on my windows boot and that also works fine.  It allows me to access my laptop perfectly.  My problem and question is how do I access my windows boot from my laptop?

Is there some other program I need to install or am I missing something with the software I'm already using?  I try to google "connect to windows from ubuntu" and I get a lot of results with "vnc, tunneling, and virtual boxes".  I am very new to the world of file sharing so these terms mean very little to me.

The computers are only on my home network so security isn't a huge issue, I would just like to be able to access files from my desktop even if someone is running the machine in Windows.

One way is to use RDP. You have to enable it on the Windows machine you want to connect to (somewhere in the control panel - exactly where may vary depending on the version of Windows). It will then run the RDP server on boot up. By default it allows up to two concurrent client connections. For more than that you have to pay Microsoft a licence fee. There are some rdp clients available in the Ubuntu repos. Check the software centre ratings. 

According to this link the RDP server comes with the pro, business or ultimate versions of Vista & 7

[http://www.howtogeek.com/howto/windows-vista/turn-on-remote-desktop-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/turn-on-remote-desktop-in-windows-vista/)


Edit. Check out the one called Remmina Remote Desktop Client. Seems to get good reviews.


If you just want to access files on the windows machine then just enable Windows file sharing on the folders you want. You can access them from Ubuntu using File Connect to Server from Nautilus. Select Windows Share in the drop down and enter the server name or ip address and the share name. It will prompt for the windows uc/password.

---

