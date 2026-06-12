---
title: "how do i use Ubuntu ?"
date: 2021-03-06
forum: New to Ubuntu
---

### Post by tangara on 2021-03-06
Hi,

I just installed Ubuntu in Windows 10 WSL2, without virtual box.

But, I have no idea how to use it.

I tried installing nginx using:

root@DESKTOP-SB41UI7:~# sudo apt-get install nginx

But, I don't know if this is the right way.

Do I have to use all my commands at root? or something else.

root@DESKTOP-SB41UI7:~# cd /etc/nginx/
-bash: cd: /etc/nginx/: No such file or directory
root@DESKTOP-SB41UI7:~# sudo service nginx start
nginx: unrecognized service

The above shows that the file is not found and I am not sure why.

Now, I am also interested to use Ubuntu to execute a Docker.compose.yml file but since I don't know the above I can't do this.

Hope someone can help me. Tks.

---

### Post by mikewhatever on 2021-03-06
How to use Ubuntu should be obvious. You learn, search, ask questions. It is the same with anything new or unknown.

Now, what was the output of the first command? Also, does <apt-get update> works?

PS: All the above commands were run as root, so there is no need for <sudo>.

---

### Post by yancek on 2021-03-06
The link below is the official documentation on using Ubuntu so try that.

[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

>  I just installed Ubuntu in Windows 10 WSL2

I've not used WSL but it is windows software and I doubt the standard methods used in Linux/Ubuntu are the same.  Microsoft has a site explaining using WSL, that would be the place to go.  Also, there is an Ubuntu wiki on using WSL with Ubuntu, link below.

[https://wiki.ubuntu.com/WSL](https://wiki.ubuntu.com/WSL)

---

