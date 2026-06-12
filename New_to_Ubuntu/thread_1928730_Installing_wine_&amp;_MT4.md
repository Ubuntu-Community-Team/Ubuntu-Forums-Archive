---
title: "Installing wine &amp; MT4"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by sticklerx on 2012-02-20
I have purchased a cloud linux ubuntu server from rackspace.com.
This is a barebone server without any GUI interface.
I want to use this to run my MT4 Forex trading server.
How do I install wine from the command prompt?

---

### Post by tnicewicz on 2012-02-20
sudo apt-get install wine

that should do the trick

---

### Post by sticklerx on 2012-02-21
I tried that. The message I received was:

root@ACG-L2:~# sudo apt-get install wine
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@ACG-L2:~#

I think there much be some other problem!

---

### Post by rajivxxx on 2012-04-18
> **sticklerx said:**
> I have purchased a cloud linux ubuntu server from rackspace.com.
This is a barebone server without any GUI interface.
I want to use this to run my MT4 Forex trading server.
How do I install wine from the command prompt?
How you set up vnc viewer, i know how to set up mt4 on ubuntu , successively set it on my own pc ,it is simple ,plz help me how you set up vnc viewer or any thing else on ubantu

---

### Post by HiImTye on 2012-04-19
close your other package managers and that error will go away (synaptic, ubuntu software center, update manager, etc)

---

