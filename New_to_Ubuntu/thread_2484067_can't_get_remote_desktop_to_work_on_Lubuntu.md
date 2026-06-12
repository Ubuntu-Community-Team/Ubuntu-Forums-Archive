---
title: "can't get remote desktop to work on Lubuntu"
date: 2023-02-16
forum: New to Ubuntu
---

### Post by mauritswoudenberg on 2023-02-16
Hi all,

I made a CNC plasma cutter that is controlled by software running on a inux computer. I want to run this computer headless and control it using VNC or any other screensharing app. 

I enabled SSH so I can run commands in the terminal. I've followed quite some guides, but couldnt get anything to work. I'm quite new to linux so more often than not I don't really know what I'm doing...

Can someone help me out?

Many thanks!

Maurits

---

### Post by TheFu on 2023-02-17
Don't use Gnome or KDE/Plasma as the DE. Stick with a lighter DE, if you need one at all. XFCE, Mate, LXQt are the main choices of lighter DEs.
Then use the client/server remote desktop x2go. [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)

I'm always surprised when people choose to use inferior software like VNC.

---

### Post by ActionParsnip on 2023-02-17
How do you control the cutter from the desktop? Is it a web browser based or do you manage it using command line?

---

### Post by mauritswoudenberg on 2023-02-17
I tried using VNC since that was the most suggested one when googling. Didn't realize it was inferior to other alternatives. I'll try X2go, thanks.

On the desktop I use Universal Gcode Sender. It's a Java based app. 

Cheers!

---

### Post by ActionParsnip on 2023-02-17
Is it a GUI based app? Is it embedded in a browser or a standalone thing?

---

### Post by mauritswoudenberg on 2023-02-17
It doesn't run in a browser, it's a standalone, GUI based app built on Java.

---

### Post by ActionParsnip on 2023-02-18
Have you tried launching it using X-Forwarding. Let's say the command is "foo"
In your Linux PC, you can run
```

ssh -X user@server foo

```
The application will be running on the remote system but display on the client system.

---

### Post by TheFu on 2023-02-18
> **ActionParsnip said:**
> Have you tried launching it using X-Forwarding. Let's say the command is "foo"
In your Linux PC, you can run
```

ssh -X user@server foo

```
The application will be running on the remote system but display on the client system.

[B]+1!   
Definitely use this rather than x2go or vnc or rdp!
[/B]
This is how to run remote applications between Unix systems on the same LAN.  I do this daily, constantly, right now.
Using remote X11 is much easier than dealing with a full remote-desktop and trivial for nearly all programs.  The only programs where it doesn't work is with those that won't work over a remote desktop either.  Also, remote X11 has much lower overhead and the window integrates into the desktop on the machine you happen to be sitting behind.

---

### Post by MAFoElffen on 2023-02-20
Additional to those last two posts, generate an ssh key and transfer it, so it automatically logs in to the target machine on the connect. Will make life much easier.

---

