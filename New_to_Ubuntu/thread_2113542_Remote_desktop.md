---
title: "Remote desktop"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by CrewDK on 2013-02-07
Sometimes i need to get access to remote PC with ubuntu. Yes, I know about ssh, but i need acces exactly to remote display, for help remote user with "desktop" application. 

Something about [TeamViewer]("http://www.teamviewer.com/ru/index.aspx") or RAdmin for Windows.

How can i do that?

---

### Post by howefield on 2013-02-07
How about Teamviewer ?

---

### Post by CrewDK on 2013-02-07
I tried this program, but for some reason it is not working well under ubuntu.

First I was not able to add a computer with  Ubuntu to my customers list. It's always shows in "online computers" list, but it is always labeled "unknown", like on this screenshot.

Then, I was able to connect to a remote machine only once. After that, all attempts were unsuccessful. :( Every time I try to connect, the program says that connection established, but there is no image of the remote machine and no output. And exactly after 1.5 minutes a session is terminated. 

With my Win PC all works great.

---

### Post by mysteriousdarren on 2013-02-10
do you have the newest teamviewer installed?

---

### Post by sudodus on 2013-02-10
As far as I know, Teamviewer is the easiest one to get working through firewalls. I find it slow, but working. You may need to tweak the settings to make it respond better.

I have used it between computers with Ubuntu 12.04 LTS and Lubuntu 12.04, via LAN and via the internet between different cities. Maybe there are problems with the newest version of Ubuntu, 12.10.

If both computers are within the same LAN, and you don't have to worry about holes in the firewall, you can use other remote desktops, for example rdesktop or remmina, which might be faster and more responsive. If you know enough about firewalls and static IP addresses, you can use these programs also via the internet.

---

### Post by prodigy_ on 2013-02-10
[x11vnc](http://www.matrix44.net/blog/?p=1106) bound to localhost only and forwarded via SSH. Slow but secure and failproof.

---

### Post by CrewDK on 2013-02-10
> **mysteriousdarren said:**
> do you have the newest teamviewer installed?

Yes. It's the latest TW8 betas. Maybe I have problem because it's still beta and doesn't very stable?

By the way, why the TW for Linux using Wine? I believed that it was an application for Linux, but when I running on my ubuntu TW, I can see that wine also starting. Why?

> **sudodus said:**
> As far as I know, Teamviewer is the easiest one to get working through firewalls. I find it slow, but working. You may need to tweak the settings to make it respond better.

I have used it between computers with Ubuntu 12.04 LTS and Lubuntu 12.04, via LAN and via the internet between different cities. Maybe there are problems with the newest version of Ubuntu, 12.10.

If both computers are within the same LAN, and you don't have to worry about holes in the firewall, you can use other remote desktops, for example rdesktop or remmina, which might be faster and more responsive. If you know enough about firewalls and static IP addresses, you can use these programs also via the internet.





   Maybe I put it is not entirely correct. Now I need to have the ability to remotely control from Win PC to Linux PC. If I understand correctly, and rdesktop, and remmina can connect Linux PC -> WinPC\Linux PC, but not WinPC -> LinuxPC. Am I correct?



> **prodigy_ said:**
> [x11vnc]("http://www.matrix44.net/blog/?p=1106") bound to localhost only and forwarded via SSH. Slow but secure and failproof.




   
Mmmm... Could it helps me control remote Linux PC's from Win PC?

---

### Post by prodigy_ on 2013-02-10
> **CrewDK said:**
> Mmmm... Could it helps me control remote Linux PC's from Win PC?
Certainly. You can use putty and any VNC client (e.g. RealVNC). And FileZilla or WinSCP if you need to transfer files.

BTW, by default x11vnc doesn't install itself as a service. You start it manually, it waits for a connection and then automatically exits when the connection is over. Could be exactly what you need.

---

### Post by sudodus on 2013-02-10
> **CrewDK said:**
> Yes. It's the latest TW8 betas. Maybe I have problem because it's still beta and doesn't very stable?

I would recommend the stable version. That's the one I have used.
> 
By the way, why the TW for Linux using Wine? I believed that it was an application for Linux, but when I running on my ubuntu TW, I can see that wine also starting. Why?

Probably because the company thought it is easier to make the Windows version work via Wine, than to make a native linux version.
> 
Maybe I put it is not entirely correct. Now I need to have the ability to remotely control from Win PC to Linux PC. If I understand correctly, and rdesktop, and remmina can connect Linux PC -> WinPC\Linux PC, but not WinPC -> LinuxPC. Am I correct?
...
Teamviewer will connect both ways (and can use the same software at both ends). (Yes, you probably need some other front end software than rdesktop or remmina in Windows.)

---

### Post by CrewDK on 2013-02-24
Thank you all for your help. I found out what the problem was.

At startup ubuntu, as I understand it, starts analogue of windows TV service. This allows you to see if the client on the network (in the clients list of TV), but it is not possible to join with this customer. When you connect to remote system, your teamviewer tries to establish a connection, but as long as it will not run the application TV itself on remote PC with Ubuntu, normal connection won't be established.

---

