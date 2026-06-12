---
title: "HOWTO: set up secure (encrypted) Remote Desktop access (using ssh port forwarding)"
date: 2006-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by ultranet on 2006-07-22
Method 1: manual ssh port forwarding

Remote box (VNC client: receives UI events): 
1) Block port 5900 (vnc)
2) System->Preferences->Remote Desktop:
2.1) Check Allow other users to view your desktop
2.2) Check Allow other users to control your desktop (optional)
2.3) Check Require the user to enter this password: (preferred)
3) Open port 22 (ssh)
4) Ensure sshd is running on port 22

Local box (VNC server: sends UI events; note in remote desktop client and server are vice-versa in comparison to usual terminology):
1) ssh -L <some port/>:localhost:5900 <remote box IP/>
2) vncviewer -FullScreen localhost:<some port/>
E.g., 
ssh -L 5901:localhost:5900 <remote box IP/>
vncviewer -FullScreen localhost:5901

P.S.
I'll let other users add other methods (such as freeNX), if they please.

Good luck to humane computing, and everything.

---

### Post by tzulberti on 2006-07-22
A great How-to...

---

### Post by greeneemer on 2006-07-24
Is there an easy way to block a port within Ubuntu, or do I have to do that through a router or a firewall?

---

### Post by ultranet on 2006-08-09
> **greeneemer said:**
> Is there an easy way to block a port within Ubuntu, or do I have to do that through a router or a firewall?
Yes, you'd have to set up a firewall on the specific computer, or the router it's under.

---

