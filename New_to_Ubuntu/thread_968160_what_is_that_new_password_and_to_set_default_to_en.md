---
title: "what is that new password? and to set default to english?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by bunli on 2008-11-02
I use pendrivelinux.com and installed ubuntu 8.10 into USB flash drive, [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/).  Installation is successful and it is running fine.

some basic questions please,
1) how to set up a password for another user?  It asks me about a password, I have never set up any password, and in order to change a password, I need to log in with a password........... :(

2)  I accidentally pressed a different language upon boot up, and now it is always that foreign language.  In order to set  to english as default, i need to log out and log back in, and i do not have a password.  Current user is ubuntu@ubuntu.  Whoami returns ubuntu.

My system, ubuntu 8.100 usb flash boot

Sorry for the truely basic questions, TIA,

bun

---

### Post by bunli on 2008-11-02
I have another linux box and can ssh into this USB flash ubuntu 8.10.  I think you need SSH to change root password? or user password?

TIA,

bun

---

### Post by bunli on 2008-11-02
Ha, I solved the problem by poking around.  using the option -d, delete password, brilliant!

open a terminal
sudo passwd ubuntu -d
password deleted

sudo passwd ubuntu
new password user ubuntu (type your new password)
new password set

And when you log in and out, you then have the option of setting language

thanks for reading,

bun

---

