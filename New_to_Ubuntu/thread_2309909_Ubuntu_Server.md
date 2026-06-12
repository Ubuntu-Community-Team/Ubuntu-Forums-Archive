---
title: "Ubuntu Server"
date: 2016-01-14
forum: New to Ubuntu
---

### Post by jbcohen on 2016-01-14
I have three windows PCs and would like to be able to access my Ubuntu server with all three of them, I would like to ask how do I accomplish this assuming that I have bought a desktop and installed Ubuntu server on the box that I intend to use as the server?  All three laptops are running different versions of Windows: 7, 8.1 and 10.   So most likely I will need different instructions for each laptop.

---

### Post by TheFu on 2016-01-14
Use ssh, scp, sftp to access the Linux machine.  This is secure from anywhere in the world, if ssh-keys are used, not passwords.

Typical Windows tools for this are:
* Winscp
* Putty

Since you didn't say how you wanted to "access" yoru Ubuntu server, I didn't want to assume too much.  Just install **openssh-server** and **fail2ban** on the ubuntu machine to get started. That will enable ssh/scp/sftp access provided there isn't anything else blocking it like a router or firewall on the network.

If you want a remote desktop, that's a little harder. x2go is probably the best answer for most people (uses ssh tunneling and it is mostly secure). Definitely more secure than any other free alternative and many commercial alternatives.

If you want MS-Windows Exploder drag-n-drop access, that's a little more involved (Win10 broke some things) and it isn't secure.

Basically, with ssh and sftp, your Linux machine can be accessed from anywhere in the world, securely, assuming a few fairly simple details are addressed.  Pretty much every networked OS has both a nice, free, ssh and a nice sftp clients, so you're covered there.

---

### Post by ub-newbie on 2016-01-22
As "TheFu" said, you didn't state how/why you wanted to "access" your Ubuntu server, so I will guess.

If you want to use it as a file server (store/server up movies, music, etc) and only access it from inside your local network, I would set up SAMBA.  
In the WinX world, SAMBA shares will show up/can be created in Windows explorer (on all versions you listed).

If you want to access it from OUTSIDE your local network, security becomes a issue.  I would use OpenVPN & SAMBA for files/movies/music.  That will require network and firewall knowledge/configuration on your router and Ubuntu server.

So, if you want to share movies on computers connected to your local network only (i.e. your 3x Windows laptops) creating a SAMBA server on your Ubuntu box would be my suggestion.  
If the laptops are on Wi-Fi, make sure the wireless network is NOT isolated from the wired network (in your router) {assuming your Ubuntu box is on your wired network}

---

