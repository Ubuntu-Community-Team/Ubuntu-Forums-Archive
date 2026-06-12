---
title: "update manager - connection issue"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by harry rao on 2008-04-24
hi,
my friend helped me out with a previous issue i was having at uni and fixed it by connecting to the universities internet server and he forgot to reset my connection settings, now everytime i try and run update manager i get the following error :

W: Failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/pool/main/x/xorg/xutils_7.3+10ubuntu10_all.deb](http://ftp.iinet.net.au/pub/ubuntu/pool/main/x/xorg/xutils_7.3+10ubuntu10_all.deb)
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

could someone please tell me how to get to the connection settings to change the settings made by my friend.

-harry.

---

### Post by stump138 on 2008-04-24
Your friend probably added the university's repositories to your sources list

if you edit the file with a text editor

/etc/apt/sources.list

You can comment any lines out that are corresponding to the one you're showing.

---

### Post by harry rao on 2008-04-24
thanks alot :)

---

