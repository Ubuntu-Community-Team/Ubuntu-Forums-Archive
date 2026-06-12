---
title: "Ubuntulite PCMan File Manager and Samba"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by xsilvergs on 2008-08-03
Hi

I'm two days into Ubuntu and I'm using Ubuntulite version 8.04 which comes with PCMan File Manager 0.4.1.1., it's installed on a Sony Vaio PCG-F707 laptop.

My other PC's run Windows XP and all are connected on my home network.

With Ubuntulite I can happily surf the net, I can ping to and from Ubuntulite and all PC's can be seen.

**The Problem:**
I wish to do file shareing so have installed Samba and the "Samba Web Administration Tool". I've followed the tutorials on this forum but can't share files.

From a Windows PC I once managed to "Map a Network Drive" but that didn't last long as Ubuntulite won't always appear under MSHOME.

From Ubuntulite I can't see any Windows PC's (except by ping) and I wouldn't know visually know that Samba is installed. Should Samba show up in PCMan?

Does Ubuntulite and PCMan work with Samba?

If anybody could shed light I'd be greatfull.Thanks in antisipation.

---

### Post by northern lights on 2008-08-03
Run ```
sudo apt-get update
sudo apt-get install fusesmb curlftpfs sshfs
```to get Samba, FTP and SSH in PCMan.

---

### Post by xsilvergs on 2008-08-03
northern lights, thanks for info. Have carried out your instructions, at this moment my Ubuntulite PC is showing up by name only in Windows, I'm unable to see the shared folder. The shared folder viewed in SWAT shows up as:

[MyFiles}
path = /usr/local/share/TonyShare

is this the correct location for a shared file, I don't understand Ubuntu file system yet and not sure where to put files for Downloads and Shares etc.

I still can't see my windows PC's from Ubuntulite.

Thanks for any more help.

---

### Post by northern lights on 2008-08-03
> **xsilvergs said:**
> path = /usr/local/share/TonyShare

is this the correct location for a shared file, I don't understand Ubuntu file system yet and not sure where to put files for Downloads and Shares etc
No, it isn't. All your personal files should be in your home folder. A regular user doesn't have permissions to alter "/usr/any/path" anyways - didn't that seem a bit fishy?

Create folders such as
/home/USER/shared
/home/USER/downloads
/home/USER/documents
/home/USER/music
--> You get the idea (USER of course needs to be replaced by your username).

---

### Post by xsilvergs on 2008-08-03
Ok, setup shared folder and ticked all permissions. From Windows "Run" if I type \\192.168.1.7 file explorer opens and I can see icons for "MyFiles", "Samsung" (the network printer) and "Printers and Faxes". If I double click the "MyFiles" icon a box open asking for my password, I add this and the message box tells me I might not have permisson and the Group Name could not be found.

I still can't see out from the Ubuntulite PC.

Thanks for help so far.

---

### Post by xsilvergs on 2008-08-05
Ok I've sorted things out and can now share files between all my PC's. I had to rem out a few lines from the smb.config and then install pyNeighborhood. Thanks for help.

I've one last question, before pyNeighborhood I installed LinNeighborhood as a tar.gz from [http://www.bnro.de/~schmidjo/download/index.html](http://www.bnro.de/~schmidjo/download/index.html), how do I unistall LinNeighborhood?

Thanks

---

