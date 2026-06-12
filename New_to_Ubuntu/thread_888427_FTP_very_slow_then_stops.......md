---
title: "FTP very slow then stops......"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-08-13
I have been trying to do an FTP transfer using both Filezilla and gFTP with no luck

The transfer starts very slow at 1kbs then basically fails..

The system that I am trying to transfer from does have an FTP server client ( and actually runs an early version of Mandrake ) and I am able to perform FTP if I boot up windows, on the same laptop and transfer at 140Kbs....the file is approx 3Mb

I have double checked the setting, turned off firestarter,and checked with  Network managers for correct switch port and IP settup.

I have no trouble with telnet sessions from terminal in ubuntu

Anyone got any ideas, cause it is very frustrating..  ](*,)

---

### Post by cmnorton on 2008-08-13
Some indicator might be present in the logs (/var/log). 

This sounds very obvious, but have you tried to ftp a small file, then larger, and so on?

---

### Post by OffAxis on 2008-08-13
can you log onto the server from the command line with an ftp client (and get an ftp prompt)?
```

ftp username@hostname
```

---

### Post by Ducatiboy Stu on 2008-08-14
> **OffAxis said:**
> can you log onto the server from the command line with an ftp client (and get an ftp prompt)?
```

ftp username@hostname
```

Yes I can...and can do long telnet sessions

I had another try today.

self IP Add 10.70.8.179
Sub 255.255.255.128
Gate 10.70.8.1

host 10.70.8.142

Had various issues with connection. It seems that the FTP session quits only after a few minutes ( BUT not using windows ..), sometimes it disconnects when trying to select the relevant dir/file. I was also unable to ping the gateway router, kept getting a permission deinied msg...? ,but was able to ping other add within the subnet ie 10.70.8.10 or 10.70.8.180...

The network mngr was also unable to ping me thru the router,but when I connected using XP he was...cause he rang me to say he had succesfull ICM packets

I also had lots of trouble with Firestarter, damn prog was just unresponsive and I had to force guite "Kill" it every time as it would grey out. I am not sure if is actually disabling the firewall,which is what i was trying to do, and being on a very secure network, there is not an issue with this

I also set up wireshark/ethereal and could see the FTP session being set up...but it the session stopped responding and disconnected every time. No i didnt save the wireshark session

---

