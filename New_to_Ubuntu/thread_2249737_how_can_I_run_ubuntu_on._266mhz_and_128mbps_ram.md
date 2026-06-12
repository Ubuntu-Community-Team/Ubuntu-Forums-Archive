---
title: "how can I run ubuntu on. 266mhz and 128mbps ram"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by JohnBlood on 2014-10-24
I''ve got an old Dell tower with. 266mhz cpu and 128mb of ram. I want to use it to practice running a website. I'm familiar with ubuntu,so I want to stay with ubuntu. Could I install ubuntu server and then install a light de, like openbox? What would you guys recommend?

---

### Post by matt_symes on 2014-10-24
Hi

> **JohnBlood said:**
> I''ve got an old Dell tower with. 266mhz cpu and 128mb of ram. I want to use it to practice running a website. I'm familiar with ubuntu,so I want to stay with ubuntu. Could I install ubuntu server and then install a light de, like openbox? What would you guys recommend?

Let me put it like this, my old router has a faster processor than that box. That box is a real dinosaur.

It does not have enough RAM to run Ubuntu server comfortably.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I would look at running Tiny Core with a web server or something like it and see if you can get that working.

Kind regards

---

### Post by /ADM on 2014-10-24
Even an LXDE desktop needs more RAM than that.  I'll second TinyCore, it will run on anything.

---

### Post by Doug S on 2014-10-24
I run Ubuntu server on an very very old computer with a 200 MHz CPU and 128 Megabytes of ram. It works surprisingly well. I even run Samba on it. As a simple web server, it is fine. I use it each cycle for minimum requirements testing, the thinking being if this computer that is less than minimum requirements works, then one that meets minimum requirements will work for sure.

However, for the 13.10 or 14.04 cycle the memory requirements for the installer increased by another 64 megabytes (I think it was) and so I now do not have enough memory for the installation process, but have no problem upgrading from an earlier version. So, I suggest you try 12.04 server. Do not try to install a GUI. Have something else to do during the installation process, as it takes quite awhile.

Edit:
see also: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1294908](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1294908)

---

### Post by tgalati4 on 2014-10-24
Or set up a freenas server:  [http://nas4free.org](http://nas4free.org)

---

