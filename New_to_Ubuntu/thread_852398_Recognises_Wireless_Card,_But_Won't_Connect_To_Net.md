---
title: "Recognises Wireless Card, But Won't Connect To Network"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Jack Bonner on 2008-07-07
Basically the title speaks for itself, I have just installed Kubuntu onto my laptop (previously running Windows Vista) and even though it recognises that my wireless card is there and working, it won't connect to my network.
I'm sorry if you've heard this before, I hear that problems with the Broadcom wireless cards are common. I've double checked my password is correct and it is. I'm running Kubuntu 8.04 on a HP Compaq 6720s laptop

Thanks in advance for any help

---

### Post by Het Irv on 2008-07-07
I have that same laptop, but I think my card is an Intel.... can you paste the output of ```
lspci
```

I did not have to do anything to get my laptop to work under Hardy (Ubuntu).

---

### Post by sujoy on 2008-07-07
mine is also a Broadcom Corporation BCM94311MCG wlan mini-PCI, and only wicd seems to work with it properly. so try it out.

---

### Post by Jack Bonner on 2008-07-07
This is what I got from the lspci


00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

---

### Post by Het Irv on 2008-07-07
Restricted Drivers are installed correctly?

---

### Post by Jack Bonner on 2008-07-07
I believe so, that was the first thing I did after installing the actual OS. Under System Settings > Network Settings I have a tick next to my wireless card so i'm assuming it's working

---

### Post by Het Irv on 2008-07-07
And you can see your wireless AP, but it will not connect?
Do you have good signal strength?
Have you tried a manual connection?

---

### Post by Jack Bonner on 2008-07-07
> **Het Irv said:**
> And you can see your wireless AP, but it will not connect?
Do you have good signal strength?
Have you tried a manual connection?

I can see my wireless network and it has a signal strength of 78. Signal isn't really a problem as i'm sat next to the router. I did try manual connection and it just came out with the same results as when I did it automatically. It attempted to connect, got to 23% then failed.

---

### Post by Het Irv on 2008-07-07
I had this problem once, but it was a conflict between the Nvidia and Broadcom drivers, and that doesn't affect you.  I'm gonna call in some backup on this one.

Note: I have had luck using WICD in the past, sometimes it works better than the default Network Manager.

---

### Post by Jack Bonner on 2008-07-07
> **Het Irv said:**
> Note: I have had luck using WICD in the past, sometimes it works better than the default Network Manager.

What exactly is WICD and where can I install it? I couldn't find it in the package manager. As i'm sure you can see, i'm a little new to the whole Linux game

---

### Post by Het Irv on 2008-07-07
WICD is a alternate network manager that sometimes will work when the default cannot.  
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

What type of security are you using?

I have been told that if you are using WPA you have to check the ACII box.
Note: I don't run KDE so I am not sure where everything is or what you are looking at.

---

### Post by Jack Bonner on 2008-07-07
> **Het Irv said:**
> What type of security are you using?

I'm using WPA Personal security, but I don't see any ACII box to tick, I'm going to try using WICD and see if I can make any progress with that

---

### Post by ibuclaw on 2008-07-07
I believe he means **ASCII** ;)

If you still get no luck from WICD, I've used a version of KDE with wlassistant on. And that worked mighty fine to connect to my router. (I use WPA2).

Copy this line, and paste it into a terminal using "**Ctrl+Shift+V**"
```
sudo apt-get install wlassistant
```
Then search for it in the KDE menu and run.

Regards
Iain

---

### Post by Jack Bonner on 2008-07-07
> **tinivole said:**
> I believe he means **ASCII** ;)

If you still get no luck from WICD, I've used a version of KDE with wlassistant on. And that worked mighty fine to connect to my router. (I use WPA2).

Copy this line, and paste it into a terminal using "**Ctrl+Shift+V**"
```
sudo apt-get install wlassistant
```
Then search for it in the KDE menu and run.

Regards
Iain

Still nothing i'm afraid, I just get connection failed. Although I find that program easier to use than the standard one

---

### Post by ajmorris on 2008-07-08
hi there,
can you please post the output of sudo iwconfig
sudo iwlist scanning

and also, have you tried ndiswrapper instead of the native linux drivers?

AJ

---

### Post by chetan.89 on 2008-07-08
Try connecting through System-->Help and support.

If that doesn't work, check out this article --> [http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958)

I hope it helps you (worked in my case)
Good luck ! :)

---

### Post by Jack Bonner on 2008-07-08
> **ajmorris said:**
> hi there,
can you please post the output of sudo iwconfig
sudo iwlist scanning

and also, have you tried ndiswrapper instead of the native linux drivers?

AJ

Here's the sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



and here's the sudo iwlist scanning


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:2A:12:74:2C
                    ESSID:"Bonner"
                    Mode:Master
                    Channel:12
                    Frequency:2.467 GHz
                    Quality=76/100  Signal level=-61 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003d1d7bc234

---

### Post by ddrichardson on 2008-10-24
Not being associated could be a number of things but the driver being for a slightly different firmware revision would seem the most likely candidate - does this system work fine in Windows?

If you have the Windows driver, try NDISWRAPPER, this chipset is problematic. I have one on an HP that will not play ball and another on a generic laptop that connects without problem.

---

