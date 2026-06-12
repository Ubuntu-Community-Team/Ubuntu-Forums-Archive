---
title: "vnc help please"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-05-21
I have vnc server installed on my other xp pc (wife wants xp) i am trying to connect to it using Remote Desktop Viewer i am putting in the ip but can not connect!

Any help please

---

### Post by Cypher on 2008-05-21
VNC != XP's Remove Desktop Viewer. You'll want to install VNCViewer on XP to be able to connect the VNC Server running in Linux.

---

### Post by CRISM on 2008-05-21
I'm not familiar with vnc server, so the following instructions may not apply. But since it's quick and easy, it's worth a try. Check to make sure the XP computer is set up to allow remote desktop sessions. Go to My Computer, right click and choose Properties. A window with multiple tabs should come up. Select the Remote tab, and then select Advanced. Make sure a check mark is in the box to "Allow this computer to be controlled remotely".

---

### Post by iwannalearn on 2008-05-21
I have the latest vnc which i think over comes this issue, but i have disabled user switching.

Funny i can ping my linux pc from xp but i can't ping the xp from linux?

I can ping my linux set top box ok from my linux pc!

The xp pc has a static ip 192.168.2.2
STB                       192.168.2.3
Linux pc                  192.168.2.6

Any idea please?

---

### Post by Cypher on 2008-05-21
XP's firewall might be blocking the ICMP (ping) packets..

---

### Post by iwannalearn on 2008-05-21
Yep, was a windows firewall issue working fine now:)

Thanks to all

---

### Post by iwannalearn on 2008-06-02
Bit more help please guys.

My desktop pc now has dual boot ubuntu/m$
laptop ubuntu

I can connect ok using Remote Desktop Viewer from my ubuntu-laptop to connect to m$ with VNC

But i am having trouble connecting from ubuntu-linux to ubuntu-desktop

On the desktop i went System>Preferences>Remote Desktop

Ticked all under General tab Sharing/Security
Ticked all under Advanced tab Network/Security Notification Area ticked the middle option.

Opened fire starter Policy, Allow Service from 
Name VNC
Port 5900

But still no luck:(

When i try to connect with Remote Desktop Viewer i get "Connection to host "192.168.2.5:5900" was closed."

What have i done wrong:confused:

---

### Post by iwannalearn on 2008-06-02
bump

---

### Post by maybeway36 on 2008-06-02
Sounds like a server-side problem. There must be some sort of log file on the Ubuntu machine, but I don't have a clue where it is.
I personally use x11vnc for remote access. I suppose you could install that, then type "x11vnc" in a terminal and try to connect. It will tell you there if anything went wrong.

---

### Post by iwannalearn on 2008-06-02
Be doing some more reading and tried following this nice tutorial [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH) which is very nice, all seems to have gone well, only thing i am lost with the very last stage, connecting to server

This is the part i don't get:

The Local Computer (Client)

To connect to the server's VNC desktop, from the client you'll simply use the -via parameter of the vncviewer command. The syntax of the command then resembles the following when using our example host information from above:

vncviewer -via hendrix@82.211.81.166 hendrix:1

This tells VNC to forward the connection to the server computer (hendrix) via the server computer's external, or public facing IP address, 82.211.81.166 (a valid, resolvable hostname would work here too).

Upon entering this command at a terminal prompt, you'll notice some VNC-specific information on screen, and then you'll be prompted for the SSH password. Enter the SSH password, and upon correctly doing so, the SSH tunnel will be established. Next, you'll receive a prompt for your VNC password (which may, or may not be the same as the SSH password) which resembles the following: 

It's this line which i don't get 
vncviewer -via hendrix@82.211.81.166 hendrix:1

Thanks for any help

---

### Post by quelx on 2008-06-02
> **iwannalearn said:**
> 
It's this line which i don't get 
vncviewer -via hendrix@82.211.81.166 hendrix:1


This tells VNC to forward the connection to the server computer (hendrix) via the server computer's external, or public facing IP address, 82.211.81.166 (a valid, resolvable hostname would work here too).

Upon entering this command at a terminal prompt, you'll notice some VNC-specific information on screen, and then you'll be prompted for the SSH password. Enter the SSH password, and upon correctly doing so, the SSH tunnel will be established. Next, you'll receive a prompt for your VNC password (which may, or may not be the same as the SSH password) which resembles the following

---

