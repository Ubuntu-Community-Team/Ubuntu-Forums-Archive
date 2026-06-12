---
title: "Mini HowTo: Install a Samsung ML-2571N Network Printer"
date: 2007-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by ArgentSilver on 2007-01-20
The documentation that comes with the Samsung ML-2571N for installation under Linux is abysmal. But it's a very nice, inexpensive network printer that works flawlessly under Linux once setup correctly. This setup was done under 32-bit Edgy. No support for the guide; use at your own risk!

Two CDs come with the printer, a Network Utilities disk and a Software/Drivers disk. You'll need them both. And the nastiest part of the install: you need a Windows PC hooked up to the network to do the initial configuration of the printer, since Samsung only supplies Windows software on the Utilities disk.

1. Start with the printer hooked up to your network and turned on.
2. Install the SetIP utility on your Windows machine from the Network Utilities disk.
3. Run the SetIP utility. It should scan your network and find the printer. If you have firewall software which prevents outgoing traffic from SetIP (e.g. ZoneAlarm), you may need to temporarily disable it.
4. Use SetIP to set a static IP address into the printer. If you have DHCP on your network, supposedly the printer will already be using it, but it didn't work on mine. In any case, even with DHCP, you can usually limit the range of addresses that are supplied, leaving a range that can be used for static assignment. Use one! You're now done with initial setup.
5. On your Ubuntu machine, go to System -> Administration -> Printing, and select Printer -> Add Printer. When the Add A Printer box comes up, select 'Network Printer' of type 'CUPS printer (IPP)', then type in the URL [http://xxx.xxx.xxx.xxx:631](http://xxx.xxx.xxx.xxx:631), where the xxx is the static IP address you assigned to the printer.
6. In the next box, select Samsung, put the Software/Drivers disk into your CD drive and select 'Install Driver'. Navigate to the /Linux/noarch/at_opt/share/ppd directory, and open the 2570 series ppd file. Select this to drive the printer; give it a name or description, and you're done!

A couple of notes: 
a. You can accomplish the same end as steps 5 & 6 by going into the CUPS web interface in your browser at [http://127.0.0.1:631](http://127.0.0.1:631) and installing the driver that way.
b. Access the printer's control interface by putting its IP address into your browser [http://xxx.xxx.xxx.xxx](http://xxx.xxx.xxx.xxx)

Edit: Later additional info from other users (see below) shows that a Windows-free install CAN be done (excellent!). I'm still using the same printer under Hardy and it's still a good cheap laser printer. I don't know whether it's still a current model, but probably later models can be installed in the same way.

Edit: Under Intrepid, Windows-free installation is now simple. When you start to install a new printer, Intrepid now looks for and finds the Samsung ML-2571N on the network. You can use your web browser to connect to the printer's web interface if you need to set a static IP address. All you need is the PPD driver file from the CD to finalize the setup.

---

### Post by jamb on 2008-01-06
> **ArgentSilver said:**
> The documentation that comes with the Samsung ML-2571N for installation under Linux is abysmal. But it's a very nice, inexpensive network printer that works flawlessly under Linux once setup correctly. This setup was done under 32-bit Edgy. No support for the guide; use at your own risk!

Two CDs come with the printer, a Network Utilities disk and a Software/Drivers disk. You'll need them both. And the nastiest part of the install: you need a Windows PC hooked up to the network to do the initial configuration of the printer, since Samsung only supplies Windows software on the Utilities disk.

I recently installed the Samsung ML-2571N (networked laser printer) on several Linux PC's, all running Xubuntu 7.10 and printing now works great.

Here follows a Windows free installation. :)

Note b) in the above thread is the starting point

Open your browser with the printer IP address, which you can find in many ways

i) Check if your router have an attached devices list with IP addresses 
ii) Do a broadcast ping 
iii) install nmap and scan the network

Depending on number of hosts on the network adjust the count, here we use 5. 
The network is 192.168.0.0/24 thus the highest address is the broadcast address. 
Type in a terminal:
```

ping -c 5 -b 192.168.0.255

```
If you have many hosts on the network, install nmap and run host discovery:
```

sudo apt-get install nmap 
sudo nmap -sP 192.168.0.0/24

```

nmap prints some more useful information:
```

Starting Nmap 4.20 ( http://insecure.org ) at 2008-01-01 22:54 CET
Host 192.168.0.1 appears to be up.
MAC Address: 00:0F:76:65:47:A5 (Netgear)
Host 192.168.0.4 appears to be up.
MAC Address: 00:13:16:33:B5:47 (D-Link)
Host 192.168.0.21 appears to be up.
Host 192.168.0.30 appears to be up.
MAC Address: 00:16:99:65:AF:50 (Samsung Electronics Co.)
Nmap finished: 256 IP addresses (4 hosts up) scanned in 42.142 seconds

```

The Samsung printer is easy to identify. 
Point your browser to the printer address:
```

http://192.168.0.30

```

1. Click the Network Settings tab, in menu 'General' printer can be given a host name (optional)
2. Select the TCP/IP on left menu and assign IP address assignment method as, 'STATIC'
3. Fill in your preferred printer IP address, and any applicable other network information below. Click apply and close the browser. 

The remainder of the ML-2571N driver installation follows tweedledee's thread (but those steps for the ML-2571N are described in detail below):
[http://ubuntuforums.org/showthread.php?t=341621&highlight=samsung+driver]("http://ubuntuforums.org/showthread.php?t=341621&highlight=samsung+driver")

====================================================
See the updated procedure at the bottom of the page
====================================================
(skip this)
Download the latest Linux Unified Printer Driver.
Samsung have now a global driver archive (accessible by [www.samsung.com](www.samsung.com)), this will redirect you to your country archieve. 
If the UnifiedLinux-driver is named without a date/release code, then the final step below, about the symbolic PPD link, is not required. 

Type in a terminal to confirm that you got it:
```

cd Desktop
ls -l

```
Move the downloaded driver to /opt
```

sudo  mv  20070720154941625_UnifiedLinuxDriver.tar.gz /opt

```
Untar and and set ownership of files:
```

cd /opt
sudo  tar  -xzvf  20070720154941625_UnifiedLinuxDriver.tar.gz
cd cdroot
sudo chown  -R  root:root *

```
Run the driver install script and follow the instructions:
```

sudo Linux/install.sh

```

Below step is not required if the UnifiedDriver name starts without yearmonthday-code.

Set the PPD path.
Note also for Gutsy and Hardy that there were a change (level 'custom' was removed) in the path /usr/share/ppd/.../samsung.
```

sudo ln -s  /usr/share/cups/model/samsung   /usr/share/ppd/custom/samsung

```

Again: the installer changed the path from unified driver 2.00.97 or later, 
the right side in the last command should be without /custom/: aka: /usr/share/ppd/samsung

Here you may/may not require to use KDE/Gnome Add Printer utilities.. 
but in Xubuntu [Gutsy/Hardy/Intrepid] nothing more was needed than described above.
======================================================================

**UPDATE**: Thanks to the excellent work by tweedledee, follow these steps to install your laser printer.
This short procedure have been tested on Ubuntu Intrepid (8.10), Jaunty (9.04), Karmic (9.10) and Debian Lenny (5,0).
Open /etc/apt/sources.list in an editor with: 
> 
sudo nano /etc/apt/sources.list

add one line at the end:
> 
deb [http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/)  debian   extra

Save and exit. Download the required gpg-key, and add this to the trusted keys for your packaging system:
> 
sudo apt-get update
cd /etc/apt
sudo wget [http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg](http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg)
sudo apt-key add 
 
Install the required packages:
> 
sudo apt-get install samsungmfp-driver samsungmfp-configurator-qt3 cupsys-common

To start the Samsung graphical GUI installer (as root):
> 
cd /opt/Samsung/mfp/bin
sudo ./Configurator

Once the Samsung application start, push the [Add printer...] button once, and wait ~15-30s. Then complete the guide. Enjoy your printer!

---

### Post by SZVSZ on 2008-05-02
> **ArgentSilver said:**
> the nastiest part of the install: you need a Windows PC hooked up to the network to do the initial configuration of the printer, since Samsung only supplies Windows software on the Utilities disk... Use SetIP to set a static IP address into the printer. If you have DHCP on your network, supposedly the printer will already be using it, but it didn't work on mine.


I found that SETIP.exe can be installed and run in Wine. It functions perfectly (in Wine) so no need for a Windows installation!

I've got a SAMSUNG ML-2851ND networked printer. I had the same problem with DHCP as you did - for whatever reason my router didn't seem to be able to assign it an IP address on the internal network. SETIP.exe had to be used before it became pingable. A network utilities disk wasn't included in the box, so I had to download SETIP.exe from the samsung website.

---

