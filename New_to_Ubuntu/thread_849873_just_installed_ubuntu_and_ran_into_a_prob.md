---
title: "just installed ubuntu and ran into a prob"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by vistasucksss on 2008-07-04
hey all. just want to say hi and thank you all for reading. 

i just dual-booted ubuntu and vista on my hp dv6839cl. just want to know if anyone can help me with setting up the wifi card built into my system. if you need more information about my laptop please let me know although i am not sure how to navigate this OS yet. 

thanks again,
chris

ps if there are any other things i should know please feel free to advise me!

thanks 10x

---

### Post by PinkFloyd102489 on 2008-07-04
Open a terminal by going to Applications > Accesories > Terminal. Type in lspci and hit Enter. It'll spit out some text. Copy that text here.

---

### Post by vistasucksss on 2008-07-04
PINK - thanks for the quick reply...


chris@Cali-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
chris@Cali-PC:~$

---

### Post by PinkFloyd102489 on 2008-07-04
Unfortunately, this isnt going to be noob friendly. You need to install the wireless drivers using ndiswrapper. Wireless support for Ubuntu at the moment is very lackluster, so good luck.

[http://ubuntuforums.org/showthread.php?t=185174&highlight=BCM4310](http://ubuntuforums.org/showthread.php?t=185174&highlight=BCM4310)

---

### Post by tamoneya on 2008-07-04
your wifi card is a BCM4310.  Take a look at this thread as well as the ones it references: [http://ubuntuforums.org/showthread.php?t=830188](http://ubuntuforums.org/showthread.php?t=830188).  If you run into some errors post back here and include what you tried and where it failed.

---

### Post by vistasucksss on 2008-07-05
hey pink and tamoneya.. thanks for the quick reply

im a noob but im a quick learner and follow directions well!! but thanks for the replies.. ill post back with my results.. thanks again.

---

### Post by vistasucksss on 2008-07-05
pink the guide you gave me is talking about dapper.... is this ok?? i am using hardy... lol damn i guess i am a nooob

---

### Post by PinkFloyd102489 on 2008-07-05
It should be ok.

---

### Post by Tatty on 2008-07-05
The Dapper guide should give you a good overview of what you are dealing with.  But before you do anything, just check in System->Administration->Hardware Drivers to see if there are drivers in there you can enable.

If not, then this page should help get you through using ndiswrapper [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by vistasucksss on 2008-07-05
hey tatty thanks for that info. i just checked the hardware drivers and there is only one titled "wl" and it says its enabled but not in use? i installed a few new things in the 'add/remove' programs window and found 'wireless network drivers' and installed that. now it is asking for the 'inf' file... am i doing the right thing? is this ndisweeper that everyone is referring to or is that something else?

---

### Post by GuitarRocker2562 on 2008-07-05
that would b it, now you have to find the windows driver for your wireless card and select the .inf

---

### Post by vistasucksss on 2008-07-05
hey everyone really appreciate the support...

been trying for a while now i cant seem to find any inf file for this model... can anyone help me? maybe give me a torch helmet like the frog prince gave to lemmiwinks??? ;) thanks again...

is it located in the .exe file on hp's website? and if so how would i open that?? 

much appreciated...
chris

---

### Post by vistasucksss on 2008-07-05
hope that question wasnt beyond noob... thanks again in advance.. just not sure how to get the drivers to work and what i should be doing... :confused:

---

### Post by vistasucksss on 2008-07-05
also does this do anything for anyone??


chris@Cali-PC:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:3b:58:f3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.4 latency=0 module=r8169 multicast=yes
chris@Cali-PC:~$

---

### Post by kornhead127 on 2008-07-05
Looks like you can download the .INF file that you need from here [http://www.fjall.org/d505/wlan/bcmwl5.inf](http://www.fjall.org/d505/wlan/bcmwl5.inf)

---

### Post by vistasucksss on 2008-07-05
thanks alot man i really appreciate the reply...


now.. what do i do with this? do i copy/paste it??

---

### Post by kornhead127 on 2008-07-05
You can right click the link and click 'Save Link As'. Save it to your home folder or desktop.

---

### Post by vistasucksss on 2008-07-05
ok i just right clicked on the page.. saved it on desktop.. and tried to install it with the wireless network driver utility.... and now it is saying invalid driver

---

### Post by kornhead127 on 2008-07-05
Give this page a try [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)

For step 2 your choice would be step 2e because of this line.
```
02:00.0 Network controller: Broadcom Corporation **BCM4310** USB Controller **(rev 01)**
```

---

### Post by vistasucksss on 2008-07-05
k ill give it a try. thanks again

---

### Post by vistasucksss on 2008-07-05
damn i really dont know what im doing.... 

chris@Cali-PC:~$ 
chris@Cali-PC:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
chris@Cali-PC:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@Cali-PC:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
mkdir: cannot create directory `/home/chris/bcm43xx': File exists
chris@Cali-PC:~/bcm43xx$ wget [http://myspamb8.googlepages.com/R174291-pruned.zip](http://myspamb8.googlepages.com/R174291-pruned.zip)
--04:37:11--  [http://myspamb8.googlepages.com/R174291-pruned.zip](http://myspamb8.googlepages.com/R174291-pruned.zip)
           => `R174291-pruned.zip'
Resolving myspamb8.googlepages.com... 209.85.173.118
Connecting to myspamb8.googlepages.com|209.85.173.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,155,991 (1.1M) [application/octet-stream]

100%[====================================>] 1,155,991     53.79K/s    ETA 00:00

04:37:34 (50.12 KB/s) - `R174291-pruned.zip' saved [1155991/1155991]

chris@Cali-PC:~/bcm43xx$ unzip R174291-pruned.zip
Archive:  R174291-pruned.zip
  inflating: bcmwl564.sys            
  inflating: bcmwl5.sys              
  inflating: bcmwl5.inf              
  inflating: bcm43xx64.cat           
  inflating: bcm43xx.cat             
chris@Cali-PC:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
chris@Cali-PC:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4315) present (alternate driver: wl)
chris@Cali-PC:~/bcm43xx$ sudo depmod -a
chris@Cali-PC:~/bcm43xx$ sudo modprobe ndiswrapper
chris@Cali-PC:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
chris@Cali-PC:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

chris@Cali-PC:~/bcm43xx$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

chris@Cali-PC:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
chris@Cali-PC:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
chris@Cali-PC:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:3b:58:f3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.4 latency=0 module=r8169 multicast=yes
chris@Cali-PC:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:3b:58:f3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.4 latency=0 module=r8169 multicast=yes
chris@Cali-PC:~/bcm43xx$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
chris@Cali-PC:~/bcm43xx$ chris@Cali-PC:
bash: chris@Cali-PC:: command not found
chris@Cali-PC:~/bcm43xx$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
chris@Cali-PC:~/bcm43xx$ echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
#Hardy ssb/ndiswrapper workaround, added Sat Jul 5 04:44:01 EDT 2008 
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
chris@Cali-PC:~/bcm43xx$

---

### Post by vistasucksss on 2008-07-05
woo hoo!!!! just want to thank everyone who helped me out with this issue. finally got wifi to work! i guess i had to restart my computer and it was right there waiting to be used!!! tip for other noobs: make sure the wifi switch is ON! haha thanks again everyone....

---

