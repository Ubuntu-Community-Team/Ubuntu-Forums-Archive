---
title: "How do I mimic a display on headless computer"
date: 2019-07-31
forum: New to Ubuntu
---

### Post by cablefreeantonio on 2019-07-31
Hello,

i'm trying to do remote desktop that doesn't have a screen plugged in, when I try apps like DWService or X2go I get a black screen or "No desktop available" is there a way I can trick the graphic card to think there's a screen attached?

Regards,

---

### Post by TheFu on 2019-07-31
x2go doesn't need a screen connected for the remote connection to work. It does need X/client libraries, however.  I run x2go on headless systems (and inside VMs) all the time - daily use systems.  The only real tricks to x2go are:
a) setup plan ssh between the client and server first.
b) the remote system needs a supported DE .... which is basically mate, xfce, lxde. Anything heavy will fail.
c) For Windows clients, load the font package too.

I don't know what DWService is, but there are some commercial service programs where the vendor company's programmers where so lazy that they left X/Client library dependencies in the code for 100% server programs. Idiots.  And charging $100K for the software ...   anyway, there is a virtual driver ... xvfb is the name I think. It works on every Unix. [https://manpages.ubuntu.com/manpages/trusty/man1/Xvfb.1.html](https://manpages.ubuntu.com/manpages/trusty/man1/Xvfb.1.html)

---

### Post by cablefreeantonio on 2019-07-31
Hi, thanks for the reply, they way you do it am I going to be able to view the proper desktop screen or just a terminal/xfce environment?

many thanks,

---

### Post by TheFu on 2019-07-31
None of what I've suggested provides only a terminal.

Running an X/client to display on your local X/Server will work 100% like it does locally, except fancy video playback and fancy audio. The other 30,000+ X/Client applications all work.

BTW, xfce **is** a proper desktop.  So is Mate, LXDE.  These won't work using remote X/Windows, but they will work in x2go.  x2go works sorta like vnc, but faster.  x2go provides a full desktop experience and while video playback and audio can work, it won't be smooth. To get smooth video, you'll need either a commercial tool or to use the SPICE display protocol. Unfortunately, SPICE only works when used with a hypervisor like KVM.

---

### Post by cablefreeantonio on 2019-07-31
> **TheFu said:**
> None of what I've suggested provides only a terminal.

Running an X/client to display on your local X/Server will work 100% like it does locally, except fancy video playback and fancy audio. The other 30,000+ X/Client applications all work.

BTW, xfce **is** a proper desktop.  So is Mate, LXDE.  These won't work using remote X/Windows, but they will work in x2go.  x2go works sorta like vnc, but faster.  x2go provides a full desktop experience and while video playback and audio can work, it won't be smooth. To get smooth video, you'll need either a commercial tool or to use the SPICE display protocol. Unfortunately, SPICE only works when used with a hypervisor like KVM.

It's much clearer to me now, thanks for that. Would you be able to point me to the direction of a tutorial to setup the way you mentioned? Sorry if I'm souding newbie to not know the basics.

Regards,

---

### Post by TheFu on 2019-07-31
Oops. Sorry.  I got this thread confused with another one.

---

