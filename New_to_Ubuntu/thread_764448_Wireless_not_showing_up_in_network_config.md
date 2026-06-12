---
title: "Wireless not showing up in network config"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Berzerker55 on 2008-04-23
Ok so i just got a laptop compaq presario C751NR, first thing i did was put ubuntu onto it, but when i try to connect to my wireless internet it doesnt show anything, only options for wired and modem connection.

I know the wireless internet card is/was working because i downloaded ubuntu onto the computer and burned it to a cd before installing.

any ideas?

---

### Post by nicedude on 2008-04-23
Hey berzerker wifi problems are really common and sometimes tricky to figure out how to fix. Good news is once you figure out what to do most can be made to work well. The people here will try to help you out but you should post what wifi chipset your laptop uses. also in that post put the results of the following commands, as this will help me or anyone else here try to help you.

lspci

iwconfig

---

### Post by Berzerker55 on 2008-04-24
sorry to bump, i cant find this post on my other computer >_>

---

### Post by Berzerker55 on 2008-04-24
Wireless card =

Atheros Communications, Inc. AR5006EG 802.11 b/g wireless PCI Express Adapter.

lspci is a lengthy text =

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



iwconfig = 

lo        no wireless extensions.

eth0      no wireless extensions.


sorry about all the text, just telling you eveything i got when i put it in.

---

### Post by subzero316 on 2008-04-24
Hey check this thread [<----Link---->]("http://ubuntuforums.org/showthread.php?t=512828")..
 It will guide u step by step.
Also make sure that you downlad the latest ndiswrapper u can go visit [http://sourceforge.net/project/showfiles.php?group_id=93482]("http://sourceforge.net/project/showfiles.php?group_id=93482")

also u can google n get your windows driver then follow the rest of the steps.

---

### Post by nicedude on 2008-04-24
you need ndisgtk you can get it by copying & paste the following in a terminal window command line and then pressing enter

sudo apt-get install ndisgtk

Download XP drivers for your laptops wifi

Extract them with right click and just look towords bottom you should see 
extact here option thats fine and it should make a folder on your desktop with the drivers in it.

Run ndisgtk ( press alt + F2 then when window pops up check the box runinterminal and paste name ndisgtk click run) , when ndis opens click install & go to the directory of the extracted drivers 

Click the .inf & install, then close ndisgtk.

Give it about 10 secs and you should see networks in the network manager.

To make it boot on startup you have to add it to a config text file here is a command to open it in a text editor so paste command in terminal & hit enter

sudo gedit /etc/modules

Add "ndiswrapper" (without the quotes) to the bottom of the file and save. 

now reboot 

You should be all good now.

---

