---
title: "Connect Ubuntu desktop to server edition."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Jarlathg on 2008-09-16
Hello, :confused:I need to connect a laptop with ubuntu 8.04 desktop to an ubuntu server running ubuntu 8.04 server edition. Easy I'm sure, but I have no idea other then create user account connect to network and fail to logon. Can anyone point me towards some docs or how to? I'm drawing blanks on search's.

---

### Post by ggaaron on 2008-09-16
What do you mean by connect? Do you mean ssh, transfering files or something else?

---

### Post by Jarlathg on 2008-09-16
logon to the network. Use the network with a laptop with ubuntu installed.

---

### Post by Jarlathg on 2008-09-16
I should mention I am relatively new to ubuntu.And we have a network with all ltsp thin clients. But I have a couple of users who want there own laptops for obvious reasons. So I thought it would be straight forward and simple to logon to the network with a laptop with 8.04, But I'm struggling to find some basic how to docs.

---

### Post by ggaaron on 2008-09-16
Still I don't understand your question:/ What does logon to network mean? Do you want to make a machine work as a router and let every computer plugged in your local network access the internet?

---

### Post by Jarlathg on 2008-09-16
Yes I want to logon to the network with the laptop and  access network based files and network based applications such as firefox and access internet over the network.

---

### Post by Iowan on 2008-09-16
[Here]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall") is an article about setting up LTSP server.  [LDAP-client]("https://help.ubuntu.com/community/LDAPClientAuthentication") information in this help page.

Otherwise, the confusion is that you log into a machine, not a network. It's possible to set up an SSH-server that lets you "log into" the server.

---

### Post by ggaaron on 2008-09-17
If you want to setup router and dhcp server then I've used this guide:
[http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)

---

### Post by Jarlathg on 2008-09-17
Thanks guys just a newbie and connvert to ubuntu and not sure where to start with respect to server admin and client management. Will check out links.

---

