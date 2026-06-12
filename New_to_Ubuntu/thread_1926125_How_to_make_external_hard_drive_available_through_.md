---
title: "How to make external hard drive available through the network?"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-02-15
I want to make an external hard drive available through our network so I can back up multiple computers to it. How do I do this?

Thanks,
DG

---

### Post by jldoll on 2012-02-15
I'm away from the computers I have set up this way at moment, but
here's links to several pages I found helpful. 

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

[https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba](https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba)

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

I set up an external drive to automatically mount at boot using fstab.  Then created shares with samba on that local machine.  Then attached to the shares from the remote machines. Another thing I had to work through was why things were horribly slow through my wireless network.  It was because the laptop I was using most often had a power save mode that was killing the wireless card performance when not plugged into an outlet.  Heres' the command to override if necessary: sudo iwconfig eth1 power off

---

