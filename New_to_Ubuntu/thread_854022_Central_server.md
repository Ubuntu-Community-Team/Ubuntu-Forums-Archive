---
title: "Central server"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by roffemuffe on 2008-07-09
I am looking to set up a central server for my home. I need all users to be able to log on to the server (from local workstations) before they gain access to a) internet, b) games and c) media-files. Well, pretty much must be logged in to be able to use the computer.

Is an central Ubuntu server able to the trick ? Creating users and keeping their rights and accesses seperate ? Or do I need a more specialized software for that ?

---

### Post by iaculallad on 2008-07-09
For the internet connection part, I'd suggest you use IPCop w/ Advproxy addin. You can create user authentication (User Management) w/c will allow users to input correct username and password before they can access the internet.

Games and Media-Files cannot be accessed in this Server so I guess it won't be applicable in your setup. This is just a suggestion.

---

### Post by superprash2003 on 2008-07-09
for the media files you could setup NFS (if its a linux only network) or samba ( for windows +linux clients

---

### Post by roffemuffe on 2008-07-10
Since this is the Absolute Beginner Forums, I will ask the obvious question :)

So I need to set up a computer with Ubuntu Server edition, then install these programs on that computer. I will be connecting the server to the internet router, printer, etc.

The workstation USER1 (with ubuntu OS) will be connected to the server via a normal 100Mbit switch-box. This workstation will only have access to the internet (and it's qualities) if USER1 successfully logs on to the server, where USER1 is a normal user.

The scenario is that my brother wants me to be the 'hands-on' to set up his home-network. He's got pre-teenage kids, so these will be the primaary users along with him, his wife and a Guest-account. I have experience with windows, so I know what I'm in for (should've said no :))

I need a central database/server, so I can create users on the server, save their settings and reuse them at the various computers around the house, so no matter where the kids logged in, they still have their own interface. No more fighting!

---

