---
title: "Need help with drivers from Broadcom wireless"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Arlo26 on 2008-10-18
You know what? Honestly? I really wanted to go with Ubuntu. I installed, and was excited, but I couldn't get my wireless to work. I tried to get the right drivers, but there was no simple answer online. And everything I DID try, just left me out in the dark completely, with no progress at all. It shouldn't be THAT hard. I mean, I'm quite proficient with computers, and what I don't know I usually can figure out, but this was just ridiculous. If someone is willing to try and help me, I would be MORE than glad to switch as I've seen nothing but good things.

Here are my computer specs: 

Operating System 	  	System Model
Windows XP Home Edition Service Pack 3 (build 2600) 	  	Hewlett-Packard Presario V2000 (PV341AV#ABA) Rev 1
System Serial Number: CNF5400ZLD
Enclosure Type: Notebook
Processor a 	  	Main Circuit Board b
2.00 gigahertz AMD Turion 64
1024 kilobyte primary memory cache 	  	Board: Quanta 3093 47.0D
Bus Clock: 200 megahertz
BIOS: Hewlett-Packard F.11 08/04/2005
Drives 	  	Memory Modules c,d
120.02 Gigabytes Usable Hard Drive Capacity
64.29 Gigabytes Hard Drive Free Space

Generic DVD-ROM SCSI CdRom Device [CD-ROM drive]
TSSTcorp CD/DVDW TS-L532M [CD-ROM drive]

ST9120822A [Hard drive] (120.03 GB) -- drive 0, s/n 5LZ8NF7C, rev 3.ALE, SMART Status: Healthy 	  	896 Megabytes Installed Memory

Slot 'U5' has 512 MB
Slot 'U6' has 512 MB
  	Local Drive Volumes
  	
		
c: (NTFS on drive 0) 	120.02 GB 	64.29 GB free

ATI RADEON XPRESS 200M [Display adapter]
MS_ 19.7 [Monitor] (19.7"vis)

And the card is:


******_***Broadcom 802.11b/g WLAN***_**********

I've honestly done nothing but read forums and try what was listed, but I couldn't get anywhere. I had the 64bit ubuntu and everything, and everything else worked fine, just couldn't connect. Any help, please please please. I beg of you. Otherwise, I'll just have to give up until something better comes along, and I really don't want to.

---

### Post by Nepherte on 2008-10-18
What's the model number of your broadcom? You can start with taking a look at: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by eternalnewbee on 2008-10-18
> **Arlo26 said:**
> You know what? Honestly? I really wanted to go with Ubuntu. I installed, and was excited, but I couldn't get my wireless to work. I tried to get the right drivers, but there was no simple answer online. And everything I DID try, just left me out in the dark completely, with no progress at all. It shouldn't be THAT hard. I mean, I'm quite proficient with computers, and what I don't know I usually can figure out, but this was just ridiculous. If someone is willing to try and help me, I would be MORE than glad to switch as I've seen nothing but good things.

Here are my computer specs: 

Operating System 	  	System Model
Windows XP Home Edition Service Pack 3 (build 2600) 	  	Hewlett-Packard Presario V2000 (PV341AV#ABA) Rev 1
System Serial Number: CNF5400ZLD
Enclosure Type: Notebook
Processor a 	  	Main Circuit Board b
2.00 gigahertz AMD Turion 64
1024 kilobyte primary memory cache 	  	Board: Quanta 3093 47.0D
Bus Clock: 200 megahertz
BIOS: Hewlett-Packard F.11 08/04/2005
Drives 	  	Memory Modules c,d
120.02 Gigabytes Usable Hard Drive Capacity
64.29 Gigabytes Hard Drive Free Space

Generic DVD-ROM SCSI CdRom Device [CD-ROM drive]
TSSTcorp CD/DVDW TS-L532M [CD-ROM drive]

ST9120822A [Hard drive] (120.03 GB) -- drive 0, s/n 5LZ8NF7C, rev 3.ALE, SMART Status: Healthy 	  	896 Megabytes Installed Memory

Slot 'U5' has 512 MB
Slot 'U6' has 512 MB
  	Local Drive Volumes
  	
		
c: (NTFS on drive 0) 	120.02 GB 	64.29 GB free

ATI RADEON XPRESS 200M [Display adapter]
MS_ 19.7 [Monitor] (19.7"vis)

And the card is:


******_***Broadcom 802.11b/g WLAN***_**********

I've honestly done nothing but read forums and try what was listed, but I couldn't get anywhere. I had the 64bit ubuntu and everything, and everything else worked fine, just couldn't connect. Any help, please please please. I beg of you. Otherwise, I'll just have to give up until something better comes along, and I really don't want to.
You mean proficient with Windows. This is Linux and if you are really looking for help, then you have come to the right place.
Patience is a virtue. Children don't give up learning to walk, just because they had fallen...
Good luck.

---

### Post by conehead77 on 2008-10-18
> **eternalnewbee said:**
> You mean proficient with Windows. This is Linux and if you are really looking for help, then you have come to the right place.
Patience is a virtue. Children don't give up learning to walk, just because they had fallen...
Good luck.

Why do you post when you dont have a tip for the OP? Obviously he came to the right place (this forum) to ask a question. And obviously he has a lot of patience. Otherwise he wouldnt take the time to read the forum and ask his question here.

Anyways, Nepherte already provided a link which should do the job. There are some wireless manufacturers who dont support drivers for linux, thats why many people have problems to get it work. Ndiswrapper is a dirty hack to make those devices work. I had to install ndiswrapper on the laptop of my girlfriend too and it works quite well.
If you cant make your wireless work and _really_ want to use Ubuntu, you could also purchase a new wireless card. Here is a list of what devices are supposed to work: 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Manufacturer](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Manufacturer)

---

### Post by sethvath on 2008-10-18
Speaking of draconian, someone is not allowed to post a reply because he does not have a tip for the OP? 

Arlo26, the HP v2000 model shares the same broadcom wireless card with several other laptops, you might want to search for those models as well for help getting wireless to work. ie. "HP v2000 ubuntu linux broadcom drivers"

If its the bcm43xx series, start here: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

If that does not work, you can try downloading the official drivers from broadcom and getting them to work with nsdiswrapper.

---

### Post by stanwow on 2008-10-18
Please don't give up. Several days ago, I got the same problem that was just as yours.My wireless device did not work. And I have tried many ways to fixed the problem. Again and again.Finally I solve the problem, and I can connect the network with the wireless device.
My wireless device is AR242X, I am sorry but I have forgot the link that may be help you.But I think you can go on searching on the ubuntu forum and finally find a way to connect the network.That is great when you fix your wireless.

---

### Post by Big_Kahunaca on 2008-10-18
> **Arlo26 said:**
> And the card is:


******_***Broadcom 802.11b/g WLAN***_**********

If you could give us the output of "lspci", more specifically, the line with the Broadcom statement in it.

And don't give up hope.  I'm on a HP Pavilion dv6404ca with a Broadcom card in it and my wireless works fine with the proprietary Broadcom driver.  If your Broadcom card is of the 43xx class, don't despair, help is on the way in the new Ubuntu release! (I'm using the Intrepid beta btw...)

---

### Post by eternalnewbee on 2008-10-18
> **sethvath said:**
> Speaking of draconian, someone is not allowed to post a reply because he does not have a tip for the OP? 

Arlo26, the HP v2000 model shares the same broadcom wireless card with several other laptops, you might want to search for those models as well for help getting wireless to work. ie. "HP v2000 ubuntu linux broadcom drivers"

If its the bcm43xx series, start here: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

If that does not work, you can try downloading the official drivers from broadcom and getting them to work with nsdiswrapper.

Thanks for that.

---

### Post by Big_Kahunaca on 2008-10-18
> **sethvath said:**
> If that does not work, you can try downloading the official drivers from broadcom and getting them to work with nsdiswrapper.

There are Linux Broadcom drivers as well that perhaps he could try first instead of using ndiswrapper.

[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by sethvath on 2008-10-18
> **Big_Kahunaca said:**
> There are Linux Broadcom drivers as well that perhaps he could try first instead of using ndiswrapper.

[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

Yes indeed. I was looking for the article about the new broadcom linux drivers when I posted that. Found it this time:

[http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive](http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive)

---

### Post by nhasian on 2008-10-18
I might have missed it, but did you mention which version of ubuntu you where trying?  I understand the new 8.10 is suppose to support a lot more wifi cards.

also it wouldnt hurt if you upgraded your bios.  the most current version for your notebook is from 03-2006 is F.23 A

[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=500508](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=500508)

---

