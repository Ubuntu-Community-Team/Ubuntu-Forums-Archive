---
title: "help with wireless setup!!"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by matthewbrave on 2008-08-13
i have just installed ubuntu 8.04.1 on my computer yesterday. and i am having some dificilty getting my netgear wg111v2 to connect to my wireless router.

i have a belkin wireless mimmo g plus. firstly on the dongle there is supposed to be a blue light flashing to let you know that it is talking to the router and there is never one.

secondly in linux there are 2 small computer monitors. when i click on them it gives me all the wireless routers in the local area.

so i click on mine and it prompts me for a password. i type in the password but there is no option for 'wpa/psk' so i clicked on the dropdown for wpa personal and the drop down and selected tkip.

sometimes it will connect and sometimes not. when it doesent i click to edit the wireless options. it brings up a window with my router name wpa personal tkip and the last date i have connected to it.
 
also in the password box there is a very long password but when i show the letters it isnt my password, it is a combination of letters over and over again.

when i am connected i go on to google and type ramdom things in to see if it is working and it comes back with the results but only for a short while and then loses connection.

the blue light never lights up, but on my windows machine it does!!


if anyone can help please do as i dont want to boot my windows machinge again!!!!! :lolflag:

---

### Post by Kevbert on 2008-08-13
Assuming that the dongle is a USB device please go to Applications - Accessories-Terminal and enter 
```
lsusb
```
Highlight the output displayed and go to Edit-Copy.  Now open up your next post and press Ctrl+V to paste the info here.  It sounds like you have firmware drivers missing.

---

### Post by matthewbrave on 2008-08-13
i will have to type out result as the wireless is dodgy

---

### Post by Crafty Kisses on 2008-08-13
> **matthewbrave said:**
> i will have to type out result as the wireless is dodgy

When it's plugged in, post the following output:
```
lshw -C network
```

---

### Post by matthewbrave on 2008-08-13
in to the terminal thingy and post on here

---

### Post by Crafty Kisses on 2008-08-13
> **matthewbrave said:**
> in to the terminal thingy and post on here

Yes, that's correct.

---

### Post by matthewbrave on 2008-08-13
Bus 002 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

for kevbert







Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)



for code name

---

### Post by Crafty Kisses on 2008-08-13
That looks like you only did:
```
lshw -C
```
You should try the following:
```
lshw -C network
```

---

### Post by matthewbrave on 2008-08-13
matthew@linux-pc:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

matthew@linux-pc:~$

---

### Post by nothingspecial on 2008-08-13
CAPITAL C  :wink:

---

### Post by matthewbrave on 2008-08-13
oh!!!!!

1 sec

---

### Post by ladr0n on 2008-08-13
anything you type into a terminal in linux is case sensitive: that is, "lshw -c network" and "lshw -C network" are two different commands.  -c is not a valid option for lshw so you need to run "lshw -C network"

---

### Post by falcon61102 on 2008-08-13
Just FYI, pretty much everything in Ubuntu is case sensitive.  Also, as a general rule you can copy and paste sections of code that are posted for you to run from the forum straight into the terminal.  This will save you a lot of typing.  Just be careful with any code that has "rm" in it, because "rm" is used for removing things and is very powerful.

-Wow my page was slow refreshing...

---

### Post by matthewbrave on 2008-08-13
i have just had to put in my live cd as the bios isnt booting from hdd and it is set to boot from the hdd

---

### Post by matthewbrave on 2008-08-13
got it working


here


matthew@linux-pc:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 11
       serial: 00:10:dc:c8:d4:c2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:aa:cf:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
matthew@linux-pc:~$

---

### Post by matthewbrave on 2008-08-13
i have to go out now 

i will be back in a few hours

---

### Post by falcon61102 on 2008-08-13
Could you run and post the results of:
```
lspci
```

That will provide some more details on your hardware type as there was not much on your hardware list.

---

### Post by matthewbrave on 2008-08-13
i am at a friends house atm.

i will be back on in a few hours on my linux desktop

---

### Post by matthewbrave on 2008-08-13
matthew@linux-pc:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8361 [KLE133] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8361 [KLE133] AGP Bridge
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0f.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1
matthew@linux-pc:~$

---

### Post by falcon61102 on 2008-08-13
It doesn't appear that Ubuntu is recognizing your wireless card.  What type of card do you have?

---

### Post by Kevbert on 2008-08-14
Probably your best bet is to install ndiswrapper and use the windows driver that came with the dongle.  
What you need to do first is to install some files from your Ubuntu CD.  To do this you need to go to System-Administration-Synaptic Package Manager.  Put your Ubuntu CDROM in the drive. In the Synaptic menu bar go to Edit and select Add CDROM.  Press OK and select No when prompted.  Now go to Search and enter ndis.  The files you need to install are 
ndiswrapper-common
ndiswrapper-utils-1.9 (or whatever version is displayed
ndisgtk
Right-click on each of the boxes next to them in turn and select Mark for Install. Now click on Apply to install them.  
Now go to Settings-Repositories and remove the tick from the CDROM box by clicking on it (this will stop you needing to put the CDROM in the drive every time you want to add software or perform an update). Remove the CDROM from the drive.  Close Synaptic.
Now go to System-Administration-Windows Wireless Drivers and select Install new driver.  You'll need to point the program to where your Windows INF file is (on the right of the box is a folder icon, click on this and browse to the driver).
Hopefully this should work, any questions please ask.

---

### Post by matthewbrave on 2008-08-14
i currently am not able to get to that computer as it is in london and i have gone on holiday to north yorkshire.

but i will try that when i get back down!!

---

### Post by matthewbrave on 2008-08-23
ok i have now come back to the linux box after being on holiday.

i have tried to do what you have suggested kevbert but i am still not successfull. since i have lost the cd which came with the usb dongle i have downloaded the zipped file and looked in there and there but are no .inf files but there are .ini what should i do now.

---

### Post by nothingspecial on 2008-08-23
I don`t think you need to do all that ndiswrapper stuff. The Belkin dongle should work and as it is detecting wireless networks and connecting intermittently the problem is something else.
Remember google is your freind.

---

### Post by matthewbrave on 2008-08-24
sorry but it is not a belkin dongle but a netgear wg111v2. the wireless router is a belkin.

---

### Post by nothingspecial on 2008-08-24
Sorry.
Ok, you say you can only see .ini files.
In the zipped folder do you have a subfolder called xp or winxp (something like that) the inf file should be in there.
Follow kevberts earlier instructions.
Hope the weather wasn`t too bad in North Yorkshire.
Before you do that have a look here. It`s more complicated but might work better. (No garuntees from me -just trying to help)

---

### Post by nothingspecial on 2008-08-24
Sorry forgot the link.
[http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/](http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/)

---

### Post by matthewbrave on 2008-08-24
i am new to linux and i dont want to have to reinstall it again as i had a hard time the first time and dont want to go through that again.

there seems to be no end of trouble with this dongle as it is all over google and other fourms.

there are so many soultions to fix it but i dont know which one to use. 

if the one poosted above WILL work i will use it but as i said i dont want to reinstall ubuntu again. then tell me if it will.

i have tried what kevbert said but to no efect. i have tried downloading the 1.3 version off netgear and used the 98 driver. the blue light lights up but still no connection.

if you can give me very simple and clear instructions on what to do then please go ahead and do so. Eg tell me how to go in to terminal cos i dont know where it is.


thanks!!

---

### Post by Kevbert on 2008-08-24
Hi Matthew.  Please have a look at this [[COLOR="Red"]link[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-632651.html").  It's for an older version of Ubuntu but should still work.  Part of your problem is that you are using a wireless USB dongle and Ubuntu doesn't seem to work all that well with these types of devices.
To get to terminal select Applications-Accessories-Terminal.
Attached is the drivers you need to use.  To extract them save the file to your Desktop, right-click on the folder and select 'Extract here'.  Please try using the method I suggested to install in my earlier post.
Good luck.

---

### Post by matthewbrave on 2008-08-24
RIGHT i will get on to it now!!!


THANKS!

---

### Post by matthewbrave on 2008-08-24
there is no end of trouble with this GRRRRR!


i have tried the link you posted and i couldnt even do the first step as the command was not recocnised.

---

### Post by matthewbrave on 2008-08-24
then trying kevberts post again... it said i was connected but with a 0% connection. shall i put it on manual not auto.

---

### Post by porchrat on 2008-08-24
you probably can't do it because he is using the text editor 'mousepad'.  Where it says mousepad just substitute in 'gedit' and it should work fine

---

### Post by matthewbrave on 2008-08-24
ok

---

### Post by matthewbrave on 2008-08-24
i have given up with this evil thing and hope that the ubuntu devlopers will allocate a better driver in the next ubuntu.

i am going to go and get a very long lan cable and run it under the floor boards and operate it that way!!


thanks for all the help!!!

---

