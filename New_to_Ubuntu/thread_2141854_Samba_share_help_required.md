---
title: "Samba share help required"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by loveuppal on 2013-05-03
Hi all

i'm running a headless server 12.04

i can ssh this server and can view this in windows workgroup
i'm trying to share a folder from this server to my laptop (win 7). So far i have done the following:

install webmin on server
make workgroup same on server and win 7 so that they can see each other and have been sucessful
change samba config and added a new share which i can see in win 7 network
but when i try to add a file or create a folder, it says permission denied

how can i use this share on win 7 machine...i know it has something to do with user security/authentication but so far not sure how to proceed

thanks

---

### Post by jamiem731 on 2013-05-04
Is Windows Homegroup the only sharing set up on on your laptop?

Homegroup is NOT an SMB:  share !!!

It is also IPV6 dependent.

Try creating a user account on the win7 machine specifically for this purpose and also on your server.

---

### Post by BluNova on 2013-05-04
It might be worth looking at this [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

Also it is NOT IPV6 dependent, he never even mentioned homegroup and he doesn't have to create an account specifically for the purpose on any of the machines

---

### Post by Morbius1 on 2013-05-04
> change samba config and added a new share which i can see in win 7 network
but when i try to add a file or create a folder, it says permission denied
This does not appear to be a Samba issue at all to me. You can see the Linux share from Win7. If it requires credentials to access you have apparently provided them because you are at the point of adding a file. So that leaves Linux permissions. Can the samba client user ( on Win7 ) - be he guest or a real user - actually write to the directory being shared on the Linux server.

I would suggest you post the output of the following command so the folks here can see how you are set up:
```
testparm -s
```

---

### Post by BluNova on 2013-05-04
I believe that samba is sharing it as read only what you need to do is open the terminal and type
```
gksudo gedit /etc/samba/smb.conf
```
Then find your share and change writable from no to yes and read-only from yes to no. For more info read here [https://help.ubuntu.com/community/Samba/SambaServerGuide#File_Sharing_.28Basics.29](https://help.ubuntu.com/community/Samba/SambaServerGuide#File_Sharing_.28Basics.29)

---

### Post by Morbius1 on 2013-05-04
> **BluNova said:**
> ```
gksudo gedit /etc/smb/samba.conf
```

It doesn't really matter because he's using webmin to do all this but you have the path discombobulated. Maybe just a typo:
```
gksudo gedit /etc/samba/smb.conf
```

---

### Post by loveuppal on 2013-05-12
Thank you guys for the help. I ended up using installing desktop and using GUI to share folders. But even that did have few problems which I'm trying to workout by reading the documentation.

Is ther any other way of sharing the home folders?

---

