---
title: "lan sharig"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by guptavivek34964 on 2008-11-09
ubuntu 8.04      i hav installed samba but still ihav problem to share the folders on lan ....it is showing a msg "can't open /var/opt/samba/" .......... 
what it does mean????
what should i do???/

---

### Post by mapes12 on 2008-11-09
If you're struggling with Samba try openssh instead: [http://ubuntuforums.org/showthread.php?t=793308](http://ubuntuforums.org/showthread.php?t=793308)

---

### Post by Peter09 on 2008-11-09
Here is a samba setup guide.

[http://samba.netfirms.com/](http://samba.netfirms.com/)

---

### Post by Kellemora on 2008-11-09
Hi Gup

Go into Synaptic and check the following.

Green Box on Samba, Samba-commmon and further down the list, a green box on smbclient.
IF there is a green box on smbfs UNCHECK IT.
Then hit apply.

After doing that, then go into terminal and type
sudo /etc/init.d/samba restart

You should be good to go now!

If not, in terminal type smbtree to see if you can see all your shares that way.
If it says smbtree not installed, type
sudo apt-get install smbtree
in your terminal.

By the way, it can take around 10 to 12 minutes for your network to repopulate itself from a clean startup.

I won't add any more info here until we see how you stand now!

TTUL
Gary

---

### Post by MrWES on 2008-11-09
smbtree -- nice command, thanks!

---

