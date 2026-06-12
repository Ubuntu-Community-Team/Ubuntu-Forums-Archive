---
title: "Transmission ?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by nu2this2 on 2008-11-30
Hi all,

Trying to use transmission and having very slooooow DL speed.
I went to edit-preferences and noticed that the incoming tcp port indicates "closed". Is there a firewall installed automatically with 8.04?

Also, "Automaqtically Map Port" is checked. What does that mean?

Any suggestions?-------------Thank you.

---

### Post by gandaran on 2008-11-30
> **nu2this2 said:**
> Hi all,

Trying to use transmission and having very slooooow DL speed.
I went to edit-preferences and noticed that the incoming tcp port indicates "closed". Is there a firewall installed automatically with 8.04?

Also, "Automaqtically Map Port" is checked. What does that mean?

Any suggestions?-------------Thank you.
all ports are usually open in ubuntu (maybe it's your router firewall), and yes there's a firewall in ubuntu, you can install a firewall gui [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html) and set up transmission like this [http://img67.imageshack.us/my.php?image=example2pq6.png](http://img67.imageshack.us/my.php?image=example2pq6.png)

---

### Post by nu2this2 on 2008-11-30
Thanks for the quick response. I have forwarded the ports in my router

---

### Post by nu2this2 on 2008-11-30
Is there a way to shut down the firewall in Ubuntu while downloading?

---

### Post by madsmeg on 2008-11-30
> **gandaran said:**
> all ports are usually open in ubuntu 

Are you sure on this point, because that does not sound right to me at all....

---

### Post by gandaran on 2008-11-30
> **nu2this2 said:**
> Is there a way to shut down the firewall in Ubuntu while downloading?
type **ufw** in terminal for options if you don't want the gui

---

### Post by MrWES on 2008-11-30
do you have UPnP enabled on your router, and might you be running moblocker and/or ipblocker?

Bill

---

### Post by jgoguen on 2008-11-30
> **nu2this2 said:**
> Hi all,

Trying to use transmission and having very slooooow DL speed.
I went to edit-preferences and noticed that the incoming tcp port indicates "closed". Is there a firewall installed automatically with 8.04?

Also, "Automaqtically Map Port" is checked. What does that mean?

Any suggestions?-------------Thank you.
There is a firewall installed by default, but not turned on by default.  This is because no ports are open by default in a standard Ubuntu installation.  Thus, if you haven't set up a firewall, there's nothing to shut down while downloading.  The "Automatically Map Port" option tells Transmission to try to talk to your router to set up port forwarding.  If this doesn't work, make sure your router has UPnP enabled.

Your slow speeds might be related to the port being closed.  You said that you had enabled port forwarding on your router, did that fix it?  Also, do you have a static address?  If not, your port forwarding may suddenly stop working if you get a different IP address.  The better solution is to make sure UPnP is enabled on your router (directions are different for every brand) and make sure that Transmission opens the ports properly.  If port forwarding isn't working properly, that should be filed as a bug against Transmission.

---

### Post by mkvnmtr on 2008-11-30
When I have used transmission I too noticed that it said the port was closed. In spite of that if I had seeders I could attain the maximium speed that my ISP allows. I have no idea why. On my mac system I used port fowarding but I never did anything on Ubuntu. I now use KTorrent and like it better. It is the same I never did anything and get the maximium speed. Sometimes al little better than I got on Mac.

---

### Post by CLomax on 2008-12-10
When using bit torrents the speed depends more on the number of seeders (people uploading) and leechers (people downloading). Even with closed ports it's possible to get high-ish speeds.

---

### Post by philinux on 2008-12-10
> **jgoguen said:**
> There is a firewall installed by default, but not turned on by default.  This is because no ports are open by default in a standard Ubuntu installation.  Thus, if you haven't set up a firewall, there's nothing to shut down while downloading. 

Basic iptables howto

Iptables is a firewall, installed by default on all official Ubuntu distributions (Ubuntu, Kubuntu, Xubuntu). When you install Ubuntu, iptables is there, **but it allows all traffic by default**. Ubuntu 8.04 Comes with ufw - program for managing a netfilter firewall

There is a wealth of information available about iptables, but much of it is fairly complex, and if you want to do a few basic things, this How To is for you. 

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

