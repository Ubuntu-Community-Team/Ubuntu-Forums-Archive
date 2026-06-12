---
title: "correct PCI insertion for wifi?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by scholzilla on 2008-05-10
I'm running Hardy Heron on a gateway laptop (64bit) that uses the RTL8187B chipset, which is on the list of supported chipsets. To troubleshoot my lack of wifi connectivity, I followed the [instructions here]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html"), which state:
-----------
Open Device Manager (System &#8594; Preferences &#8594; Hardware Information).

Check to see [if] the hardware is recognised [,and] if it is then [go to] the section called “Check for driver”

If your device is not displayed then there may be a hardware problem. Ensure if it is PCMCIA or PCI that it is inserted correctly.
-----------
(Note: there is no such option as System &#8594; Preferences &#8594; Hardware Information; better to use alt+F2 and show the list of known applications). 

Unfortunately, my device is not displayed. Since this is a laptop, I really don't know how to check if my PCI is inserted correctly. I should also note that I successfully used ndiswrapper to install the correct driver, yet I can't see any APs (and yes, there are many available where I am). I used to get wifi--albeit with frequent droppages--before I upgraded to hardy, so i'm not entirely convinced that my device is incorrectly inserted.

If this issue isn't easily addressed, can someone suggest a good hardy-compatible external device I can buy for wifi?

thanks

---

### Post by inportb on 2008-05-10
What does lspci say?

---

### Post by Journeyman on 2008-05-10
You won't have any PCI slots since it is a laptop, it is just a general message, to make sure you installed your card correctly, but I am assuming it is an internal card, which means it is a driver/configuration problem. do you remember what kind of WIFI card it is?

---

### Post by scholzilla on 2008-05-10
Thanks. <lspci> lists a load of devices. I can't reproduce the list here (I don't have connectivity with the laptop and dont have a flash drive or CD to port the output to the computer I'm using). I can tell you that there is an ethernet controller listed, but I see no wireless controller or mention of realtek.

---

### Post by scholzilla on 2008-05-10
Yeah, it's internal: RTL8187B chipset, which is on the list of supported chipsets. I used ndiswrapper to first uninstall the existing drivers and reinstall the recommended win98 driver, net8187b. The .inf and .sys files are in the same folder as they should be. <ndiswrapper -l> gives me:

matt@Darwin:~$ ndiswrapper -l
net8187b : driver installed
device (0BDA:8187) present (alternate driver: rtl8187)

I've tried removing the alternate driver by editing /etc/modprobe.d/blacklist file, but it still appears as the alternate when I query <ndiswrapper -l>, even after restart.

Furthermore when I do:

sudo depmod -a
sudo modprobe ndiswrapper
dmesg | more

the result is a lot of crap, including many lines of output that say "ndiswrapper (import:242): unknown symbol: blablabla" followed by messages that say:
------
ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8187b'
ndiswrapper (load_sys_files:112): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
usbcore: registered new interface driver ndiswrapper
lp: driver loaded but no devices found
-------

---

### Post by Journeyman on 2008-05-10
Take a look at [this]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/configuring-a-rtl8187b-wireless-card-on-a-toshiba-satellite-a215-s5802-in-ubuntu-7.10-631453/") maybe it will help.  Also I guess there have been some issues with people getting the wrong driver, make sure you get it from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B")

---

### Post by game_plan on 2008-05-24
Your lspci wont show anything since its an internal usb card (use lsusb). And you can use the driver from any OEM website or Realtek directly as long as the modified line listed in the previous link is present. And only the Windows 98 driver works in 32bit version.

If you find a way to get the 64bit version to work PLEASE let me know, I've worked on this for a very long time.

---

### Post by scholzilla on 2008-05-25
Sorry, game_plan, I've basically given up on trying to get the internal wireless to work. I bought a netgear card (bad choice) that I'm now having problems with. I'm probably going to return it for something else.

---

