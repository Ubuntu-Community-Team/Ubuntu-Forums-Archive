---
title: "[SOLVED] xdcmp Client"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by satjat on 2008-06-27
I have two Ubuntu PCs in use and I would like to access one from the other via xdcmp but without loging off. I believe xdcmp is much faster than any other method of remote login and the second pc is on a very slow internet line. I tried vnc and it is slow.
I can xdcmp from the login window and it works fine but I would like to do that in a window and not loging off all the time.
Thank you

---

### Post by HalPomeranz on 2008-06-28
Why not just use SSH?  With X forwarding you can run GUI apps from the remote system over the SSH connection.

---

### Post by satjat on 2008-06-28
I am not familiar with X forwarding. It sounds like exactly what I am looking for though.
If I undersand correctly it is like remote desktop but the window manager commands are executed localy.
Is that so? Do I need a specific client software?
Thanks

---

### Post by HalPomeranz on 2008-06-28
> **satjat said:**
> I am not familiar with X forwarding. It sounds like exactly what I am looking for though.
If I undersand correctly it is like remote desktop but the window manager commands are executed localy.
Is that so? Do I need a specific client software?


It's not exactly like a remote desktop software like VNC.  You log into the remote system with a command like "ssh -X remotehostname" (the -X enables X forwarding).  That gives you a command-line interface to the remote system.  However, if you then execute an X program like xterm, gedit, synaptic, etc, on the remote system, the window created will pop up on your local desktop because the X events are being tunneled through your SSH connection.  It depends on what you're trying to accomplish, but for most things it works very well.

And since you also have a command-line interface to the remote system, you can also do a lot of stuff on the command-line rather than gobbling up bandwidth with lots of GUI apps.

---

### Post by satjat on 2008-06-29
Thanks a lot.
It works exactly as I want it.

---

