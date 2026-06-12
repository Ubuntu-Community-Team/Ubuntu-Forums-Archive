---
title: "Samba setup"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by paul.lav on 2008-05-06
With help from ppl on the forum i got samba installed but how do i run it or set it up to share files on my windows network.

Sorry for asking dumb questions but i want to learn this and really don't have a clue

---

### Post by bluefrog on 2008-05-06
the simplest way is to open your file explorer (nautilus), right click on a folder and select sharing options.

Full full samba knowledge
[http://samba.org/samba/docs/man/Samba-Guide/](http://samba.org/samba/docs/man/Samba-Guide/)

---

### Post by ENigma885 on 2008-05-06
If u r planning to share in a Windows network..this [[COLOR="Red"]tutorial[/COLOR]]("http://www.watchingthenet.com/enable-file-sharing-in-ubuntu-using-samba.html") will help alot...
u can follow the step by step video 
btw...i use Hardy Heron and i couldn't find the File Sharing thing in System>>Administration ..u can launch it using terminal 
```
shares-admin
```

---

### Post by Girya on 2008-05-06
before you can access your shared folders you need to set up a samba password. open a terminal Applications>Accessories>Terminal, type in  smbpasswd enter a password. this is the password you'll use when prompted when accessing shares on another computer. there's a little more to it than that but it's not that hard. I got to go haul trash or I'd stick around and try to help some more. kevin

---

### Post by mlentink on 2008-05-06
You might want to peruse this as well: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by paul.lav on 2008-05-06
Thanks guys. i'll try these when i get home. fingers crossed and i let you's know how it goes.

---

