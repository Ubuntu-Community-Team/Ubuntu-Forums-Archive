---
title: "[SOLVED] setting up ubuntu"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by revpaul on 2008-06-05
A few questions as i am totally hacked off with windows and moving all my machines to ubuntu 8.04 2 desktops 1 laptop, please remember i am fairly new to ubuntu and have limited knowledge of terminal. 
1. Is it better to clean install or upgrade as i am taking windows off machines i can format HD and fresh install. At present i have upgraded from 6.06 through to 8.04.
2. Is it possible to set up 3 ubuntu machines on a LAN via belkin router or do i need to make one a server. please direct me to tutorial.
3. can a wireless laptop access and share files across other machines or can it only use ethernet cable for LAN access same as windows. 
4. Is there any ubuntu/linux software for a belkin print server.

many thanks for your help.

---

### Post by powerpleb on 2008-06-05
> **revpaul said:**
> A few questions as i am totally hacked off with windows and moving all my machines to ubuntu 8.04 2 desktops 1 laptop, please remember i am fairly new to ubuntu and have limited knowledge of terminal. 
1. Is it better to clean install or upgrade as i am taking windows off machines i can format HD and fresh install. At present i have upgraded from 6.06 through to 8.04.
2. Is it possible to set up 3 ubuntu machines on a LAN via belkin router or do i need to make one a server. please direct me to tutorial.
3. can a wireless laptop access and share files across other machines or can it only use ethernet cable for LAN access same as windows. 
4. Is there any ubuntu/linux software for a belkin print server.

many thanks for your help.

1. Downloading the .iso and using it to clean install on all your machines will probably be faster and use a lot less bandwidth. But you loose all your settings.
2. Yes, should all work fine. If you want to share files you will need to make one a NFS server:[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
3. Yes, I have a dlink wireless router with my desktop plugged in with an ethernet cable and a laptop connected by wireless. The desktop is the NFS server and I am able to share files fine.
4. don't know

---

### Post by superprash2003 on 2008-06-05
if your belkin router has 4 ports.. then just connnect all pcs to the router.. Better fresh install.You can share files wirelessly as well

---

### Post by revpaul on 2008-06-05
Yes router is belkin mimo 4 port router with 1 port taken for belkin print server. I did not want to run wires round house if I am able to use wireless side of router for file sharing/swapping.

---

### Post by superprash2003 on 2008-06-05
if its a wifi router then connect all pcs to wifi router wirelessly..to share files you could use samba [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by revpaul on 2008-07-08
Followed all tutorials in the above thread which solved the problems.:)

---

