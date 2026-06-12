---
title: "What am I doing worng with VNC?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2008-06-07
i followed [this guide]("http://www.ubuntu-unleashed.com/2007/10/setup-vnc-server-for-ubuntu-gutsy.html") to set up Remote Desktop

i installed **x11vnc** and **vnc-java**

i ran the command *x11vnc -storepasswd*

i added *x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800* to my sessions so it starts on boot

on my home network:

my laptop is on **192.168.1.100**

and my desktop is on **192.168.1.101**

i forwarded (on my router) port _57102_ on my laptop and _57103_ on my desktop, and specified the alternative ports in the remote desktop preferences for each (i double checked, each is on the correct machine)

what i'd like to do is have both a shortcut under Applications>Internet and a bookmark in firefox from one machine to the other, but i can't seem to establish a connection.

in firefox on my desktop, i'll type "[COLOR="Red"]My IP Address[/COLOR]:57102" and hit enter. it will say "VNC Authentication" while asking for a password, then it will say "java.net ConnectException: Connection Refused"

i've done this enough times to rule out the possibility of a simple typo.

on my laptop i entered the terminal command ```
gksu gedit /home/ryan/.vnc/passwd
``` and even double checked the password. it's correct.

what am i doing wrong? please let me know if there is any other info needed to diagnose the problem

PS i'm fairly certain once we fix this that the connection from my laptop **TO** my desktop will be a consistent command, but the command to access my laptop **FROM** my desktop would change with whatever network my laptop is on. is there a way to be able to connect to my laptop no matter what? it would be really cool to be able to pick a file off my laptop from home if my sister borrows it for school or something.

---

### Post by Monicker on 2008-06-07
You have vnc listening on port 5800, not 57102.  What happens if you try to connect on port 5800?  Or you could change the http port in the command to start x11vnc.

---

### Post by Sonic Reducer on 2008-06-07
> **Monicker said:**
> You have vnc listening on port 5800, not 57102.  What happens if you try to connect on port 5800?  Or you could change the http port in the command to start x11vnc.

whoops, i copy/pasted from ubuntu-unleashed there.

what i have in my Preferences>Sessions is ```
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 57103
```

---

### Post by krunge on 2008-06-07
> **Sonic Reducer said:**
> whoops, i copy/pasted from ubuntu-unleashed there.

what i have in my Preferences>Sessions is ```
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 57103
```

You also need to add the rfb port to that x11vnc cmdline, e.g.
```
-rfbport 57104
``` and forward that port from the router as well, and then use YourIPAddress:57103  (**not** 57102) in the web browser.

If you want to access both your laptop and your desktop this way I think you will need to forward 4 ports on your router: Two for HTTP java applet retrieval and Two for VNC traffic.

If you are doing this over the internet you may want encryption.  In that case you could point your -httpdir to the x11vnc SSL enabled java viewer applet (e.g. unpacked x11vnc tarball) instead of /usr/share/vnc-java.  More info:   [http://www.karlrunge.com/x11vnc/faq.html#faq-ssl-tunnel-viewers](http://www.karlrunge.com/x11vnc/faq.html#faq-ssl-tunnel-viewers)

---

### Post by Inxsible on 2008-06-07
how about opening the ports in the firewall as well. I am not sure if you have done that yet. Firestarter can help you do that.

---

### Post by TalioGladius on 2008-06-07
Go to system -> preferences -> remote desktop


Turn it on and use vnc to connect to it...

---

