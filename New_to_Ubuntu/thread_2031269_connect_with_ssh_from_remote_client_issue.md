---
title: "connect with ssh from remote client issue"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by vikka on 2012-07-21
Hello,

So I've setup my ubuntu server (12.04) with openssh and its been working just fine. I can remotely access it from putty using a local ip-adress, and it also works just fine if i use my public ip plus port 22 which is open.

I've forwarded port 22,80 and 21 on the router and also allowed these ports on the server firewall (UFW), this should enable http,ftp and ssh. 
Remotely a colleuge of mine can access the ip+80 without any issue and see the website, he can also access the ftp by using ip+21 in a ftp program. (vsftp installed on server-side).

However he can not access the server via ssh (ip+22) and an emulator like putty, for me it works just fine using the public ip+22 and a program like putty, 
but i am also inside the network and so it might be taking shortcuts?

Any idea? or particular things i need to setup in the sshd_config?
I find it strange that it works with port 80,21, but ssh towards 22 he just gets "timeout". The timeout also eliminates any possibility  that it would be account, permissions-issues etc.

Thanks ahead,

---

### Post by vikka on 2012-07-22
It works now, thread can be closed.
Solved by running client at administrator @ putty .. lol, server was fine all along.

---

