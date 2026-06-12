---
title: "HOWTO: share your desktop with your friends"
date: 2005-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by i3dmaster on 2005-06-22
You probably would have never thought this can be so easy now under Linux. I had long time with the other apps like normal vnc, xdmcp, etc cause they all have a session issue and the server side just could not allow you to listen on the current display screen. Ok, now    let's see how we can share our current desktop to thr world. 

```

sudo apt-get rfb vncviewer

```
Yes, that's all you need. if you have vncviewer already (I think most of us do), then you just need the server side rfb pkg. After apt gets it installed, then do
```

x0rfbserver

```
Easy, just put the password you need and some other settings you like, and then it will start to share your current desktop. And this is just needed for the first time. Later, you can just 
```

x0rfbserver &>/dev/null &

```
Go to another box has network connectable to your rfb server, then use normal vncviewser to hook up and enjoy it... Its a very nice tool to do presentation under Linux.

---

### Post by SGC on 2005-06-22
I found x11vnc ( In the universe ) to be a better solution to connect to the real display (display :0 ) than rfb .

---

### Post by i3dmaster on 2005-06-22
[QUOTE=SGC]I found x11vnc ( In the universe ) to be a better solution to connect to the real display (display :0 ) than rfb .[/QUOTE]

Good. thanks for sharing that. I just tried and its very cool, also more function then rfb. rfb is simple and easy to use, so they are all very good stuff as I can see.

---

### Post by Ride Jib on 2005-06-23
what ports need to be open/forwarded on my router for this to work?

---

### Post by spacemonkey on 2005-06-23
Can't you just go to System-Preferences-Remote Desktop and set it up from there?  I've had vnc since I installed Ubuntu, no extra packages needed.

---

### Post by i3dmaster on 2005-06-24
[QUOTE=i3dmaster]Good. thanks for sharing that. I just tried and its very cool, also more function then rfb. rfb is simple and easy to use, so they are all very good stuff as I can see.[/QUOTE]
The port is 5900

---

### Post by i3dmaster on 2005-06-24
[QUOTE=spacemonkey]Can't you just go to System-Preferences-Remote Desktop and set it up from there?  I've had vnc since I installed Ubuntu, no extra packages needed.[/QUOTE]

yep, that's using vino. But it does not have the man page for the server so not sure how to use the server flags and options. So you are pretty much stuck on using the vino-preference... The other thing I found is that most of the lightweight vncserver does not have options to adjust the geometry. The triditional vncserver has it but a little bit harder to config it to show the current screen... So if you have a bigger screen resolution than the viewer, the viewer couldn't see the whole screen...

---

