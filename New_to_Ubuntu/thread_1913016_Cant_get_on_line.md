---
title: "Cant get on line"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by desgnr on 2012-01-21
I am trying to run Ubuntu on a USB flash drive on my Dell Mini 9 Laptop.
I get it to load but Wireless connection is greyed out.
I can't get on line.
When  i load Windows XP i get my wireless connection.
How do i get online ?

---

### Post by Double.J on 2012-01-21
Hi there!

You most likely have a broadcom card...

connect the netbook to the router via a cable, check to see if the driver is listed in additional drivers (press windows key, type additional drivers and enter)


If not, look up what package you need from [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") and download it in the software centre (the logo on the left that looks like a shopping bag - search for broadcom.

You'll probably have to restart to take effect ;)

Hope it helps :)

---

### Post by anewguy on 2012-01-21
While it may end up being a Broadcom card, it doesn't mean it has to be just because the wireless doesn't work.

Please open a terminal window, type in the following, copy the outputs and post back here:

lspci

lsusb

lshw -C network

ifconfig

iwconfig

This will give us more information to go on, including the true manufacturer and chipset used in the wireless adapter.

Dave ;)

---

### Post by Double.J on 2012-01-22
Good catch anewguy! I made an assumption based on the laptop model :oops: 

Hope you're now online desgnr :)

---

### Post by desgnr on 2012-01-22
Since i am new to this system what is a Terminal window where i can type what you want ?:popcorn:

---

### Post by Soulcage on 2012-01-22
press ctrl alt t to open the terminal.

---

### Post by Nick_Kats on 2012-01-22
> **desgnr said:**
> Since i am new to this system what is a Terminal window where i can type what you want ?:popcorn:

In the dash home (or if you are using a previous Ubuntu version, it is under the Applications tab), search for Terminal and open it. Terminal is a console window, where you can type in Unix-like commands.

There just execute (and by execute i mean type each command and then press enter) the commands (one after the other) that anewguy posted.

When you do, Copy all the output and post it here.

I hope I helped you :D

---

### Post by desgnr on 2012-01-22
This is wild.
I found a way to activate a Broadcom driver & it showed my Network,BUT i still couldn't get online with Firefox.
I tried rebooting & when it reloaded my network was missing again.
I did what you sugested to type in the terminal & pasted it to a document but i have no way of printing it or emailing it without an internet connection.
Otherwise i am stuck.
I can't figure why Firefox would not go online.

---

### Post by anewguy on 2012-01-22
We'll need you to do the following, which will create a file of the outputs which you can then copy to a USB stick and take to the PC you are posting from.  Please be aware that only the first statement has a single ">" - all the rest have 2.

echo "** lspci **" > dwetest.txt

lspci >> dwetest.txt

echo "** lsusb **" >> dwetest.txt

lsusb >> dwetest.txt

echo "** lshw -C network" >> dwetest.txt

lshw -C network >> dwetest.txt

echo "** ifconfig **" >> dwetest.txt

ifconfig >> dwetest.txt

echo "** iwconfig **" >> dwetest.txt

iwconfig >> dwetest.txt

Use the file explorer and copy the file dwetest.txt to a USB stick.

Take the USB stick to the computer you are posting from and attach the file dwetest.txt from that USB stick to a reply here.


Dave ;)

---

### Post by desgnr on 2012-01-22
Do i use all the " "  >that you show & do i hit enter after each one ?
How do i save the file on Unbuntu

---

### Post by SuaSwe on 2012-01-22
Hi desgnr,

The steps described by anewguy will create the file - just copy-paste exactly what he's written. :)

To explain a bit, let's say I open a Terminal window and do this:

```

suaswe@lxpc~$ pwd
/home/suaswe
suaswe@lxpc~$ iwconfig > dwetest.txt
suaswe@lxpc~$ lspci >> dwetest.txt

```

The first command, 'pwd', will tell me where the file will be created (in this case in my home directory), which will allow me to find it using the file browser later, usually accessed via Places => Home - using this you can transfer the file from the directory to your USB stick just as you would on Windows.

The second line runs the command 'iwconfig' and as a result of the > symbol *creates* the file dwetest.txt, inserting the output of the command into it. The third line, via the >> symbol, *appends* the output of the command 'lspci' to the same file. 

Essentially, the > symbol followed by a filename will create a new file if none exists with that name, and overwrite the existing file if one does; the >> symbol followed by a filename will append the output of whatever command you're running to the end of that file if it exists, or create a new file with that name if none does.

---

### Post by desgnr on 2012-01-23
Here is the file.



** lspci **
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```
** lsusb **
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13fe:3e00 Kingston Technology Company Inc. 
```
```
** lshw -C network
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:48:ed:ad
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.100.82.38 ip=192.168.1.114 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:d5:98:e8
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0610000-f0610fff memory:f0600000-f060ffff memory:f0620000-f063ffff
```
```
** ifconfig **
eth0      Link encap:Ethernet  HWaddr 00:21:70:d5:98:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:23:08:48:ed:ad  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8ff:fe48:edad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3721 errors:0 dropped:0 overruns:0 frame:18233
          TX packets:2904 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4654226 (4.6 MB)  TX bytes:420458 (420.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16224 (16.2 KB)  TX bytes:16224 (16.2 KB)

** iwconfig **
```

---

### Post by anewguy on 2012-01-23
Indeed, it's a Broadcom 4312 - it says it's currently using the wl1 driver, however things don't look right.

If possible, hard-wire your PC to the router and do the following:

- open a terminal window

- type:

sudo apt-get update <press enter>

sudo apt-get upgrade <press enter>

- close the terminal window

Go to Additional (might say Restricted) drivers.  It should take a while for it to check your PC and check the net for a driver that would work.  It should eventually come back showing a driver which you then need to enable.

Disconnect the hard-wire.

Now check in network manager and see if wireless networks show.  If so, try testing them.

Dave ;)

BTW - I'm also going to have a user who is better at the communications stuff take a look at this thread - they may other suggestions for you!

---

### Post by desgnr on 2012-01-23
Thanks for all the help.
What is wrong because i can get online.

Is there any good reason why i should use Ubuntu ?

The only thing i don't like is i can't use Quicken.

---

### Post by varunendra on 2012-01-24
> **desgnr said:**
> 
Is there any good reason why i should use Ubuntu ?
It's entirely a matter of choice which is upto you to make. None of us was invited to use linux, none of us is forced to stay either. If we wish to leave, we can do so anytime. If we leave now and comeback later - we'd be welcomed again!

So you see, it's entirely dependent upon one's specific needs and preferences why or why shouldn't he/she use Linux (Ubuntu, or any other linux-based OS). Some of the main reasons why I personally prefer it -

[LIST=1]
[*]It's free (free in price, free to use, free to change/modify, free to distribute)
[*]It's virus-free
[*]It's restrictions-free
[*]It's faster
[*]It's safer
[*]It's much-much more customizable to "My" needs
[*]It's looks and feel and ease of use can be awesome, once setup properly
[*]It's DIFFERENT! (the way of working - more comfortable for me)
[/LIST]
Some of the reasons why you may hate it:

[LIST=1]
[*]It's DIFFERENT! (the way of working - may not be comfortable for beginners, especially those who switch from windows)
[*]It may be tricky to setup if the drivers didn't work out-of-box
[*]It maybe unstable if you don't stick with defaults and blindly follow others' suggestions without knowing what you are doing (in short - it requires some learning experience to stay happy with it)
[*]**And the most bitter fact -** less chance of working out-of-box with any latest hardware which has just been launched, and is radically different from its predecessors.
[/LIST]
In any case, we can always ask questions and will get answers when and if available. So if we have the will to figure out ways to find the better than what we already have, Linux (which is not limited to ubuntu) is always much more open, offering, helping and welcoming than any other OS out there.


But if we just want to be comfortable and don't have time to learn new things, we should stick with what 'just works' for us and should be ready to accept any and all of the problems that come with it.


That said, I would repeat that I feel myself more comfortable with Linux, and I'm sure there would be many others as well who are just normal users, not computer geeks, who are comfortable with it. Another thing I'd like to add - I used to be a windows-only user, and am still using it for my specific needs. There's nothing wrong with using multiple OSes if you like or need so, or dump one totally if it doesn't work for you.




**[s]Now onto the problem you originally posted for-[/s]**[s]
Your wireless adapter (BCM4312) is well supported in linux, and from the outputs you posted, it seems it is working now as the correct driver is loaded and it has got the IP address (**192.168.1.114**). If you are still having any problems with it, please post the details of the problems and we may be able to figure out the culprit.[/s] [COLOR=Red]Confused ethernet with wireless :oops:! Please disregard and follow what *lkraemer *suggested below.[/COLOR]

---

### Post by lkraemer on 2012-01-25
desgnr,
Your quote of: > The only thing i don't like is i can't use Quicken. isn't true.
I run Quicken 2004 on Debian 6.0 "SQUEEZE", Ubuntu 8.04 LTS, and Ubuntu 10.04 LTS by
downloading and installing Crossover by Codeweavers.  It is good software
that is worth the purchase price.  Quicken was the ONLY software besides
TurboCAD 7.1 (& Ver 10.0) that was preventing me from giving up Win XP.
Now those days are past...................

[http://www.codeweavers.com/](http://www.codeweavers.com/)


As for your Broadcom Issue:
We need a bit more detail on what modules are loaded by default and if you
have previously tried to use any of the Windows Drivers. Please copy and
paste the following commands into a Terminal Window (Console) ONE at a TIME,
so we have that information.  Post the output of each command.
```
 
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
ls -alt /lib/firmware/*.fw
ls -alt /lib/firmware/b43legacy/*.fw

```

Your Firmware is likely missing.  You will need to have an Ethernet Connection
and ENABLE the Driver, or if you don't have an Ethernet Connection, you can just
download the firmware, then copy the Firmware to the proper folders.

Download the Firmware files located at:
[http://www.omattos.com/node/6](http://www.omattos.com/node/6)
to a USB Flash Drive and copy them to your Desktop, and Extract.
You should have two folders b43 & b43legacy. You will be copying
these folders to /lib/firmware/b43 and /lib/firmware/b43legacy

Here are the commands I used on my old Compaq V5201US, running the
10.04 LiveCD to get it working: (Open a Terminal Window)
```

cd /
cd /lib
cd firmware
pwd
ls
sudo cp -r /home/loginname/Desktop/b43* .
cd b43
ls -alt *.fw
cd ..
cd b43legacy
ls -alt *.fw
exit

```
Now you just have to Enable the Broadcom Driver:
SYSTEM -> ADMINISTRATION ->HARDWARE DRIVERS
should have a Broadcom Driver listed a driver listed for your wireless,
if so enable it. (If by chance you have already ENABLED it, go ahead
and let it try to uninstall, then install it again by clicking again.
It should find the drivers and load them, because the Firmware is where
it needs to be.

Check Network Manager (right click on the icon) to be sure the "Enable Wireless"
box is checked (It should be ENABLED already by default.)

Check to see if you have wireless now. If not, you might need to
check the Loaded Modules, making sure there are no conflicts with other
Wifi drivers that might have been loaded, or others that cause conflicts.
```

lsmod

```
Post the output of lsmod.

You can check for errors with:
```

dmesg | tail

```
You may have to remove other modules depending on what lsmod shows:.... ..
What you will REMOVE depends on what you post as output from your commands.

If lsmod shows module bcm43xx and other conflicts installed you will
need to blacklist them.

For now take a few steps and post the output you are getting.

LK

---

### Post by anewguy on 2012-01-25
Thanks much for coming by to help out LK.  I really appreciate it!

Dave ;)

---

