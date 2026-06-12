---
title: "[SOLVED] connecting ubuntu client to ubuntu server"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by waterrr on 2008-08-04
hi all,
i have a ubuntu server and have available a shared folder via samba and i can connect to that server perfectly fine with the macs and window pc's, but when i try to connect to it via a ubuntu client using connect to server->windows share, i get an error that says
```
The folder contents cannot be displayed
Sorry, couldn't display all the content.
```
:confused:

---

### Post by ibuclaw on 2008-08-04
I think you need smbfs installed first.
```
sudo apt-get install smbfs
```

And you should be able to mount it using the following line
```
mount -t smbfs //192.168.1.2/folder /home/user/mountdir
```

Regards
Iain

---

