---
title: "Who supports Atheros"
date: 2008-11-01
forum: Other OS Talk
---

### Post by n8ek on 2008-11-01
Wireless cards out the box? Mandriva 2009 did but had probs with graphics the latest Suse did then stopped (never to run agian?)

Thanks

---

### Post by lisati on 2008-11-01
> **n8ek said:**
> Wireless cards out the box? Mandriva 2009 did but had probs with graphics the latest Suse did then stopped (never to run agian?)

Thanks

My Toshiba A100 laptop has Atheros and it works "out of the box"

---

### Post by regomodo on 2008-11-01
I've not used a Distro that doesn't support my atheros card. All the big binary distros have worked out the box and all the smaller ones usually have the "madwifi" package for install.

---

### Post by Xanatos Craven on 2008-11-01
Some people, myself included, don't have access to ethernet at all and needed to resort to convoluted means to get madwifi installed and working. That could be n8ek's issue.

---

### Post by 67GTA on 2008-11-01
Which card model do you have?

---

### Post by n8ek on 2008-11-02
AR5007 in a HP Pavilion dv6000 laptop,

Thanks

---

### Post by 67GTA on 2008-11-02
Any distro with the 2.6.27 kernel should work out of the box with the ar5007 since we now have the new open ath_pci driver. I have seen reports that Ubuntu 8.10 doesn't work for some reason. Some I have tested lately that I know work out of the box are:
 
Opensuse 11.1 (still beta)
Mepis 8 (still beta)
PCLinuxOS 2009 (still beta)
Mint 5 (use the "Windows Wireless Drivers" tool in the menu and when it asks for a driver, point it to /usr/lib/linuxmint/mintWifi/drivers/Atheros_AR5007eg/net5211.inf)
Mint 6 should, but no public beta yet.

---

### Post by deltaprime on 2008-11-02
obviously Back track 3 works out the box with it ; )

---

### Post by n8ek on 2008-11-02
> **67GTA said:**
> 
 
Opensuse 11.1 (still beta) *Tryed that 1 worked ok until i installed it*
Mepis 8 (still beta)
PCLinuxOS 2009 (still beta)*still waiting for that 1*
Mint 5 (use the "Windows Wireless Drivers" tool in the menu and when it asks for a driver, point it to /usr/lib/linuxmint/mintWifi/drivers/Atheros_AR5007eg/net5211.inf)*downloading that 1 as i type*
Mint 6 should, but no public beta yet.

Thanks

---

### Post by hanzomon4 on 2008-11-03
Ubuntu works with my  AR5008 in my macbook pro out of box. The only problem I have is that I can only connect to one network at login, if try to connect to any other wifi signals or even a wired connection it just fails. Don't know why but currently it's my only grip, any help would be appreciated.

---

### Post by Twitch6000 on 2008-11-03
Ok I have a Atheros 5009 and these distros worked out of the box for me or with a bit of tweaking.

Ubuntu 8.10 (works out of the box)

Mandriva 2009 (I needed to get mad wifi set up though)

PClinuxOS2009 (This you will need ethernet if you don't have ethernet don't try it)

---

### Post by n8ek on 2008-11-06
Thanks 67GTA your advice on enabling wireless in mint was really helpful (using it now).

the problem I have and not sure if its common is the screen is a lot darker than window's I even had that problem with Mandriva but a lot worse than mint my graphics card is Nvidia I installed the driver using default driver install app (cant remember what its called its gone)

Thanks

---

