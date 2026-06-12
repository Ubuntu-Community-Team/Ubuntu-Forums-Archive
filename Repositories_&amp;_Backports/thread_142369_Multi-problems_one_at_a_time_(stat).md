---
title: "Multi-problems one at a time (stat)"
date: 2006-03-10
forum: Repositories &amp; Backports
---

### Post by smileyme on 2006-03-10
This started out as the need to get my linux machines on my cross-platform LAN. I have successfully installed Breazy on a PC and an Old-World Mac. Both are on line and working pretty good. Initially, neither could be seen by any other machine, but both could see and utilize the MSHOME network on an XP machine. I tried installing Samba and NFS, but get this Warning whenever I open Synaptic:

> W:Could not stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breazy/main Packages (/var/lib/apt/lists/ archive/ubuntu.com_ubuntu_dist_breazy_main_binary_i386_Packages) - stat (2 No such file or directory)

The Mac seems to have overcome this, but I'm not sure what I did. I can now see the Mac on the MSHOME network from my G4 (10.4.5), but can't connect to it, and neither the PC or the Old World Mac can now see MSHOME. I feel like I'm digging myself into a hole.

I think I need to solve the "stat" problem first, as the PC is the one I am more likely to be using.

Any help would be greatly appreciated,

Rick :)

---

### Post by fdoving on 2006-03-11
Hi.
Try to run 'sudo apt-get update' in a terminal
Then try to start synaptic again.


- Frode

---

### Post by smileyme on 2006-03-11
Thanks for the reply.

I ran the CL as you suggested and after compiling the list gave me the same message. The Mac, on the other hand seemed to have overcome the problem. I was able to install NFS and SMB, but I still can't connect to the network.

Rick :)

---

