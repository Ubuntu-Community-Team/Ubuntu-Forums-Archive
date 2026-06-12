---
title: "Kubuntu - XP networking"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Gnomad on 2008-08-20
Hi everybody,

Yes i am another Windows refugee, and very new to Kubuntu, Ubuntu and the whole linux world.
So far having an easy time With Kubuntu 8.04 but have hit a brick wall with networking my existing XP machine to share files and a printer. I can see all drives and folders in XP, but cannot use them, Windows cannot see Kubuntu at all.
Kubuntu sharing settings are all greyed out and untouchable, and it tells me to install SMB and NFS servers to enable the module?
I have searched the web and this site for help but they all explain for Ubuntu and assume you can make changes to settings!
Any help would be much apreciated.

---

### Post by linuxguymarshall on 2008-08-20
I'm not much into the whole 'file-sharing over LAN thing' but I think in Kubuntu go to System Settings and find Samba Sharing. Play around with those settings.

---

### Post by Gnomad on 2008-08-21
Thanks for the reply, it gets lonely sometimes!

I'll give Samba some playtime and see what happens.:)

---

### Post by anjilslaire on 2008-08-21
Yes, you need to install SAMBA to share files with Windows.
```

Sudo apt-get install samba

```
Once that's done, go back into the Kubuntu Sharing settings, and you should be able to set your prefered folders to be shared.

I'm running kubuntu, and use samba to share content over my lan to Windows, LInux, and even my old xboxes. It's great :)

---

### Post by Gnomad on 2008-08-21
Hi!
Many thanks,
I have installed SAMBA,and windows can see at last.
Its looking good!!
Again many thanks.:):)

---

