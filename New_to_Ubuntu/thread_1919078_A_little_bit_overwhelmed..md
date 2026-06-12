---
title: "A little bit overwhelmed."
date: 2012-02-02
forum: New to Ubuntu
---

### Post by Myxoma on 2012-02-02
Greetings everybody. Cut right to the chase with the same ole same ole you guys probably hear all the time... I am TOTALLY new to linux. I've used windows my whole life and recently put together my first homebuild pc... Decided I wanted to try something different in terms of os because I was getting tired of my old system getting bogged down with spyware and being harassed by microsoft with constant updates and what have you... 

So here I am now, just installed the latest version of ubuntu (64 bit) to my new build and I just can't seem to get it connected to the internet. The goal is to set up a wired connection via ethernet cable. Plugged it in and the computer doesn't seem to be picking it up at all.

I used the ifconfig command (been writing down every new command that I've been picking up online) and all that's showing up is lo. I did more searching and read somewhere that dhcp does not come "pre-installed" (I guess that's the proper terminology) with ubuntu and all the guides I've seen have said to use the 'apt-get install dhcp3-server' command. I've realized too though that that command is useless if I'm not connected to the internet. Those instructions were also lined out for older version of ubuntu and likely don't apply with 11.10.

If the info is important:
Mobo is msi p67a-g43 and I've been using the ethernet outlet that's integrated with it. Also, I'm using my hard drive from my old computer because I had no place to back up my files... I partitioned off some space for the ubuntu os and it's all I've been using. Everything else is working fine. Just can't seem to get online for some reason.

And don't feel bad if you have to dumb it down for me... Like I said, totally new to linux and would greatly appreciate the help!:p

---

### Post by roger_1960 on 2012-02-02
Hi

Sorry if this is too basic, but have to check..

In the top right of the screen there is an icon like a fan.  If you click this, have you got "enable networking" ticked?

---

### Post by Myxoma on 2012-02-02
> **roger_1960 said:**
> Hi

Sorry if this is too basic, but have to check..

In the top right of the screen there is an icon like a fan.  If you click this, have you got "enable networking" ticked?

Yes indeed. I also disabled wifi just in case that was interfering or something (old wifi card anyway and I don't have the drivers for it).

---

### Post by Bartender on 2012-02-02
Who's your ISP provider, what're you on (DSL, fiber, satellite), are you hooked directly to the modem or a router in between?

---

### Post by Myxoma on 2012-02-02
> **Bartender said:**
> Who's your ISP provider, what're you on (DSL, fiber, satellite), are you hooked directly to the modem or a router in between?
ISP is xfinity cable internet. I'm hooked up through a router in between at the moment, but I also attempted to connect directly to the modem to no avail.

---

### Post by roger_1960 on 2012-02-02
Hi

A bit of googling found this:

[http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)

which may help.

---

### Post by wyliecoyoteuk on 2012-02-02
Hi, you don't need to install DHCP-server, but DHCP client, and that should be installed anyway by default.
If 

 sudo ifconfig

 does not show anything but lo, you may need a proprietary driver.

edit: the post above is probably correct.

---

### Post by Myxoma on 2012-02-02
I'll give that info outlined through that link a shot, Roger. I'm not getting those messages in my log, but I am getting a series of "PCI interrupt link" messages.

Real weird thing though is that "eth0" is nowhere to be found on my computer. Not in the kernel log, and the terminal isn't finding it either. I'll try that link though and do a little more research myself. I'll post later on tomorrow if there are any other issues or if the current one isn't resolved. Thanks for the responses thus far!

---

### Post by Myxoma on 2012-02-02
> **wyliecoyoteuk said:**
> Hi, you don't need to install DHCP-server, but DHCP client, and that should be installed anyway by default.
If 

 sudo ifconfig

 does not show anything but lo, you may need a proprietary driver.
 what model of ethernet card is it?
Realtek 8111E that came integrated with the board. MSI actually offers their own linux based os called 'winki' so I would hope the drivers the board comes with are compatible... Although we're talkin about ubuntu here, not winki.

Where do you suggest I find a driver for it? Just directly from msi?

---

### Post by cryptotheslow on 2012-02-02
Realtek provide drivers for Linux here:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I believe you would want the second one down in the linux section list.

Shout up if you need a hand getting it installed and working. It has been done successfully before with other Realteks as witnessed here: [http://ubuntuforums.org/showthread.php?t=1434757](http://ubuntuforums.org/showthread.php?t=1434757)

Although trying to work out what steps to take from that thread may be a bit tricky as it contains a few false starts and is referring to an older version of Ubuntu.

You may find this walkthrough useful too:
[http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)

---

### Post by Myxoma on 2012-02-02
> **cryptotheslow said:**
> Realtek provide drivers for Linux here:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I believe you would want the second one down in the linux section list.

Shout up if you need a hand getting it installed and working. It has been done successfully before with other Realteks as witnessed here: [http://ubuntuforums.org/showthread.php?t=1434757](http://ubuntuforums.org/showthread.php?t=1434757)

Although trying to work out what steps to take from that thread may be a bit tricky as it contains a few false starts and is referring to an older version of Ubuntu.

You may find this walkthrough useful too:
[http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)

Oh yes dreaded installation process. I gotta learn these things. It's like a game now! Thanks for all the help thus far. I was posting from roommates computer and she needs it back now so I'll give that driver a shot tonight. Again, greatly appreciate the help. If I can't figure it out or I've still problems afterward I'lllet you folks know.

---

### Post by N00b-un-2 on 2012-02-02
two things... 1) it seems odd that Ubuntu did not automatically configure your network card.  You may want to try a later version of Ubuntu, try booting up a live cd or usb.
2) you mentioned having an older wifi card that you don't have the drivers for.  Typically legacy hardware is very well supported in the Linux kernel.  Try firing up the wireless card and connecting to your wifi.  I know your end goal is to get your ethernet NIC to work, but if in fact you need to install a driver for it you're going to have to compile it, and to compile you're going to need to install dependencies.  Typically for basic things, once connected to the internet running
```
sudo apt-get install build-essentials
```
should handle the majority of what you will need to build packages.

Don't be afraid of compiling.  It's a very good skill to have.  that being said, there really is no big secret to it.  most packages will compile with three commands
```
./configure --prefix=/usr
make
sudo make install
```
If you run into any unsatisfied dependencies, the make process will notify you of them saying the "blah blah blah package is not satisfied" or something to that effect.  From there, google the package or program name it mentions along with the version of Ubuntu you're running.  You will more than likely end up back at an Ubuntu web page with a list of packages and dependencies.  My recommendation is to use aptitude to search for the package name and then install it.  Later on you can learn to use tools like apt-file, build-dep etc.  but for now, Google is your friend until you're more familiar with the command line.

---

### Post by kevdog on 2012-02-02
Think of this as a great opportunity to learn about linux.  Unfortunately your experience is common to myself and others missing certain drivers and such.  With persistence however you'll get it solved :)

Lets learn about your hardware.

The first command you want is
lshw -C network  (Translated list (ls) hardware (hw) subsection class (-C) network). lshw will list all hardware on your computer.

This should list your networking card.  Within the output should be a line that has driver= (if you have an associated driver).  

lspci -nn (list pci bus devices) should also specifically list your networking card as well, but will not give you the driver.

Also typing dmesg at the command prompt gives you access to the system log which you can peruse since it often gives clues as to why a specific driver didn't load or couldn't be found.

/var/log/messages is also another system log.  Often this log file is extensive, so to just show like the last 100 lines:
tail -100 /var/log/messages

Hopefully this will help you.

---

### Post by Myxoma on 2012-02-02
> **cryptotheslow said:**
> Realtek provide drivers for Linux here:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I believe you would want the second one down in the linux section list.

Shout up if you need a hand getting it installed and working. It has been done successfully before with other Realteks as witnessed here: [http://ubuntuforums.org/showthread.php?t=1434757](http://ubuntuforums.org/showthread.php?t=1434757)

Although trying to work out what steps to take from that thread may be a bit tricky as it contains a few false starts and is referring to an older version of Ubuntu.

You may find this walkthrough useful too:
[http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)

I can't even seem to get the tar unfile packed. I keep getting the message "cannot open: no such file or directory"

I've typed the command multiple different ways as listed in that first thread you posted, but I'm not making any progress at all. From what I'm reading it seems simple, but I haven't punched in a command yet that has worked... well, other than ifconfig and other such things.

---

### Post by Myxoma on 2012-02-02
Also, already tried my wireless card as well. Couldn't seem to figure out how to install those drivers either. airforce54 broadcom something or another.

Otherwise though I am using the latest version of ubuntu.

@kevdog:

Tried that first command and got the message that I needed to enter it as a super-user (which I thought I was logged in as already).

Just seem to have a lot of trouble getting commands to do what they're supposed to do.

---

### Post by kevdog on 2012-02-02
Ok --- I think airforce broadcom are b43 drivers.

tar files are unpacked like:
tar zxf <file name>

Dont worry about the superuser thing since the output comes anyway (think of it as a handy warning).

For your wireless card what does it list for lspci -nnn (just for the wireless card line) or is this a usb device?

---

### Post by Myxoma on 2012-02-02
> **kevdog said:**
> Ok --- I think airforce broadcom are b43 drivers.

tar files are unpacked like:
tar zxf <file name>

Dont worry about the superuser thing since the output comes anyway (think of it as a handy warning).

For your wireless card what does it list for lspci -nnn (just for the wireless card line) or is this a usb device?

'802.11g Wireless LAN Controller [14e4:4318] (rev 02)'

---

### Post by Myxoma on 2012-02-03
Alright, I got the realtek driver extracted. What's the next step to install it?

---

### Post by wolfen69 on 2012-02-03
I didn't see this mentioned, but did you check your BIOS setting in the integrated section? See if the card is enabled.

---

### Post by Myxoma on 2012-02-03
> **wolfen69 said:**
> I didn't see this mentioned, but did you check your BIOS setting in the integrated section? See if the card is enabled.

yeah all integrated hardware is enabled in bios

---

### Post by kevdog on 2012-02-03
I dont mean to be taking you down the wrong path since I don't know about your situation, however are you sure your downloaded files are correct.

I'll just assume they are -- I have no idea.

Within the tarball you extracted, is this source code?

If its source code that needs to be compiled, these are general guidelines
sudo apt-get install build-essential linux-headers-`uname -r`

These are going to install the compile tools you need.

Within the source code main directory its going to be either:
./configure
make
sudo make install

or if you don't have a configure file, it might be:
./autogen.sh
./configure
make
sudo make install

Now just because its installed, its not actually activated within the userspace.

This would be done with:
sudo modprobe <driver name>

I dont know what the driver name is going to be, since I don't know enough about your package.

If you are lucky -- I mean really lucky -- you could check
lshw -C network
And hopefully you will see the section --driver associated with your card.

Similar to mine (but mines not a realtek):
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:3f:00.0
       logical name: eth0
       version: 01
       serial: 00:15:60:9c:06:ec
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **[SIZE="3"]driver=tg3[/SIZE]** driverversion=3.119 duplex=full firmware=5752-v3.10 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:e0800000-e080ffff

---

### Post by Myxoma on 2012-02-03
I actually don't have anything described as 'ethernet interface'

Other than my wireless card (which I'm not bothering with right now) I have this coming up under lshw -C network:
description: network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 1
bus info: pci@0000:04:01.1
version: 02
width: 32 bits
clock: 33mhz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=32
resources: irq:17 memory:fb200000-fb201fff

...

After seeing that I'm actually double confused because that doesn't appear to be a realtek interface. In fact, sounds like my wireless card... but then right below that listing it has a disable "wireless interface" listed. If that's the case though, my ethernet interface isn't being picked up at all.

---

### Post by kevdog on 2012-02-03
Does lspci -nnm list your network card (wired)?

---

### Post by kevdog on 2012-02-03
Ok -- your bcm4318 chipset requires the b43 driver.  To install this you are going to need two packages --

b43-fwcutter
firmware-b43-installer

You have no internet access -- so this could be a problem (if they are not on the install disc!!).

Lets try an experiment to see if they are on the install disc.

sudo apt -cdrom add

Put cd in drive
sudo apt-get b43-fwcutter firmware-b43-installer

reboot -- see if things work (Don't forget to take cd out of drive.
If everything works
Modify your /etc/apt/sources list and remove the cd-rom line.

---

### Post by Myxoma on 2012-02-03
> **kevdog said:**
> Does lspci -nnm list your network card (wired)?

Here's what I got...
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "2nd Generation Core Processor Family DRAM Controller [0100]" -r09 "Micro-Star International Co., Ltd. [1462]" "Device [7681]" 
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [0101]" -r09 "" "" 
00:16.0 "Communication controller [0780]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family MEI Controller #1 [1c3a]" -r04 "Micro-Star International Co., Ltd. [1462]" "Device [7673]" 
00:1a.0 "USB Controller [0c03]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [1c2d]" -r05 -p20 "Micro-Star International Co., Ltd. [1462]" "Device [7673]" 
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family High Definition Audio Controller [1c20]" -r05 "Micro-Star International Co., Ltd. [1462]" "Device [7673]" 
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family PCI Express Root Port 1 [1c10]" -rb5 "" "" 
00:1c.4 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 PCI Bridge [244e]" -rb5 -p01 "" "" 
00:1c.5 "PCI bridge [0604]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family PCI Express Root Port 6 [1c1a]" -rb5 "" "" 
00:1c.6 "PCI bridge [0604]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family PCI Express Root Port 7 [1c1c]" -rb5 "" "" 
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [1c26]" -r05 -p20 "Micro-Star International Co., Ltd. [1462]" "Device [7673]" 
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "P67 Express Chipset Family LPC Controller [1c46]" -r05 "Micro-Star International Co., Ltd. [1462]" "Device [7673]" 
00:1f.2 "IDE interface [0101]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family 4 port SATA IDE Controller [1c00]" -r05 -p8a "Micro-Star International Co., Ltd. [1462]" "Device [7673]" 
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family SMBus Controller [1c22]" -r05 "Micro-Star International Co., Ltd. [1462]" "Device [7673]" 
00:1f.5 "IDE interface [0101]" "Intel Corporation [8086]" "6 Series/C200 Series Chipset Family 2 port SATA IDE Controller [1c08]" -r05 -p85 "Micro-Star International Co., Ltd. [1462]" "Device [7673]" 
01:00.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "G92 [GeForce 8800 GT] [0611]" -ra2 "Unknown vendor [196e]" "Device [053c]" 
03:00.0 "PCI bridge [0604]" "ASMedia Technology Inc. [1b21]" "Device [1080]" -r01 "" "" 
04:01.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [4318]" -r02 "Linksys [1737]" "WMP54GS v1.1 802.11g Wireless-G PCI Adapter with SpeedBooster [0042]" 
05:00.0 "USB Controller [0c03]" "NEC Corporation [1033]" "uPD720200 USB 3.0 Host Controller [0194]" -r04 -p30 "Micro-Star International Co., Ltd. [1462]" "Device [7673]"

---

### Post by Myxoma on 2012-02-03
> **kevdog said:**
> Ok -- your bcm4318 chipset requires the b43 driver.  To install this you are going to need two packages --

b43-fwcutter
firmware-b43-installer

You have no internet access -- so this could be a problem (if they are not on the install disc!!).

Lets try an experiment to see if they are on the install disc.

sudo apt -cdrom add

Put cd in drive
sudo apt-get b43-fwcutter firmware-b43-installer

reboot -- see if things work (Don't forget to take cd out of drive.
If everything works
Modify your /etc/apt/sources list and remove the cd-rom line.
Ah, I understand now. But uhm... I installed ubuntu with a usb key. Can it be used the same way?

---

### Post by wildmanne39 on 2012-02-03
Hi, here is the what you need to get your wireless working.

Download the b43 zip file to a flash drive using a computer with internet then drag and drop the file to your ubuntu desktop. 

Right-click it and select Extract Here. Open a terminal and do the following commands one line at a time:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
if you have not installed any other wireless drivers your wireless should come on.
Thanks

---

### Post by kevdog on 2012-02-03
Yes but with modifications

Yes I believe you can do this.

First have the stick in the drive.

Then type mount

Your going to look for the mount mount of the USB drive. Here is what mine states:
/dev/sdc1 on /media/PORTFIREFOX type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

/dev/sdc1 is the physical node of the device (in my example).  

So I believe the statement would be:
sudo apt -sdc1 add
Substitue sdc1 for whatever you have for your usb device mount point.

---

### Post by kevdog on 2012-02-03
> **wildmanne39 said:**
> Hi, here is the what you need to get your wireless working.

Download the b43 zip file to a flash drive using a computer with internet then drag and drop the file to your ubuntu desktop. 

Right-click it and select Extract Here. Open a terminal and do the following commands one line at a time:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
if you have not installed any other wireless drivers your wireless should come on.
Thanks

That kind of ruined my fun -- but yea that will work!! I was just wondering if this stuff was on the default install media.

---

### Post by wildmanne39 on 2012-02-03
Hi, no it is not. The sta driver is.

---

### Post by kevdog on 2012-02-03
> **wildmanne39 said:**
> Hi, no it is not. The sta driver is.

Ok -- Is the provided firmware 64bit specific?

---

### Post by Myxoma on 2012-02-03
Hahaha. Alright, wildmanne, thanks to that post my wireless card is working now and I'm FINALLY online because of it. So thank you very much for that.

Only problem now... how do I set up my wired connection?

---

### Post by wildmanne39 on 2012-02-03
Hi, I am glad your wireless is now working.

I am not an expert with wired connections but post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
ifconfig
lsmod
```
and I may be able to help.
Thanks

---

### Post by Myxoma on 2012-02-03
I think I got it figured out now, actually. That brings me to one final subject though...

As soon as I connected to the internet, ubuntu found a huge list of updates for me. Problem is, I installed ubuntu on a partition. It's actually an old hard drive from my last computer and I'd partitioned about 7GB of space for ubuntu and the other 393GB are all on the main partition that contains my files that I don't want to lose as well as my windows system files (which I couldn't care less about anymore).

I have gpart now and I'm wondering... How can I get rid of alllllll my windows system files and then basically combine my partitions without losing any personal files?

---

### Post by Vaphell on 2012-02-03
if your windows works you might want to keep that for a while. You never know when you may need some obscure thing done and the only program that does that is windows one. Of course you can install windows in virtual machine and the need to have dual boot disappears but vm can be pain if you need fancy 3d or whatever.

As for repartitioning - i wouldn't touch that without backing up the files. You should have them backed up either way, what happens when the drive malfunctions? 

7GB for the system alone is ok, though you will run out of space if you will install apps left and right. You could reformat that big partition and create /home out of it. In linux subsections of system structure can get their own partition and /home responsible for everything user-related is often picked for that (it's like having D: with all the important stuff which is safe when you play dirty with C: ). It makes it trivially easy to reinstall the system with user data and settings untouched (sometimes reinstalling is easier than fixing)

Think about backing up and redoing everything from scratch - it may be the most pain free method. Resizing partitions takes hours. 20GB for / (root), few gigs for swap and the rest for /home.

---

### Post by wildmanne39 on 2012-02-03
Hi, also you need to know did you do a normal dual boot install or a wubi install?

It would be best to mark this thread solved and start a new one with a good title for your new question because that way it will get the peoples attention that know the answers for your particular question and each thread is suppose to stay on one topic.
Thanks

---

### Post by d4m1r on 2012-02-03
If DHCP isn't install, try sudo eth0 or sudo network-manager eth0 (or something like that, google it)

It will override your network settings with info for a hardwired LAN connection to your modem.

---

