---
title: "Dual boot Win 7 x64 and Ubuntu 12.04 LTS"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by Ghot on 2014-02-01
Ok, here's the problem.  I've booted from the 12.04 LTS Live CD a number of times.  EVERY time, I get to the Ubuntu desktop with no internet.  It SEEMS to be searching for a wireless signal, even though I have no wireless.  I'm on a desktop comp, with Ethernet...specifically Verizon FIOS 50/25.  I want to install and finally try Ubuntu...dual boot with Win 7 x64.  However, If I can't even get the Live CD to work, I wary of trying this.

My system:

Windows 7 Home Premium x64 SP1

AMD FX-8350 Vishera 4.0GHz (4.2GHz Turbo) Socket AM3+ 125W Eight-Core Desktop Processor 
ASUS SABERTOOTH 990FX R2.0 AM3+ SATA 6Gb/s USB 3.0 ATX Motherboard ( 1302 BIOS)
EVGA 06G-P4-2791-KR GeForce GTX TITAN 6GB 384 bit GDDR5
CORSAIR Dominator Platinum 16GB (2 x 8GB) DDR3 1866Mhz RAM (factory settings)
COOLER MASTER Hyper 212 EVO RR-212E-20PK-R2 CPU Cooler (push/pull)

WD 500GB Velociraptor - SATA III	
WD 1TB Caviar Black FAEX - SATA III
WD 1TB Caviar Black FAEX - SATA III
LG GH22LS30 CD/DVD Burner

PC Power & Cooling Silencer 750W Quad EPS12V

DELL Ultrasharp U3011, 30" monitor
Klipsch Pro Media 2.1 THX Speakers (Black)
Ducky DK9008 Shine II Blue LED Backlit Mechanical Keyboard (Cherry MX Black)
Logitech Optical M-100

COOLER MASTER ATCS 840 Full Tower Case
3x230mm, 1x120mm, Optional: 3x Scythe S-Flex SFF21G 120mm (installed)


My HDD's layout at present:

[IMG]http://i.imgur.com/Nh0oAAG.jpg[/IMG]


Things I am worried about:

1.  My backup system after dual booting Ubuntu.
2.  No matter what goes wrong, I can access my Win 7 full Image backups from my Acronis Boot CD.
3.  Why I have no internet when using the live CD.
4.  I have all, late 2012 hardware and a UEFI BIOS.

Please don't link me to tutorials, I have read them and do not understand them.

I know this is a tough forum, what I would like is one informed person to walk me through this, one time.  After that, and assuming my backup and restore system still works for Win 7, I can carry on, on my own, hopefully.


Thx in advance.

---

### Post by Gone fishing on 2014-02-01
The connection problem is probably Ubuntu trying to get an IP address does you router automatically give out IP address? Open a terminal and check run ifconfig and your are looking for something like eth0 with an IP address of 192.168.X.X (the X are numbers). If no such address exists than check you machine in Windows (it probably has been given a fixed IP address) and set up Ubuntu in the same way. (Click the network icon > edit connections > select the wired connection and edit).

As for installing the safest way would be to boot into Windows remove partitions D: and E and then when you install Ubuntu allow it to install into the lagest free space Ubuntu will the use the free space you have created it will set up the system to dual boot. I would suggest that you back up all your data first (although I don't and have never had a problem).

---

### Post by mikewhatever on 2014-02-01
I don't see any reference to an ethernet card in your specs. Have you, somehow, left it out?
I've heard that Verison is an Internet provider somewhere in North America, but that's probably irrelevant to the problem at hand.
...and now the list:
1. What system? You've not told us anything about it.
2. Sounds like a good thing, not sure why you'd be worried.
3. Hard to tell without more info.
4. Same as 2.

PS: I don't think the forum is tough at all, on the contrary, this comunity is rather friendly.

---

### Post by Mark Phelps on 2014-02-01
Yours may be different, but my Verizon router also provides wireless -- it comes with the hardware.

---

### Post by oldfred on 2014-02-01
I might consider reorganizing a bit, so Windows is on one drive and Ubuntu is on another drive.
Then you have less conflict. And when (not if) one drive fails you can go back into BISO/UEFI and choose to boot from the other drive.
But it is a bit more complex unless you physically disconnect drives.

I prefer to partition in advance. If installing on same drive as Windows only use Windows to shrink the Windows NTTFS partition and reboot so it can run chkdsk.

You show two empty NTFS partitions. Ubuntu cannot install into NTFS partitions. And it looks like your Windows install is in BIOS mode not UEFI as UEFI has many more partitions for Windows. If Windows is in BIOS boot mode and MBR partitions you need to install Ubuntu in BIOS boot mode. But if on separate drive Ubuntu can be in BIOS boot mode on gpt partitioned drive. And if you include an efi partition at beginning of drive you can then easily convert to UEFI boot. But if MBR partitioned you cannot UEFI boot.

How you boot install media is how it installs, so if Windows is BIOS, you must boot Ubuntu in BIOS mode. IF UEFI system it should show Ubuntu install flash drive twice, one UEFI and the other BIOS, but descriptions from UEFI are usually not clear.
This shows screens so you know which mode you have booted in, so you do not attempt to install in wrong mode.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using. You do not want anything else from this link as it is for UEFI boot which you do not want.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Ghot on 2014-02-01
Well I found out the problem with the internet.  Since I have no router, I have to do ipconfig /release on Win 7 BEFORE booting from the 12.04.3 LTS Live CD...then the internet works fine.
Something about having no router means that whenever I switch to a diff comp or a diff OS, I have to release the IP first, and then release it again when I switch back.

The reason I don't use a router is that even the best ones have a very small NAT table..aka RAM...and after a while I get tired of having to reboot comp when the NAT table fills up.

As for dual booting, YES I intend to delete the D: and E: partitions, before I attempt an install, or at minimum the D: partition.



Ty all, very much for your responses...give it another few months, and I may actually attempt a dual boot.  Microsoft is digging their own grave, and I think Linux is the future for an OS.  My only disappointment with the live CD is that it wouldn't let me change resolution from 1920 x 1080 to my monitor's res of 2560 x 1600.  But I guess I should expect that from a Live CD.

For the meantime I'll stick with Win 7, just out of familiarity, but no more MS OS's for me.  When they stop support, or even indicate they may, it'll be Linux for me.


Have to admit though, for me the Live CD was like playing a game of Baldur's gate for the first time.  Go into a room and break all the barrels and open all the treasure chests, and see what I find.  That in itself was pleasurable   :)

---

