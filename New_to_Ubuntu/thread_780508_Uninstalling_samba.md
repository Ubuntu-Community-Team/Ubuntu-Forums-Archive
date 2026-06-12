---
title: "Uninstalling samba"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Joishi on 2008-05-03
Will uninstalling Samba mess anything up on a Hardy Heron install?

As a parallel note, my computer also seems to not be connecting correctly to the windows workgroup for our LAN (with router as DNS server).  I suspect that it might be related to samba, but I'm unsure.  Thus I've been considering uninstalling it and then maybe reinstalling it.

Any help is appreciated.

---

### Post by Hospadar on 2008-05-03
I'm pretty sure it isn't even installed by default, so you should be fine.

---

### Post by Joishi on 2008-05-03
Synaptic Package Manager says Samba-Common is installed, and I'm certain that I didn't install it.  I was thinking it might be installed for printer sharing (I don't know if CUPS needs samba or not).

---

### Post by Monicker on 2008-05-03
> **Joishi said:**
> Synaptic Package Manager says Samba-Common is installed, and I'm certain that I didn't install it.  I was thinking it might be installed for printer sharing (I don't know if CUPS needs samba or not).

I'm pretty sure that some of the samba client side utilities, which let you connect to and view remote windows shares, are what is in the samba-common package.

---

### Post by Joishi on 2008-05-03
So if I uninstalled it, you guys think it wouldn't mess up with my printer sharing?  My linux box hosts a printer that my wifes box (WinXP) needs to print to.  However, we've been having issues with it under Hardy.  I don't think I'm being broadcast on the windows workgroup properly .. her computer doesn't recognize the name of my computer (and vice-versa) while we can still ping each other via our ip addresses.  I added the printer to her computer via my ip address (which I don't like - would vastly prefer the name of my computer instead), but when she sends a print request absolutely nothing happens on my end of things.

I really don't know what the issue is..  But I changed some settings under the smb.conf file in trying to fix it and don't want to keep the changes I made.  I was just going to dump samba if it's not needed for printer sharing.

---

### Post by Monicker on 2008-05-03
> **Joishi said:**
> So if I uninstalled it, you guys think it wouldn't mess up with my printer sharing?  My linux box hosts a printer that my wifes box (WinXP) needs to print to.  However, we've been having issues with it under Hardy.  I don't think I'm being broadcast on the windows workgroup properly .. her computer doesn't recognize the name of my computer (and vice-versa) while we can still ping each other via our ip addresses.  I added the printer to her computer via my ip address (which I don't like - would vastly prefer the name of my computer instead), but when she sends a print request absolutely nothing happens on my end of things.

I really don't know what the issue is..  But I changed some settings under the smb.conf file in trying to fix it and don't want to keep the changes I made.  I was just going to dump samba if it's not needed for printer sharing.

The whole purpose of the Samba server is to share file and print services with Windows machines.  So, if the XP machine was connecting to the printer via Windows sharing services, then yes removing Samba would cause a problem.  If you want to her to access the printer via you linux box and not directly to the printer itself, then you should reinstall Samba.

---

### Post by Joishi on 2008-05-03
The address I typed in for the printer was

http://<my ip address>:631/printers/deskjet_5550

That would have her connect directly to my printer via CUPS instead of (?) using Samba, correct?

---

### Post by mrzaius on 2008-05-03
You don't have to **uninstall** samba. Just turn it off. "/etc/init.d/samba stop" will do just that on the live system. See this guide to get hints on doing so in a more permanent manner: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) (or just "rm /etc/rc.*/*samba" if you're feeling lazy and don't want samba running by default at any runlevel. The init script will still be in /etc/init.d if you want to restore the defaults later.)

---

