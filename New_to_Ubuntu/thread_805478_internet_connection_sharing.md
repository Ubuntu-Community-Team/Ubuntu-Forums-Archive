---
title: "internet connection sharing"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by licksboxalot on 2008-05-24
can i share an internet connection with a computer running windows xp

---

### Post by dRock1286 on 2008-05-24
Which computer will have the access to the computer?  It is easier to setup in windows (IMO) then all you need to do is connect the Ubuntu-box to your Windows-box via a crossover cable...

---

### Post by sayakb on 2008-05-24
Use Samba to access Windows file sharing.
To open the network location which has file sharing enabled:
```
smb://REMOTE-COMPUTER-NAME
```

---

### Post by dRock1286 on 2008-05-24
He wants to share the internet connection.

So, in Ubuntu, he would have to setup a bridge between his two connections...I have tried this and find it rather difficult for someone new to Ubuntu and Linux...that's why I recommended sharing from Windows.

---

### Post by sayakb on 2008-05-24
Ok sorry.. I misread. Well, there is a simple method for that. On the Windows machine, install an application called ProxyI (google it to get download links). This would open a port on the remote WinXP machine (probably port 6588 ). Now open Firefox and add the Windows machine's IP address and the port as 6588. You should be able to use the internet in that way.

EDIT: [http://www.freewareweb.com/cgi-bin/archive.cgi?ID=875](http://www.freewareweb.com/cgi-bin/archive.cgi?ID=875) <= Download link

---

### Post by licksboxalot on 2008-05-24
my windows computer has the internet connection so i want the ubuntu to share from it

---

### Post by licksboxalot on 2008-05-24
the reason i want to try the ICS is cuz i get unsecured wireless from my neighbor but on the ubuntu laptop even though it shows a strong signal i internet is going very slow. it will load homepage no problem sometimes i can even google something but whenever i try to click on a link from my google results it craps out. also when i try to dload updates the speed its crazy slow.  i have read the boards and support pages some and seems like it has something to do with ipv6 or whatever. im just not used to linux and everything i have tried doesnt seem to work

---

