---
title: "How to move files from Windows to Ubuntu with VNC??"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by JustGus on 2008-08-10
Can anyone point me to a "how to" on how to take files (flac for audio) and take them from my Windows PC to my Ubuntu machine.  I use the Windows computer to access  the Linux machine headlessly with REALVNC.  I was hoping there was a simple copy/paste or drag and drop way of doing this, but haven't had any luck.
THanks in advance!
Gus

---

### Post by damis648 on 2008-08-10
Maybe it's not realVNC I'm thinking of, but I thought that there was an option in one of the menus of its client or Web UI that let you send files... I may be wrong. You may just want to set the workgroup in your smb.conf to whatever it is on your windows machine and then you can go to My Network Places and on the left click Workgroup Computers and you should be able to see Ubuntu (Assuming you rebooted and set a username and password for samba... and that it's installed). Good luck!

---

### Post by bpowell2005 on 2008-08-10
> **damis648 said:**
> Maybe it's not realVNC I'm thinking of, but I thought that there was an option in one of the menus of its client or Web UI that let you send files... I may be wrong. You may just want to set the workgroup in your smb.conf to whatever it is on your windows machine and then you can go to My Network Places and on the left click Workgroup Computers and you should be able to see Ubuntu (Assuming you rebooted and set a username and password for samba... and that it's installed). Good luck!

That sounds like your best bet; I've never tried dragging and dropping from within VNC, but I don't think it's built with that in mind. Samba is the way to go...set up a shared folder on the Ubuntu machine, make sure other users can write to it, and then move stuff to your hearts content!

---

### Post by JustGus on 2008-08-10
Thank you both for the recommendations.  Looks like Samba is exactly what I'm after.  Will try installing and setting it up tonight.
Cheers,
Gus

---

### Post by jamesrfla on 2008-08-10
Samba or file sharing is very easy to get working. Just find a folder you want to share and right click it and hit sharing options. Then install the service when you try to share the folder. Then log out and log back into Ubuntu (or Reboot). Then go back to the folder and click the boxes.

---

