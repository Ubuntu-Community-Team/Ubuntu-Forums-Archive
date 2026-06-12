---
title: "Wireless connection to Ubuntu 8.04"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by johnnic on 2008-07-22
Hi

I have attempted to solve my problem for the past two weeks but have had no success.  Hence, I am hoping someone can help me with what is, no doubt, a VERY basic question.

I have a Dell Inspiron 9100 laptop which I have formatted and then installed a clean version of Ubuntu 8.04.  I am now trying to set up my wireless connection.  Initially, I clicked on the network connection icon on the top toolbar and tried 'Connect to Other Wireless Network'. I provide my network name, wireless security type (WPA Personal) and input the password.  No success.

I ran lspci and iwconfig (based on advice I had read on this forum) and received the following information:

john@john-laptop-linux:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

john@john-laptop-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Can someone please tell me where I go from here?  I have no idea  

Thanks

John

---

### Post by kdb424 on 2008-07-22
Does it show a wireless option but you pick up no network? If not, you might want to find different drivers. Let me know what's going on.

---

### Post by waspbr on 2008-07-22
from what I can see your netword card is already installed but, do 
```
iwlist scanning
```

just to check if networks are being seen.

to me network manager generally works well, but to some people there have been some issues. Just be sure which security protocol you have. 

another option that some people seem to like is wicd [http://downloads.sourceforge.net/wicd/wicd_1.5.0rc10_all.deb?modtime=1216546040&big_mirror=0]("http://downloads.sourceforge.net/wicd/wicd_1.5.0rc10_all.deb?modtime=1216546040&big_mirror=0")

this is the newest testing version, there's an older stable version on synaptic, but I reckon the testing version is stable enough.

oh yeah, don't forget to tell us if you can see networks after inputing the code above into terminal

---

### Post by johnnic on 2008-07-22
Thanks for the help.

kdb424 - no, it doesn't show a wireless network at all.

waspbr - iwlist scanning reports "Interface doesn't support scanning".  I tried to install wicd and I get the message "Error. Conflicts with the installed package 'network manager'".

Any thoughts?

John

---

### Post by kdb424 on 2008-07-22
If you can, find and uninstall and drivers that it conflicts with, then try reinstalling the drivers.

---

### Post by johnnic on 2008-07-22
kdb424

Thanks.  Ummm, you're starting to confuse me.  

I haven't previously installed any drivers as I believed they came with the Ubuntu package. How would I "find and uninstall drivers"?  Where would I then go to get new drivers and install them?

John

---

### Post by anewguy on 2008-07-22
First, the conflict message is telling you that you need to uninstall network manager, then install wicd.

Second, did you ever install any drivers for the wireless in Ubuntu either via the fwcutter method or the ndiswrapper method? While some people seem to be doing fine with the fwcutter and the Broadcom 43xx series, I personally (this is just me, not anything other than choice) prefer to use ndiswrapper and the Windows drivers.

There are many, many posts in this forum for using both the fwcutter method and the ndiswrapper method to get this series of cards working.  I would first suggest you find the Windows drivers for your card (non-Vista) - they should be something like bcmwl5.inf and bcmwl5.sys.  Once you have these you can follow the ndiswrapper method quite easily.  

You may need to install ndiswrapper - just check in synaptic package manager to see if it is there.  While doing so, this is when I would mark network manager for removal and wicd for installation and apply.

---

### Post by anewguy on 2008-07-22
I did a zip in Ubuntu of the 2 files I think you need for your driver for your wireless card.  You should be able to use these in ndiswrapper.  I've never used zip in Ubuntu before but I would imagine you can just unzip it.  I've attached the zip file.

---

### Post by kdb424 on 2008-07-22
Zips are basicly just like folders. You can just drag the files into a folder that you make. Pretty easy.

---

### Post by anewguy on 2008-07-22
> **kdb424 said:**
> Zips are basicly just like folders. You can just drag the files into a folder that you make. Pretty easy.

Thanks for the info!  I had used tar in the past but the tar file I made of these 2 files was too large for the forum.  Did a man zip and tried zip to get a file in the size the forum would accept.  I'll try playing with that zip file's local copy as you suggest to get familiar with it.

Thanks again!
Dave

---

### Post by johnnic on 2008-07-22
anewguy - thanks for the zip file.  I'm trying to install ndiswrapper.  The Help menu tells me to install ndisgtk but I cannot find it in the Synaptic Package Manager.

---

### Post by johnnic on 2008-07-22
Well, I've managed to install ndiswrapper and I've added the device driver bcmw15.inf but still no internet connection.

Thanks for all the advice, I guess I'm simply not ready to tackle Linux just yet.  Perhaps I'll check back in a few years when it (hopefully) really does become as simple as Windows. Pity, as I can really some huge advantages of running Linux but it simply isn't user-friendly enough for a computer cretin such as I.

John

---

### Post by nickdbliss on 2008-07-22
With ur wireless chipset it is pretty easy to install wireless drivers n able to use it. As far as linux as an OS is concerned, well linux is far more stable, reliable n user friendly than windows. THing is manufacturers are not releasing drivers for linux. Imagine what if u dont have windows drivers? What u ll do? At least at linux community guys are trying to get it work.

---

### Post by nickdbliss on 2008-07-22
I also have same wireless manufacturer n has the wireless running all great. Try to post what u did ,what steps u followed, which guide? then someone ll be able to understand ur problem n point u in right direction.

Here is how i did it:
[http://ubuntuforums.org/showthread.php?t=827799](http://ubuntuforums.org/showthread.php?t=827799)

Also try to narrow down ur problem by enabling SSID broadcasting and using no encryption in place of WPA. If it works doing that then u can proceed. THats how it works with linux specially wireless problems

---

### Post by edwardLS on 2008-07-22
I also have a Dell 9100 with the Broadcom 4306 Rev 3, and I have wireless working very well.  I am not sure if this will help, however I will pass it on for you use.  I was NOT able to get wireless working initially on 8.04.  When version 8.04.1 was release, I did a re-install using 8.04.1.  I was then able to get wireless working from the System -> Administration -> Hardware Drivers - (I am not at my ubuntu PC, so I hope I have that right).  When I "enabled" the b43..... it did not require a reboot; however, I was not able to get on the internet wirelessly until after I rebooted.

Good luck, and I hope this may help.

---

### Post by anewguy on 2008-07-22
I would also STRONGLY suggest the following:

sudo ndiswrapper -l <enter> that's a lower case "L"

post the output back here

Also:

You need to be sure wireless is set to roaming under System/Administration/Network.

If you can see wireless networks but can't connect:

disable all "protection" at the router temporarily.  This means no WEP, no WPA, no address blocking.  Then try to connect.

If you are using WEP or WPA, be sure you select the correct number of "bits" in the connection menu - I believe it defaults to 128 on WEP and mine needed to be 64.  

If you are running WPA, be sure WPA supplicant is installed and running (I think it's a default in 8.04).  Look at other posts in this forum dealing with getting WPA to work - it isn't always as straight forward as you might think.

Please post back the output of that ndiswrapper request, and we can go from there.  Remember, the .inf and .sys files must be in the same folder, and by default you should be in that folder when you issue the ndiswrapper -i command, otherwise it may not find everything.

If using ndiswrapper, be sure you have blacklisted the bcm43xx driver.


Dave  :)

---

### Post by johnnic on 2008-07-23
Thanks everyone for your help; it is much appreciated.

I will spend the next few days (when I get the opportunity) to try all of the suggestions that have been made and let you know how I go.

John

---

