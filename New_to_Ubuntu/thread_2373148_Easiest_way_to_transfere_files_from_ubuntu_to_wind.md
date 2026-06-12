---
title: "Easiest way to transfere files from ubuntu to windows 10"
date: 2017-10-03
forum: New to Ubuntu
---

### Post by k28 on 2017-10-03
hi 

what is the easiest way to transfere files from ubuntu to windows 10?

please tell me that there is an app like send anywhere where i can just drag and drop files and it transfares it within the network. preferably with crossover.

i tried samba and ftp. in both methods it fails at some point and i really dont want to waste more time on this. i mean everytime i have to waste at leaste a couple of hours for such basic things. in android you just open the playstore and bam 50 apps for the same solution. where are the linux/win guys who want to grap my money(or do it for free with ads)? :D

---

### Post by leunam12 on 2017-10-03
You haven't explained very well what you want to do, where are those files located? on the same computer? on different computer on the same network? On different computers on different networks? I usually transfer files from a windows computer to an Ubuntu computer, both are on the same local network and I have one directory shared via Samba on my Ubuntu computer. I place all the files that I want to transfer on that directory and connect to it from windows by typing \\<ip address>\ on the address bar of any folder, press enter and then enter user name and password, the rest is just drag and drop.

There are also wireless routers that allow you to plug a USB stick or removable HDD and share it on the network, check the back of your router.

If I want to transfer files from one computer to another computer on a different network I just place those files on Google drive or mediafire, then I can access them from anywhere.

---

### Post by k28 on 2017-10-03
> **leunam12 said:**
>  I usually transfer files from a windows computer to an Ubuntu computer, both are on the same local network and I have one directory shared via Samba on my Ubuntu computer. I place all the files that I want to transfer on that directory and connect to it from windows by typing \\<ip address>\ on the address bar of any folder, press enter and then enter user name and password, the rest is just drag and drop.



thats what i lso tried yesterday but it diddnt work. now it seems to work somehow but it asks me for a password. what is the user name and password?

edit:

[https://wiki.ubuntuusers.de/Samba_Server/](https://wiki.ubuntuusers.de/Samba_Server/)


add new user to the database.



OT: as much as i like ubuntu over microsoft, ubuntu cant be the feature as long as you have to google hours for every step in atutorial

---

### Post by HermanAB on 2017-10-03
Actually, FTP is by far the easiest way to transfer files between UNIX and Windows.  Anonymous FTP is supported natively by the Windows file browser.

You can install FileZilla server on either Linux or Windows and then easily transfer files with FileZilla client, or simply with the file browser of the other system.

---

### Post by Morbius1 on 2017-10-03
> **k28 said:**
> thats what i lso tried yesterday but it diddnt work. now it seems to work somehow but it asks me for a password. what is the user name and password?

edit:

[https://wiki.ubuntuusers.de/Samba_Server/](https://wiki.ubuntuusers.de/Samba_Server/)


add new user to the database.



OT: as much as i like ubuntu over microsoft, ubuntu cant be the feature as long as you have to google hours for every step in atutorial

It depends on how you set up your share. I did this on a Xubuntu 17.10 Beta machine I just installed:

** Installed samba
** Created a share in smb.conf:
```
[Public]
path = /home/tester/Public
read only = no
force user = tester
guest ok = yes
```
** On Win10 I opened up explorer and entered:
```
\\vxub1710.local
```
Bada Bing as granny used to say:
[ATTACH=CONFIG]276954[/ATTACH]
No password required.

---

