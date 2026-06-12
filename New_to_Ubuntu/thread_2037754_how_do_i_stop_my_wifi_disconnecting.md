---
title: "how do i stop my wifi disconnecting?"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by mick_86 on 2012-08-05
i have just installed 12.04 and when i leave my laptop running for any length of time it goes into suspend mode and disconnects from the wifi. when i unlock the screen it trys to reconnect continuesly but doesn't. the only way i can reconnect is by restarting the laptop.

i like to leave my laptop running overnight to download stuff while i sleep, but at the moment its getting about 10 mins of downloading time before it disconnects!

any ideas how i can resolve this problem.

thanks in advance!

---

### Post by levlaz on 2012-08-05
What type of wifi card do you have specifically? 

If it is an internal wireless card please open a terminal and type 

```
 lspci 
```

If it a USB card please open a terminal and type 

```
 lsusb 
``` 

then post the output here.

---

### Post by mick_86 on 2012-08-05
> **levlaz said:**
> What type of wifi card do you have specifically? 

If it is an internal wireless card please open a terminal and type 

```
 lspci 
```

If it a USB card please open a terminal and type 

```
 lsusb 
``` 

then post the output here.


```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

when i had 10.10 installed there was no issues!

---

### Post by Dylan1473 on 2012-08-05
It recognizes your card, at least. Sounds as though you might need some proprietary drivers for that card, though it's odd it would work in earlier versions of Ubuntu. I'm looking into it, I'll edit/post back in a bit. You need rtl8191se drivers, I'm just going to look up how to properly install them. I'm finding a bunch of results from like a year ago...I wonder if this is even still applicable?

Wait, in 10.10 did you maybe have an option to install some kind of "Ubuntu restricted extras" that you took and didn't do this time?

---

### Post by mick_86 on 2012-08-05
> **Dylan1473 said:**
> 
Wait, in 10.10 did you maybe have an option to install some kind of "Ubuntu restricted extras" that you took and didn't do this time?

i did take that option. when i'm using the laptop and stay logged in the wifi stays connected no problems, the problem only appears when the laptop goes into suspend mode.

---

### Post by Dylan1473 on 2012-08-05
Okay, _[this guide]("http://michael-peeters.blogspot.ca/2011/10/fixing-rtl8191se-wifi-under-ubuntu-1110.html")_ looks promising. You might need to install some kernel headers but hopefully not.

A quick explanation:

1. [Download the drivers from here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE")
2. Extract those files somewhere
3. Enter the following into your terminal:
```
sudo -i
cd [PATH TO THE DIRECTORY WHERE YOU EXTRACTED THE FILES]
make
make install
modprobe rtl8192se
exit
```4. Edit the modules file so this is loaded every time on startup  (you can later remove this if it doesn't help and you want it to stop).  To edit the file, enter this into your terminal:
```
gksudo gedit /etc/modules
```and add rtl8192se to the file.

If it's a driver issue that should fix it. Otherwise I'm out of ideas. Keep the source package around in case it doesn't work and you want to uninstall afterwards (that could be ugly if, like most source packages, it doesn't technically include an uninstall option).

---

### Post by Hadaka on 2012-08-05
Hi, your computer is going into suspend mode because of lack of
keyboard or mouse activity. To prevent this, click the SYSTEM SETTINGS
icon,..wrench and cogged gear in the launcher. Then click POWER SETTINGS
icon of battery and power cord. In the power settings box...choose ..DON"T SUSPEND.
in the Suspend when inactive for....box
This should keep things running all night for you.
good luck

---

### Post by mick_86 on 2012-08-05
> **Hadaka said:**
> Hi, your computer is going into suspend mode because of lack of
keyboard or mouse activity. To prevent this, click the SYSTEM SETTINGS
icon,..wrench and cogged gear in the launcher. Then click POWER SETTINGS
icon of battery and power cord. In the power settings box...choose ..DON"T SUSPEND.
in the Suspend when inactive for....box
This should keep things running all night for you.
good luck

[IMG]http://img193.imageshack.us/img193/3506/screenshotfrom201208051.png[/IMG]
By [raum86](http://profile.imageshack.us/user/raum86) at 2012-08-05

already had these settings in place.

---

### Post by Hadaka on 2012-08-05
ok..I also forgot to mention to check the settings under SYSTEM SETTINGS
BRIGHTNESS AND LOCK...sorry about that..thats where the request for a 
password on timeout is .
that should do it for you.
good luck

---

### Post by wildmanne39 on 2012-08-05
Hi,
 Download the zipped wireless script file then:
 Open a terminal using ctrl+alt+t then copy and paste each command online at a time.
 cd ~/Downloads
 chmod +x netscript.sh
 ./netscript.sh
 then reply back,  and attach the netinfo.txt file.

The script removes the MAC Address, WPA and WEP keys.
Thanks

---

