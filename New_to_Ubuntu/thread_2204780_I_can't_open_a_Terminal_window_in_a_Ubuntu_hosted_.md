---
title: "I can't open a Terminal window in a Ubuntu hosted virtual machine on VMware"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by janko2 on 2014-02-10
Hi,

When I try to open a Terminal window, it just flashes, and disappears. It worked before, and suddenly stopped working.

Here is a video I made of it happening (cursor is invisible so you have to guess where the mouse is):

[http://www.youtube.com/watch?v=jbOyJqufw8w](http://www.youtube.com/watch?v=jbOyJqufw8w)

I tried connecting with Putty, but it just crashes when I type in a password.

---

### Post by janko2 on 2014-02-10
I tried uninstalling and installing Terminal, but it doesn't work. I tried installing other terminals, but they don't work either. And Ubuntu without Terminal is quite useless..

---

### Post by ajgreeny on 2014-02-10
So how did you eventually get the terminal that appears toward the end of your video?

I don't like or use unity, nor do I know how to check the command in the launcher for terminal, but it may be worth looking to see what that command is.

---

### Post by janko2 on 2014-02-10
> **ajgreeny said:**
> So how did you eventually get the terminal that appears toward the end of your video?

Sorry, I should have showed that better in the video. Ubuntu that you see is in a VMware window, that Terminal brought up was Putty from the Windows machine underneath. I tried to connect over ssh, but the Putty client crashed in windows. It's like whenever anything tries to show me the Ubuntu command line, that crashes.

> **ajgreeny said:**
> I don't like or use unity, nor do I know how to check the command in the launcher for terminal, but it may be worth looking to see what that command is.

I'm not sure Unity is the cause, I installed several other Terminals, all crash at startup.

---

### Post by janko2 on 2014-02-10
I made a .sh script, and ran it in Terminal, and that way it opened and showed what it worked. So maybe it is a Unity problem.

---

### Post by sudodus on 2014-02-10
> **janko2 said:**
> Sorry, I should have showed that better in the video. Ubuntu that you see is in a VMware window, that Terminal brought up was Putty from the Windows machine underneath. I tried to connect over ssh, but the Putty client crashed in windows. It's like whenever anything tries to show me the Ubuntu command line, that crashes.

I'm not sure Unity is the cause, I installed several other Terminals, all crash at startup.

0. Do you try to connect with Putty via the network from the guest to the host?

1. Have you tested that the network is working (that the guest operating system can connect to other computers (for example the host)?

2. Are you running a server program in the host, for example openssh-server?

3. You can try another program, for example ssh instead of Putty.

---

