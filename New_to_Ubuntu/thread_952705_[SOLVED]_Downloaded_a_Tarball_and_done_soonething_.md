---
title: "[SOLVED] Downloaded a Tarball and done soonething foolish methinks"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by potatoehead64 on 2008-10-19
Hi, 
I downloaded Cg-2.0_May2008_x86.tgz yesterday trying to follow a complicated procedure to do with compiling a program and I think I've made a foolish mistake. The above file was supposed to be placed in the "root" file before extracting it, but I extracted it on the desktop. I'm now unable to move of delete anything from my desktop. 
I'm sure its to do with file permissions that can be changed in "root" or "terminal" but I've been unable to find out what to do. 
Can anyone help?

Thanks. 
Marty
running 8.04 Hardy.

---

### Post by sethvath on 2008-10-19
If you understand chmod/chown, do it via terminal. My guess is you're not comfortable with terminal so I'll lead you from nautilus instead. 

1. In terminal: gksu nautilus (this logs you as root on nautilus)
2. Navigate to your desktop from nautilus ie. /home/potatoehead/Desktop
3. Copy and paste the folder to wherever you like. 
4. Profit. 

If you want to change ownership of the files, right click the folder and choose permissions. Modify the owner and group to yourself.

---

