---
title: "HOWTO: Install PCI Lucent winmodem (ltmodem/ltserial)"
date: 2006-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by blastus on 2006-06-17
HOWTO: Install PCI Lucent winmodem (ltmodem/ltserial) 

This guide covers how to install the Lucent winmodem driver under Dapper. I realize that the Lucent modules are included with Dapper, so downloading and compiling the driver is not necessary, but I feel that users should know how to compile them just in case. For example, in Breezy the modules were listed, but not included so users had no other choice but to learn how to compile them. Eventually this guide will include alternative instructions to use the precompiled modules that are included with Dapper.

Any and all comments are welcome! I want to improve this guide to make it as simple as possible for newbies and also make sure everything in it is accurate.

This guide assumes you know:
- how to use a Terminal
- how to use the "sudo" command
- how to use some basic commands such as "cp", "mv", "cd", "ls"...
- how to use gedit
- what a file archive is like zip, gz, bz2 etc...

**1. DOWNLOAD THE DRIVER**

a. Create a temporary directory called "lucent" (we will delete this directory after we are done)
```
mkdir ~/lucent
```
b. Download the file [ltmodem-2.6-alk-8.tar.bz2](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-8.tar.bz2) into your ~/lucent directory
(NOTE: the ~ character in ~/lucent refers to your "home" directory...for example, if you login to Ubuntu as the user "neo", then ~/lucent would refer to the directory /home/neo/lucent)

c. Extract the contents of the archive file
```
cd ~/lucent
tar jxf ltmodem-2.6-alk-8.tar.bz2
```

**2. COMPILE THE DRIVER**

a. Insert your Ubuntu 6.06 CD into the drive and click on the "Start package manager" button when prompted

b. After Synaptic Package Manager has fully opened, close it

c. Install the stuff you need to compile the driver
```
sudo apt-get install build-essential linux-headers-`uname -r` wvdial
```
(NOTE: The expression `uname -r` in the above is surrounded by angled single quotes, not straight single quotes. On most keyboards, you can type an angled single quote by pressing the key above the TAB key)

d. Compile the driver
```
cd ~/lucent/ltmodem-2.6-alk-8
make

```
If your login name is neo, you may see something like this:
```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/neo/lucent/ltmodem-2.6-alk-8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /home/neo/lucent/ltmodem-2.6-alk-8/lt_modem.o
  CC [M]  /home/neo/lucent/ltmodem-2.6-alk-8/serial.o
  LD [M]  /home/neo/lucent/ltmodem-2.6-alk-8/ltmodem.o
  LD [M]  /home/neo/lucent/ltmodem-2.6-alk-8/ltserial.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/neo/lucent/ltmodem-2.6-alk-8/.ltmdmobj.o.cmd for /home/neo/lucent/ltmodem-2.6-alk-8/ltmdmobj.o
  CC      /home/neo/lucent/ltmodem-2.6-alk-8/ltmodem.mod.o
  LD [M]  /home/neo/lucent/ltmodem-2.6-alk-8/ltmodem.ko
  CC      /home/neo/lucent/ltmodem-2.6-alk-8/ltserial.mod.o
  LD [M]  /home/neo/lucent/ltmodem-2.6-alk-8/ltserial.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
```

Compiling the driver created a bunch of files. However, there are only two files that we need; ltmodem.ko and ltserial.ko. These two files are the “kernel object” files for your modem—they are binary code for your modem driver.

**3. INSTALL THE DRIVER**

a. Uninstall the previous driver
```
sudo rmmod ltserial ltmodem
sudo rm /lib/modules/`uname -r`/volatile/ltmodem.ko
sudo rm /lib/modules/`uname -r`/volatile/ltserial.ko
```
b. Tell Ubuntu where the modem is located
```
sudo mknod --mode=0660 /dev/ttyLTM0 c 62 64
sudo ln -s /dev/ttyLTM0 /dev/modem
```
c. Install the driver
```
sudo mkdir /lib/modules/`uname -r`/other
sudo cp ~/lucent/ltmodem-2.6-alk-8/*.ko /lib/modules/`uname -r`/other
sudo depmod -a
sudo update-modules
sudo modprobe -v ltserial
```
The above modprobe command should output the following:
```
insmod /lib/modules/2.6.15-23-386/other/ltmodem.ko
insmod /lib/modules/2.6.15-23-386/other/ltserial.ko
```
d. Tell Ubuntu to remember the /dev/ttyLTM0 symbolic link
```
sudo gedit /etc/udev/rules.d/ltmodem.rules
```
Enter in the following lines in the new file and save it
```
# ltmodem
KERNEL="ttyLTM0", SYMLINK="modem"
```
e. Delete the temporary directory
```
cd ~
rm ~/lucent -r
```

**4. CONNECT TO THE INTERNET WITH WVDIAL**

Now that the modem driver has been installed, we can connect to the Internet. There are many ways of connecting to the Internet. This section explains how to connect with a program called wvdial.

a. Configure wvdial to dial your modem
```
sudo wvdialconf /etc/wvdial.conf
```

The wvdialconf command should output something like this:
```
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttyLTM0 first, /dev/modem is a link to it.
ttyLTM0<*1>: ATQ0 V1 E1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 Z -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyLTM0<*1>: Modem Identifier: ATI -- LT V.92 Data+Fax Modem Version 8.30
ttyLTM0<*1>: Speed 4800: AT -- OK
ttyLTM0<*1>: Speed 9600: AT -- OK
ttyLTM0<*1>: Speed 19200: AT -- OK
ttyLTM0<*1>: Speed 38400: AT -- OK
ttyLTM0<*1>: Speed 57600: AT -- OK
ttyLTM0<*1>: Speed 115200: AT -- OK
ttyLTM0<*1>: Max speed is 115200; that should be safe.
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
Modem Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Modem Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Modem Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Modem Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Modem Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47

Found a modem on /dev/ttyLTM0, using link /dev/modem in config.
Modem configuration written to /etc/wvdial.conf.
ttyLTM0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```

b. Configure wvdial to connect to your ISP

The wvdialconf command created the file /etc/wvdial.conf. We need to edit this file and specify your ISP's phone number and your username and password. If your ISP phone number is 759-3651 and your username/password is sandra/morph then your /etc/wvdial.conf file should look something like this:
```
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 7593651
Modem = /dev/modem
Username = sandra
Password = morph
Baud = 115200

```
To edit the wvdial.conf file enter
```
sudo gedit /etc/wvdial.conf
```
c. Dial out with wvdial

Dial out by entering:
```
sudo wvdial
```
You should see a bunch of text output and hear your modem dial. After it finishes dialing you should be connected to the Internet. Press CTRL-C to hang up.

**5. CONNECT TO THE INTERNET WITH GNOME NETWORKING**

Now that the modem driver has been installed, we can connect to the Internet. There are many ways of connecting to the Internet. This section explains how to connect with GNOME networking.

a. Configure GNOME networking to dial your ISP

- Goto System->Administration->Networking
- On the Connections tab, select the "Modem connection" item
- Click on the Properties button
- On the Interface properties->General tab, click "Enable this connection" and enter your ISP phone number, and the username/password you connect to your ISP with
- On the Modem tab, enter /dev/modem for the "Modem port"
- Click OK to go back to the Network settings dialog

b. Dial out with GNOME networking

- Goto System->Administration->Networking
- On the Connections tab, select the "Modem connection" item
- Click on the Activate button

You should hear your modem dial. After it finishes dialing you should be connected to the Internet. Press the Deactivate button to hang up.

NOTE: Sometimes the Activate/Deactivate buttons in the Network settings dialog in GNOME don't properly reflect the state of your connection to the Internet. Sometimes, you may find you have to close the Network settings dialog and open it up again, and/or play around with the Activate/Deactivate buttons.

**6. USE THE NETWORK MONITOR APPLET**

The Network Monitor applet is useful for monitoring your dialup connection. The Network Monitor applet is kind of like the "modem lights" that appear in the system tray in Windows 2000/XP.

a. Add the Network Monitor applet to a panel
- Right-click on a panel and select "Add to Panel..."
- Select the Network Montior applet and click on the Add button

b. Configure the Network Monitor applet
- Right-click on the applet and select "Properties"
- In the Connection section, select ppp0 for the "Name"
- Click on the Close button

NOTE: If you don't see ppp0 in the drop-down for the "Name", then close the applet properties dialog, connect to the Internet and try again. As with the Network settings dialog, the Network Monitor applet sometimes doesn't properly reflect the state of your connection to the Internet. Sometimes, you may find you have to reconfigure the applet by selecting something other than ppp0, then selecting ppp0 again to get it to work properly.

- version 1.0.0

---

### Post by sawjew on 2006-07-03
I followed your guide and all went well until I tried to use wvdial.  As soon as I use wvdial or Gnome PPP the system freezes and I have to restart to get anything working.  Now the system will not even reboot, it freezes at "configuring network interfaces" and won't go any further.  I am just going to try using the live cd to delete the wvdial configuration file and see if it will boot up after that.  It did dial using Gnome networking but I didn't check the connection.  Any ideas?

---

### Post by blastus on 2006-07-07
> **sawjew said:**
> I followed your guide and all went well until I tried to use wvdial.  As soon as I use wvdial or Gnome PPP the system freezes and I have to restart to get anything working.  Now the system will not even reboot, it freezes at "configuring network interfaces" and won't go any further.  I am just going to try using the live cd to delete the wvdial configuration file and see if it will boot up after that.  It did dial using Gnome networking but I didn't check the connection.  Any ideas?

Sorry for this very late reply!

What is the output of wvdial before your system freezes? Also, what is the output of the command ```
lsmod | grep '^lt'
```

---

### Post by AndrewCaul on 2006-07-09
Nice Howto. I don't know what it does, but it worked great for me. Now I just need the GNOME Networking app to remember my dial prefix. :-({|=

---

### Post by sawjew on 2006-07-10
Blastus,

I managed to get it working alright by going back to the 386 kernel.  It would not work with the 686 kernel but works fine with the 386 so I'll stick with that.  Thanks for the Howto.

---

### Post by blastus on 2006-07-10
> **sawjew said:**
> Blastus,

I managed to get it working alright by going back to the 386 kernel.  It would not work with the 686 kernel but works fine with the 386 so I'll stick with that.  Thanks for the Howto.

This is a known issue. The lucent modules don't work with the 686 kernel. [Bug #41991 ltmodem use hangs 686 kernel](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/41991)

Great to hear it's working for you on the 386 kernel ;)

---

### Post by Gregy1727 on 2006-07-10
I've just recently moved and high speed is not available here so i am confined to dialup. I have been trying for ages to get my Agere winmodem to work under dapper (near to the point of just going to buy an external dialup modem) I've followed your guide (Very informative, by the way) and got up to modprobe and got this error

```
FATAL: Error inserting ltserial
 (/lib/modules/2.6.15-23-386/other/ltserial.ko): No such device
```

Can you help me with this?

---

### Post by AndrewCaul on 2006-07-11
> **Gregy1727 said:**
> I've just recently moved and high speed is not available here so i am confined to dialup. I have been trying for ages to get my Agere winmodem to work under dapper (near to the point of just going to buy an external dialup modem) I've followed your guide (Very informative, by the way) and got up to modprobe and got this error

```
FATAL: Error inserting ltserial
 (/lib/modules/2.6.15-23-386/other/ltserial.ko): No such device
```

Can you help me with this?

What files are currently in /lib/modules/2.6.15-23-386/other currently?

---

### Post by Gregy1727 on 2006-07-11
```
me@me-ubuntu:~$ ls /lib/modules/2.6.15-23-386/other/
ltmodem.ko  ltserial.ko

```

That's what's so confusing about it. I don't get what's going on and i'm at the end of my rope :(

[http://paste.ubuntu-nl.org/17779](http://paste.ubuntu-nl.org/17779)

---

### Post by blastus on 2006-07-11
> **Gregy1727 said:**
> ```
me@me-ubuntu:~$ ls /lib/modules/2.6.15-23-386/other/
ltmodem.ko  ltserial.ko

```

That's what's so confusing about it. I don't get what's going on and i'm at the end of my rope :(

[http://paste.ubuntu-nl.org/17779](http://paste.ubuntu-nl.org/17779)

I don't think your modem has a DSP (digital signal processor.) As far as I know the driver only works with modems that have a DSP. If your modem has a DSP you should see a line somewhere in the scanModem ModemData.txt file that says something like "The modem has a supported Lucent/Agere DSP (digital signal processing) chipset." 

Also your modem looks like is not being recognized. The scanModem ModemData.txt file should say something like "Communication controller: Agere Systems 56k WinModem (rev 01)" not "Communication controller: Agere Systems: Unknown device 0620"

Does your modem say HSP (host signal processing) anywhere on it? If it does then it doesn't have a DSP.

Here is the relevant output from my scanModem ModemData.txt file:
```
Class 0780: 11c1:0442   Communication controller: Agere Systems 56k WinModem (rev 01)
  SubSystem 141b:9300  Zoom Telephonics Inc: Unknown device 9300
	Flags: bus master, medium devsel, latency 0, IRQ 185
 Checking for IRQ 185 sharing with modem.
O-APIC-level  uhci_hcd:usb2, ltserial

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:0442 141b:9300 debian_version 2.6.15-23-386  4.0.3 4.0.3    i686
 == Checking PCI IDs through modem chip suppliers ==
	  
 The modem has a supported Lucent/Agere DSP (digital signal processing) Mars or Apollo DSP
 (digital signal processing) chipset with primary PCI_ID:  11c1:0442
 DSP=1
```

---

### Post by Gregy1727 on 2006-07-11
> **blastus said:**
> I don't think your modem has a DSP (digital signal processor.) As far as I know the driver only works with modems that have a DSP. If your modem has a DSP you should see a line somewhere in the scanModem ModemData.txt file that says something like "The modem has a supported Lucent/Agere DSP (digital signal processing) chipset." 

Also your modem looks like is not being recognized. The scanModem ModemData.txt file should say something like "Communication controller: Agere Systems 56k WinModem (rev 01)" not "Communication controller: Agere Systems: Unknown device 0620"

Does your modem say HSP (host signal processing) anywhere on it? If it does then it doesn't have a DSP.

Here is the relevant output from my scanModem ModemData.txt file:
```
Class 0780: 11c1:0442   Communication controller: Agere Systems 56k WinModem (rev 01)
  SubSystem 141b:9300  Zoom Telephonics Inc: Unknown device 9300
	Flags: bus master, medium devsel, latency 0, IRQ 185
 Checking for IRQ 185 sharing with modem.
O-APIC-level  uhci_hcd:usb2, ltserial

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:0442 141b:9300 debian_version 2.6.15-23-386  4.0.3 4.0.3    i686
 == Checking PCI IDs through modem chip suppliers ==
	  
 The modem has a supported Lucent/Agere DSP (digital signal processing) Mars or Apollo DSP
 (digital signal processing) chipset with primary PCI_ID:  11c1:0442
 DSP=1
```

I think that may be the problem. I guess that means i'm out of luck? :(

---

### Post by Gregy1727 on 2006-07-11
```
There is a Bad IRQ=255 . Carefully read the related guidance in Modem/ModemData$
 The modem will NOT function because of interrupt assignment: IRQ 255
 Possible corrections are:
   1) to access the  the boot up BIOS change to a non-PNP mode.
   Instructions for accessing BIOS are at:
      http://linmodems.technion.ac.il/resources.html within:  Additional Resources   
2) Within some BIOS setups, IRQ assignments can be changed.
   3) On non-laptop systems moving the modem card to another slot has helped.
   4) Sometimes upgrading the kernel changes IRQ assignment.
```

It said that when i first tried to do it in dapper and breezy. so i went into the BIOS and disabled PNP.  and the disabled PNP output is the one in my above pastebin. Would disabling PNP interfere? I've tried it on 2.6.12 under breezy and now 2.6.15 in dapper so obviously kernel upgrades didnt help. perhaps i need to upgrade to 2.6.17 but i don't know if that'd help.

also, 

```
Agere Systems PCI-SV92PP Soft Modem
```

is what the name of my modem is on "phone and modem options" if that helps.

---

### Post by blastus on 2006-07-11
[quote=Gregy1727]I think that may be the problem. I guess that means i'm out of luck?[/quote]

One thing you may try, and I know this is a crappy suggest, is download SimplyMepis 3.4. It supports Lucent modems out-of-the-box. All you have to do is boot with the live CD and then go into KPPP and setup a connection. 

If the modem works in Mepis then it should work in Ubuntu. If it doesn't work in Mepis then it probably won't work in Ubuntu either. It is possible to download ISOs on dialup, just use a good download manager (like [Free Download Manager for Windows](http://www.freedownloadmanager.org/).) It'll take about 40 hours though.

[quote=Gregy1727]It said that when i first tried to do it in dapper and breezy. so i went into the BIOS and disabled PNP. and the disabled PNP output is the one in my above pastebin. Would disabling PNP interfere? I've tried it on 2.6.12 under breezy and now 2.6.15 in dapper so obviously kernel upgrades didnt help. perhaps i need to upgrade to 2.6.17 but i don't know if that'd help.[/quote]

That one is beyond me. Perhaps this is why your modem isn't being recognized properly. I'd read up on the guides scanModem provides and try it out...you can always revert back to your original BIOS settings, just keep track of them before you change anything. It also helps to document everything you try so you can eliminate what doesn't work.

[quote=Gregy1727]Agere Systems PCI-SV92PP Soft Modem[/quote]

Yep your modem does NOT have a DSP. Soft modems are full-blown Windows modems and usually require proprietary Windows drivers to work. This page, [How to Buy The Right 56K Modem For You](http://www.diamondmm.com/howtobuy56kmodem.php) explains the difference between the types of modems.

Before you give up, and depending on how much time you want to spend on this I'd:
-try some of the suggestions the scanModem provides regarding your BIOS settings (try also putting the card in a different slot)
-try the SimplyMepis 3.4 Live CD and see if it recognizes your modem
-try reinstalling Ubuntu...sometimes an installation just gets botched I've seen it happen

I'm quite sure but, but I could be wrong, that the driver only works with modems that have a DSP but your modem doesn't have a DSP.

---

### Post by Gregy1727 on 2006-07-12
i'm just going to buy an external modem. can you name a good cheap one? I was going to try "Diamond SupraMax external USB 56k modem" but i don't know if it's compatible and I don't want to go through this again.

---

### Post by blastus on 2006-07-14
> **Gregy1727 said:**
> i'm just going to buy an external modem. can you name a good cheap one? I was going to try "Diamond SupraMax external USB 56k modem" but i don't know if it's compatible and I don't want to go through this again.

This is one of my old posts:
> Basically from what I've read is that ALL PCI modems and ALL external USB modems are "soft modems" and you will have great difficulty getting them to work under Linux if it is even possible. ONLY "hard modems" are really supported under Linux. ALL ISA modems and ALL external serial (RS-232) modems are hard modems and should work with Linux. I have an old ISA Rockwell modem that works fine under Fedora Core (on an old machine that has ISA slots) but none of the PCI modems I have work under Fedora Core.

A soft modem is a FAKE modem that does not have the basic circuitry and ROM software to maintain a network connection. Soft modems use the CPU to perform this kind of stuff and so they need specialized drivers and they can drain your CPU performance especially on older machines (< 400 Mhz.) The problem is is that these drivers are usually very proprietary and you'll basically only find drivers for Windows.

A hard modem is a REAL modem that contains the necessary circuitry to maintain network connections. Hard modems are identified by their price--they are usually much more expensive than soft modems because they have the necessary hardware to work without specialized software drivers.

ISA MODEMS: Unfortunately modern computers do not have an ISA slots so you can't use an ISA modem on these. ALL these modems are hard modems because the idea of striping the basic hardware out of the modem (to reduce manufacturing costs) and making it a soft modem didn't become popular until PCI slots were introduced and CPU speeds increased to be able to handle the load soft modems put on CPUs. By that time ISA was being phased out and replaced with PCI.

PCI MODEMS: ALL these modems are "soft modems" and manufacturers don't care to share the specs with anyone so there's little to no support for these under Linux. The PCI bus enables the modem to communicate with the computer fast enough so that the modem can be controlled by software (not hardware.) Some people have said that a "Linux compatible" message on a PCI modem box is an oxymoron -- because they're ALL WinModems. A WinModem is another name for a "soft modem."

EXTERNAL USB MODEMS: ALL these modems are "soft modems" because the USB interface allows the computer to communicate with the computer fast enough that the modem can be controlled by software (not hardware.) You would connect this modem to a USB port on your computer.

EXTERNAL SERIAL MODEMS: ALL these modems are "hard modems" and should work with any Linux distribution. These modems communicate through the RS-232 serial port (a COM port.) They don't/shouldn't require any drivers because all Linux has to do is communicate with the serial port using standard ATA (modem) commands. ALL serial modems are hardware modems because the RS-232 port is not fast enough for the modem to be completely controlled by software (and not hardware.) Therefore you don't need specialized drivers for them.

From what I've read is that the U.S. Robotics 56K external serial (RS-232) modem is your best bet for dialup under Linux. They're expensive but you can use them on any machine and in theory you shouldn't have to mess with drivers and stuff under Linux.

If you do get an external serial modem, make sure your computer has a serial port otherwise you'll have to buy an adapter card (some computers don't have serial ports anymore.)

---

### Post by finnish on 2006-07-22
i thank authors of this topic.
since i moved to DD 6.06, i had a problem with my modem again (solved with 5.10 and 6.04 here [http://ubuntuforums.org/showthread.php?t=93852)](http://ubuntuforums.org/showthread.php?t=93852)).

and i didn't take my route (though they are similar with what is written here), i jsut tried your way.

what was new to me? commands rmmod and update-modules :)

my modem wasn't noticing the carrier,
adding Carrier Check = no and Stupid Mode = yes to wvdial.conf solved problem :)

--
have a nice day

---

### Post by jpx3m on 2006-07-30
i finished the guide without errors and when i try to connect my modem it connects amd after a minute or so disconnect...
also on firefox i cannot browse any webpage... why is that?
any help would be much appreciated...
thanks... 

complete newbie here...

---

### Post by jpx3m on 2006-08-01
thanks blastus... my modem works now! :D  you're the man!

another think... i have to download over 100MB using dial up... lolz... it's g0nna take me 2 days to finish updating... ^__^

---

### Post by blastus on 2006-08-01
> **jpx3m said:**
> thanks blastus... my modem works now! :D  you're the man!

another think... i have to download over 100MB using dial up... lolz... it's g0nna take me 2 days to finish updating... ^__^

Hey that's great :) I was just gonna get to this thread now. What was the problem and how did you fix it?

---

### Post by blastus on 2006-08-01
> **finnish said:**
> i thank authors of this topic.
since i moved to DD 6.06, i had a problem with my modem again (solved with 5.10 and 6.04 here [http://ubuntuforums.org/showthread.php?t=93852)](http://ubuntuforums.org/showthread.php?t=93852)).

and i didn't take my route (though they are similar with what is written here), i jsut tried your way.

what was new to me? commands rmmod and update-modules :)

my modem wasn't noticing the carrier,
adding Carrier Check = no and Stupid Mode = yes to wvdial.conf solved problem :)

--
have a nice day

That's awesome that we can bring the knowledge from the community together and get our stuff working!

I encountered the no carrier problem also. In my case, the modem would dial but then sometime after just hang up. It took me a day or two to figure out that I needed to remove the pre-installed modules with rmmod to get the modem to work. The -v option for the modprobe command saved the day. :)

---

### Post by favad on 2006-08-18
Well I believe I have a similar problem. Although my Lucent modem was picked and drivers installed by Ubuntu 6.06, it gives this no carrier problem after about 30 seconds, after dialing the number. The log is pasted below. I'll be extremely thnkful if someone could help me fix this and tell me how and where am I supposed to give these commands (rmmod and update-modules), although I am a bit familiar with Terminal.

[B]favad@Intel2400mhz:~$ sudo wvdial
--> WvDial: Internet dialer version 1.55
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
favad@Intel2400mhz:~$ sudo gedit /etc/wvdial.conf
favad@Intel2400mhz:~$ sudo wvdial
--> WvDial: Internet dialer version 1.55
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT13198765
--> Waiting for carrier.
ATDT13198765
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT13198765
--> Waiting for carrier.
ATDT13198765[/B]

_Modem configuration is as follows:_
[B][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 38400
New PPPD = yes
Modem = /dev/modem
ISDN = 0
Phone = 13198765
Password = honzpqk
Username = favad[/B]

favad

---

### Post by blastus on 2006-08-19
> **favad said:**
> Well I believe I have a similar problem. Although my Lucent modem was picked and drivers installed by Ubuntu 6.06, it gives this no carrier problem after about 30 seconds, after dialing the number. The log is pasted below. I'll be extremely thnkful if someone could help me fix this and tell me how and where am I supposed to give these commands (rmmod and update-modules), although I am a bit familiar with Terminal.

You have to open up a Terminal to enter the commands. Did you do step 3a in the guide? I experienced the same problem also by not doing step 3a; wvdial would dial but then after 30 seconds or so would report NO CARRIER and hang up. What is the output from the modprobe command in 3c and also the contents of ModemData.txt from ScanModem?

---

### Post by favad on 2006-08-20
Thank you for taking out your time to help me out.
Step 3a is **a. Uninstall the previous driver** and step 3c is **c. Install the driver**. After doing these will I not have to follow the complete guide i.e download, compile and install the drivers from scratch. My drivers were preinstalled by Ubuntu 6.06, and the modem was dialing aswell, so I thought I could fix the **No Carrier** thing right here. So could u please recommend the next coarse of action now.:neutral: 

favad

---

### Post by blastus on 2006-08-20
I haven't actually tried to get the modem to work with the stock kernel modules that come with Dapper. I've always compiled them. Have you tried adding ```
Carrier Check = no 
Stupid Mode = yes
```
to wvdial.conf? If that doesn't work let me know and I'll see if I can get my modem to work with the stock kernel modules.

---

### Post by favad on 2006-08-21
I tried doing that before and I triede it again today but it dint work. Here's the log. 
[B]favad@Intel2400mhz:~$ sudo wvdial
--> WvDial: Internet dialer version 1.55
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT13198765
--> Waiting for carrier.
ATDT13198765
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT13198765
--> Waiting for carrier.
ATDT13198765
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Mon Aug 21 19:56:09 2006[/B]

Thanks for your help anyways.

favad

---

### Post by blastus on 2006-08-21
Can you try the guide from start to finish? When you get to step 3c, post the output of the "sudo modprobe -v ltserial" command. Also can you post the output of the ModemData.txt file from ScanModem so that I can see what kind of modem you have? 

Has the modem ever worked in any Linux distribution before (like Mepis?) I would also contact your ISP and ask them if there are any issues with connecting to them with Linux or a Mac-perhaps your ISP doesn't accept anything but Windows clients (I don't know if that is possible but it may be helpful to look into.) I know some ISPs require special programs or login scripts and such to dial in and connect; I'd ask your ISP about these things so that we can eliminate some of the causes.

---

### Post by favad on 2006-08-22
I prefer not following the guide from scratch because:
1 My modem worked perfectly after I installed the correct drivers in Ubuntu 5.10 (ltmodem-2.6.12-9-386_8.31b1_i386.deb) from here [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/Ubuntu/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/Ubuntu/) It was only when I happily reinstalled Ubuntu i.e 6.06 this time that things got messed up.
2 I used the same ISP which worked with Ubuntu 5.10 to connect. Now I tried another ISP aswell. They recommended me to decreasing modem speed which I did but of no help. And they still works pretty fine with WIN XP.

Was it that the builtin drivers din't work in your case too or u couldn't try. If thats the case I think I'll have to follow the whole guide. Otherwise I really don't wanna fiddle with my builtin support cuz I know I'll get it wrong somewhere.

Moreover I checked the help file aswell but couldn't really find where to download the scan modem file and also the scanmodem command which I have to write in Terminal. May be u could help me fix things up from here, otherwise please let me know if u want me to follow the guide. Thank you again.

favad

---

### Post by blastus on 2006-08-22
favad, I'll take a look at this and get back to you tommorrow. To use ScanModem check out this link:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by favad on 2006-08-23
Ok Thank you. Attached is the modemdata.txt file which might help u sort out things for me. :) 

And a word about your guide. I looked at it deeply and there was **c. Install the stuff you need to compile the driver** Over here do I simply need to follow the corresponding code, or install some specific stuff using Synaptic Package Manager.

favad

---

### Post by blastus on 2006-08-23
> **favad]Ok Thank you. Attached is the modemdata.txt file which might help u sort out things for me.[/quote]

Your modem is definitely supported. I just installed Dapper on a separate partition. Then I typed in ```
sudo wvdialconf /etc/wvdial.conf
``` and edited /etc/wvdial.conf accordingly. The modem dialed out but then later hung up:

```
CONNECT 44000 NoEC
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Aug 23 20:35:23 2006
--> Pid of pppd: 5905
--> Using interface ppp0
--> pppd: &#65533 said:**
> [08]&#65533;&#65533;[05][08]
--> pppd: &#65533;&#65533;[05][08]&#65533;&#65533;[05][08]
--> pppd: &#65533;&#65533;[05][08]&#65533;&#65533;[05][08]
--> pppd: &#65533;&#65533;[05][08]&#65533;&#65533;[05][08]
--> pppd: &#65533;&#65533;[05][08]&#65533;&#65533;[05][08]
--> Disconnecting at Wed Aug 23 20:35:53 2006
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
```

So the default kernel modules do not work with my modem. It is possible that something has changed with my ISP. To verify I'll need to compile the modules and install them as per the guide. 

[quote=favad]And a word about your guide. I looked at it deeply and there was c. Install the stuff you need to compile the driver Over here do I simply need to follow the corresponding code, or install some specific stuff using Synaptic Package Manager.

You only need to follow the commands in the guide. You don't need to do anything with Synaptic except open it then close it (steps 2a and 2b.) I'm not sure why, but you need to open it so that it "registers" your Ubuntu CD with the package management system so that you can enter in the command in step 2c.

Keep in mind that the guide is for a fresh install of Dapper. If you upgrade your kernel, you'll have to compile the modules and install them again. However, there are some steps in the guide that you don't have to do again, like step 3b for example. Once you do it once it gets a lot easier. Eventually you'll be able to get your modem working in less than five minutes. I've been compiling and using the modules for this modem since Hoary so I know they work. Give it a try!

---

### Post by favad on 2006-08-24
I am extremely thankful to you for helping me after going through in detail of every thing. I followed all steps of the guide (installation log file is attached), added 
[B]Carrier Check = no 
Stupid Mode = yes [/B]
and then dialed, but it failed to work. Then I removed 
[B]Carrier Check = no 
Stupid Mode = yes[/B]
and tried again but again of no avail.
Attached are 2 files.
1 Modem Installtion Log with carrier check thingy
2 Modem Installtion Log without carrier check thingy

Maybe this proves out to be of some help for u, and then me;) 

favad

---

### Post by justplayin on 2006-08-24
Hello blastus,

first of all, thank you very much for writing a comprehensive guide how to get a ltmodem working in Ubuntu Dapper!
I'm following this thread for a while, because it worked for my fathers pc, but after a while it stopped working. I know this is a very bad description, but unfortunately I have no access to the pc anymore, so I can't give you any details. I live 400km away from my parents home.
The thing is, after the self-compiled kernel modules stopped working, I went through the installation again and after that it worked again. Could it be, that the new modules don't get loaded correctly, although I followed all the steps in your guide and always had the right output? For example, could it be, that after a hibernate something goes wrong with loading of the modules?

What I would like to do now, is to provide my father with a script, that does all these steps automatically, so that I don't have to walk him through the installation process. He wouldn't make it to the end :wink: 

But then again this wouldn't solve the initial problem: why do the compiled modules after a few reboots behave just like the original kernel modules did (e.g. dial, but no connection gets established)?

But thanks again for your guide, maybe I have some other programm interfering with the modem modules. I'll try to figure out a script for the pc in question.

@favad: Do try to compile the modules yourself. I had the same problems with the original modules and it only worked out after I followed every step of the guide.

justplayin

---

### Post by blastus on 2006-08-24
> **favad said:**
> I am extremely thankful to you for helping me after going through in detail of every thing. I followed all steps of the guide (installation log file is attached), added 
[B]Carrier Check = no 
Stupid Mode = yes [/B]
and then dialed, but it failed to work. Then I removed 
[B]Carrier Check = no 
Stupid Mode = yes[/B]
and tried again but again of no avail.
Attached are 2 files.
1 Modem Installtion Log with carrier check thingy
2 Modem Installtion Log without carrier check thingy

Maybe this proves out to be of some help for u, and then me;) 

favad

You should be connecting at least 44000 bps most of the time. I would try Baud = 115200 in wvdial.conf like this...
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/modem
ISDN = 0
Phone = 13198765
Password = * (your password here)
Username = favad
```
One thing you may want to look into is is the modem initialization string for your modem under Windows. Try putting that string into wvdial.conf where Init2 = the string. 

I would see if you can try your modem again in Ubuntu Breezy just to make sure it is not a compatibility problem with your ISP and your modem can connect at at least 44000 bps most of the time. I'm not really sure what the problem is. :(

---

### Post by favad on 2006-08-25
Well I have to check the modem initialization string for my modem under Windows. And I'm again not very optimistic about installing Ubuntu 5.10 again as that would mean formatting my hard drive. Is it possible to upgrade to Ubuntu 6.06 if I now format and install Ubuntu 5.10 again?

Moreover I contacted [email]DISCUSS@linmodems.org[/email] and they tried to give a solution aswell. I have pasted the mail and also uploaded the zipped version of martian-2.6.15-23-386.tgz :) 
May be u could explain the instructions better, and it might turn out to be useful for the Ubuntu Community aswell. 

[B]I gather from:
$ apt-cache search ltmodem
linux-restricted-modules-2.6.15-23-386
---
that the older ltmodem drives are installed on your System.

Try addiing to /etc/wvdialconf:
Carrier Check   =  no

Then retest
If no improvement try the new package attached.

But firsst find the old ltmodem.ko and ltserial.ko pair with:
$   find /lib/modules/2.6.15-23-386 -name lt*
Record their position

Move the ltserial.ko and ltmodem.ko pair to /root/ for storage
as they might compete with the newer replacement martian_drv.ko driver.

Unpack the Attached within Linux
$ tar zxf martian-2.6.15-23-386.tgz
$ cd martian-2.6.15-23-386
Do NOT do a "make clean" at this time, or you will destroy the driver
Just:
$ sudo make install
$ sudo depmod -a
These steps complete the installation

$ sudo modprobe martian_drv
$ sudo martian_helper
which should announce port creation

Open another console
$ sudo wvdialconf wvtest
should find the modem.

If so, dialout with
$ sudo wvdial
The "Carrier Check  =  no "  is REQUIRED by martian.

Report back

MarvS
ltmodem co-maintainer[/B]

...........................................................................

And one last thing I chnaged the modem initialization string to AT&F E0 Q0 X4 S0=0 &D2 &C1 &S0 V1 W2 a general standard for PCI modems, and also added our favourite carrier thing, and it suddenly got connected :D (I'm writing this post from actually getting online from Ubuntu 6.06) However when I closed the Terminal it got disconnected, or maybe it was just a coincidence and it actually got disconnected for some other reason. Then I tried connecting from GNOME Networking Client and it failed as always. However when I dialed again through Terminal it got connected again, and what happens next I can only tell you tomorrow. 

Thank you very much for helping me throughout this difficult task of **getting my modem on the right track**:p  Lets hope things don't get any worse from here.

favad

---

### Post by blastus on 2006-08-26
[quote=justplayin]The thing is, after the self-compiled kernel modules stopped working, I went through the installation again and after that it worked again. Could it be, that the new modules don't get loaded correctly, although I followed all the steps in your guide and always had the right output? For example, could it be, that after a hibernate something goes wrong with loading of the modules?

What I would like to do now, is to provide my father with a script, that does all these steps automatically, so that I don't have to walk him through the installation process. He wouldn't make it to the end

But then again this wouldn't solve the initial problem: why do the compiled modules after a few reboots behave just like the original kernel modules did (e.g. dial, but no connection gets established)?[/quote]

When you compile the kernel modules you compile them against a specific kernel version. The compiled modules will only work for the kernel version that you compiled them against. If you install a new kernel you have to recompile and install the modules. When the Ubuntu team updates the kernel, they roll it out via the Update Manager. The installation modifies your /boot/grub/menu.lst file so that when you reboot, you will boot to the newly installed kernel by default.

The reason why the modem even dials at all after booting to a new kernel, is because the linux-restricted-modules package is downloaded and installed along with the new kernel. This package contains the precompiled kernel modules for the modem for the specific kernel version the package is listed for.

Unfortunately, when you reboot to the new kernel, your Internet connection won't work anymore. It's a pain because you have to boot to the old kernel, connect to the Internet, and install the appropriate linux-headers package for the new kernel. Depending on the updates, what you have to download can be quite large. Then you have to boot to the new kernel, compile the modules and install them--essentially repeating a lot of the steps again. 

So it's not very user-friendly to the new user! If they don't update their kernel then they are fine, but if they do then they have to go through much of the same process again in addition to booting to the old kernel just to download the headers package for the new kernel. 

I think a script could be made. One of the challenges would be determining the new kernel version so that the appropriate linux-headers package could be downloaded. The user would have to reboot the machine though.

---

### Post by blastus on 2006-08-26
[quote=favad]And one last thing I chnaged the modem initialization string to AT&F E0 Q0 X4 S0=0 &D2 &C1 &S0 V1 W2 a general standard for PCI modems, and also added our favourite carrier thing, and it suddenly got connected (I'm writing this post from actually getting online from Ubuntu 6.06) However when I closed the Terminal it got disconnected, or maybe it was just a coincidence and it actually got disconnected for some other reason. Then I tried connecting from GNOME Networking Client and it failed as always. However when I dialed again through Terminal it got connected again, and what happens next I can only tell you tomorrow.[/quote]

Ah so it was an initialization string :) It seems to me that having to mess with init strings is an ISP thing. You can lookup those AT modem commands on Google if that helps. IMO, one shouldn't need to use the carrier check and stupid mode options to connect to their ISP.

If you are using wvdial, then it has to be running to stay connected (i.e. if you close the wvdial terminal you'll lose the connection.) You could try "wvdial &" to run it in the background but I usually just move the window to another workspace. GNOME networking can be a little quirky--there also doesn't seem to be a place where you can specify an init string anyway. If wvdial works then I'd just stick with it. You can see the output with wvdial and note the speed that your modem connects at. For those reasons I prefer wvdial.

---

### Post by whitehornmatt on 2006-08-26
I also got my modem working under ubuntu 6.06 with the martian driver, and web pages seem to load faster under it than on Windows. I had similar problems to favad too. 
On another note I don't think the initilization string was the problem mine worked fine with: ATQ0 V1 E1 M0 S0=0 &C1 &D2 +FCLASS=0 (which is what wvdialconf told me to use, apart from M0 which I added so I don't annoy people by dialing up)

The fact it worked was also a surprise because when I last tried the martian driver under SLED (I went and tried other distros after ubuntu wouldn't work) it dialed and worked for a few minutes then died, but on ubuntu it's flawless. 

Now I'm off to get my TV card working :)

---

### Post by justplayin on 2006-08-26
Hello blastus,

the modem stops working without changing the kernel version. That's what's funny about it. But don't worry, maybe I did something wrong in the installation process. And in 3 weeks time the pc in question gets broadband access :)

justplayin

---

### Post by whitehornmatt on 2006-08-26
Well the modem worked flawlessly yesterday, but when I went to use it today it wouldn't go. I am now having the same problem I had with the martian driver on SLED, it would connect most of the time, but would only last around 3-8 minutes before it would die and have to reconnect. And in those few minutes I could open pages for one minute but after that nothing would actually load.
Something might have changed with my setup when I rebooted, but I don't know how it can go from working perfectly to barly working in one day. 
I am having to type this from windows ](*,) 
So if anyone has any suggestons of things to try I will try them all.

---

### Post by favad on 2006-08-27
Well Blastus I must thank u again, for helping me get my modem on track. It connects well, doesn't disconnect at is also giving me a higher downloading speed then Win XP. However I'll still be grateful if I could manage my connections from the graphical dialer interface than this Terminal. Can I make and save more than 1 profiles wvdial.conf files, just like u can make more than one connections in Win XP?

Furtheremore there's one more thing. My Lucent Dual Chipset Hardware Modem - 56K FAX MODEM CARD V.92 supposedly supports call waiting option i.e I can get the internet on hold and attend a call. Would it be possible for u to tell the details as I couldn't find elsewhere. Do I need some special drivers or software? I asked my ISP and they said they were providing the facility. I'll be very much grateful if someone could help.

favad

---

### Post by blastus on 2006-09-01
> **whitehornmatt said:**
> Well the modem worked flawlessly yesterday, but when I went to use it today it wouldn't go. I am now having the same problem I had with the martian driver on SLED, it would connect most of the time, but would only last around 3-8 minutes before it would die and have to reconnect. And in those few minutes I could open pages for one minute but after that nothing would actually load.
Something might have changed with my setup when I rebooted, but I don't know how it can go from working perfectly to barly working in one day. 
I am having to type this from windows ](*,) 
So if anyone has any suggestons of things to try I will try them all.

Sorry for this late reply. So the line just disconnects? Does it always disconnect after 3 to 8 minutes? What is the output from wvdial?

I don't know what the issue is but I would try it on a fresh installation of Dapper. I have a separate partition for things like that. Don't install any updates or anything and see if you get disconnected after a few minutes. Also note if you do get disconnected, if it is consistently after 3 to 8 minutes. I'd test it out over the course of several days. 

If you don't encounter any problems, then maybe there's a problem with the driver interacting with your modem on the newer Dapper kernels. It could just be a temporary problem with your phone line and/or ISP, but if it has worked flawlessly in Windows that possibility is ruled out. You can find out your kernel version (hence find out if a new kernel has been installed) by entering ```
uname -r
```

I'm sorry I don't have a real answer. Sometimes these things take a while to figure out--through trial and error and finding out what works and what doesn't and documenting everything.

---

### Post by blastus on 2006-09-01
[quote=favad]It connects well, doesn't disconnect at is also giving me a higher downloading speed then Win XP.[/quote]

That is strange. I wouldn't trust the numbers. I have another 56k modem that reports it connects at 115,000kps (which is like over 13 MB/s) in both Windows 2000 and XP.

> However I'll still be grateful if I could manage my connections from the graphical dialer interface than this Terminal.

In theory, /dev/modem should work if it is setup correctly.

> Can I make and save more than 1 profiles wvdial.conf files, just like u can make more than one connections in Win XP?

If you take a look at the man page for wvdial by entering ```
man wvdial
``` you can use sections in your configuration file. I haven't done it but it should be possible.

> Furtheremore there's one more thing. My Lucent Dual Chipset Hardware Modem - 56K FAX MODEM CARD V.92 supposedly supports call waiting option i.e I can get the internet on hold and attend a call. Would it be possible for u to tell the details as I couldn't find elsewhere. Do I need some special drivers or software? I asked my ISP and they said they were providing the facility. I'll be very much grateful if someone could help.

You could try +pcw=0 in your initialization string. 0 - enable for modem-on-hold and collect caller-id info if available; 1 - Hang up; 2 - Ignore. I don't know if the driver supports this though.

---

### Post by whitehornmatt on 2006-09-02
> **blastus said:**
> Sorry for this late reply. So the line just disconnects? Does it always disconnect after 3 to 8 minutes? What is the output from wvdial?

A late reply is better then none at all :D. It sometimes gets up to around 20 minutes but it is useless for most of that time, it can't connect to any servers after a minute or so. 
The error message I get is 'a modem has hung up the phone' (I can get some logs for you later) Error 16 I think it was.

> I don't know what the issue is but I would try it on a fresh installation of Dapper. I have a separate partition for things like that. Don't install any updates or anything and see if you get disconnected after a few minutes. Also note if you do get disconnected, if it is consistently after 3 to 8 minutes. I'd test it out over the course of several days. 
I will give a bit of background on my experiances with the modem, which may help in diagnosing the problem.
I first got the modem working with Red Hat Linux 9, it was using precompiled kernel modules that I downloaded from a site. It worked perfectly on the 2.4 kernel. On 2.6 kernels my experiance has been fairly good. And by working through a huge amount of documentation for other distros I got it working on Ubuntu Warty (it wasn't untill after I figured it all out myself that I found the Wiki page that explained it all) And it was all well and good until breezy when there was the GCC version trouble, but I still got it working. So it was fine on 2.6.12-whatever that Breezy used. But on dapper, the driver that comes with it won't work, the system hangs completely just before it gets an IP adress in wvdial. I can't move the mouse, no key is responded to, it doesn't even beep, the only way out is reseting. I tried to compile the driver myself like I did on previous versions but it wouldn't let me, (I will edit this post with logs soon). So I was out of ideas, and removed Ubuntu.
I reinstalled it when I saw that someone had success with the martian driver (that actually does compile). So I had a completely fresh Dapper 6.06 install with no updates (apart from build-essentials from the CD). That brings me back to my last two posts, success and then failure.

I will post logs of everything that is remotely relevant soon.

EDIT:
Well I think I may have figured out what was wrong, and it was probably all my own fault. I did a lsmod to see if the ltmodem driver was loaded or not and found to my surprise that the martian_drv module gets loaded at boot. Up until then I always did modprobe first and seemingly I loaded the driver again which may have caused the driver to fight itself for the use of the modem. 
 I am writing this from Ubuntu now and all is going well, hopefully.
I haven't reset yet (as I am downloading packages) so I don't know if this is another one time fluke or not, but I hope it isn't, because I am sick of windows.
The ltmodem driver actually compiled this time (which is why I ended up running lsmod) but it still hangs the system if I try to use it. But if the martian driver stays working I won't worry about it.
All signs are good at the moment, and I will keep you updated

---

### Post by favad on 2006-09-02
Well it was giving me a better download speed than Win XP, I downloaded Real Player 10 for Linux at an average speed of 5kb/s compared to 3.5kb/s in Win XP.

Could u please explain this a bit further **You could try +pcw=0 in your initialization string. 0 - enable for modem-on-hold and collect caller-id info if available; 1 - Hang up; 2 - Ignore. I don't know if the driver supports this though.**

I am presently using this init2 string. **AT&F E0 Q0 X4 S0=0 &D2 &C1 &S0 V1 W2** Which string should I change to see if things work. This or init1. Can you please post exactly what I'm supposed to replace it with. :) 

favad

---

### Post by caseyaberhart on 2006-09-02
hi all, i followed these instructions and the modem works until i reboot, i try to re- insert the modules in step c but it gives me an invalid argument error. if i re-do the steps again it works fine... until reboot. i triple checked my commands.... i cant figure it out. i just want to delete my windoze partition and get on with my life, will ubuntu ever support winmodems 'out of the box'? i have kernel 2.6.15-23-386. please tell me if i'm posting in the wrong place
 
i just read this thread : [http://www.ubuntuforums.org/showthread.php?t=89353](http://www.ubuntuforums.org/showthread.php?t=89353)
 
does anyone know a surefire way of solving this??? i'll try this and delete my post if it works

---

### Post by blastus on 2006-09-04
A lot of folks here are having problems with the driver; specifically rebooting causes the modem to no longer work. There are a few things that will cause this:

1. Upgrading to a new kernel.
2. Not creating a udev rule.

The solution to #1 is to recompile the modules and reinsert them. The solution to #2 is to complete step 3d of the guide. 

If the above does not cover your case then I would recommend you:

1. Run ScanModem and make sure your modem has a DSP.
2. Make sure you uninstall the previous driver (step 3a) before you install the new driver. If you don't then the modem may dial but then you may get a "no carrier" message when you try to connect.
3. Check the modem initialization string (if applicable) in Windows and try that in wvdial.conf (and call your ISP.)
4. Try the "Stupid Mode = yes" and "Carrier Check = no" options in wvdial.conf (see previous posts in this thread.)
5. Finally, reinstall Dapper from scratch and try to get the modem to work. But don't install any updates via update manager. This way you can localize the problem and note what works and what doesn't.

---

### Post by blastus on 2006-09-04
[quote=favad]Well it was giving me a better download speed than Win XP, I downloaded Real Player 10 for Linux at an average speed of 5kb/s compared to 3.5kb/s in Win XP.[/quote]

Download speeds can't be trusted. There are many factors that can skew the measurement. One such factor is compression. With compression you can occasionally get upwards of 10kb/s on some downloads. The actual bandwidth of the connection though is still 5kb/s.

[quote=favad]Could u please explain this a bit further You could try +pcw=0 in your initialization string. 0 - enable for modem-on-hold and collect caller-id info if available; 1 - Hang up; 2 - Ignore. I don't know if the driver supports this though.

I am presently using this init2 string. AT&F E0 Q0 X4 S0=0 &D2 &C1 &S0 V1 W2 Which string should I change to see if things work. This or init1. Can you please post exactly what I'm supposed to replace it with.[/quote]

Search Google for "+pcw=0" There's quite a bit of documentation about it. "+pcw=0" means puts the modem on-hold when a call comes in. "+pcw=1" means hang up the modem when a call comes in. "+pcw=2" means don't do anything when a call comes in. You would add that to the init string. I don't know what init string you should change but I'd just try them both and see what happens.

---

### Post by caseyaberhart on 2006-09-05
> **blastus said:**
> A lot of folks here are having problems with the driver; specifically rebooting causes the modem to no longer work. There are a few things that will cause this:

1. Upgrading to a new kernel.
2. Not creating a udev rule.

The solution to #1 is to recompile the modules and reinsert them. The solution to #2 is to complete step 3d of the guide. 

If the above does not cover your case then I would recommend you:

1. Run ScanModem and make sure your modem has a DSP.
2. Make sure you uninstall the previous driver (step 3a) before you install the new driver. If you don't then the modem may dial but then you may get a "no carrier" message when you try to connect.
3. Check the modem initialization string (if applicable) in Windows and try that in wvdial.conf (and call your ISP.)
4. Try the "Stupid Mode = yes" and "Carrier Check = no" options in wvdial.conf (see previous posts in this thread.)
5. Finally, reinstall Dapper from scratch and try to get the modem to work. But don't install any updates via update manager. This way you can localize the problem and note what works and what doesn't
 

 
i have to un install it and then re-install the driver every time i wnt to use it. it has a dsp, stupid mode and carrier check have no effect, the initialisation string is no different in windows. i have an old copy of warty i could try, would that help? i havent updated dapper in any way as i didn't want to mess with it until i knew that the modem was working correctly.
 
It still disappears on reboot, i've put udev rules in every .rules file i can think would help but it still disappears. if i try and insert the module again without un-installing the modules first i get an invalid argument error.....
 
i will try the latest kernel, maybe that will help?
 
MORE INFO:
 
when i remove the modules it claims that ltserial doesnt exist in /proc/modules not a problem but i thought it might help.
 
it seems to me that it is not loading the drivers on startup, how do i tell it to manually and is there anything i can check to see if it is loading them on startup?
 
the symlinks are fine, they do exist, when i try to create them manually, i get a file exists error so the problem is not there. 
 
if all else fails i think i'll give ubuntu the boot on this machina as it doesnt serve any real purpose if i have to write terminal commands everytime i want to use the internet.
 
any ideas?

---

### Post by favad on 2006-09-07
Well I did search Google for internet strings. Shall update you on that later.

However there's another small issue. My GNOME dialer automatically dials to the internet as soon as I login. The only way to stop is to **uncheck** the "enable the connection checkbox". In that case I have to fill in the username, pass, and number everytime I have to get online.

favad

---

### Post by blastus on 2006-09-08
> **caseyaberhart said:**
> i have to un install it and then re-install the driver every time i wnt to use it. it has a dsp, stupid mode and carrier check have no effect, the initialisation string is no different in windows. i have an old copy of warty i could try, would that help? i havent updated dapper in any way as i didn't want to mess with it until i knew that the modem was working correctly.
 
It still disappears on reboot, i've put udev rules in every .rules file i can think would help but it still disappears. if i try and insert the module again without un-installing the modules first i get an invalid argument error.....
 
i will try the latest kernel, maybe that will help?
 
MORE INFO:
 
when i remove the modules it claims that ltserial doesnt exist in /proc/modules not a problem but i thought it might help.
 
it seems to me that it is not loading the drivers on startup, how do i tell it to manually and is there anything i can check to see if it is loading them on startup?
 
the symlinks are fine, they do exist, when i try to create them manually, i get a file exists error so the problem is not there. 
 
if all else fails i think i'll give ubuntu the boot on this machina as it doesnt serve any real purpose if i have to write terminal commands everytime i want to use the internet.
 
any ideas?

If the command ```
lsmod | grep '^lt'
``` shows ltserial and ltmodem then they are loaded. There's one thing you can try. ```
sudo gedit /boot/grub/menu.lst
``` and add the pci=routeirq option. Look for the line that starts with # kopt (kernel options) and add the pci=routeirq option onto the end of it. 

For example, if the file contains the line: ```
# kopt=root=/dev/hda2 ro
```
you would change it to: ```
# kopt=root=/dev/hda2 ro pci=routeirq
``` Don't remove the # (pound) symbol from the start of the line. Then enter ```
sudo update-grub
``` then reboot. I wish I could be more help but I haven't had any problems with the stability of the driver. As long as there is a udev rule and I haven't upgraded the kernel, I've never had a problem rebooting.

---

### Post by ocean on 2006-09-20
[FONT="Verdana"][/FONT]

Hi Blastus, i must say your doing a great job contributing to the community with such dedication. 

I am having problems simmilar to caseyaberhart, /dev/modem is no longer available after i boot the system.

teh udev rules are set and also the grub is accordingly updated by adding entries you mentioned of.

an additional problem is if dont re boot my system, though wvdialconf gives the exact output which you have mentioned in the thread. 

when i do a sudo wvdial the modem gets successfully initialzed, 
but keeps waiting for the carrier and eventually a "NO DIALTONE" message appears( i have plugged my pstn phone line in the modem line slot)

---

### Post by blastus on 2006-09-25
[quote=ocean]Hi Blastus, i must say your doing a great job contributing to the community with such dedication.

I am having problems simmilar to caseyaberhart, /dev/modem is no longer available after i boot the system.

teh udev rules are set and also the grub is accordingly updated by adding entries you mentioned of.

an additional problem is if dont re boot my system, though wvdialconf gives the exact output which you have mentioned in the thread.

when i do a sudo wvdial the modem gets successfully initialzed,
but keeps waiting for the carrier and eventually a "NO DIALTONE" message appears( i have plugged my pstn phone line in the modem line slot)[/quote]

Hey thanks :)

How do you know /dev/modem isn't available? It should stick and link to ttyLTM0. I would try Googling this one. Maybe it's a connection string problem. Sorry I couldn't be much help. :(

---

### Post by pandan on 2006-09-26
**Try removing the LAN card.**

I was almost about to give up, but realized there was something I needed to understand more.

I installed Kubuntu 6.06.1 on a pentium2.

The installation detected my Netcomm internal PCI modem and installed the driver and device (i saw /dev/LTM0) which the /dev/modem device linked to.

I used wvdial (which has been the most robust for my use) and it did succesfully dial into my ISP (Netbay in Australia) after setting up /etc/wvdial.conf and /etc/resolv.conf .
I didn't use any 'special settings' here.

I was unable to ping succesfully or surf with my browser.
I knew I had a successful connection as my ISP had logged the time in my account.

Wvdial invoked pppd and it seemed pppd was not doing its job properly.

So I read these helps and began to realise that there might be a routing problem- that the pppd might be looking at my LAN card for it's connection.

With the computer off, i took out the LAN card, boot up the computer and voila! the connection worked correctly.  I was able to ping a website and surf to it with my browser (Konqueror).

I don't know the details of what exactly is going on but I now know to read up 'routing.'

BTW. did you know about WWWOFFLE and FETCHMAIL these are my next projects.

---

### Post by Turin Turambar on 2006-10-31
So.......... did anyone try this in Edgy?

I tried everything....... and no luck. ](*,)

---

### Post by pr_009 on 2006-11-05
I installed drivers for my "Lucent V.92 Data+Fax Modem Version 8.23" following your instructions painlessly and then configured wvdial adding "Carrier Check = no" and "Stupid Mode = yes" in wvdial.conf otherwise it wouldn't work. I was very happy when the connection get established thinking that i've accomplished a mission impossible.
I didn't know the worst part had to come. That first connection lasted only 10 minutes and that wasn't it, each time i get disconnected with because of modem hang up with the exit code 16. None of my connections lasted more than 15 minutes.

Then i came across favad threads who was experiencing the same problem but he was able to fix it by tweaking with the INIT STRING. So I also thought about working on the same line. I'm still using a dual boot with WinXp (cuz my modem isn't workin' in dapper). I searched for the .inf file for my modem and in it i found the following init string

	init1 = AT&F E0 &C1 &D2 V1 S0=0 \V1
	init2 = ATS7=60 S30=0 L0 M1 \N3 %C1 &K3 B0    B15 B2 N1 \J1 X4

I tried this in wvdial.conf but among these two init strings \N3 and \J1 didn't work. Anyhow I omitted these two and finally it became

	init1 = AT&F E0 &C1 &D2 V1 S0=0 \V1
	init2 = ATS7=60 S30=0 L0 M1 %C1 &K3 B0 B15 B2 N1 X4

I continued with the above init string and this time my connection lasted for 47 minutes but still it hung up. Next time my connection lasted for 40.7 minutes. At least I got the time for disconnection prolonged but still i was experiencing hung ups and each time with the same exit code i.e. 16.

I'm totally lost now and the situation is getting really frustrating. I don't know what to do to get my modem work flawlessly on ubuntu dapper. I really need an expert advice because i still haven't loose hope nor i will (cuz i'm an optimist).

---

### Post by Bomper on 2006-12-01
> **Turin Turambar said:**
> So.......... did anyone try this in Edgy?

I tried everything....... and no luck. ](*,)

  [http://ubuntuforums.org/showthread.php?t=290963&highlight=lucent](http://ubuntuforums.org/showthread.php?t=290963&highlight=lucent)

  [http://wiki.ubuntu-br.org/LucentWinmodem/Edgy](http://wiki.ubuntu-br.org/LucentWinmodem/Edgy)

---

### Post by blasedeviant on 2006-12-04
Is there anyway to get this to compile under a 64-bit kernel?

---

### Post by Bomper on 2006-12-05
> **blasedeviant said:**
> Is there anyway to get this to compile under a 64-bit kernel?

1.- Download "martian-full-20061203.tar.gz" :
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20061203.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20061203.tar.gz)

2.- Read INSTALL:

"...
...

x86_64 platform. 
----------------

martian_modem is a 32-bit application. It can be built on x86_64 the way prescribed, but you need 32-bit development environment for that. Second option is to use binary built on i386. 

To compile and install module only do 
$ make -C kmodule/ modules
$ su
# make -C kmodule/ install 
... "

---

### Post by bodhi.zazen on 2006-12-07
Nice How-to

This thread has been added to the UDSF wiki.

[PCI_Lucent_winmodem](http://doc.gwos.org/index.php/PCI_Lucent_winmodem)

---

### Post by preciousRoy on 2006-12-23
Excellent howto. I spent some time getting my ltmodem problems on a Thinkpad R31 nailed down last night and I this thread was the first step in getting things working. I did however find that the modem is a controllerless (winmodem) unit BUT is supported with some jiggery pokery in slmodemd. Apparently the HSP versions will work if your chipset is properly supported in the kernel. 

To check this run lspci -vv | grep Modem
it should respond with something similar to:
"0000:00.1f.6 Modem: Intel Corporation 8201CA/CAM AC'97 Modem Controller" (results may vary based on your hardware)

here's what I did:

1) Run scanmodem, it should suggest that you remove and reinsert the module that corresponds to your modem controller for further diagnostics. DO SO and make note of the module name.

2) install the slmodemd daemon from [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/)

I used SLMODEMD.gcc4.tar.gz

simply unpack the file with 'tar -xzf SLMODEMD.gcc4.tar.gz' and copy slmodemd from the resulting directory to /usr/sbin/slmodemd by executing:

cp ./SLMODEMD.gcc4/slmodemd /usr/sbin/slmodemd

3) edit /etc/rc.local and add the following commands between the last comment line and "exit 0"(as an example from my system)

modprobe -r snd-intel8x0m
modprobe snd-intel8x0m
/usr/sbin/slmodemd --alsa -c USA modem:1 -p 0666 -g dialout &

you should now have a functioning device at /dev/ttySL0 which works with wvdial and gnome-ppp that works both as root and your user. Mileage may vary and remember, this relies on your system having a supported ALSA modem module.

---

### Post by xmman on 2007-03-20
:guitar:  (my english is not good) i finally(after six moths) intall my modem in ubuntu 6.06 lts and works  great!!!  but i dont have very much experiencie in linux.....my cuestion is..
how do i that in ubuntu 6.10 ????:popcorn:

---

### Post by le12 on 2007-10-26
i got an error said "couldn't find package build-essential". I am using ubuntu 7.10. please help

---

### Post by pandan on 2007-11-21
I had success with a Agere Lucent under Gutsy 7.10.

See my (pandan) entry.
[http://ubuntuforums.org/showthread.php?t=328050](http://ubuntuforums.org/showthread.php?t=328050)

---

### Post by renatosilva on 2008-01-07
I use Martian driver. I made a script to automate the whole process. It's just about getting the package, and running the script, then I get a GNOME-PPP shortcut on Desktop and ready to connect with everything installed. It's really nice...

**But I'm curious about ltmodem, does anyone got this working with Agere? Everything was fine to me, except when wvdial connected but did not receive DNS servers and related stuff, instead it says the conncetion timed out.**

---

