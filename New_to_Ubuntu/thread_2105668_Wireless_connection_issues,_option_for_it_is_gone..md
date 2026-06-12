---
title: "Wireless connection issues, option for it is gone.."
date: 2013-01-16
forum: New to Ubuntu
---

### Post by FruitPunchSamurai on 2013-01-16
I'm using Linux 12.10. I just installed today on my Lenovo G550. At first i had no issues with my Wifi, it was connected. Then(i assume cause i did the software updates and restarted) i could not connect via Wifi, but only Wired. It didn't even have any of the Wireless options anymore. So after looking at a lot of posts i decided to just reinstall. It worked, but i did the software updates again(not thinking that was what caused this), and it once again was gone when i restarted. I can reinstall, but would much rather know the cause of this. Would appreciate it very much if someone could help a noob like myself out. Thank you.

---

### Post by mad2-814 on 2013-01-16
Open a terminal and enter this into the terminal
```
sudo lspci -nn
```
then post the output back on here.

and welcome to Ubuntu!

---

### Post by FruitPunchSamurai on 2013-01-16
hmmm, i did that. This is what i got. For some reason i can't enter my password. Which i assume is my login password. the terminal is Ctrl+Alt+T, correct?

ian@Fruit-Punch-Samurai:~$ sudo lspci -nn
[sudo] password for ian:

---

### Post by FruitPunchSamurai on 2013-01-16
:mad: sorry, it not showing up confused me. Here ya go, thank you. 

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

---

### Post by FruitPunchSamurai on 2013-01-16
Sorry guys, i know there is a lot of information about this already(and ive been looking at it). I just feel i have done something to complicate things, cause everything insists the wireless/hidden wireless option is there. I think i deleted the connection by accident, but i don't understand why that option isn't in the menu anymore...:mad:

---

### Post by FruitPunchSamurai on 2013-01-16
[http://askubuntu.com/questions/76207/wireless-option-gone-from-network-center](http://askubuntu.com/questions/76207/wireless-option-gone-from-network-center)

this seems to be very similar to what i am experiencing. If you were confused by what i meant about the wireless option not being there.

---

### Post by FruitPunchSamurai on 2013-01-16
Ok, i did a fresh install of Ubuntu. It fixed my problem, and i was able to use Wifi. Then i downloaded all the software updates, then once i restarted the same thing happened(the option for wireless is gone again ext). So i assume it has something to do with that software update, cause that is basically what happened last time. Here is the results of the Terminal command after the fresh install. Would really appreciate some help, couldn't figure this out by searching other posts. 

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

---

### Post by FruitPunchSamurai on 2013-01-17
Anyone? I could really use some help with this.

---

### Post by iMac71 on 2013-01-17
since you have a Broadcom BCM4312 wireless card, it might help you to give a look to the following guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by cottfcfan on 2013-01-17
Just see if your problem is the same as mine with 12.10.
If I restart my computer, I lose wireless connection totally.
But if I shut the computer down & switch back on, wireless is fine.
Stab in the dark, but worth a try.

---

### Post by warraagal on 2013-01-17
post the output of 

```
sudo nmcli con list
```

---

### Post by FruitPunchSamurai on 2013-01-17
> **r4rounak said:**
> post the output of 

```
sudo nmcli con list
```

NAME                      UUID                                   TYPE              TIMESTAMP-REAL                    
Wired connection 1        9a41e5b8-9132-4bac-9462-3192ef9f285a   802-3-ethernet    Thu 17 Jan 2013 03:07:29 PM EST   
BP8C0                     70628488-7d6d-473c-b12a-d3458a5a8f62   802-11-wireless   Wed 16 Jan 2013 07:14:37 PM EST   



I see it says when i last was using my wireless, that was after doing a fresh install. Then i did the updates and restarted and the wireless was gone(even the option for looking for them when i left click the connection icon in the upper right). Tryed the shut down advice given by [cottfcfan]("http://ubuntuforums.org/member.php?u=763277"), didn't work. Thanks for the replys.

---

### Post by FruitPunchSamurai on 2013-01-17
@imac, these are the results i got. I couldn't figure out exactly what driver i should download from this information. I didn't want to just download random drivers, so here's what i got if anyone can help me with that. Sorry i am a total noob. 


04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)

---

### Post by iMac71 on 2013-01-17
> **FruitPunchSamurai said:**
> @imac, these are the results i got. I couldn't figure out exactly what driver i should download from this information. I didn't want to just download random drivers, so here's what i got if anyone can help me with that. Sorry i am a total noob. 


04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)since you're able to use a wired interned connection, open a Terminal window and run the following command in it:```
sudo apt-get install firmware-b43-lpphy-installer
```this should solve your trouble.

---

### Post by FruitPunchSamurai on 2013-01-17
I tryed that just now, and restarted. Unplugged the hardwire, tryed resetting my router, nothing happened. There still isn't even an option for wireless connection when i left click the connection icon. It looks like this 

[http://i.stack.imgur.com/IuFZs.png](http://i.stack.imgur.com/IuFZs.png)

I might try another fresh install, cause it worked up until i did the software updates and restarted...I have heard that you lose preformance everytime you do fresh installs on a PC, so i'm a little worried about that(don't know if it's true). Also if i can't install updates for some odd reason, that wouldn't be good. Thanks for the advice so far, hope i can get this working. Kind of a pain cause i only have a 3ft LAN and being tied down to my router is a nuisance.

---

### Post by iMac71 on 2013-01-18
before of making a new fresh installation, you might try these other commands:```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe wl
```as suggested by the [Community Help Wiki.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by warraagal on 2013-01-18
> **FruitPunchSamurai said:**
> 
NAME                      UUID                                   TYPE              TIMESTAMP-REAL                    
Wired connection 1        9a41e5b8-9132-4bac-9462-3192ef9f285a   802-3-ethernet    Thu 17 Jan 2013 03:07:29 PM EST   
BP8C0                     70628488-7d6d-473c-b12a-d3458a5a8f62   802-11-wireless   Wed 16 Jan 2013 07:14:37 PM


if nmcli is showing the existence of the connection see if this works :
```
nmcli con up id "BP8C0"
```

---

