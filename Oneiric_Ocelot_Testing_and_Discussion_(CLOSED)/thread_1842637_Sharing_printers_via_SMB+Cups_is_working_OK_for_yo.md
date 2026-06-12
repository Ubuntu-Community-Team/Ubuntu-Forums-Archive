---
title: "Sharing printers via SMB+Cups is working OK for you guys?"
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-09-11
I've been battling to install / share 2 USB printers: 1 HP MFP Deskjet and 1 LaserJet. Normally I use hplip, samba and cups. 

It seems to be installed as usual. Hplip sees the printers and prints locally. Cups is installed and sees the printers. There are no firewall restrictions for cups or smb ports. Samba is working fine for shared folders in this small network. Network machines see the shared printers.

There are no error messages whatsoever, logs have no messages regarding printer, samba or cups errors. But the printers are dead quiet for jobs sent from network. Can't get a single reaction from them. 

This is so basic, I'm probably overlooking something stupid. 
 Just wanted to know if anyone is actually using such a setup successfully.

Thanks,
Effenberg

---

### Post by effenberg0x0 on 2011-09-11
Ah damn, its working, forget about it. 

I forgot about a couple outdated entries in /etc/hosts, restarted winbind, nmbd and its working, obviously. That was embarrassing :-)

Regards,
Effenberg

PS: Sorry... It's rare for me to post my own questions here. That was a stupid one lol.

---

