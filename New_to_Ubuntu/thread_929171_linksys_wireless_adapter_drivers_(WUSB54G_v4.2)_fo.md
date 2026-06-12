---
title: "linksys wireless adapter drivers (WUSB54G v4.2) for linux?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-09-24
I have installed Ubuntu on a HP Pavilion a1610n and have been trying to get the wireless (Linksys Adapter (WUSB54G v.4.2) for the past couple of days. I think I'm getting closer with the help of you folks... I need a driver for this puppy. When I Googled this, it re:Ubuntuforum... Different model of adapter though. There has to be a driver out there, somewhere. Any ideas??? Thanks

---

### Post by lwvmobile on 2008-09-24
If your looking for the Windows Driver for use with ndiswrapper then get it from the linksys site

maybe this url will work [HERE]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3D1115416827517&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377527517B03&displaypage=download#versiondetail")

---

### Post by anewguy on 2008-09-24
Also, please copy/paste the output of "lspci" back here so we can the chipset, revision, etc., being used so that we might be able to point you to a driver.

One thing to remember is that there isn't always a Linux driver, but instead special tools (ndiswrapper, ndisgtk) are used to load in a copy of the Windows XP driver (you have to have the driver, it doesn't just find it).

If this is a usb device, please post back the output of "lsusb".  We then can tell you a statement to use to give us more detail on that specific usb device.


Dave :)

---

### Post by CoCoKnots on 2008-09-24
cole@captain-desktop:~$ sudo lspci
[sudo] password for cole:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem

cole@captain-desktop:~$ sudo lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 13b1:000d Linksys 
Bus 001 Device 002: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  
cole@captain-desktop:~$ 

Thanks

---

### Post by lwvmobile on 2008-09-24
It looks like you have been involved in a number of threads revolving around the same issue so it is nearly impossible for us to determine what steps you have already taken to get the adapter working.

I would personally try to use ndiwrapper, the link I provided earlier will give you the driver, but I just noticed its an .exe file and cabextract does not work on it, so I would extract it in windows and copy it over if you have windows or use wine to extract it otherwise.

---

### Post by CoCoKnots on 2008-09-24
Yeah, I've been around this block a few times... I think each time I get a little closer, but i just seem to be lacking that one or tow things which keep me from completing the assignment. The driver idea was new just a couple of post ago. Prior to that it was mostly information gathering & toggling access points on & off without much success. Obviously, I'm still at it... Day 3

---

### Post by CoCoKnots on 2008-09-24
IWVMobile, I have the driver which came on the CD with the adapter. However, I don't know how to bring it in thru Wine. Linux doesn't like reading the Windows XP files... I know that is what Wine is for. I just don't know how to use it that well yet. Any suggestions ?

---

### Post by crazypenguin2008 on 2008-09-24
not much to add other than wireless adapters that have a RA LINK chipset are compatiable with linux. some adapters have that chipset some dont. my linksys/cisco usb adapter cinnected right out of the box.

---

### Post by CoCoKnots on 2008-09-24
I'm afraid this one has me stumped. I started three days ago to put Ubuntu on my son's HP Desk Top. We have Ubuntu on a couple of other computer & love it. Everyone on the forum has been wonderful in assisting us with all the 'Bumps' along the way. Fortunately this one has a 'work around'. Instead of going wireless with the desk top, we're installing an ethernet cable system to the various rooms of the house. Just wanted to say Thanks again for all the effort.

---

### Post by crazypenguin2008 on 2008-09-24
ive got a spare usb adapter that i know works with ubuntu that i could pass along if interested in it.

---

### Post by anewguy on 2008-09-24
Try the following and post back the results here (assuming the device is still plugged into the same USB port:

lsusb -v -d 0bda:0111

Also, if you have the Windows driver cd you should be able to read it fine in Linux.  Reading NTFS is fine and a normal CD is no problem.  If the driver is "packed" - an executable or zip - let me know the file name and I'll see if I can download it somewhere and extract it for you.

Dave :)

EDIT:  Here's a link to getting a version 4 of this device working in Dapper - still applies for any subsequent release such as 8.04.  Just skip the part about downloading and making ndiswrapper -> it's on the livecd in /pool/main/n and can be installed by just double clicking each of the files in that subfolder.

[URL="http://ubuntuforums.org/showthread.php?t=192588"]http://ubuntuforums.org
/showthread.php?t=192588[/URL]

---

