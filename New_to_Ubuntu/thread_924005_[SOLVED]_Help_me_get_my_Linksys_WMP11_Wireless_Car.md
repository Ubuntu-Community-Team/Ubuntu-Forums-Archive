---
title: "[SOLVED] Help me get my Linksys WMP11 Wireless Card working with Ubuntu please!"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by GameGuru on 2008-09-19
Ubuntu doesn't even find the card.  What can I do to get it to work with Ubuntu?

---

### Post by anewguy on 2008-09-19
Post the results of lspci back here please.

Also, check Linksys' web site for the availability of a Windows XP driver - if available please download it and save to a new folder.

Also, post the results of ndiswrapper -l (that's a lower case "L") back here also.

Thanks
:)

---

### Post by GameGuru on 2008-09-19
Results of ndiswrapper -l

[B]patti@PattisComputer:~$ sudo ndiswrapper -l
[sudo] password for patti: 
lsipnds : invalid driver!
patti@PattisComputer:~$ [/B]

Results of lspci:
[B]patti@PattisComputer:~$ sudo lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:07.0 Ethernet controller: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card
[/B]

Is that what you wanted?

---

### Post by GameGuru on 2008-09-20
Can anyone help?

---

### Post by anewguy on 2008-09-20
If nobody has any other options, I would do the following:

- locate (perhaps at the Linksys website) the Windows XP (not Vista) drivers for the wireless card.  Download them, then "unpack" them if need be and put the .inf and .sys files in a new folder

- via Synaptics package manager, check to see if ndiswrapper is installed.  If not, install it.  You can use the LiveCD as a software source and click the reload (I think it's reload - you'll get the idea when you see it) to include the CD in Synaptics

- in a terminal window:

cd xxxxx <enter>  where xxxxx is the folder you put the driver .inf and .sys files in

ndiswrapper -l <enter> where that's a lower case "L" for list

If anything is returned, delete them 1 at a time via:

sudo ndiswrapper -e xxxxxx <enter> where xxxxxx is returned in the list above

Once nothing is returned from the ndiswrapper list command:

sudo ndiswrapper -i xxxxxx.inf <enter> where xxxxxx is the name of the driver .inf file

sudo depmod -a

sudo modprobe ndiswrapper

sudo gedit /etc/modules

This will open up the /etc/modules file in an editor.  This file describes kernel modules you want to load at boot.  At the end of this file add this line:

ndiswrapper

then "save" and exit.

Reboot.

Check your network manager to see if wireless networks show.

If any problems or questions, please post back.

Dave :)

---

### Post by GameGuru on 2008-09-20
I followed this step for step and still no go.  What am I doing wrong?

---

### Post by nothingspecial on 2008-09-20
Install the package ndisgtk which will give you a nice gui for ndiswrapper.
Have a go that way.
Once it`s installed it will appear somewhere in your menus as windows drivers or something like that.

---

### Post by GameGuru on 2008-09-20
Awesome, that made it so easy.  I am connected and it is working sweet thanks.

---

### Post by nothingspecial on 2008-09-20
No problem

:guitar:

---

### Post by GameGuru on 2008-09-20
Ok small issue though.  It doesn't autoconnect when I boot the computer.  It shows the computer icon with an X on it and I have to left click on that icon, click on "Connect to other wireless network", enter in the network name and hit Connect.  Like I said, I connect and it works good but it doesn't autoconnect.  How do I make it autoconnect so I don't have to do this everytime I boot?

---

### Post by GameGuru on 2008-09-20
Anyone?

---

### Post by GameGuru on 2008-09-21
Anyone still?

---

### Post by GameGuru on 2008-09-22
Not possible?

---

### Post by sea_monkey987 on 2008-10-04
are you using WEP encryption?  i ask this because i myself am struggling to get WEP encryption to work

what are you having to do over again?  install the card (i.e.  go through System > Administration > Windows Wireless Drivers)?  or just put in the information for your computer to connect to the network (i.e.  connect to SSID 'home' with key 'abcd....')

---

