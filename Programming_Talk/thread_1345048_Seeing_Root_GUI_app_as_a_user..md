---
title: "Seeing Root GUI app as a user."
date: 2009-12-03
forum: Programming Talk
---

### Post by weaver4 on 2009-12-03
I am developing software that will run upon boot up and has a gui.  Let say a security app.  

When the system boots up the application will run.  I will change the startup script of rc.local to start the application.  

But when a user logs in I want them to be able to see the gui of the application.  Each system will only have one user.  The application does need to have root permission to run.

How do I do that?

---

### Post by The Cog on 2009-12-03
That sounds to me as though you need to separate the application into server and GUI halves. Then launch the server at boot, and launch a GUI that connects to it as the user logs in. Connecting by unix sockets is probably the way to go, but if you were to use TCP/IP networking, you could then also have a remote GUI (if you wanted).

---

### Post by weaver4 on 2009-12-03
Yeah, that is one thing I was thinking, but the application is already complete.

---

### Post by falconindy on 2009-12-03
> **weaver4 said:**
> Yeah, that is one thing I was thinking, but the application is already complete.
Apparently it's not done if it isn't doing what you (the developer) wants.

---

