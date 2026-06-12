---
title: "Where is x11vnc config file"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by seattle vic on 2008-08-10
I'm using Hardy on one machine, and am setting up an old 2nd machine with Hardy as well.  I'm trying to set up x11vnc on it.  I loaded it via synaptic, but cannot find where the config file is.  I can't even find it on my newer machine, and I'm pretty sure I had edited it at one time.

---

### Post by Mister.Vash on 2008-08-10
Do you have a .x11vncrc file in your home folder?

---

### Post by seattle vic on 2008-08-10
I looked for ~/.x11vncrc but it's not there...

---

### Post by krunge on 2008-08-10
> **seattle vic said:**
> I'm trying to set up x11vnc on it.  I loaded it via synaptic, but cannot find where the config file is.  I can't even find it on my newer machine, and I'm pretty sure I had edited it at one time.

x11vnc doesn't have a system config file of its own (but the ~/.x11vncrc can be used by a user to set his preferences).

You probably want some other application to start x11vnc, and so you need to put the call to x11vnc in its startup script or configuration somehow.

Maybe the section "Continuosly" in the following FAQ:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager")

There are also other apps that can run x11vnc for you, e.g. inetd.   You can find info about them in these forums.

---

