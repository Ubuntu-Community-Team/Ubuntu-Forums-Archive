---
title: "export desktop to laptop display"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by xolot1 on 2008-05-11
well im planning on upgrading my laptop to a nice quad core desktop this coming summer, and am really looking forward to getting ubuntu going full throttle on it (im working now to learn to multithread my programs, hehe).

anyways, im wondering what i will be able to use this current laptop for.  its got a nice 17" screen, so id really like to keep using it for something.  now i know i can keep it going as its own separate machine, but i was hoping to perhaps integrate it more.

are there any ways to export specific screens other linux displays?  i know i can export an entire session, but im not looking to use the laptop as a full terminal -- just the screen.  i imagine i can also set up some kind of cloned display, but thats not going to be too helpful for me.

can i trick X into displaying some portion of its rendering across a network/other connection to be received by the laptop (which could be running a minimal ubuntu install with some sort of viewer)?

im suspecting this is all just wishful thinking, but i figured id at least posit the possibility...

thanks for any responses!

---

### Post by amohanty on 2008-05-12
Running a minimal ubuntu with X on the laptop, if you have allowed XDMCP login (System->Preferences->Login Window:Remote Login & the Security tabs) enabled on the desktop, you can start an X session on the laptop which connects to the X server on the desktop.
[http://tldp.org/HOWTO/XDMCP-HOWTO/](http://tldp.org/HOWTO/XDMCP-HOWTO/)

HTH
AM
PS forgot to mention, you can also connect to a running session on the desktop. refer to the Howto.

---

