---
title: "create .vnc file for dummies"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by jak.plopelor on 2008-06-10
how do I create vnc file so I can open it in any location and remote control my desktop?
thanx

---

### Post by mgmiller on 2008-06-10
vnc server is built into ubuntu.  Click on System > Preferences > Remote Desktop.

On the General tab, under Sharing, click "Allow other users to view your desktop".  Also click Allow other users to control your desktop.

Under Security, unclick "Ask you for confirmation".

Click close.

On the other machine you want to connect with, if it's windows, install tight vnc or ultravnc, etc.  and then use that to enter your first machines IP address.  On connect, it should ask for your user name and password.

If the other machine is an ubuntu box prior to 8.04, click on Applications > Internet > Terminal Server Client and in the Computer field, put in your ip address or domain name if that applies.  under protocol, select VNC.  input the user name and password and at the bottom, click Connect.

If this is a clean install of Hardy on the computer you are trying to connect from, you will go to Applications > Internet > Remote Desktop Viewer instead of the Terminal services Client. 

Click on the Connect button and it will ask for the ip address or domain you want.  Then click the connect button in the window and it should prompt you for your user name and password.


All this being said, I'm not sure I would leave this turned on all the time.

---

### Post by ians1 on 2008-06-15
Many thanks

Wish I'd read this first!

Worth noting its default port is 5900 as usual

ian

---

