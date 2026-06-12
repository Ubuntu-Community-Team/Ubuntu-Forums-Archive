---
title: "wireless issue on ubuntu 11.10 alpha 2"
date: 2011-07-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by opengl_cpp on 2011-07-13
hi. I just installed ubuntu 11.10. everything works just fine except for my wireless card. Ubuntu automatically detected my card version and activated it for me but actually I doesn't work. I can't see wireless network list. I tried to reinstall it and I even installed ndisgtk but no success.

my wireless card model is: Broadcom BCM4311 802.11b/g WLAN

what should I do?
:mad::(

---

### Post by cpatrick08 on 2011-07-24
> **opengl_cpp said:**
> hi. I just installed ubuntu 11.10. everything works just fine except for my wireless card. Ubuntu automatically detected my card version and activated it for me but actually I doesn't work. I can't see wireless network list. I tried to reinstall it and I even installed ndisgtk but no success.

my wireless card model is: Broadcom BCM4311 802.11b/g WLAN

what should I do?
:mad::(
you would get more response in the  Ubuntu +1 (Oneiric Ocelot) [http://ubuntuforums.org/forumdisplay.php?f=403](http://ubuntuforums.org/forumdisplay.php?f=403) fourm and btw i have that problem also with a intel pro/wireless 3945abg card

---

### Post by Perfect Storm on 2011-07-24
Thread moved.

---

### Post by lucazade on 2011-07-24
What is the output of:

```
iwconfig
```

and 

```
iwlist wlan0 scanning
```

"wlan0" might change from card to card so check from first output the correct interface name

---

### Post by cpatrick08 on 2011-07-24
> **lucazade said:**
> What is the output of:

```
iwconfig
```

and 

```
iwlist wlan0 scanning
```

"wlan0" might change from card to card so check from first output the correct interface name

```
[noparse]iwfonfig    lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
wlan0     Scan completed :
          Cell 01 - Address: 00:22:75:B8:AF:EF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Patrick's\xA0Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009807a1193
                    Extra: Last beacon: 1744ms ago
                    IE: Unknown: 00115061747269636B2773A04E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060D0000000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000007A4000023A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060D0000000000000000000000000000000000000000
                    IE: Unknown: DDA00050F204104A00011010440001021041000100103B0001031047001000000000000000011000002275B8AFEF1021001242656C6B696E20436F72706F726174696F6E1023000C463644343233302D3420763310240007332E30302E30331042000E31323933323432333030323431371054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020084[/noparse]
```


iwlist wlan0 scanning

---

### Post by lucazade on 2011-07-25
wireless drivers seems working from your output... try to connect to your router with:

```
iwconfig wlan0 key restricted **wap-key** mode managed essid **essid-network-name**
```

where wap-key is router password and essid-network-name is the name of your router network.

---

### Post by cpatrick08 on 2011-07-25
> **lucazade said:**
> wireless drivers seems working from your output... try to connect to your router with:

```
iwconfig wlan0 key restricted **wap-key** mode managed essid **essid-network-name**
```

where wap-key is router password and essid-network-name is the name of your router network.

did not work for me sorry here is what i got when i entered it [IMG][IMG]http://i56.tinypic.com/34g53zt.png[/IMG][/IMG]

---

### Post by lucazade on 2011-07-25
have a look at this guide to connect wifi via terminal:
[http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)

anyway connecting via cli is only a workaround, if you don't see wifi handled from network indicator (panel applet) there is probably some issue in /etc/network/interfaces

mine looks like this:
```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

if eth0/wlan0 connections are already defined in this file you won't see network lists in indicator-network.

---

### Post by wnelson on 2011-07-26
Have you ever tried using wicd. It is graphical program for network management. It works for both wired and wireless.

---

### Post by cpatrick08 on 2011-07-28
bump

---

### Post by cpatrick08 on 2011-07-28
> **wnelson said:**
> Have you ever tried using wicd. It is graphical program for network management. It works for both wired and wireless.
did not work said bad password when password was correct

---

### Post by cariboo on 2011-07-29
Did you use your user password, of your wpa2 password?

---

### Post by cpatrick08 on 2011-07-29
> **cariboo907 said:**
> Did you use your user password, of your wpa2 password?
i used my wpa2 password

---

### Post by lucazade on 2011-07-29
could you paste the output of:

```
ps -ax | grep keyring
```

probably the keyring manager is not running and this prevent wifi to work, at least happend here on my dad pc.
related bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/813755](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/813755)

---

### Post by cpatrick08 on 2011-07-29
> **lucazade said:**
> could you paste the output of:

```
ps -ax | grep keyring
```probably the keyring manager is not running and this prevent wifi to work, at least happend here on my dad pc.
related bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/813755](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/813755)
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 1447 ?        Sl     0:00 /usr/bin/gnome-[COLOR=Red]keyring[/COLOR]-daemon --daemonize --login
 3636 pts/0    S+     0:00 grep --color=auto [COLOR=Red]keyring[/COLOR]


i am using xubuntu 11.10 btw

---

### Post by lucazade on 2011-07-30
> **cpatrick08 said:**
> Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 1447 ?        Sl     0:00 /usr/bin/gnome-[COLOR=Red]keyring[/COLOR]-daemon --daemonize --login
 3636 pts/0    S+     0:00 grep --color=auto [COLOR=Red]keyring[/COLOR]


i am using xubuntu 11.10 btw

it is a different issue, gnome keyring is running on your machine.
hmmm.. no other ideas :S

---

### Post by Peter09 on 2011-07-30
Just for a little more clarity, can you post the output of

```
nm-tool
```

---

### Post by haddog on 2011-07-30
> **cpatrick08 said:**
> Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 1447 ?        Sl     0:00 /usr/bin/gnome-[COLOR=Red]keyring[/COLOR]-daemon --daemonize --login
 3636 pts/0    S+     0:00 grep --color=auto [COLOR=Red]keyring[/COLOR]

i am using xubuntu 11.10 btw

cpatrick08, I had a similar problem after updating and then upgrading Ubuntu 11.10 alpha 2 using apt-get, my wireless card was inop and I could see no wireless hotspots or even my wifi router. My card is a Broadcom Corporation BCM4312. Wireless problem was solved by pluggin in to a wired internet connection first, and then removing "bcmwl-kernel-source" using Synaptic Package Manager, then re-installing "bcmwl-kernel-source" using Synaptic. Also you can go here and try  this: 

[http://ubuntuforums.org/showthread.php?t=1748245&highlight=BCM4312+driver&page=3](http://ubuntuforums.org/showthread.php?t=1748245&highlight=BCM4312+driver&page=3)

Refer to post #30. Hope this helps.

---

### Post by cpatrick08 on 2011-07-30
> **haddog said:**
> cpatrick08, I had a similar problem after updating and then upgrading Ubuntu 11.10 alpha 2 using apt-get, my wireless card was inop and I could see no wireless hotspots or even my wifi router. My card is a Broadcom Corporation BCM4312. Wireless problem was solved by pluggin in to a wired internet connection first, and then removing "bcmwl-kernel-source" using Synaptic Package Manager, then re-installing "bcmwl-kernel-source" using Synaptic. Also you can go here and try  this: 

[http://ubuntuforums.org/showthread.php?t=1748245&highlight=BCM4312+driver&page=3](http://ubuntuforums.org/showthread.php?t=1748245&highlight=BCM4312+driver&page=3)

Refer to post #30. Hope this helps.
i have  a intel pro wireless 3945abg card but thanks anyways

---

### Post by geojorg on 2011-07-31
I have the same issue, can you point me to a bug report ?

---

### Post by northd_tech on 2011-08-26
> **cpatrick08 said:**
> did not work said bad password when password was correct
Apparently there is a conflict between Wicd & [Gnome] Network Manager under Ubuntu 10.xx (and likely 11.xx) that throws "Bad Password" errors (and precious little else other than the fact that you **cannot** connect to wireless routers).  You might have some NM packages that don't like some Wicd packages that are still installed on your system.

It sounded to me like you are communicating with the wireless router (up until the WPA/WPA2, etc. authentication phase).  You might want to look at post #5 on this thread:

[http://ubuntuforums.org/showthread.php?p=11190843#post11190843](http://ubuntuforums.org/showthread.php?p=11190843#post11190843)

---

### Post by 3zoz on 2011-09-28
Hi guys

i tried to install wireless driver i couldn't any ideas ?

when i tried  iwconfig this the result :

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
and when i tried this iwlist wlan0 scanning:
wlan0     No scan results

---

### Post by cariboo on 2011-09-28
> **3zoz said:**
> Hi guys

i tried to install wireless driver i couldn't any ideas ?

when i tried  iwconfig this the result :

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
and when i tried this iwlist wlan0 scanning:
wlan0     No scan results

What wireless device does your system have? Could you paste the output of:

```
lspci
```

in your next post.

---

### Post by OpSecShellshock on 2011-09-28
Something kind of similar, though not precisely the same, happened to my 11.10 system just a bit ago. I did my updates for the day, but stupidly didn't make a note of whether or not any network related updates were applied.

Then when I restarted, I was unable to connect to my AP. I tried to go into the network manager and disable wireless, then I figured I'd re-enable it. When I went to do so, however, the option to enable was not available. I restarted again, and this time wlan0 didn't even show up in my network interfaces. That's pretty much where I am at the moment.

I just checked for updates again, and there is a network-manager update which I've installed. I'm restarting now and will see what happens.

EDIT: OK, this is odd. Now the network manager in the panel says I'm disconnected and that there are no network interfaces available, but ifconfig output shows me connected, and I am able to access the web just fine. Still no sign of my wireless interface.

---

### Post by OpSecShellshock on 2011-09-28
Well it turns out that my specific problem was that the wireless interface had somehow been disabled in the BIOS. Always the last place you look I guess. Everything's in working order now.

---

### Post by | MM | on 2011-09-28
hi opengl_cpp,

This bug could be worth keeping an eye on:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677)

For me the broadcom wireless drivers available in the main repo have not worked since 11.04. 

If we are experiencing the same issue, the bug is known and experienced by many as it is common driver/hardware combo.  The workaround is to use either natty or maverick packages of the same driver, see bug comments for links.


Cheers
Matt

---

### Post by 3zoz on 2011-10-05
> **cariboo907 said:**
> What wireless device does your system have? Could you paste the output of:

```
lspci
```in your next post.

Dear this what it's shows 

The program 'lscp' is currently not installed.  You can install it by typing:
sudo apt-get install nilfs-tools
--------------------------
after i tried to install it it shows this


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nilfs-tools

---

### Post by cariboo on 2011-10-05
> **3zoz said:**
> Dear this what it's shows 

The program 'lscp' is currently not installed.  You can install it by typing:
sudo apt-get install nilfs-tools
--------------------------
after i tried to install it it shows this


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nilfs-tools

You have a typo, the command is:

```
lspci
```

just copy it and paste it in a terminal, and press enter.

---

### Post by 3zoz on 2011-10-05
> **cariboo907 said:**
> You have a typo, the command is:

```
lspci
```just copy it and paste it in a terminal, and press enter.


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation WiFi Link 5100
04:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
04:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
04:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
04:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
azbdulaziz@azbdulaziz-Satellite-A300:~$ 

any idea?

---

