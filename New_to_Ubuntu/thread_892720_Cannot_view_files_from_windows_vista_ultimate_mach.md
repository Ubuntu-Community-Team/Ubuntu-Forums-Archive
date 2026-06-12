---
title: "Cannot view files from windows vista ultimate machine"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by iceman1984 on 2008-08-17
Good day I recently installed Ubuntu 8.0.4 LTS about 2 days ago on my vaio laptop. Please note that I'm a complete noob since this is my first experience with any OS beside Windows. I'm connecting wirelessly through a WRT300N router. Presently I have one other machine connected to the router which uses Windows Vista Ultimate and is used mainly for accessing files. 
Currently I'm experiencing 2 problems, firstly I can't remote desktop to the vista machine and vice versa and secondly I cannot access any files from the vista machine.

However, from my Vista Machine I can see my laptop in Networks but I cannot access any files from it. I ensured that both machines belong to the same workgroup. I would also like the vista machine to act as an ftp server so that I can access my files via laptop. Any help would be greatly appreciated, this is somwthing I'd like to get sorted out quickly. Thanks

---

### Post by Gamma746 on 2008-08-17
> **iceman1984 said:**
> Currently I'm experiencing 2 problems, firstly I can't remote desktop to the vista machine

Make sure you're using "Terminal Server Client", not "Remote Desktop Viewer"

> **iceman1984 said:**
> and secondly I cannot access any files from the vista machine.

Read [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba).

---

### Post by ender8282 on 2008-08-17
> **iceman1984 said:**
> 
Currently I'm experiencing 2 problems, firstly I can't remote desktop to the vista machine and vice versa  I am not famaliar with a port of the MS remote desktop connection for Linux.  You will likely need to install an application on both the Linux and the windows machine.  You might look into something like [RealVNC]("http://www.realvnc.com/vnc/").  

 > and secondly I cannot access any files from the vista machine.

However, from my Vista Machine I can see my laptop in Networks but I cannot access any files from it. I ensured that both machines belong to the same workgroup. I would also like the vista machine to act as an ftp server so that I can access my files via laptop. 
I don't recommend 'sharing' files on your laptop.  When you go to a different wireless network those shared files are still being shared and are pretty easy for other people to view.  If they are writable then someone can maliciously ruin your day.  

As far as a Vista FTP server I found this [article]("http://www.bleepingcomputer.com/tutorials/tutorial134.html") after a quick Google search.  Other than that I have no clue.  I don't have vista so I can't really be much help.  If you can get vista set up to publish files you should be able pull to the laptop, and push to the server and never need to publish anything on the laptop.

---

### Post by iceman1984 on 2008-08-17
> **Gamma746 said:**
> Make sure you're using "Terminal Server Client", not "Remote Desktop Viewer"



Read [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba).

I did try Terminal Server Client and encountered this error:
Error: recv: Connection reset by peer.

I'll check VNC in the mean time. Thanks all for he help

---

