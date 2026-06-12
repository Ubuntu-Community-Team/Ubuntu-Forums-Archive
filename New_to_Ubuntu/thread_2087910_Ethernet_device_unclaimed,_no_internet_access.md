---
title: "Ethernet device unclaimed, no internet access"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by helmcken on 2012-11-24
[FONT="Century Gothic"][SIZE="2"][COLOR="Black"]I have been searching forums and trying to solve this problem since I purchased this new FragBox in February2012! I found the closest situation in this thread [http://ubuntuforums.org/showthread.php?p=9449490]("http://ubuntuforums.org/showthread.php?p=9449490") so I followed Pytheas22's suggestions in reply #6 but still had no luck! I was able to successfully download, save, burn a copy then save to desktop the file named "compat-wireless-2.6.tar.bz2". But when I entered the commands in terminal that were suggested, nothing worked as it did for the other person, sadly. 
    I am including the terminal's output for several queries which I hope you will find useful in helping me solve this headache! 
sudo ifconfig -a
lspci
ifup eth0
ifconfig -a
lshw -C Network
sudo lshw -C Network
lspci -nn

```
heathcliff@FragBox:~$ sudo ifconfig -a

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:112 errors:0 dropped:0 overruns:0 frame:0

          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:8648 (8.6 KB)  TX bytes:8648 (8.6 KB)



heathcliff@FragBox:~$ lspci

00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)

00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)

00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)

00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 05)

00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)

00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)

00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)

00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)

00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)

00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)

00:1f.0 ISA bridge: Intel Corporation Device 1c44 (rev 05)

00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)

00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)

01:00.0 VGA compatible controller: nVidia Corporation Device 1200 (rev a1)

01:00.1 Audio device: nVidia Corporation Device 0e0c (rev a1)

03:00.0 USB Controller: Device 1b21:1042

04:00.0 USB Controller: Device 1b21:1042

heathcliff@FragBox:~$ ifup eth0

ifup: failed to open statefile /var/run/network/ifstate: Permission denied

heathcliff@FragBox:~$ sudo ifup eth0

Ignoring unknown interface eth0=eth0.

heathcliff@FragBox:~$ ifconfig -a

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:112 errors:0 dropped:0 overruns:0 frame:0

          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:8648 (8.6 KB)  TX bytes:8648 (8.6 KB)



heathcliff@FragBox:~$ lshw -C Network

WARNING: you should run this program as super-user.

  *-network UNCLAIMED     

       description: Ethernet controller

       product: Intel Corporation

       vendor: Intel Corporation

       physical id: 19

       bus info: pci@0000:00:19.0

       version: 05

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list

       configuration: latency=0

       resources: memory:fa300000-fa31ffff memory:fa328000-fa328fff ioport:f040(size=32)

heathcliff@FragBox:~$ sudo lshw -C Network

  *-network UNCLAIMED     

       description: Ethernet controller

       product: Intel Corporation

       vendor: Intel Corporation

       physical id: 19

       bus info: pci@0000:00:19.0

       version: 05

       width: 32 bits

       clock: 33MHz

       capabilities: pm msi bus_master cap_list

       configuration: latency=0

       resources: memory:fa300000-fa31ffff memory:fa328000-fa328fff ioport:f040(size=32)

heathcliff@FragBox:~$ lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0100] (rev 09)

00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)

00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)

00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1503] (rev 05)

00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)

00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)

00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)

00:1c.4 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 5 [8086:1c18] (rev b5)

00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)

00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)

00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c44] (rev 05)

00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c02] (rev 05)

00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)

01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1200] (rev a1)

01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0e0c] (rev a1)

03:00.0 USB Controller [0c03]: Device [1b21:1042]

04:00.0 USB Controller [0c03]: Device [1b21:1042]
```

    There is no wireless capability for the FragBox so I simply MUST get the wired, ethernet connection established ASAP. ALL help and suggestions greatly appreciated! Thank-you for reading this. [/COLOR][/SIZE][/FONT]

---

### Post by PapaNerd on 2012-11-25
What is the contents of your /etc/network/interfaces file?

---

### Post by helmcken on 2012-11-26
[COLOR="Black"]** I REALLY LOVE Ubuntu; I TOTALLY DESPISE having to endure Win7 until I repair this problem! Please help!** Thank-you for your interest PapaNerd. Perhaps I should have mentioned this specifically, but I am new enough to Ubuntu that I have the *most limited acquaintance* with the commands needed to enter into the terminal to complete your suggestion.```
etc/network/interfaces 
```Please, if you could supply the commands needed, I will happily enter those into terminal and post back the results. I tried ```
-l etc/network/interfaces 
```thinking that would _list_ them. Then I tried ```
-s etc/network/interfaces 
```hoping it would _show_ them. No luck, so I am writing this. I will continue to check in at least once daily, hoping for a solution. Again, thank-you for taking an interest![/COLOR]

---

### Post by PapaNerd on 2012-12-10
Sorry, I haven't been checking this thread regularly.

The command would be "cat /etc/network/interfaces" (without the quotes).

---

### Post by helmcken on 2012-12-12
[FONT="Century Gothic"][SIZE="2"]PapaNerd, Thank-you for your continuing interest! I tried to get the info you're after. However, when I used terminal and entered ```
cat/etc/network/interfaces
``` the terminal returned the following: ```
bash: cat/etc/network/interfaces: No such file or directory
```  Then, I thought maybe you meant run as root user, so I tried ```
sudo cat/etc/network/interfaces
``` and, after supplying the password, the terminal returned the following: ```
command not found 
```Is there any other commands you'd like tried? 

    [COLOR="Blue"]_[SIZE="3"]For everyone else[/SIZE]_: [/COLOR][FONT="Comic Sans MS"][COLOR="Red"]PLEASE HELP!! WAITING SINCE FEBRUARY 2012  This computer runs flawlessly and is dual-booted with Ubuntu and Win 7. The internet works perfectly through Internet Explorer hard wired ethernet. THERE IS NO WIRELESS DRIVER HARDWARE INSTALLED. I seek ethernet, hard wired access to internet from Ubuntu. All hardware is present, but necessary software is missing. Please instruct which files to burn to disk so I can let Ubuntu update and correct itself. Thank-you![/COLOR][/FONT][/SIZE][/FONT]

---

### Post by Bashing-om on 2012-12-12
helmcken; Hi !
For that above terminal command (valid) insert a space between "cat" and "/etc" ;
Or copy/paste this same code:
```
 cat /etc/network/interfaces
```[INDENT][INDENT]just try'n to help < == BDQ

[/INDENT][/INDENT]

---

### Post by squakie on 2012-12-13
Or just attach the file to a post here - avoid the cat and then us asking for more ;)

---

### Post by GordThompson on 2012-12-13
Hello helmcken.

If the command

```
cat /etc/network/interfaces
```returns just the following (as I expect it will)...

[FONT=Courier New]auto lo
iface lo inet loopback
[/FONT]
...then I suspect that you'll need to do something similar to what was proposed in the thread you cited earlier, but with a different driver.

Start by grabbing the latest e1000e driver source from

[http://sourceforge.net/projects/e1000/files/e1000e%20stable/2.1.4/e1000e-2.1.4.tar.gz/download]("http://sourceforge.net/projects/e1000/files/e1000e%20stable/2.1.4/e1000e-2.1.4.tar.gz/download")

Copy the e1000e-2.1.4.tar.gz file to your Ubuntu desktop like you did before.

Now, before you try the following commands you should do two things:

1. Put your Ubuntu install CD/DVD in the CD/DVD drive of your machine.

2. From the Ubuntu menu bar at the top of the screen, click...

System > Administration > Software Sources

...and make sure that the option...

Installable from CD-ROM/DVD
[x] Cdrom with Ubuntu 10.04 'Lucid Lynx'
   
...is selected.

Now, in a Terminal window, use these commands to ensure that you have the tools required to build a new version of the e1000e driver

```
sudo apt-get install build-essential
sudo apt-get install dkms
```Next, use these commands to unpack the driver archive and then switch to the directory that contains the driver files

```
cd /usr/src
sudo mv ~/Desktop/e1000e-2.1.4.tar.gz ./
sudo tar xvfz e1000e-2.1.4.tar.gz
cd e1000e-2.1.4
```Now you need to create a configuration file. Enter the command

```
sudo nano -w dkms.conf
```and in the empty editor window type the following

```
PACKAGE_NAME='e1000e'
PACKAGE_VERSION='2.1.4'
CLEAN='make -C src/ clean'
MAKE='make -C src/ BUILD_KERNEL=$kernelver KERNELDIR=/lib/modules/${kernelver}/build'
BUILT_MODULE_NAME[0]='e1000e'
BUILT_MODULE_LOCATION='src/'
DEST_MODULE_LOCATION[0]='/updates'
AUTOINSTALL='yes'
REMAKE_INITRD='yes'
```To save the file, hit [Ctrl-X], then say "Yes" to confirm the save, and hit [Enter] to confirm the file name.

Now use the following commands to build and install the new driver

```
sudo dkms add -m e1000e -v 2.1.4
sudo dkms build -m e1000e -v 2.1.4
sudo dkms install -m e1000e -v 2.1.4
```When that's done, remove the CD/DVD from the drive, reboot Ubuntu, and see if your network adapter is recognized.

(Thanks to user 'srocrown' for posting detailed instructions here:
[http://ubuntuforums.org/archive/index.php/t-1741686.html)]("http://ubuntuforums.org/archive/index.php/t-1741686.html")

---

### Post by helmcken on 2012-12-21
[FONT="Century Gothic"][SIZE="2"][COLOR="Black"]Hello Gord Thompson! You are correct that entering```
 cat /etc/network/interfaces
``` does indeed return the following, as expected! ```
auto lo iface lo inet loopback
``` I have tried unsuccessfully to follow your helpful detailed advice. From the beginning of your instructions, I have managed to use my other Ubuntu os computer to locate the e1000e -2.1.4.tar.gz file. I successfully burned it to its own separate disc.  But, frustratingly, whenever I insert the disc containing the iso for Ubuntu 10.04 'Lucid Lynx' into the CD/DVD drive of the problem computer, I get the message box```
 UPGRADE VOLUME DETECTED. Would you like to try to upgrade from it automatically? Cancel, Start Package Manager or Run upgrade buttons available.
``` When I select **Run Upgrade** and enter my password, 2 messages appear one on top of the other. The underneath message is entitled **Distribution \upgrade** and is blocked from proceeding by the top box:```
 **Unable to get exclusive lock**. This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first. Has a CLOSE radio button available.
``` Sometimes it says it doesn't exist.  So, this was as far as I could get! I was able to ensure that under System > Administration > Software Sources...that the option...*Installable from CD-ROM/DVD [x] Cdrom with Ubuntu 10.04 'Lucid Lynx'* ...**is** selected.  
Next, I opened the terminal to enter these commands ensuring I have the tools required to build a new version of the e1000e driver. ```
sudo apt-get install build-essential
sudo apt-get install dkms 
```  after supplying my sudo password, this was returned: ```
E:Could not get lock /var/lib/dpkg/lock - open (11 : Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
``` (Once again, it doesn't like that dkms term.) The Ubuntu iso disc is in the CD/DVD drive. So, I am blocked at this point. Your next set of commands begins with cd. I wondered which cd? The Ubuntu iso or the e1000e disk? In either case, when I enter```
 cd/usr/src
``` terminal simply states that no such file or directory exists! Of course by now, the Update manager sits permanently as a red triangle on the top, being some 272 days out of date now!Likewise up top, the network manager reports no network connection. On the wired tab,auto ethernet was last used never. 
Please don't give up. I'm sure you're on the right track! Thanks again!  [/COLOR][/SIZE][/FONT]

---

### Post by GordThompson on 2012-12-22
At this point I think it would be best if you seriously considered a fresh install of 12.04 LTS. Search around for discussions on the various Desktop Environments (DEs); I quite like Unity (the new default DE in Ubuntu 12.04), but you might prefer Xubuntu or something else. In any case, download the ISO for the flavor of *buntu you want to try, burn it to CD/DVD, use it to boot your FragBox and choose "Try Ubuntu" (aka "Live CD" mode), and see if it works better for you.

---

### Post by helmcken on 2013-08-30
[FONT=Century Gothic][SIZE=2][COLOR="#000000"]Hello everyone. *At last*, **success!!** It was a matter of waiting. When I bought this FragBox, it was *absolutely* brand new, including the all-important motherboard. The Maximus IV Gene-Z/Gen 3 by Asus that was installed had _*literally_ just been released two weeks prior to my purchase*!! Simply put,** the network drivers that were needed were _not included_ in the first general LTS release of Ubuntu 12.04**. Naturally, they weren't in any earlier Long Term Release favourites like ver. 8.04 (Hardy Heron) or ver.10.04 (Lucid Lynx?) either. Also, there were no fixes, easy, terminal-talk-style, hard, not anything.* I waited until October of 2012 before they came out with the solution*! By now, the forums (particularly here in Absolute Beginners Section!) were**_ full_** of people _asking this same question_. Ubuntu released LTS ver 12.10, but that didn't work either.
   **Here's what did work:** the very next release is called **_Ubuntu LTS ver 12.04.2_** - desktop -i386. **Notice that on the end of the release number is the .2** - that is _hugely important_!!** The missing network drivers for both ethernet and for wireless are part of the improvements included in the .2 release that were not present in the original release! ** I can see this situation reoccuring *every time* someone buys a super-new computer. So, **please remember, it may take awhile before the drivers/software you seek are even released!!** As for me, I am now back to happily enjoying my Ubuntu!! Without disrespecting Windoze further, I was ready to dropkick my new rig off the balcony! So grateful there's this alternative operating system! SITUATION SOLVED!!! :grin: [/COLOR][/SIZE][/FONT]

---

