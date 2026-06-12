---
title: "[SOLVED] Cant connect to internet - Ethernet"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Ubuntscrewed on 2008-08-26
Hi - 

I'm an absolute noob to Ubuntu/Linux.  My problem is two-fold.

Problem #1 Ubuntu (8.04) will not connect to the internet.

Problem #2 (only slightly less serious) Windows XP Home will not load since Ubuntu install (dual boot).  The message I get when trying to boot into Windows  is "A disk read error occurred press ctrl+alt+del to restart."  I only mention this problem here and now, so I'm not directed to use my Windows install for anything regarding the rectification of Problem #1, as this is impossible at present.  I do look forward to solving Problem #2, however, no internet is a much bigger problem for me.  I've been searching the forums, Google, etc. for days until the wee hours of the morning and I am no closer to a solution to either of my problems.  I hope someone can help. Thanks in advance for even reading this post.

My system specs are as follows:
Intel Core2Duo E2180 2 GHZ, Gigabyte S-series mobo GA-945GCM-S2L, 2gb DDR Ram, 250 GB SATA HDD, SATA DVD/RW, 80 GB ATA (PATA or IDE if you prefer) HDD (not found by Ubuntu - was working fine with Windows XP Home).  

This system is two months old and came with Windows XP Home pre-installed.  Aside from connecting my old 80 GB HDD, and the usual peripherals, ie, printer and scanner (both Canon), and a Sony camcorder docking station, no other hardware has been added to this system.  All Microsoft updates were installed, including SP3.  And the C drive was defraged about two weeks prior to the Ubuntu install.  We have a hard-wired home network using a  Belkin 4-port Cable/Dsl Gateway Router, connecting to a Speedstream 4200 ADSL 2+ modem. 

Prior to the installation of Ubuntu, internet and LAN worked flawlessly, so I don't believe the fault lies with the cables, connections, hardware, etc, as I have changed nothing.  

Here's what has happened thus far:  

Ran Ubuntu Live CD but was not able to connect to internet, all other features appeared to work fine, barring not seeing my 80 GB HDD.  After a perfunctory search of the forums regarding failure to connect to internet, I decided to do a dual install of Ubuntu, hoping, erroneously it appears, that the problem might rectify itself after a proper install.  

I let Ubuntu partition my HDD, giving Windows 75% and Ubuntu 25%, the install incurred no errors, or at least didn't mention any to me.  After the install and reboot, Ubuntu launched itself as I was afk during startup.  I tried Firefox and had no internet connection.  Then I tried rebooting/resetting router, modem and computer with no success.  

Then I manually configured the the Network, by unchecking the roaming option and setting to Auto config. DHCP.  

In Firefox Connection Settings, I have selected Auto-detect proxy settings, ensuring that Work Offline under File drop down is unchecked. 

I have tried a ping in Network Tools to 82.211.81.158 and 5 packets are sent 0 packets received.  Further I've attempt to ping Ubuntu.com and get an error message “the address 'ubuntu.com' cannot be found.”  Nor am I able to reach my router on 198.168.2.1, please note I have disabled the firewall within the router and have no other firewalls installed. 

Also, I used a command in Terminal which I am unable to find, it did contain word 'modprobe' from memory, turning IPv6 off.  

I have also tried bypassing the router and directly connecting to my modem via Ethernet, no success, the Ethernet LED on modem did not illuminate.  The modem also supports USB but it's too far away to try this option without a Herculean effort.  

Under 'Devices -Network Tools' I have  selected and tried to configure eth0 and eth0:avahi only to be told 'the interface does not exist.' 

I have also tried a static IP address in Network Settings eth0 properties using IP Add: 192.168.2.1,  Subnet mask 255.255.255.0, Gateway address 10.1.1.1 – I just sort of made this up as I was out of options last night and thought I'd give it a try, no luck.  

By the way the LED on router for port 4, where I'm connected, is NOT illuminated.  I have tried swapping ports, same result, no joy.  I know I've tried other things but I can't remember what they are.  Sorry.  

The output from 'ifconfig' reads as follows: 

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:62:54:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:1747935702 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:221 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:62:54:c0  
          inet addr:169.254.7.246  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1410 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1410 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:72544 (70.8 KB)  TX bytes:72544 (70.8 KB) 

I hope that covers everything, I apologize if the solution to my problem has already been posted within this forum and for the lack of berevity of this post.  Thanks for reading all the way to the end.  

Sitting with my first steaming cup of Ubuntu spilled in my lap.  Cheers, Ubuntscrewed.

---

### Post by prshah on 2008-08-26
> **Ubuntscrewed said:**
> 
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:62:54:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:1747935702 overruns:0 frame:0 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:62:54:c0  
          inet addr:169.254.7.246  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 

Thanks for reading all the way to the end.


Phew, that's some post. A solid wall of text. For the future, a properly paragraphed post will ensure that more people read it, rather than just skim through the lot.

For now ignoring the 80Gb HDD not visible part, cause I don't understand how that's possible unless you are using SATA, but you claim to be using IDE/PATA.

From the ifconfig output you have posted, I notice that eth0 has not been assigned an ip address.

This, and considering the information about LEDs _not_ being lit, means out first step is to check if the connection is active or not: Open the terminal (Applications-Accessories-Terminal) and give the below commands, then post back the output (Try to post exact output, rather than paraphrase- maybe you could use a USB stick?)```
sudo mii-tool eth0
sudo fdisk -l
```

(The second command is to do with the HDD issue.)

---

### Post by Ubuntscrewed on 2008-08-26
Cheers for the reply prshah, if my newborn EVER goes to sleep I'll edit my original post - thanks for the tip.

BTW 80 GB HDD is PATA/IDE.  Also, I did use micro drive to post output, not paraphrased.  Did I cut something off?

Output:
john@john-desktop:~$ sudo mii-tool eth0 
eth0: no link 
john@john-desktop:~$

sudo fdisk -l output:

Disk /dev/sda: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x68fc68fc 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       22886   183831763+   7  HPFS/NTFS 
/dev/sda2           22887       30401    60364237+   5  Extended 
/dev/sda5           22887       30088    57850033+  83  Linux 
/dev/sda6           30089       30401     2514141   82  Linux swap / Solaris 

Disk /dev/sdb: 1021 MB, 1021125120 bytes 
32 heads, 63 sectors/track, 989 cylinders 
Units = cylinders of 2016 * 512 = 1032192 bytes 
Disk identifier: 0xe0af874b 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1         989      996788+   6  FAT16 
john@john-desktop:~$ 


Sadly, I don't know what any of the aforementioned information means.  But i hope it's what you wanted.  Thanks again.

---

### Post by Michael.Godawski on 2008-08-26
hey
I also want to help

let`s start with some basic input, pls go into the terminal and give us the result of the following command:

```

iwconfig
```

you want to connect to the internet via ethernet not via wlan right?

---

### Post by Ubuntscrewed on 2008-08-26
Thanks Michael.  The output you requested is as follows:

john@john-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

john@john-desktop:~$ 

Seems a bit bereft of information but I hope it's what you wanted.

Yes, I want to connect via Ethernet.  I don't/won't use wireless as they operate at frequencies incompatible with human life and longevity.  If at all possible, do yourself and your neighbors a HUGE favor by going back to a wired connection.  I'll get off my soapbox now.  Thanks

Cheers

---

### Post by michael.693 on 2008-08-26
i have the same problem as you, 



Please help.

---

### Post by Michael.Godawski on 2008-08-26
You know thats odd, because usually Ubuntu does not have problems with a wired connection ( I know this info does not help you...)

Your modem should be seen by Ubuntu because it is supported
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsSpeedstream](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsSpeedstream)

Do you you an USB Moden? Then have a look here:
[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

This tutorial says that usb modems are not so easy to install on linux...

---

### Post by ugm6hr on 2008-08-26
We need to know your chipset...

The output of the following is helpful:

```
lspci
lshw -class network
```

---

### Post by Ubuntscrewed on 2008-08-26
Cheers ugm6hr.

john@john-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 

john@john-desktop:~$ lshw -class network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1f:d0:62:54:c0 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.1 latency=0 module=r8169 multicast=yes 
john@john-desktop:~$ 

Wow, hope you can make sense of this.

---

### Post by Michael.Godawski on 2008-08-26
The part which are of interest to us are:

>
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

>
product: RTL8111/8168B PCI Express Gigabit Ethernet controller 

and
>
configuration: **broadcast=yes driver=r8169** driverversion=2.2LK ip=192.168.2.1 latency=0 module=r8169 multicast=yes 

so your ethernet connection is recognized... which makes this issue  a big one :)

---

### Post by Ubuntscrewed on 2008-08-26
> **Michael.Godawski said:**
> 

so your ethernet connection is recognized... which makes this issue  a big one :)

That doesn't sound good... Yikes.  Good thing I shaved my head, or I'd be pulling my hair out.  Perhaps I'll find a dark corner in which to cry.

---

### Post by ugm6hr on 2008-08-26
As Michael says - driver is OK; ethernet chipset is supported.

So why doesn't it work?  Dunno.

Couple of things that strike me:
> Nor am I able to reach my router on 198.168.2.1

configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.1

eth0 Link encap:Ethernet HWaddr 00:1f:d0:62:54:c0
UP BROADCAST MULTICAST MTU:1500 Metric:1 

This doesn't make sense.  Your ethernet card appears to have an allocated IP identical to the router, which obviously won't work.  Also, ifconfig doesn't list the ip.  Are you still using DHCP or static?

One other thing to consider: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1) (see point 8 ).  Unfortunately, if this is the issue, you may be a bit stuck given XP is misbehaving...

---

### Post by Ubuntscrewed on 2008-08-26
> **ugm6hr said:**
> Also, ifconfig doesn't list the ip.  Are you still using DHCP or static?

One other thing to consider: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1) (see point 8 ).  Unfortunately, if this is the issue, you may be a bit stuck given XP is misbehaving...

I switched back to DHCP before posting output of 'ifconfig'.

It would, no doubt, be a great benefit if I could get Windows to load and try the solution posed on the MS guide; however, the few solutions I've tried to restore Windows have failed and I don't possess the skills, knowledge or abilities to rectify that problem either.  Anyone?

---

### Post by Ubuntscrewed on 2008-08-26
Oh crap.  I just double checked, it somehow reverted back to static.  My bad, I'm so very sorry, that was extremely careless of me.  I've switched back to DHCP and the 'ifconfig' output is as follows:

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:62:54:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:3249738202 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:221 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:62:54:c0  
          inet addr:169.254.7.246  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1426 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1426 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:73884 (72.1 KB)  TX bytes:73884 (72.1 KB) 

john@john-desktop:~$ 

I hope I haven't wasted anyone's time through this oversight, please accept my sincerest apologies.  Do I need to rerun any of the previous commands?  Sorry folks.

---

### Post by natirips on 2008-08-26
I remember I got a similar problem recently: there was a wired connection (Fedora would connect normally with it), but Ubuntu failed to connect. There was a driver assigned, but no IP whatsoever. I tried sudo modprobe -r drivername & sudo modprobe drivername but to no avil.** In the end I solved the problem by installing a PCI Ethernet card** (**The one that didn't work with Ubuntu was a 1GBit Ethernet LAN integrated on** an Asrock **motherboard** (please don't ask me why I bought from Asrock)).


> **Ubuntscrewed said:**
> I don't/won't use wireless as they operate at frequencies incompatible with human life and longevity.  If at all possible, do yourself and your neighbors a HUGE favor by going back to a wired connection.  I'll get off my soapbox now.  Thanks


This is a little offtopic, but I have 4 computers in my bedroom, of which 2 use wireless LAN (due to lack of wired LAN connectors on my router). I haven't noticed any problems with that so far. I don't know who told you that WLAN frequencies are "incompatible with human life and longevity", but even if that's true, are you going to stop going out of your house just because it is dangeours to cross the road (i.e. not to get hit by a car)? Besides, the amaount of pollution in the air is a far greater problem in my opinion...


Edit upon seeing above message: If your internet is working you don't need to rerun anything. If it isn't working I think above is enought for a start. It is pointless to run everything and give tons of outputs here. Unless I'm wrong :S, you will be told if we need any more commands' output.

---

### Post by Ubuntscrewed on 2008-08-26
> **Michael.Godawski said:**
> https://help.ubuntu.com/community/UsbAdslModem[/url]

This tutorial says that usb modems are not so easy to install on linux...

Not using USB, I read the same thing re: difficulty using USB and the computer is too far away to attempt a USB connection without more work than just buying a new one.

Cheers

---

### Post by ugm6hr on 2008-08-26
Repost *lshw -class network* too.

---

### Post by Ubuntscrewed on 2008-08-26
> **natirips said:**
> 



 I don't know who told you that WLAN frequencies are "incompatible with human life and longevity", but even if that's true, are you going to stop going out of your house just because it is dangeours to cross the road (i.e. not to get hit by a car)? Besides, the amaount of pollution in the air is a far greater problem in my opinion..

I agree air pollution is a major problem; however, the work of Dr. Emoto Masaru [https://www.hado.net/watercrystals/index.php](https://www.hado.net/watercrystals/index.php), clearly demonstrates the positive and negative effects of the common, everyday frequencies (including thought) on water.  As human beings are 70%+ water, it's not rocket science to see that minimizing one's exposure to these frequencies is beneficial.  Please note I did say "if possible..."  And no, of course I must leave my house in spite of the risks associated with automobiles and their operators.  I believe you have made a logical fallacy in your argument, although I'm not an academician.  I have managed to live a full and rewarding life without the use of a microwave, cell phone, cordless phone or any other wireless device except a TV and radio, for more than 6 years.  Note: I do have a mobile phone in the glove box of each car I own for emergencies.  They remain off, unless needed.  And you're right this is a bit off topic but I can't help myself, please forgive me.

---

### Post by Ubuntscrewed on 2008-08-26
john@john-desktop:~$ lshw -class network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1f:d0:62:54:c0 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes 
john@john-desktop:~$ 

Cheers

---

### Post by ugm6hr on 2008-08-26
I'm afraid I'm out of ideas, apart from the Windows power-saving issue (which requires Windows to rectify).

There is no good reason for your wired connection not to work from the LiveCD apart from this.

It might just be worth checking whether BIOS has any settings for the ethernet card e.g. boot from LAN etc. that *may* be able to override Windows software switch (altho I have never done anything like that).

---

### Post by prshah on 2008-08-26
> **Ubuntscrewed said:**
> 
Output:
john@john-desktop:~$ sudo mii-tool eth0 
eth0: no link 
john@john-desktop:~$


eth0: no link means that there's nothing plugged into the ethernet port, now you should check:

a) That you have actually plugged the damned thing in
b) That it's tight, and no possibility of a loose contact
c) That the other end is plugged into the router/hub/switch
d) that the other end is tight and there is no loose contact
e) that the cable is fine
f) that the router/hub/switch is actually turned on

Until mii-tool reports a connection, along with speed (10Mbps, 100Mbps, 1000Mbps) you can try commands till you're blue in the face nothing will help.

And about the newborn: Hey, get used to it; my 20-monther _still_ doesn't let me use the computer; when he's awake, he insists on pushing me off, and when he's about to sleep, he insists on me talking/singing to him.

---

### Post by Ubuntscrewed on 2008-08-26
**IT WORKED!!!**

Thank you ugm6hr! Boo effin Ya.   Here's what I did...

In the BIOS under 'Integrated Peripherals' I Enabled 'Onboard LAN Boot ROM' don't know what it means but I'm bloody surfing.  You beauty!  **All hail ugm6hr**  And a huge thanks to everyone else who has injected their positive frequencies into this problem.  NAMASTE. (The light in me salutes the light in you. A rough translation.)  

You people are the very best.  Thanks again.

And to prshah, thanks for the advice re: newborn, this one is my second, number one is now 6 years old and has been able to sleep unassisted for over a year, good luck with yours.  

And to natirips, please don't think me flippant, I offered the advice re: frequencies for the benefit of mankind and understand we must live in our modern world in spite of the dangers, plus I yearn for adult conversation not related to babies.

---

### Post by Ubuntscrewed on 2008-08-26
Do I need to mark this thread as SOLVED?  If so, how?

---

### Post by prshah on 2008-08-26
> **Ubuntscrewed said:**
> Do I need to mark this thread as SOLVED?  If so, how?

Yes, you should ( considering your last ecstatic post:) ). Near the top right hand side of the page, click on "Thread Tools"-"Mark thread as solved"

---

### Post by natirips on 2008-08-26
> **Ubuntscrewed said:**
> And to natirips, please don't think me flippant, I offered the advice re: frequencies for the benefit of mankind and understand we must live in our modern world in spite of the dangers, plus I yearn for adult conversation not related to babies.

I agree it's not healthy to use WLAN, but it's just that humans need to do compromises sometimes. For example, it is dangeours to ride a bike (you can fall off and hurt youself), but it's still usefull. I agree using wlan for a desktop computer that is 5 meters from the router is pointless. But than again, it's very practical on a laptop, or when it takes 20m cable to reach the router.

And no, I won't think of you as a flippant :) .




As for marking the thread as solved there is "Thread tools" or such above the posts list to the right. (Edit: prshah beat me to that.)

---

### Post by ugm6hr on 2008-08-26
Glad that worked...

I'll remember that little trick for the future too!

---

