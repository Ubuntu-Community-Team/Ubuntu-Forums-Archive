---
title: "Remote Desktop/Terminal connection + ubuntu Server (Without GUI)"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by TheeDudes on 2013-05-08
Hello, 

This is my first post, Thank you for everyone's help to help me figure it out.

I would like to know how could I with ubuntu, setup a server so I can connect via SSH straitght in the terminal without having to install a GUI. I want to keep my server GUI FREE but still be able to remote connect and install packages and/or play around in the terminal with an encrypted tunnel or secured connection from a Windows 7 desktop pc... Is that possible ?

Thanks :)

---

### Post by mastablasta on 2013-05-08
yes. install Ubuntu Server on server.

then to connect to it from windows use:

putty

also winscp is a good option.

if you want to control your server via web browser as well then install webmin or zentyal on it.

---

### Post by Cheesemill on 2013-05-08
You need to install an SSH server on your server...
```
sudo apt-get install openssh-server
```
You can then just use the ssh command to connect to it from a Linux box, or use [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") to connect from a Windows box.

---

