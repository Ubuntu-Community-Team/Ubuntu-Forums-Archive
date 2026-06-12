---
title: "Networking Confusion"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Agrajag27 on 2008-08-24
I have Ubuntu on my laptop and have a Windows XP (SP3) desktop on the network. 

I don't understand something that's happening when I try to mount shares from Ubuntu.

If I use "Connect to Server" and choose "Windows share" I can then type in the IP address (192.168.1.20) and any share name and Ubuntu has NO problem accessing that data on the Windows box.

I can also type in the name of the network, say "Main" and provide a share name and that gets me a password prompt and then the same positive access happens.

HOWEVER, that's annoying as I have to do it all manually each time. When I choose Places/Network I can see "Windows Network" but then clicking on it shows NO shares what-so-ever. I'd prefer to go through that for simplicity.

Why does one approach work reliably but the other fails every time?

---

### Post by cwsnyder on 2008-08-24
I believe your problem is that Places/Network is assuming a GNU/Linux network, where "Connect to Server" makes you choose "Windows Share" so that you can log on to the WinXP computer properly.  Have you tried loading samba prior to checking out Places/Network?

cwsnyder

---

### Post by Agrajag27 on 2008-08-24
I was trying to avoid loading Samba on the PC side. Since it worked without it via Connect to Server I thought I might be able to get around this.

I have loaded Samba on the Ubuntu side though I don't recall specifically exactly what I did to install it. I followed some other post to do it.

---

### Post by cariboo on 2008-08-24
When you create a share in Ubuntu, it will automagically install samba, if you haven't installed it already.

Jim

---

### Post by Agrajag27 on 2008-08-24
How do I officially create a share in Ubuntu that will see my Windows XP shares then?

---

### Post by bab1 on 2008-08-24
You don't.  When you are using Ubuntu to connect to a Windows host, you use "smbfs"  Ubuntu is the client and Windows is the server (Yes Windows has it built into the share).  You do use some of the Samba libs.  Install smbfs:```
sudo apt-get install smbfs
```

---

### Post by halitech on 2008-08-24
from what we can tell in this thread

[http://ubuntuforums.org/showthread.php?t=887061](http://ubuntuforums.org/showthread.php?t=887061)

there seems to be a bug in Network places that does not show Windows shares but if you go in the way you have been, it works. To avoid having to type in the address everytime, simply bookmark the folder once you get there

---

### Post by Agrajag27 on 2008-08-25
Thanks! That explains it. Didn't even realize Bookmark was an option. Works great until they get this fixed.

---

### Post by halitech on 2008-08-25
I didn't either till I was working on this with a few other people :)
glad we got it working for you :D

---

