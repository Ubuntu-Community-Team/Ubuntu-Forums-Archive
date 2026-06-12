---
title: "Control remote desktop on Xubuntu from a Windows machine?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by tnek on 2008-10-14
Hi,

I am wondering about remote desktop and being able to see and control the screen from a Windows machine using Xubuntu. What's the easiest way to set it up?

---

### Post by nhasian on 2008-10-14
easy to do.  go to system/preferences/remote desktop.
check the two boxes to allow remote access to view and control the desktop.  also input a password.

on your windows computer install ultraVNC or something similar.  you can then use the VNC client to connect to your ubuntu machine using port 5900.

if your ubuntu pc is behind a firewall you'll need to forward the port to the correct ip address to gain access.

PS You can even use the remote desktop from your iPhone or Windows Mobile Device :)

---

### Post by cozadaman on 2008-10-14
Im trying to figure out the same thing, i can RDC my windows machine from my Xubuntu but not not the other way...
I keep getting error messages saying i cannot connect, connection refused. So im guessing i havent setup the RDC from my Xubuntu machine properly.
Ive currently got rdesktop, xtightvnc and xvnc4viewer installed.
If i find out, ill drop a line.

nhasian - your thinking of Ubuntu, Xubuntu and Ubuntu dont quite have the same menus. 

If anything i said is wrong, hit me up, might be the reason im failing also :confused:

---

### Post by cozadaman on 2008-10-14
Okay, this is what ive got.
I have rdesktop, xtightvnc and xvnc4viewer installed. I then installed vino the gnome rdc app.
sudo apt-get install vino
Open vino settings by vino-preferences in terminal, tick the boxes "Allow other uses to view your desktop" and "Allow other users to control your desktop" rest is optional.
Then you need to start the vino server by typing in
/usr/lib/vino/vino-server &
in the terminal.
Go to you windows machine that has VNC and type in the ip:screen
eg 127.0.1.1:0 and it should work.

Tell me if this works or not for you, and ill try give you more of what i did or just incase ive forgotten anything. Haha good luck.

---

### Post by stephanvaningen on 2008-10-14
RDC isn't the way I think. What nhasian is saying should be working: UltraVNC on the Windoze-machine and Remote Desktop-config setup on the Xubuntu-box

---

### Post by Lowcountry on 2008-10-14
> **stephanvaningen said:**
> RDC isn't the way I think. What nhasian is saying should be working: UltraVNC on the Windoze-machine and Remote Desktop-config setup on the Xubuntu-box

Xubuntu doesn't come with VNC built-in...it's a Gnome thing, which is why Ubuntu has it.  This should work:

[http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html]("http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html")

---

### Post by nhasian on 2008-10-14
My bad.  i was so eager to help with an issue i was familiar with i didnt notice it was for xubuntu.  I'll have to install that in virtual box and play around with it.  

I read that x11vnc is a VNC server recommended for xubuntu and is available in the universe repository.

> **cozadaman said:**
> 
nhasian - your thinking of Ubuntu, Xubuntu and Ubuntu dont quite have the same menus. 


---

### Post by cozadaman on 2008-10-17
My bad, i just mean "RDC" as a general remote connection, not that specific app.
Any how, just all my "research" as a small tute. Just need to download the vino server and then you should be all set to use your own tools and what not. Hope it helpd. :)

---

### Post by cozadaman on 2008-10-17
Another note, Ubuntu is a bit easier to use for this instance, Xubuntu is just good for light weigth machines, so if u can ubuntu is the better choice.

---

