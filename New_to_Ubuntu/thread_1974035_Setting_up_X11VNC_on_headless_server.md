---
title: "Setting up X11/VNC on headless server"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by Znerox on 2012-05-05
I'm setting up a new headless server, and I want to have the ability to connect from my W7 pc for some programs that require a GUI. I'm new to X, and from what I've read it seems like it works in a completely diffrent way than VNC. I can't find any guides to how you actually set it up and conect from windows. Can anyone point me in the right direction?

---

### Post by HermanAB on 2012-05-05
You'll have better luck with SSH and Cygwin on Windows.

---

### Post by Znerox on 2012-05-05
How about VNC? I tried tightvncserver, but when I connected I could only see the background, nothing else.

---

### Post by steeldriver on 2012-05-05
I've had good results on WinXP with UltraVNC

I have 2 sessions open right now, one via a PuTTY SSH tunnel to a remote machine running Xvnc (at work), and one connected directly to a 'forever' instance of x11vnc running on a headless box (laptop with a busted screen) as described here:

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

The SSH tunneling setup is somewhat less intuitive - basically start a PuTTY session with a tunnel from your remote port (usually 5900 + display number) to an equivalent port on the Windows box and point the Windows VNC viewer to *that* (e.g. localhost:5905) - I didn't bother to do the same for the headless box because it's within my home LAN.

---

### Post by Znerox on 2012-05-05
It actually worked :eek: Thanks!

---

