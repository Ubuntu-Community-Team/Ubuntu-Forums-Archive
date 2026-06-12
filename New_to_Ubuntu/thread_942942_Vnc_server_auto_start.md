---
title: "Vnc server auto start"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by SAFULK on 2008-10-09
Hi,

New to Ubuntu and linux in general! Does anyone know if,when or how it's possible to auto start VNC server without logging into an account? I'm setting up a headless server with ubuntu and I need to administer it with VNC! I know that I can set auto login for an account but that could be a security risk! Any suggestions or info would be greatly appreciated!

Thank You,
Scott

---

### Post by ahsile on 2008-10-09
Personally, I log into my box via SSH. Start up VNC. Then I tunnel the VNC connection through the SSH session to provide some encryption. When I'm done, I shut down vnc and log out of the SSH terminal.

This may not be what you're looking for... but it works for me! :)

---

### Post by SAFULK on 2008-10-09
Thanks! maybe I'll give that a try!!!

---

### Post by SAFULK on 2008-10-09
I can't get that to work can you tell me how your setting that up??

---

### Post by ahsile on 2008-10-10
Ok, I'm at work... so I've got putty pulled up.

What I have set up is under my 'home' session, I have the following set under the 'Tunnels' config:

```

Source port: 2000
Destination: home.ip:5900

```

If you were going to do this from another linux box, you could accomplish it like this:

```

ssh remotehost -L 2000:remotehost:5900

```

That tells your ssh session to forward local port 2000 (this is just the port I use, it can be anything you want) to remotehost port 5900, but from the other side. This means that all your VNC traffic will be forwarded through the SSH session on port 2000, to port 5900 on the remote host.

Next, while I'm connected to the SSH session I use the following to start up VNC:

```

sudo x11vnc -bg -forever -rfbauth /etc/vnc/passwd -display :0 -auth /var/lib/gdm/:0.Xauth

```

I should note that you will need to run this command twice. It will die after you log in to the remote server. Also, the password file is generated with the vncpasswd command.

Then, from VNC I connect to the address: localhost::2000

When I'm done, I log out of the Ubuntu session, then kill vnc (just a kill command after getting the pid... if you remove the -bg -forever from the command above, you could just CTRL-C it though).

Hope this helps :)

---

