---
title: "HOWTO: Netgear WG311v3 ndiswrapper"
date: 2007-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by TheIrishGuy on 2007-11-13
note : ive posted this because there are so many beginners having problems with this card, even though it is easy for some, there is still a need for this post

this is for rev 03, look at the end of the post for the other revisions

[SIZE="4"][COLOR="DarkRed"]NetGear WG311v3 (marvell chipset)[/COLOR][/SIZE]

Install Ndiswrapper
```

sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common

```

Download marvell chipset Drivers (i cant find the link where i got em, so i uploaded them to my own webspace)
```

wget http://www.feeditout.com/marvell/wlandrivers.zip

```

Unzip them
```

unzip wlandrivers.zip

```

Load the driver (ini file) (i used the win2k xp drivers)
```

ndiswrapper -i /path/to/ini

```

lets see if it is present
```

ndiswrapper -l
mrv8335 : driver installed
        device (11AB:1FAA) present

```

Save our settings 
```

sudo ndiswrapper -m

```

Start the device
```

sudo modprobe ndiswrapper

```

once the driver has been installed you can remove the unzipped files, as the needed files have been copied elsewhere

```

rm -rvf /path/to/folder

```
[SIZE="5"][COLOR="Red"]note : alwasy be carefull of what you delete, use GUI if unsure[/size][/color]
check this sticky out
[http://ubuntuforums.org/showthread.php?t=611908](http://ubuntuforums.org/showthread.php?t=611908)


Network-manager will make it work automatically in gnome

if you want it on boot, advanced config for terminal usage can be found here

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking)




[SIZE="4"][COLOR="DarkRed"]Does not work with madwifi[/COLOR][/SIZE]

Madwifi Netgear Info for WG311
-------------------------------------------------------------------------------------------

Chipset:	AR5212 (b/g)
URL:	[www.netgear.com](www.netgear.com)

Interface:	Mini PCI in PCI carrier. (Can be removed).

Antenna Connector:	RP-SMA.
Device Information:	168c:0013 (rev 01)

Notes:	Rev 01 works fine with Madwifi(ng?) under Ubuntu 7.04 with NetworkManager.
Rev 02 has a TI chip, and is not compatible (Device Information : 104c:9066, Work with ndiswrapper).
[SIZE="2"][COLOR="DarkRed"]Rev 03 has a **Marvell Chip**, and is also **not compatible** (Device Information : 11ab:1faa (rev 03), **Work with ndiswrapper**)[/COLOR][/SIZE]

---

### Post by possmann on 2008-02-09
I'd love to use this but I cannot get access to that web site you posted for the drivers. I'm having a real heard time getting this card to work and cannot seem to find the right drivers.  Would you please email that zip file to me?
[email]petersppc@hotmail.com[/email]
THANKS!

---

### Post by dimitris1972 on 2008-05-12
Hello !
I tried to use your instructions to make my wireless card work but it didn't work !
In the step 3, when I type the command " unzip wlandrivers.zip" I get the following answer : " cannot find or open wlandrivers.zip, wlandrivers.zip.zip or wlandrivers.zip.ZIP.".
Do you have any ideas how to fix this problem ?
Thank you,

dimitris

---

### Post by FadexToxBlack81 on 2008-10-22
ok so im a noob when it comes to ubuntu so go easy on me XD

but at the first step it says couldnt find package ndiswrapper-utils-1.9....so idk if i have to download out else where but if i do do i put it on i the edrive?

---

