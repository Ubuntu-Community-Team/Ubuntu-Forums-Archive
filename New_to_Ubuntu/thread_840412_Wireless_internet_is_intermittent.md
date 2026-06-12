---
title: "Wireless internet is intermittent"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by matthewhaworth on 2008-06-25
Okay, I've managed to get my wireless internet working with ubuntu (I was trying to connect at 128bit instead of 64bit lol) but now, it takes ages to load google and sometimes won't even load a page at all, I had to come out of it and come back into windows to post this message on here.  Any ideas as to what may be causing the problem?  My internet connection is 8mb/s and it works fine on Windows so it had to be a problem with ubuntu.  

Also, I'm interested in developing with Ubuntu, any advice on where to start? I've done a lot of PHP programming before but no real application programming, I've dabbled with Java and I'm very comfortable with object oriented programming languages, it's just I want to start developing with Ubuntu, applications and such.. 

Any help will be greatly appreciated.

---

### Post by jualin on 2008-06-25
ok if you are using firefox try disabling IPV6. To do this type > about:config on the Firefox address bar and then look for IPv6 (use the filter search utility) and Toggle it from False to true. Maybe this will speed up things a little bit.

---

### Post by superprash2003 on 2008-06-25
try changing dns servers to opendns 208.67.222.222 and 208.67.220.220

---

### Post by matthewhaworth on 2008-06-25
How would I go about that?
Thanks for your help guys, I'll try both when I reboot

---

### Post by phidia on 2008-06-25
What method and driver are you using to get wireless? What card do you have?

---

### Post by matthewhaworth on 2008-06-25
How do I find that out lol? I'm really new to Linux lol

---

### Post by jualin on 2008-06-25
If you wireless card is a PCI card then type > lspci This will **List** all of your PCI devices. If your wireless network worked by default you are most likely using a native linux driver and not ndiswrapper (windows driver).

---

### Post by matthewhaworth on 2008-06-25
> 06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

There's that? My wireless network did work by default, so that means I'm using a native linux driver? I don't know, I've wired my laptop to the router for now.. it was working on wireless quite well for about, two minutes, then it just died again for no reason..

Thank you for your help so far :)

---

### Post by jualin on 2008-06-25
That's the model of the Ethernet (wired internet) so that is not it. If your wireless card is a USB device then you need to type > lsusb. Post the complete results from both commands.

---

### Post by matthewhaworth on 2008-06-25
> matthewhaworth@matthewhaworth-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
06:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
06:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
matthewhaworth@matthewhaworth-laptop:~$ lsusb
Bus 005 Device 002: ID 0db0:6877 Micro Star International 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Is that okay? It's definity not a USB but I thought I'd do it anyway lol

---

### Post by jualin on 2008-06-25
I don't see your wireless card listed in there. Are you using a PCMCIA card (little card that you plug in and out)? Post the results of > lspcmcia. And tell us the model and make of your computer.

---

### Post by matthewhaworth on 2008-06-25
There is absolutely no output to the lspcmcia :(.
Erm, I'm using an Advent 7109A.. if that means anything.. Ubuntu can definitely find my wireless card as it's found some networks lol.. odd huh?

Apparently it's a "Ralink 2500 WLAN"

---

### Post by jualin on 2008-06-25
That is pretty odd since the wireless card is not showing on your lspci output. Maybe someone more experienced can confirm that. I will look up a solution for your problem. Just hang in there buddy.

---

### Post by jualin on 2008-06-25
Ok, how about a different approach, post the results of > ifconfig
iwconfig

---

### Post by jualin on 2008-06-25
I found this guide online that you may want to take a look at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw")

---

### Post by matthewhaworth on 2008-06-25
> matthewhaworth@matthewhaworth-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:55:94:96  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe55:9496/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85877 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:196260639 (187.1 MB)  TX bytes:8074453 (7.7 MB)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:133031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7168617 (6.8 MB)  TX bytes:7168617 (6.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:13:d3:7e:98:17  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1062701 (1.0 MB)  TX bytes:127721 (124.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-7E-98-17-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

matthewhaworth@matthewhaworth-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:14:7F:9F:20:47   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I shall take a look at the guide.  Thank you :).

---

### Post by phidia on 2008-06-25
Try also > lspci -nn. See if that outputs your network device.

---

### Post by matthewhaworth on 2008-06-25
> **phidia said:**
> Try also . See if that outputs your network device.

I'm afraid it doesn't :(.

---

### Post by jualin on 2008-06-25
try this > **[B]lsmod | grep rt**[/B]

---

### Post by matthewhaworth on 2008-06-25
> matthewhaworth@matthewhaworth-laptop:~$ lsmod | grep rt
parport_pc             36260  0 
parport                37832  3 ppdev,parport_pc,lp
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
iTCO_vendor_support     4868  1 iTCO_wdt
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
agpgart                34760  3 drm,intel_agp
usbcore               146028  5 rt73usb,rt2x00usb,ehci_hcd,uhci_hcd


That right?

---

### Post by jualin on 2008-06-25
Ok according to that your wireless device is installed and the modules are loaded. Try doing an scan to see if the wireless works > sudo iwlist wlan0 scan

---

### Post by jualin on 2008-06-25
I was reading the guide from the link that I sent you and if the connection is established correctly but then is lost is maybe a problem with channel interference. Maybe you can try changing the Wireless Channel in your router to a channel that no one else is using around your house.

---

### Post by matthewhaworth on 2008-06-25
> wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:B5:10:18
                    ESSID:"SKY24226"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/100  Signal level=-84 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000001958f2ca4
          Cell 02 - Address: 00:14:7F:9F:20:47
                    ESSID:"BTHomeHub-41D1"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=54/100  Signal level=-34 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000180b05aacc1
          Cell 03 - Address: 00:11:50:F9:D9:14
                    ESSID:"Belkin54g"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/100  Signal level=-78 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000006bfdeef12f3


Lol, it's been able to find the different networks since the beginning, it's just when I'm connected that the problem exists.. it stay  fine for about five seconds after being connected but then just dies and fails to find websites or use pidgin

> **jualin said:**
> I was reading the guide from the link that I sent you and if the connection is established correctly but then is lost is maybe a problem with channel interference. Maybe you can try changing the Wireless Channel in your router to a channel that no one else is using around your house.

It works fine with Windows though?

---

### Post by jualin on 2008-06-25
My knowledge reached to an end. What I would do next is try using Ndiswrapper with a windows XP driver. Go to the Package Manager and install ndiswrapper and ndisgtk. And try installing a windows XP driver since apparently the Linux native driver is not working for you very good.

---

### Post by matthewhaworth on 2008-06-25
Thanks a lot Jualin, I'll try your suggestion :).

---

### Post by jualin on 2008-06-25
Are you trying to connect to a Network with WPA Encryption?, if you are I found this post that it's supposed to enable WPA support for RT2500 wireless cards. Try it if that's your case [http://ubuntuforums.org/showpost.php?p=3595458&postcount=6]("http://ubuntuforums.org/showpost.php?p=3595458&postcount=6")
I hope you solve everything. Just be patient dude someone else might have the solution for your problem.

---

### Post by matthewhaworth on 2008-06-26
[http://www.jarviser.co.uk/jarviser/howto1.html#type9](http://www.jarviser.co.uk/jarviser/howto1.html#type9)

If you go right to the very bottom of that page it shows that windows has an option to obtain ip addresses and DNS automatically, is there an ubuntu equivalent?

---

### Post by jualin on 2008-06-26
Yes Ubuntu Network Manager works the same way.

---

### Post by flytripper on 2008-06-26
hmm in my such and such years of computing i have found that wireless networks simply just ARE intermittent and that you simply cant beat having a cable plugged into your computers harris.

---

