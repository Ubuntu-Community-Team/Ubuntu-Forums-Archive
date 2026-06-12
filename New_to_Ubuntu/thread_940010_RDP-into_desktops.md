---
title: "RDP-into desktops"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by kiloraw on 2008-10-06
Hey, I am a newb...I really get tired of saying that.
I work as a help desk guy. So I usually remote into computers on our domain. What type of software is on Linux that I could use on Windows domain to do this. I know some default software came with it.I really don't know what to use for this...help would be apperciated:confused:

---

### Post by cek on 2008-10-06
sudo apt-get install rdesktop


rdesktop is a Windows RDP client, works extremely well.

---

### Post by mlentink on 2008-10-06
Applications>Internet>Terminal Server Client

As a windows-user, you will undoubtedly be familiar with remote desktop and its protocols. tsc supports these. Obviously, your windows-clients will have to be set-up to allow for remote assistance...

---

### Post by haydnc on 2008-10-06
From memory rdesktop also lets you use a VNC connection - assuming you've got the client installed on the remote machine. 

I don't believe there is anything out there that lets you use a VNC style connection to let you view the remote desktop while the other person is still working without having pre-installed the remote software on the client machine.

Dameware is possibly one of the few remote support tools I really miss from Windows (as much as I hate to admit I miss anything at all).

---

