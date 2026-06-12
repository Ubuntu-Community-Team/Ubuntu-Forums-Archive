---
title: "GUI interface to my Ubuntu"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by bjnr on 2008-08-05
Hi,

I have a dedicated server from one hosting provider with Ubuntu 8.04 installed on it.

The provider gave me ssh details.

How do I install/access any GUI interfaceon that server.

How do I check if something is already installed?

Thank you.

---

### Post by Joeb454 on 2008-08-05
You wouldn't be able to use a GUI on that server, as it's remote, though you can use SSH :)

To see if something is installed, ssh to that server, and try and run the program

---

### Post by bjnr on 2008-08-05
Hi, is there a kind of Remote Desktop (vnc) available for ubuntu?
What do you mean by "try to run something" in ssh? It is CLI and I need GUI..
I am just wondering how to find out if there is a GUI already installed or not (gnome or kde or whatever).

Sorry for these dummy questions, but this forum is supposed for dummies. Isn't it?

---

### Post by Sef on 2008-08-05
> Sorry for these dummy questions, but this forum is supposed for dummies. Isn't it?

The only questions that are dumb are the ones not asked.

---

### Post by bjnr on 2008-08-05
> **Sef said:**
> The only questions that are dumb are the ones not asked.
Thanks! =)
So how do I get a list of applications and what are they used for on my server? What is the best way to have a remote GUI for it?
Thanks for answers!

---

### Post by Bachstelze on 2008-08-05
> **bjnr said:**
> Hi, is there a kind of Remote Desktop (vnc) available for ubuntu?

There are lots of vnc servers and clients available for Ubuntu. The one I'd recommend for such cases is [tightvnc](https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH#tightvncserver). However, be sure to *always* create a SSH tunnel before, and to connect through it, otherwise your password will be sent in clear text.

---

### Post by Joeb454 on 2008-08-05
> **bjnr said:**
> I am just wondering how to find out if there is a GUI already installed or not (gnome or kde or whatever).


I think you may find that calling your Hosting Provider may provide the best solution to this, as they will likely have direct access to the server

---

### Post by WRDN on 2008-08-05
> **bjnr said:**
> Hi, is there a kind of Remote Desktop (vnc) available for ubuntu?
What do you mean by "try to run something" in ssh? It is CLI and I need GUI..
I am just wondering how to find out if there is a GUI already installed or not (gnome or kde or whatever).

Sorry for these dummy questions, but this forum is supposed for dummies. Isn't it?

Although GUI based programs will not work by typing only the name, you can test if a program exists. For example, if you use SSH, and type "firefox", it will find the program, but not start, as it "Cannot find display".

There is a guide here on [Tunneling VNC Connections though SSH]("https://help.ubuntu.com/community/SSHHowto#Tunneling%20VNC%20connections%20through%20ssh"). This ensures all data is encrypted.
The "[Running GUI Programs]("https://help.ubuntu.com/community/SSHHowto#Running%20GUI%20Programs")" section of the same guide is also useful, as it allows for the forwarding of X11 through SSH, and means you do not need to tunnel VNC through SSH.

---

### Post by bjnr on 2008-08-05
> **WRDN said:**
> Although GUI based programs will not work by typing only the name, you can test if a program exists. For example, if you use SSH, and type "firefox", it will find the program, but not start, as it "Cannot find display".

There is a guide here on [Tunneling VNC Connections though SSH]("https://help.ubuntu.com/community/SSHHowto#Tunneling%20VNC%20connections%20through%20ssh"). This ensures all data is encrypted.
The "[Running GUI Programs]("https://help.ubuntu.com/community/SSHHowto#Running%20GUI%20Programs")" section of the same guide is also useful, as it allows for the forwarding of X11 through SSH, and means you do not need to tunnel VNC through SSH.
Thanks for these links!

---

