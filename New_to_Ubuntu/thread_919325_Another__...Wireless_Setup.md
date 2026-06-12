---
title: "Another ? ...Wireless Setup?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by SarahMarieNC2 on 2008-09-13
Okay, here goes. I have a WMP54G wireless linksys network card. How do I set it up? I've been reading for about 3 hours and found nothing recent about this matter. I could technically just order a new wireless card ...but.. if I can get this one to work I'd rather not. Do they make a wireless card compatible with linux/ubuntu? I don't have any other way to connect because we live in a wi-fi enabled city and got rid of our dial up service when our home went wireless. Thanks again for any help, all your patience, and time too.

Sarah

---

### Post by Freiberg on 2008-09-13
Did you do the hardware drivers yet?

---

### Post by SarahMarieNC2 on 2008-09-13
I've not done anything other than put the card in and  try to run the cd only to realize that it won't run.. I guess because its made for windows. So there must be a way around this? I just don't understand how it all works yet and reading doesn't do me much good unless Im reading instructions because I am a hands-on learner. That's what makes playing with something like this so FUN for me.  :)

---

### Post by Freiberg on 2008-09-13
Hmm.  I am new to Ubuntu as well, but I had a similar problem with my graphics card, so I had to get the ¨uncondoned¨ version in order for it to work.

---

### Post by SarahMarieNC2 on 2008-09-13
Yah, I have a notice on ubuntu desktop saying that my nvidia graphics driver needs updating too, but I can't do that until I get the internet working.. running wireless on my mother in laws laptop, she gets wireless at my house but not at hers so she has been letting me borrow her laptop

---

### Post by Freiberg on 2008-09-13
Ok, so you are not at your own laptop?  EDIT: I just realized that I also have a WMP54G wireless setup too.

---

### Post by SarahMarieNC2 on 2008-09-13
No, I have an HP M8100n Desktop PC. I downloaded some things today and then burned them to cd to get ubuntu on my computer, but after I knew I was done with the copy on this laptop I made sure to uninstall and remove anything leftover so that her computer is returned to her the same as it was when she loaned it to me.

---

### Post by Freiberg on 2008-09-13
I don´t know for sure whether or not you can get the updates with just the LiveCD.  You might try partitioning the drive and dual-booting Windows and Ubuntu, on your regular computer, of course.  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)  I would still recommend backing up your data, of course, but the forum rules require me to say that.  ;)   Seriously, though, try it on your laptop and see whether that helps.

---

### Post by SarahMarieNC2 on 2008-09-13
I  can't dual boot on this. It doesn't have the right requirements and the computer I just put ubuntu on doesn't have anything except ubuntu because vista crashed it and HP walked me through a level 5 erase. It's a long story. LOL!

---

### Post by Freiberg on 2008-09-13
Oh.  If you have full ubuntu on it, then it is complicated.  I really don´t know too much about wireless cards, but I will go look now.  Not that I am any more experienced than you at this point, but two minds could be better than one.

---

### Post by SarahMarieNC2 on 2008-09-13
Yep, I only have ubuntu on it.. The harddrive is fairly empty. At some point I am hoping I can somehow get to a placce wehre I can have Vista and Ubuntu though. But that's gonna cost me because they don't send OS cds with their computers anymore, which is ridiculous for the price we pay for the computers and then having to buy the OS cds as well... yucky!

So happy to just have a running computer again.. now if only I can get the internet set up.

---

### Post by SarahMarieNC2 on 2008-09-13
I found this information on but I'm not sure what it actually means other than it is on the list of cards that work with ubuntu. However, maybe someone here can explain it so I can get my card working.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/")

CARD LIST G-L

Card: Linksys WMP54GS Wireless-G PCI Adapter with Speedbooster
Chipset: Broadcom Corporation BCM94306 802.11g (rev 03)
pciid: 14e4:4320
Driver: Linksys [ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe](ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe) (new version)
Other: Ndiswrapper 0.11 and 0.12. Works fine with 64-bit WEP key and WPA supplicant (Fedora core-2, Kernel 2.6.8 and 2.6.9). Use WMP54GS.inf


Card: Linksys WMP54G-EU V2, 54mbps
Chipset: Broadcom BCM4306
pciid: 14e4:4320
Driver: version 3.30.15.0 as on Install CD shipped with card
Other: Suse 9.2, updated linux kernel 2.6.8-24.10, Ndiswrapper 010-3 via YAST from Suse install DVD. Stable operation, WEP and Booting/Start-Up works well. Installed according the General Guide and the very good Suse Guide by Andrew M 8^0-meow. ([http://ndiswrapper.sourceforge.net/phpwiki/index.php/Suse](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Suse) Professional 9.1)
Other:Debian testing, 2.4.26 kernel: Ndiswrapper from CVS, date 2005.03.04, driver from [ftp://ftp.linksys.com/pub/network/WMP54Gv4_20040415.exe](ftp://ftp.linksys.com/pub/network/WMP54Gv4_20040415.exe), using WPA with wpa_supplicant (from wpasupplicant .deb package)


Card: Linksys WMP54G v3, 54mbps
Chipset: Broadcom BCM94306
pciid: 14e4:4320
Driver: The current Linksys driver [ftp://ftp.linksys.com/pub/network/WMP54Gv4_20040415.exe](ftp://ftp.linksys.com/pub/network/WMP54Gv4_20040415.exe) does work well with Ndiswrapper 1.0rc1. Use the driver in WMP54Gv4_20040415/Drivers/WMP54Gv2/bcmwl5.inf.
Other: Debian Sarge, linux kernel 2.6.9, SMP, Ndiswrapper 1.0rc1 manual compile. WPA works with wpa_supplicant supplied with Debian (0.2.5), both broadcast and non-broadcast ssid.


Card: Linksys WMP54G v4, 54mbps
Chipset: Ralink RT2500
pciid: 1814:0201
Driver 0: Native GPL Ralink driver in Ubuntu Breezy (rt2500 and rt2500-source packages). Installed the source and manually built with &#8216;make&#8217;. Then used Gnome&#8217;s network configuration to setup the device. Seems to perform as well as Windows version, but haven&#8217;t tried WEP or WPA. My card was labeled WMP54G (EU), bought in 11/2005.
Driver 1: RT2500.inf from the WMP54Gv4 directory on the CD (the bundled CD has both v2 and v4 drivers), or download the drivers straight from Linksys.
Other: Debian Sarge, 2.4 kernel, and 128-bit WEP. Works great. Also works with Mandrake 10.1 with the newest versions of Ndiswrapper, not the one included on the installation CD. Note that Ralink has provided the source for an official driver at [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) but I have not tested it yet.
Driver 2: Open source driver of Ralink (serialmonkey) downloadable at [http://prdownloads.sourceforge.net/rt2400/rt2500-1.1.0-b4.tar.gz?download](http://prdownloads.sourceforge.net/rt2400/rt2500-1.1.0-b4.tar.gz?download). Tested with WPA


Card: Linksys WMP54G v4.1, 54mbps
Chipset: Ralink RT61
pciid: 1814:0301 and 1814:0302
Driver: Don&#8217;t use driver that ships with card, it didnt work with ndiswrapper. Use the close source driver from Ralink [http://www.ralinktech.com](http://www.ralinktech.com). It compiles for 2.4 and 2.6 kernels.
Other: The rt2x00 Open Source Project ([http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)) have now a driver - but realy beta.
Other: The Ralink driver works great. It is not a plug and play, you need your kernel headers, the appropiate gcc (3.4) but when you can link it together and put it where it loads at startup, it works great. I am using WPA without any problem.


Card: Linksys WMP54GX
Chipset: Airgo networks Inc unknown device 0001
pciid: 17cb:0001
Driver (linksys): use the driver found on the linksys website at [http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fzip&blobheadervalue2=inline%3B+filename%3DWMP54GX_v10.zip&blobkey=id&blobtable=MungoBlobs&blobwhere=1129216876336&ssbinary=true](http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fzip&blobheadervalue2=inline%3B+filename%3DWMP54GX_v10.zip&blobkey=id&blobtable=MungoBlobs&blobwhere=1129216876336&ssbinary=true)


ETA: This is the one specific to my card WMP54G V 4.1

Card: Linksys WMP54G v4.1, 54mbps
Chipset: Ralink RT61
pciid: 1814:0301 and 1814:0302
Driver: Don&#8217;t use driver that ships with card, it didnt work with ndiswrapper. Use the close source driver from Ralink [http://www.ralinktech.com](http://www.ralinktech.com). It compiles for 2.4 and 2.6 kernels.
Other: The rt2x00 Open Source Project ([http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)) have now a driver - but realy beta.
Other: The Ralink driver works great. It is not a plug and play, you need your kernel headers, the appropiate gcc (3.4) but when you can link it together and put it where it loads at startup, it works great. I am using WPA without any problem.

---

### Post by Freiberg on 2008-09-13
I am getting nothing.  I am really sorry, and I don´t know what time zone it is where you live, but it is 11:00 for me.  I have to get to sleep.  Again, I apologize for the fact that I could not help.

---

### Post by gali98 on 2008-09-13
Okay hi again :)

First go to System->Administration->hardware drivers 
and put in your password when prompted.
Now tell me if there is anything in that list.

then do in a terminal
cd ~/Desktop
gksudo lshw > hw.txt

now on your desktop there will be a text file named hw.txt.
Please upload that as well as tell me what is in hardware drivers window (the first step)

lastly, please post the output of the command (in the terminal... just copy and paste)

iwconfig

Thanks,
Kory

---

### Post by SarahMarieNC2 on 2008-09-13
what's a terminal and how do I open one? LOL.. maybe I should read some more... 


Yep, I found out how to open one. just needed to read more.. I'll tackle this in  the morning. Its getting close to midnight here on the east coast

Ohhhh and THANK YOU for all the help, patience, tips, etc. This has been a great experience. Maybe onbe day I'll be helping new people too... haha.. Im kidding myself.

---

