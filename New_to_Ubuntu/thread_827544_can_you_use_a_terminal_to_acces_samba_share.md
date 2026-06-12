---
title: "can you use a terminal to acces samba share???"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by stinger30au on 2008-06-12
on my lan at home i want to be able to get access to one of my windows shared directory's from the shell.

i can already access the share no drama from nautilus thats fine, but i  want access to it from shell.

any ideas???

thanks

---

### Post by Joeb454 on 2008-06-12
Yes!

```
smbclient:///192.168.1.1
``` If I remember correctly, and obviously you change the IP for the IP of the device you want to access :)

---

### Post by drs305 on 2008-06-12
I have a windows machine set up for sharing. Here is the command I use to access the windows computer, whose network is password-protected:
```
smbmount //192.XXX.X.X/"windows.network.name" /media/samba -o username=windows.username,password=XXXX
```

Then in terminal I can change to the mountpoint folder ( /media/samba ) to view and work with the windows files.

---

### Post by Joeb454 on 2008-06-12
Thanks drs305 :) It's be a while since I had to use that :)

---

### Post by bodhi.zazen on 2008-06-12
smbmount is depreciated in favor of cifs.

```
sudo apt-get install smbfs
```

Make a mount point :
```
sudo mkdir /media/smb
```

*You can use any mount point you like.

Mount :

```
sudo mount -t cifs //192.XXX.X.X/"windows.network.name" /media/smb -o username=windows.username
```

You will be asked your sudo password (if you have not used sudo in a while) and then your samba password. Not including you password in the command prevents you from typing your password in clear text (or having it in .bash_history).

> WARNING: smbmount is deprecated and not 	maintained any longer. mount.cifs (mount -t cifs) 	should be used instead of smbmount.

[http://us3.samba.org/samba/docs/man/manpages-3/smbmount.8.html](http://us3.samba.org/samba/docs/man/manpages-3/smbmount.8.html)

smbmount still works mind you , it is just you should start to transition to cifs

---

### Post by drs305 on 2008-06-12
> **bodhi.zazen said:**
> smbmount is depreciated in favor of cifs.

I learn something new every day on this forum. Good to know - I'll change my shortcut.

---

### Post by stinger30au on 2008-06-14
AWESOME!!!

you guys rocks. thanks for the help:guitar:

---

