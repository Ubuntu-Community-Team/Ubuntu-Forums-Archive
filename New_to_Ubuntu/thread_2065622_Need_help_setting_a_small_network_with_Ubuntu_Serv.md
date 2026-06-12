---
title: "Need help setting a small network with Ubuntu Server"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by Luisedgm on 2012-10-02
Hello, i have VERY little experience with linux systems and need to set a network with ubuntu server on my company. Of course i don't expect anyone to babysit me on this, but i had little luck with google search, i only find very old articles and instructions or not very relevant ones, im willing to learn, so if you guys could give me some insight it would be much appreciated.

The network is composed of 8-10 computers (we may buy 2 new ones soon), the server is your average desktop, we will buy a new printer to conect on the server for it to share with the network, and there is the complicated part of it: we need an automatic backup system.

The backup must be made by the server every 12 hours (if automatic is impossible it can be manual too, but my boss really want an automatic system), the server would update itself with data from the computers connected on the network and send a copy to the backup device that will be in a remote location (probably my boss' house).

This is the device we are planning to use: StorCenter ix2-200 Network Storage, Cloud Edition, 2TB - Iomega

We also don't know which software we should use for the backup and network management/monitoring

Any and all help is welcome.

---

### Post by 2F4U on 2012-10-02
For a general documentation about Ubuntu server, I would start by reading the official documentation:

[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

There is a lot of content about backup in the community Wiki, along with a list of backup software and comparison of features:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Bufeu on 2012-10-02
> **Luisedgm said:**
> Hello, i have VERY little experience with linux systems and need to set a network with ubuntu server on my company. Of course i don't expect anyone to babysit me on this, but i had little luck with google search, i only find very old articles and instructions or not very relevant ones, im willing to learn, so if you guys could give me some insight it would be much appreciated.

The network is composed of 8-10 computers (we may buy 2 new ones soon), the server is your average desktop, we will buy a new printer to conect on the server for it to share with the network, and there is the complicated part of it: we need an automatic backup system.

The backup must be made by the server every 12 hours (if automatic is impossible it can be manual too, but my boss really want an automatic system), the server would update itself with data from the computers connected on the network and send a copy to the backup device that will be in a remote location (probably my boss' house).

This is the device we are planning to use: StorCenter ix2-200 Network Storage, Cloud Edition, 2TB - Iomega

We also don't know which software we should use for the backup and network management/monitoring

Any and all help is welcome.
1. Which OS:es will the clients run?
2. Buy HP printers if you are going to use a Linux-based OS. HP have written Linux drivers for almost all their printers. For Windows clients, this doesn't matter, since all printers has working drivers for Windows.
3. You can use rsync running as cron for backing up the system(s). Otherwise, use the [Déjà Dup Backup Tool]("https://launchpad.net/deja-dup"), which comes pre-installed with the desktop version of Ubuntu. The client's OS:es doesn't matter, as long as the Linux server can access the clients and its files.
4. Again, if you are going to use a network server, the software depends on which OS you are going to run on the clients. Quidsup has done a great video demonstrating how to install, setup and configure a NAS using Ubuntu Server 12.04 (RAID, Samba): [https://www.youtube.com/watch?v=-5Z_-3EBIHE](https://www.youtube.com/watch?v=-5Z_-3EBIHE). Also, take a look at the help guide he wrote to the video: [https://docs.google.com/document/d/1hFw1YnH9s-1Y9M4VPLgPOOjm1iH6PJOHefg5NhGC4oA/edit?pli=1](https://docs.google.com/document/d/1hFw1YnH9s-1Y9M4VPLgPOOjm1iH6PJOHefg5NhGC4oA/edit?pli=1).

---

### Post by Luisedgm on 2012-10-02
> **2F4U said:**
> For a general documentation about Ubuntu server, I would start by reading the official documentation:

[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

There is a lot of content about backup in the community Wiki, along with a list of backup software and comparison of features:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Will read it, thank you

> **Bufeu said:**
> 1. Which OS:es will the clients run?
2. Buy HP printers if you are going to use a Linux-based OS. HP have written Linux drivers for almost all their printers. For Windows clients, this doesn't matter, since all printers has working drivers for Windows.
3. You can use rsync running as cron for backing up the system(s). Otherwise, use the [Déjà Dup Backup Tool]("https://launchpad.net/deja-dup"), which comes pre-installed with the desktop version of Ubuntu. The client's OS:es doesn't matter, as long as the Linux server can access the clients and its files.
4. Again, if you are going to use a network server, the software depends on which OS you are going to run on the clients. Quidsup has done a great video demonstrating how to install, setup and configure a NAS using Ubuntu Server 12.04 (RAID, Samba): [https://www.youtube.com/watch?v=-5Z_-3EBIHE](https://www.youtube.com/watch?v=-5Z_-3EBIHE). Also, take a look at the help guide he wrote to the video: [https://docs.google.com/document/d/1hFw1YnH9s-1Y9M4VPLgPOOjm1iH6PJOHefg5NhGC4oA/edit?pli=1](https://docs.google.com/document/d/1hFw1YnH9s-1Y9M4VPLgPOOjm1iH6PJOHefg5NhGC4oA/edit?pli=1).

All clients will run on windows, mostly windows 7, we use many applications that doesn't have linux versions.

Thank you for the tips, will take into consideration.

---

### Post by Bufeu on 2012-10-02
Well, buy HP printers anyway. You might need to access them from the server (someday)...

---

### Post by mips on 2012-10-02
I'm gonna buck the trend here and say have a look at ClearOS. It's easy to use via GUI and I know a lot of SMEs that use it.
[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)
[http://en.wikipedia.org/wiki/ClearOS](http://en.wikipedia.org/wiki/ClearOS)
I'm not saying you must use it, just to have a look at it.

As for the printer just get a printer with a LAN port as they have built in print servers and your desktop clients can print to them via normal tcp/ip. That's how I use my HP printer.

---

### Post by Bufeu on 2012-10-02
> **mips said:**
> I'm gonna buck the trend here and say have a look at ClearOS. It's easy to use via GUI and I know a lot of SMEs that use it.
[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)
[http://en.wikipedia.org/wiki/ClearOS](http://en.wikipedia.org/wiki/ClearOS)
I'm not saying you must use it, just to have a look at it.

As for the printer just get a printer with a LAN port as they have built in print servers and your desktop clients can print to them via normal tcp/ip. That's how I use my HP printer.
Yea, CentOS is a quite nice OS for servers, but I have always ended up with Ubuntu Server for several reasons. :) CentOS works great, but I rather prefer Ubuntu Server.
Maybe it's a question about what you are used to use.

---

### Post by Luisedgm on 2012-10-03
Heh, there seems to be a consensus here about HP printers, gonna talk to my boss about it.

I may decide today if we are going with Ubuntu Server or the ClearOS, im glad i posted here you guys were really helpful.

Thank you all.

---

### Post by Luisedgm on 2012-10-03
Just spoke with my boss, lucky he still haven't bought the new printer, do you guys have any suggestion? We need it to be Laser and Multifunctional. After a quick search i found this one: LaserJet Pro M1212nf Multifunction Printer
We are a small company, so we don't need anything too big, do you guys approve?

Also, about the backup device: StorCenter ix2-200 Network Storage, Cloud Edition, 2TB - Iomega
Seems to work only on windows servers, so i gonna need a recommendation here because this kind of hardware is not really my speciality.

Thank you again!

---

### Post by mips on 2012-10-03
A quick google confirms that printer works in linux with the hplip drivers. Beyond that I can't comment.

---

