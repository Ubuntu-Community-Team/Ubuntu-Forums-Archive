---
title: "Printer help im an absolute newbie"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by khalidmian on 2008-09-07
I have a USB HP Laserjet P1505 which I am sharing with other computers under share name p1505. I would appreciate assistance in trying to configure my laptop in which i installed ubuntu to be able to use the printer . Please advise me what steps i need to take under windows vista where i have the printer attached and my laptop in which i have ubuntu
:confused:

---

### Post by Xiong Chiamiov on 2008-09-07
If you're willing to get your hands a little dirty, I have found the directions on [the Arch Wiki]("http://wiki.archlinux.org/index.php/Cups#Printer_Sharing") to be quite helpful, though a few things will be a little different (anywhere you see rc.d, change it to init.d).

---

### Post by kjohansen on 2008-09-07
hp offers pretty good drivers on their site.  I know the drivers they provide for linux will allow for networked printers.  I have a standalone hp printer that is connected through the wireless network right now.

go to hp.com and find the driver, you will be redirected offsite to download linux drivers

---

### Post by cariboo on 2008-09-07
Just go to System-->Administration-->Printing, select add new printer, for connection choose Windows Printer via Samba and follow the prompts.

I'm using Intrepid Alpha5 so the syntax may be a little different. You don't need Samba installed  to connect to your printer, just smbclient that is installed by default.

Jim

---

### Post by Sef on 2008-09-08
If you are just a client, then open the terminal (Applications > Accessories > Terminal), and type or paste in this code:

```
sudo apt-get update && sudo apt-get install smbfs
```

then follow cariboo907's directions.

---

