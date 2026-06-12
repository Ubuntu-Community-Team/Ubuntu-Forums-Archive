---
title: "SSH tunneling"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by katyl on 2008-06-16
Hi Guys, Thanks for the help in advance.
I have 2 machines, that are most of the time in the same localnetwork. One of the computers is offering the LDAP for gcaldaemon. It's easy enough to to connect when they're in the same network, however I'm trying to set it up so I can access that database when I'm out of the office on my notebook. I think SSH tunneling is the solution I'm looking for but it's a concept that's baffelled me for a bit. I just want to make sure that I have this comand right before I run anything silly on my system.

If my plan is right, I should be able to run this command on my notebook, and it should ssh into the server (RSA authenition is allready set up). And whever I connect to localport 2000 on the notebook  it'll forward that to port 9080 on the server. 

ssh -f <user@ipaddressofserver> -L 2000:localhost:9080 -N

If it's wrong I'd love an explination of what is wrong, so I can learn :)

---

### Post by billgoldberg on 2008-06-16
I don't know if this applies to you, but the way I got my computers speaking with each other using openssh is explained here:

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

Again, if this doesn't apply to you, just ignore me.

---

### Post by katyl on 2008-06-16
Thanks for the reply Bill,
SSH File sharing is pretty nifty, and but I have file sharing set up that works well enough for me. I'm more worried about accessing a particular port on my SSH server, without exposing that port to the internet at large.

---

