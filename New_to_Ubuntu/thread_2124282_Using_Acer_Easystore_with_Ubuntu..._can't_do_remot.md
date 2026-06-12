---
title: "Using Acer Easystore with Ubuntu... can't do remote desktop..."
date: 2013-03-10
forum: New to Ubuntu
---

### Post by cpap01 on 2013-03-10
Hello,

I recently decided to ditch the provided Windows Server 2003 from an Acer EasyStore machine.  Because the machine is headless, I had to take the hard drive out of it and pop it into another unit in order to install Ubuntu.

In it's current state, I am able to access shared folders and move files around without a hitch.  That part is working great!  The problem I'm having is that I'm unable to connect to the machine like I was with Windows Server.  I keep getting an error message that tells me remote desktop can't connect.  Again, I'm able to access the shared folders and files just fine, but I can't seem to get onto the system itself through remote connection.

I enabled Desktop Sharing in Ubuntu.  What else have I missed here?  Can this even be done?

Thanks for any help you can offer!

Christopher

---

### Post by sully101 on 2013-03-11
Not a guru here but I found this [http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/]("http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/") hope it helps

---

### Post by sully101 on 2013-03-11
> **cpap01 said:**
> Hello,
I enabled Desktop Sharing in Ubuntu.  What else have I missed here?  Can this even be done?

Has Ubuntu actually logged in a user that is sharing thier desktop. ie Its probabbly just sitting there waiting for you to login before its got a Desktop to share unless you have it set to login automatically.

---

### Post by DuckHook on 2013-03-11
Ubuntu works well as a headless server, but you must configure it with either Samba or NFS. The best version to install is the non-GUI server version. If you need a GUI, then installing one on top of the server version is easier than installing a Desktop version and then trying to change it into a server. Reason: server version comes preconfigured with apps for server. Both images and install instructions are [here]("http://www.ubuntu.com/download/server"). After you have installed the DE of your choice, you can simply further download the remote desktop app of your choice from the repos as well.

---

### Post by Hans_Quist on 2013-08-09
Also it is possible to manage your server easily with Webmin ([www.webmin.com](www.webmin.com)). And for commandline instructions I use PuTTY.

---

