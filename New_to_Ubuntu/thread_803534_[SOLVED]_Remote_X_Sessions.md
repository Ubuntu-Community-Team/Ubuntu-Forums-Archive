---
title: "[SOLVED] Remote X Sessions"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-05-22
Ok here is what i have:

Desktop (Trip Boot Ubuntu Hardy, XP, Vista)

Server(Ubuntu Hardy Server LAMP+Samba)

I would like to be able to from the desktop initiate remote X sessions on server.  The preference however if possible is to maybe have a gnome desktop environment to run on.  Is this possible and how would one go about doing this?

And also how would i go about making this work from a Windows desktop as well?

Many thanks in advance.

---

### Post by volkswagner on 2008-05-22
To forward x you will need x-server running on the server machine.  To get a remote desktop you will need vnc.

Running X on a server is not recommended for security and waste of resources.  I you want some sort of gui for configuring the server, look at ispconfig, or webmin.

You can install the gnome desktop on the server via apt.

If you really want a desktop running on your server check out this how to.

[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by Inxsible on 2008-05-22
Running X on a server is quite wasteful, if your server is being hit all the time. But you can install X and a gnome desktop on it, if you so wish.```
sudo apt-get install xorg gdm ubuntu-desktop nautilus synaptic
``` should do it. You may or may not want to add additional packages depending on what you want on there.

To get X sessions on the server you can either use VNC - as suggested by volkswagner, But it is quite slow in my opinion. Have a look at NX(NXServer and NXClient). Its a great software for remote X sessions.

---

### Post by Mauler5858 on 2008-05-22
webmin or ispconfig seem like they might do the job.  Which one is more preferred, or more feature rich

---

### Post by neurostu on 2008-05-22
Its really easy to initiate remote X sessions all you need to do is connect over SSH.  Just add -X to the end of your ssh command and X will be forwarded over the connection.  If you want to do this over windows then you need to install Cygwin.  When you install Cygwin you will need it to install the openssh and x libraries.  Its not that complicated you just need to make sure you install all the required libs.

---

### Post by volkswagner on 2008-05-22
> **Mauler5858 said:**
> webmin or ispconfig seem like they might do the job.  Which one is more preferred, or more feature rich


It seems some die-hard server admins. don't think webmin is secure enough (I don't think they use ispconfig either).  I guess they can get around without it.  I have used webmin and I am a newbie.  I can agree with some reviews comparing the two that you still need to "know what you are doing."  

I have read ispconfig is easier on the newbie, but not as feature rich.  I am giving ispconfig a go on my new server install.

---

### Post by Mauler5858 on 2008-05-23
Thanks all i got it running Webmin & openssh(and putty).  I believe it will work fine.

Thanks

---

### Post by hyper_ch on 2008-05-23
ispconfig is for setting up a server for webhosting with user/customer management, domains, email, ......

---

