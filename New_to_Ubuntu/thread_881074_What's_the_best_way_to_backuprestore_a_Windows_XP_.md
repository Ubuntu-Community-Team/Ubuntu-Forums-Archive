---
title: "What's the best way to backup/restore a Windows XP image over the network"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by greavette on 2008-08-05
Hello,

I've searched for solutions but nothing is quite close to what I would like to implement.  

I have 11 Windows XP workstations that I would like to backup and put in place a system for easy restore.  I'm not against using commercial products like Acronis or Norton Ghost...if they are the best solution then that is fine with me but I would like to show my boss how useful Linux could be by setting up something like the following:

[LIST]
[*]Using Linux installed on a seperate PC only used for backups, I would like to backup each workstation image over our network to an external hard drive.  
[*]In the event updates are made to these workstations I would like the ability to schedule the backup.
[*]If one of the workstations was to become corrupt I would like a way to restore the backed up image to the workstation over the network.
[*]In the event the workstation hardware is the problem, I would put in a spare PC with no operating system on it and would like to be able to restore the image I choose to the new PC (I believe this is called a bare metal restore).
[/LIST]

I'm helping to support this office remotely where I would instruct a person at the office to remove the old PC and plug in the new PC.  If they need to put in a CD and boot the new PC off the CD that is fine, but then I would like to be able to remotely go into this backup Linux PC and restore back the image to the newly installed PC.  Another idea I thought would be nice would be to set the PC to PXE boot off of my Linux backup PC so that I could again restore the backed up image to the new PC.

Does this sound like it is possible?  Any help or tips I can research on would be greatly appreciated.

Thank You,

Charles.

---

### Post by bodhi.zazen on 2008-08-05
You can go with partimage or rsync ...

---

### Post by greavette on 2008-08-06
Hello bodhi.zazen,

Thanks for the response.  I'll google for partimage and PXE booting backup and restore my windows images.

Thanks!

Charles.

---

