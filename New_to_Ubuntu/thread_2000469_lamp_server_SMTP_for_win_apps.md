---
title: "lamp server SMTP for win apps"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by dennisharding on 2012-06-09
Ok so I'm not an absolute beginner with ubuntu...I've got a lamp server on my local network, 1 DSL 1 perminate ip my own domain. I did the whole setup and been working fine for months. Now my gf has bought another domain name and wants to use 1 of our other machines for her server...all windows though..SO...here's the deal. I want to get my lamp to allow her win apps to use my SMTP... I'd like to eventually probably setup a reverse proxy so we can both use the 1 ip, I think that can be done from what I've been reading. Anyway her win has IIS6 in vista and doesn't have an SMTP. So thats the first priority...lol...her...getting my lamp to allow her win apps to send simple auto reply email thru SMTP. Any pointers and help would be greatly appreciated.
Thanks in advance.

---

### Post by Lars Noodén on 2012-06-09
Regarding SMTP, either Postfix or Exim would be easy to set up.  

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[https://help.ubuntu.com/community/Exim4](https://help.ubuntu.com/community/Exim4)

---

