---
title: "Openssh server: Can't connect from remote"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by billyrobCS on 2012-10-14
Hi, sorry for the potentially stupid question. I have downloaded and installed openssh-server on a clean(just installed) ubuntu 12.04 install. I can connect just fine on the local lan with username@192.168.x.x but I don't know how/can't connect from a remote network. 

I attempted to connect to it with my android phone via the 3/4g network using the ip address (using connectbot). [email]username@xx.xx.xxx.xxx[/email] but this just times out. 

Is there anyway to setup my ubuntu machine to accept connects from any network without getting a domain name? 

Thanks!

---

### Post by paulocr on 2012-10-14
You need to have a public IP address or ddns and do port forwarding in your router

---

### Post by HermanAB on 2012-10-15
Yup, you need to forward port 22 TCP from your router to your Linux machine.

---

