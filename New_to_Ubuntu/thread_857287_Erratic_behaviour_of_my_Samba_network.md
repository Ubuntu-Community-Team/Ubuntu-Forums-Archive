---
title: "Erratic behaviour of my Samba network"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by ar-jar on 2008-07-12
I have recently installed Ubuntu 8 on three computers at home and I'm new to Ubuntu. In addition the family has a whole bunch of Windows machines on the network. Each computer has one or several shared folderd and the Ubuntu machines are all running Samba. This always eventually works but not always initially after hibernation or after restarting the Samba server on some machine. As we try to conserve energy by switching computers off and hibernating them, the network on the whole seems quite erratic and unreliable.

This is especially un-robust between Ubuntu machines actually. The _first time_ I try to access a shared folder on an Ubuntu machine from another Ubuntu machine I get messages like those in img1 and img2. img1 is after hibernation and img2 is after restarting Samba on the machine with the shared folder on it. When I got the img2 dialog, the shared folder actually opened up simultaneously so the error dialog wasn't even accurate.

The _second time_ I double click on the shared folder it usually opens up and I get img3.

I also seem to get different behavior by browsing through the Network -> <Server> -> Folder and by directly opening a shared folder icon in the left tree browser in Nautilus (like "www on Solbacka" in img3). The tree browser icons work less often.

Furthermore, after I have accessed for instance "pictures on Solbacka" through the tree browser and try to open the same folder through Network->Solbacka->... I see no folders at all in the window (img4). Again, the _second time_ I do this, I see all shared folders.

My smb.conf has the following lines for each share:

[Pictures]
   read only = no
   path = /home/Pictures
   guest ok = yes
   browseable = yes

Home has permission 757 and Pictures has 777. And as I said, most of the time I can access the folder the second time I try with all the right permissions.

I write "erratic" as I fail to even see a pattern in this (except that it tends to work the second time I try). Sorry for the confused post but I _am_ confused.

Any ideas as to how I can get a more predictable and reliable network?

Thanks!

Arto

---

