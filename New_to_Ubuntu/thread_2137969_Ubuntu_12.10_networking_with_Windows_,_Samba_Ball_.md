---
title: "Ubuntu 12.10 networking with Windows , Samba Ball ache"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by 90Ninety on 2013-04-22
Ubuntu has been mostly a pleasurable experience , for a avereage guy with moderate knowledge it has been pretty easy and has shown to be preferable in many ways in comparison to windows 

 However when it comes to sharing folders with other Windows PC'c, ubuntu has been a huge let down and has left me feeling disappointed , in fact has been a complete ball-ache in this resoect 

 Why is there no GUI for networking ? 

 The samba application  has never launched on both of my installations , which had led me to writing scrips inside of samba's configuration file , which is a pain ( if you're like me - a noob) 

If you have seen my other thread , then you'll see how much of a challenge I found it .   Why hasn't the Samba Application GUI worked for 12.10 ? Surely this should be addressed , if there was a working Samba GUI , then every-day people would surely be able to network their Ubuntu PC right  


 What else am I missing ? I didn't mention Nautilus but I remember tinkering there too , not to mention the code and other scripts i had to faff around with 

Goodness grief , surely it must be worth it in the end

---

### Post by Morbius1 on 2013-04-22
Samba and networking are 2 different things but for the Samba part of this:
> .... if there was a working Samba GUI , then every-day people would surely be able to network their Ubuntu PC right
It's the same in Ubuntu as it is in Windows:

Open the File Manager ( Nautilus ) > Right click a folder you own > Select "Sharing Options" > Mark all the boxes > You created something that looks a lot like a WinXP "simple share".

Test your share:
```
nautilus smb://192.168.0.100/share-name
```

---

### Post by 90Ninety on 2013-04-22
> **Morbius1 said:**
> Samba and networking are 2 different things but for the Samba part of this:

It's the same in Ubuntu as it is in Windows:

Open the File Manager ( Nautilus ) > Right click a folder you own > Select "Sharing Options" > Mark all the boxes > You created something that looks a lot like a WinXP "simple share".

Test your share:
```
nautilus smb://192.168.0.100/share-name
```

 So its that simple?

---

### Post by Morbius1 on 2013-04-22
It's the default mechanism that Ubuntu has to create a samba share. It's even smart enough to install the requisite samba package if the user hasn’t already installed it.

---

