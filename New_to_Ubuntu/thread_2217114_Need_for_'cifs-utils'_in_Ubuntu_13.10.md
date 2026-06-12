---
title: "Need for 'cifs-utils' in Ubuntu 13.10?"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by srikesh2 on 2014-04-15
Hello,

I am not new to Ubuntu but I am not an IT person either. Hence the question.

I have a 1TB NAS drive at home that I use for backup purposes. I am successfully able to connect to it from my Ubuntu (13.10) desktop using graphical methods (Files -> Connect to Server -> Enter Server Details). Lately, I have been thinking of automatically mounting the NAS drive at boot to a folder under the 'media' directory. According to the instructions, I have to install 'cifs-utils' first. Why?

Why am I able to connect to the drive graphically but need an additional application to connect to it with command line (even to temporarily mount)? If I can do it graphically, doesn't it mean there is some existing application that can already do what 'cifs-utils' is supposed to do? I am of the opinion that I don't absolutely need an application, I will not "clutter" my machine by installing it (just my preference).

Like I mentioned, I am not an IT guy so I would appreciate a simple but detailed response. Thanks in advance.

---

### Post by Kris_Spencer on 2014-04-17
Hello. I'm guessing that the graphically done method is just using strait up Samba. So my thought is, no. I don't think you need Cifs. I'd add in more info about using fstab to mount the NAS, but I'm afraid that I am fimiliar with the Cifs method. I completely understand that you don't want more stuff installed that you aren't going to use. I run my machine very slim.

---

### Post by Canterwood on 2014-04-17
Hello there!

Gnome uses GVFS to connect to your Samba share I believe (check out this [wiki article]("http://en.wikipedia.org/wiki/GVFS")). You can use ```
gvfs-mount
``` to mount remote folders, but ```
mount
``` can also do that. Check out this [answer]("http://askubuntu.com/questions/56428/how-to-automount-a-gvfs-file-system-on-logon") on AskUbuntu.

---

