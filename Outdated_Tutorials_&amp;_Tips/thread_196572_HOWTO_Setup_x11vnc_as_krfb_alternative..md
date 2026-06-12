---
title: "HOWTO: Setup x11vnc as krfb alternative."
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by CyberAngel on 2006-06-14
An important need for me on my system is the remote connection via VNC.
I commonly use Kubuntu but krfb is basically useless because of 100% CPU usage (at least to 5 PC`s I have tried it)
So a very simple solution is to setup x11vnc as krfb alternative with exactly the same behavior (Enable VNC per user when he logs in).

***That is generic for KDE***
-----------
With the following tip you can make something startup per user when this user logs into KDE!!

There is a folder under everyone`s home directory called ".kde/Autostart"
Generally if you type 
```
cd  ~/.kde/Autostart
```
You should be there ;)

In this folder you can make bash scripts or symbolic links that are executed everytime this user logs in his KDE Desktop environment ;) 
--------------------------


***The following is specifically for x11vnc*** :cool: 
--------------------------
First of all you need to disable krfb if you are using it.

Then apt-get the x11vnc package so do:
```
sudo apt-get install x11vnc vncserver
```

Then you need to create the password that you will be using when you are trying to login to your x11vnc server. type the following in a terminal:
```
vncpasswd
```

Then you have to create the startup script and place it under **~/.kde/Autostart/x11vnc**
```
kate ~/.kde/Autostart/x11vnc
```

Paste the following lines into the file:
```
#! /bin/sh
x11vnc -rfbauth ~/.vnc/passwd -bg -forever -noxdamage -shared &

```

Save the file and exit. Then make the above file executable by using the following command:
```
chmod 700 ~/.kde/Autostart/x11vnc
```

And it is ready :D :D 

Now restart KDE and x11vnc will start automatically instead of krfb!!!

[COLOR="Red"][SIZE="4"]EXTRA TIPS THAT YOU MAY NEED[/SIZE][/COLOR]

***If you also need a tray icon to be able to check when someone is logging into your VNC server just change the "~/.kde/Autostart/x11vnc" contents as emanaton describing on the quote below.***

> **emanaton said:**
> Greetings All,

Most excellent article!  For myself, I require the functionality described herein as well as some notification of VNC activity. I've achieved this by expanding my apt-get install to include "tk8.4" (for the needed "wish" scripting support) as follows:
```

sudo apt-get install x11vnc vncserver tk8.4

```
and expanded ~/.kde/Autostart/x11vnc as follows:
```

#! /bin/sh
x11vnc -rfbauth ~/.vnc/passwd -bg -accept "popup" -gone "popup" -rfbport 5900 -gui tray=minimal,iconfont=14x17 -forever -noxdamage -shared &

```
Not only does this provide on-screen verification to allow or disallow connections, it also provides an ugly tray icon that changes color whenever someone connects! Of course, if you don't care about receiving such notifications then remove the "accept" and "gone" arguments.

Enjoy!


--------------------------
[COLOR="DarkOrange"]# Updated 2007-11-28[/COLOR]

---

### Post by hirak99 on 2007-11-01
Thanks a lot! I just switched from Gnome to Kubuntu. Everything seems fine here except that kRfb takes up 100% CPU - I do not know why is that because Gnome's vino also doesn't take more than 4% CPU. I was looking for an alternative and your guide helps :)

At 100% CPU usage kRfb is completely not a choice for me. If x11 vnc does the job so much better, then I do not know why they included kRfb instead of that as the default desktop sharing package.

This kinda shaken my faith on KDE... in some areas it doesn't seem so good as they claim it to be after all. Is there any kRfb forum where I can post this problem? If you have already posted I'd like to second you there.

I hope there are no more problems like this in KDE.

Cheers...

---

### Post by krunge on 2007-11-01
```
x11vnc -rfbauth ~/.vnc/passwd -bg -forever 
```

You may want to add to that "-rfbport 5900" to make sure it always uses VNC display :0

Port 5900 will also need to be allowed in by any firewalls.

---

### Post by CyberAngel on 2007-11-02
[COLOR="Red"]EDITED:[/COLOR]

Added the "-noxdamage" option to make x11vnc works also over a compiz kde session.

---

### Post by emanaton on 2007-11-28
Greetings All,

Most excellent article!  For myself, I require the functionality described herein as well as some notification of VNC activity. I've achieved this by expanding my apt-get install to include "tk8.4" (for the needed "wish" scripting support) as follows:
```

sudo apt-get install x11vnc vncserver tk8.4

```
and expanded ~/.kde/Autostart/x11vnc as follows:
```

#! /bin/sh
x11vnc -rfbauth ~/.vnc/passwd -bg -accept "popup" -gone "popup" -rfbport 5900 -gui tray=minimal,iconfont=14x17 -forever -noxdamage &

```
Not only does this provide on-screen verification to allow or disallow connections, it also provides an ugly tray icon that changes color whenever someone connects! Of course, if you don't care about receiving such notifications then remove the "accept" and "gone" arguments.

Enjoy!

Sean P. O. MacCath-Moran
[Triskele Media]("http://www.triskelemedia.com/"), CIO

---

### Post by CyberAngel on 2007-11-28
[COLOR="Red"]EDITED:[/COLOR]

Added emanaton`s tip.

Thanks man ;)

---

### Post by the_mouse on 2011-06-01
Thank you, CyberAngel, I used this guide to set up an x11vnc server on Kubuntu and I'm using UltraVNC on Windows XP to connect to the server. The problem is that if for some reason the connection is lost or UltraVNC crashes, on my next attempt to start a new session to x11vncserver I get the "Server closed connection: Server runnning as application".

And so I have to restart x11vnc manually to be able to connect again, which is quite annoying sometimes when I don't have physical access to the PC.

Is there any solution to this situation?

Apparently x11vnc doesn't allow another session if the previous one is not properly ended (like in my case :().

[SOLVED]
edit: Seems like using -shared options resolves the issue ;).

---

### Post by CyberAngel on 2011-06-01
> **the_mouse said:**
> Thank you, CyberAngel, I used this guide to set up an x11vnc server on Kubuntu and I'm using UltraVNC on Windows XP to connect to the server. The problem is that if for some reason the connection is lost or UltraVNC crashes, on my next attempt to start a new session to x11vncserver I get the "Server closed connection: Server runnning as application".

And so I have to restart x11vnc manually to be able to connect again, which is quite annoying sometimes when I don't have physical access to the PC.

Is there any solution to this situation?

Apparently x11vnc doesn't allow another session if the previous one is not properly ended (like in my case :().

[SOLVED]
edit: Seems like using -shared options resolves the issue ;).

This post will become 5 years old in a few days! I am surprized that it is still working with the newest versions :) hehe

I am also adding now in the first port the "-shared" option that you have just mentioned :)

---

