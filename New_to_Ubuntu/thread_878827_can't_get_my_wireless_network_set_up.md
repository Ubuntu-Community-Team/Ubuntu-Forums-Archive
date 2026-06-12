---
title: "can't get my wireless network set up"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by phirebug on 2008-08-03
sorry if this is really elementary.  i know almost nothing about linux, but i figured hell, nothing can be worse than vista, so i took the plunge.  i've gotten most of my stuff up and running, but i can't get it to add a wireless connection.  if i open up my hardware drivers thing, it shows that the driver is installed and running, but network manager won't recognize it, and the little light won't come on no matter which position i put the wireless switch in.

a little background if it helps:
it's an hp laptop with a dual turion processor
wireless card is Atheros 802.11 

can somebody help point me in the right direction?  i found some other posts with great instructions for manually setting up the network, but they all assume that ubuntu can find my wireless card.

thanks,
james

---

### Post by rubenverweij on 2008-08-03
You might want to try NDiswrapper if your card worked under Windows. It lets you use your Windows driver under Ubuntu.

[List of supported cards]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")

[Installation]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/")

---

### Post by phirebug on 2008-08-03
i couldn't get ndiswrapper installed for the life of me.  i did find a driver that says it's compatible with my card (madwifi) but i can't figure out how to install it either.  is there anywhere with really, really simple instructions on how to install these things?  i am really unfamiliar with the command line interface.

---

### Post by bobnutfield on 2008-08-03
There are a number of variants of the Atheros chipset.  I do not have it, but most of what I read tells me that madwifi is the correct way to go for this chipset.  But, if you want to use ndiswrapper, that is available from the Synaptics Package Manager, but you will need the medibuntu repository enabled.  Madwifi is also available there and there is a howto here:

[http://ubuntuforums.org/showthread.php?t=75451]("http://ubuntuforums.org/showthread.php?t=75451")

---

### Post by nickgaydos on 2008-08-03
I got mine working by downloading the correct WINDOWS drivers, installing an app called Windows Wireless Drivers and searching for <YOURDRIVERMODEL>.itf and eventually, Wireless networks were listed in my network applet.

---

### Post by phirebug on 2008-08-03
i did what nickgaydos suggested, and now my network manager lists wireless networks as an option, but i can't connect to any of them.  it won't even list the ones that are available.  what can i try next?

thanks for the help guys, i'm getting closer :)

---

### Post by bobnutfield on 2008-08-05
If you are now seeing wireless as an option, type in a terminal:

> ifconfig -a

If your wireless card shows up, we can usually configure from the command line.

---

### Post by phirebug on 2008-08-05
i tried that and it gives me this:

bash: iconfig: command not found

---

### Post by bobnutfield on 2008-08-05
Maybe you just entered a typo, but the command is 

ifconfig -a

---

### Post by gnat79 on 2008-08-05
or you could try

iwconfig 

If it says no wireless adapters found or something, then it means you don't have the drivers installed correctly.

---

### Post by phirebug on 2008-08-05
iwconfig returned this:


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

i'm sorry for all the stupid questions, but i don't really understand what most of that means.  i really appreciate you guys taking the time to help, though.  thanks :)

---

### Post by bobnutfield on 2008-08-05
Your wireless card appears to be working, but is not associated with your router or any networks.  Try typing:

> sudo iwlist wlan0 scan

---

### Post by phirebug on 2008-08-05
wlan0     No scan results

it's sitting 2 feet from my wireless router.  i don't think it's a router problem though, because i live in a big apartment building, and it always used to pick up at least a couple signals.  

what other things can i try?


btw...assuming that the wireless adapter and network manager are both working properly, will it automatically detect when it picks up a wireless signal and give me the option to connect?  i could try going to a known wifi spot and seeing if it can find anything there to try and narrow down the problem.

---

### Post by fballem on 2008-08-05
Don't know if this helps, but up until a couple of days ago, I was using Network Manager and was able to get the wireless network working with no problems.

There was a large update on Sunday, which I think included Network Manager. Since that time, I have had no option on Network Manager to connect to wireless.

I did find an alternate program (see: [http://ubuntuforums.org/showthread.php?t=878156](http://ubuntuforums.org/showthread.php?t=878156) ) but I'm still curious to see what happened with the Network Manager. I'll be following this thread.

Output from lspci:

```
fballem@ballemco-01:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

### Post by phirebug on 2008-08-05
i downloaded wicd and installed it, and it comes up under applications>internet, but when i click on it, nothing happens.  i don't get any of the windows like the screenshots on their website, and none of the results i previously posted changed.  what might i have done wrong there?

you know, just a thought...is this something that you guys think would continue to be a problem if i switched to a different flavor of linux?  not that i'm unhappy with ubuntu or anything, i just want to get this thing working.  i don't know anything about the other versions, maybe one of them will work better for my machine.

...i hope that's not like wearing the opposing team's jersey to the game...i'm just trying to find solutions.

---

### Post by fballem on 2008-08-06
A couple of thoughts:

I am sorry that I had a BDM (Brain Dead Moment). Two questions:

[LIST=1]
[*]Have you disabled the broadcast of the SSID on your wireless router? The reason that I ask is that Linux works differently than windows for SSIDs that do not broadcast.
[*]Did you actually test your wireless, or did you simply accept that wireless was not working because the little light did not come on?
[/LIST]

The reason that I'm asking the questions is that when I first installed ubuntu, I did notice that the wireless adapter light did not come on. I do have a hidden SSID. Wireless used to work for me under Network Manager and does now work for me under wicd - but the hidden SSID works differently under Linux than under Windows - you will always have to specify the SSID.

The following link contains a tonne of useful information on running ubuntu on an HP Laptop: [http://excid3.pcriot.com/Ubuntu_on_HP_Compaq_Laptops.pdf](http://excid3.pcriot.com/Ubuntu_on_HP_Compaq_Laptops.pdf) including how to get the wireless adapter light to turn on.

In addition, if you still have wicd installed, then open it and select the downward arrow next to the Network item in the menu. If you then select Hidden network, you should get a screen to enter the ssid for the hidden network. I've attached a screenshot that may get you started. Try this regardless of whether your wireless adapter light is on or not.

Hope that this helps!

---

### Post by phirebug on 2008-08-06
i can't get that screen to come up at all under wicd.  if i go to system>administration>network, i can enable the wired and wireless connections, but it won't show me what the connections are.  if i go to applications>internet and click on wicd, it doesn't do anything.

based on what iwconfig returned (see above) i think the wireless card is working, just not detecting any networks.  i'll try reconfiguring the router later and see if that helps.

---

### Post by fballem on 2008-08-06
If the SSID is hidden, then the wireless won't automatically detect the networks (that's why they're hidden).

In Windows, once a wireless connection with a hidden SSID was made, then all of the information was saved. The next time, depending on the options, the wireless connection would be automatically made.

In Linux, I have found that I have had to provide the name of the hidden SSID everytime that I want to connect to it - it is not automatically connected.

Just some thoughts. You may also want to take a look at the other information that I linked you too, in case that provides an 'aha' moment.

---

