---
title: "missing folder"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by zorobabel on 2008-09-23
Hi every body, this is my first post here and my first 7 hours with linux (xubuntu 8.04).

I was trying to get a remote desktop connection like in this tutorial:

[http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)

... and at the part where I have to create an entry for xinetd, I don't have that folder and I can't create it. I tried logging in as root and nothing. I hope you can help with this.
Thanks!

---

### Post by Elfy on 2008-09-23
To create the folder

```
sudo mkdir /etc/xinetd.d
```

To edit file

```
gksudo mousepad etc/xinetd.d/Xvnc
```

save and close

---

### Post by zorobabel on 2008-09-25
thanks forestpixie!

---

### Post by Elfy on 2008-09-25
welcome can you mark thread solved - thread tools

---

