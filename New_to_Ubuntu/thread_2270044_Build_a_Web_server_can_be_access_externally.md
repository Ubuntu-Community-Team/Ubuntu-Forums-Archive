---
title: "Build a Web server can be access externally?"
date: 2015-03-19
forum: New to Ubuntu
---

### Post by Qiyuan_Gao on 2015-03-19
Hello guys, this is my first post in here. 

Recently I built my own website with apache2 in my university lab. However, the website can only be accessed by using the campus network, if I use my pc at home to visit it, it won't work. The server is connected to the campus server directly (no routers, but a Linksys switch), so there is no router port forwarding issues. 

Does anyone know how to solve my problem? Or is there any support documents I can learn from? I am really new to website setup.

Thanks !

---

### Post by Lee_Bhogal on 2015-03-20
I assume you have bought a domain and set the WAN IP address to it in DNS?

---

### Post by Lars Noodén on 2015-03-20
You'll have to talk with the network administrator to see if they'll open web ports for that one address.  However, it being in a lab, hey might be hard to convince.  Are they static pages or something dynamic based on PHP or similar?

---

### Post by bruce-hyatt on 2015-03-20
Look into using [ssh]("http://www.openssh.com/faq.html"):

---

