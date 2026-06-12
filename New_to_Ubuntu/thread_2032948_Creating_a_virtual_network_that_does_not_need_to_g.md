---
title: "Creating a virtual network that does not need to go outside of the host machine"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by Sacerdocio on 2012-07-25
I am trying to create an environment within VirtualBox, utilizing Ubuntu Server 12.04 LTS. I am using a Macbook Air as the host machine.

What I would like to be able to do is create and access "webpages" on my mac from the VirtualBox server. I want to be able to accomplish this without having to set up a network that would require internet access or any other form of external networking outside of my host machine.

I have been using Ubuntu on and off for a few years, but still consider myself a beginner especially when it comes to a totally command line system.

Thanks in advance for any help you may be able to provide.

---

### Post by HiImTye on 2012-07-25
just make an http server and bind it to the loopback interface

---

