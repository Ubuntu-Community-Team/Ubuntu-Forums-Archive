---
title: "Howto: Setup &amp; Install 2WIRE USB Dongle in Ubuntu Gutsy and Heron"
date: 2008-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by defconoii on 2008-02-25
The 2WIRE USB Adapter comes with 2Wire home portals, it has long plagued Ubuntu and Linux users alike, I have had one for quite a while and it has been collecting dust, to get this running on Ubuntu lets follow these directions:

Now what we must do is grab The drivers that are located in the root directory of the 2WIRE installation cdrom or wget them from my hosting:
wget [http://www.users.qwest.net/~choice240662796/WlanUIG.inf](http://www.users.qwest.net/~choice240662796/WlanUIG.inf)
wget [http://www.users.qwest.net/~choice240662796/WlanUIG.sys](http://www.users.qwest.net/~choice240662796/WlanUIG.sys)
then what we must do is sudo ndiswrapper -i WlanUIG.inf
Lets see if it loaded properly shall we?
type: 
$ ndiswrapper -l
wlanuig : driver installed
	device (1630:0005) present
Sweet! Its loaded now we are half way finished!

Then lets write module alias configuration for all devices:
sudo ndiswrapper -ma

Now lets write module install configuration for all devices:
sudo ndiswraper -mi

ok then finally lets load up ndiswrapper kernel module to see if it works!
sudo modprobe ndiswrapper
Now lets type:
sudo iwconfig
Now you should see a new wireless adaptor listed "wlan0, if not your fuqd and you need to ask for help!

Now that the driver is loaded we can move to the next step, installing wpa_supplicant:
sudo apt-get install wpasupplicant

Now lets configure Wpa Supplicant! 

Now that wpa supplicant is installed we need to grab some basic information:
Wireless SSID
Wireless psk passphrase
Once you have these we need to issue this command:
 wpa_passphrase 
usage: wpa_passphrase <ssid> [passphrase]

Ok you see whats above? Great now Lets follow the usage instructions above

wpa_passphrase 2WIRE31337 mysecurepassword

Here is the output:
network={
	ssid="2WIRE31337"
	#psk="mysecurepassword"
	psk=1a2043835852349c1c8288323f8899324259ce3845c1ee44fab7f3ee4ee8eb20
}
Ok now lets open up wpa supplicants config file
sudo gedit /etc/wpa_supplicant.conf

Now you need to edit your config file like so

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="2WIRE31337" <-- your ssid of course
       psk=1a2043835852349c1c8288323f8899324259ce3845c1ee44fab7f3ee4ee8eb20 <-- generated psk above
       key_mgmt=WPA-PSK
       proto=WPA
       pairwise=TKIP
}
Ok Save the file with ctrl-s and exit gedit.

Now we have to make wpa_supplicant load when system boots, so go back to the terminal window and type:

sudo gedit /etc/network/interfaces

Here is the static network configuration, make sure it is setup properly according to your router/network settings:
auto wlan0
iface wlan0 inet static
address 192.168.1.66
netmask 255.255.255.0
wireless-essid 2WIRE31337
gateway 192.168.1.254
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

Alternately Here is the Dynamic Configuration, uncomment to use:
#auto wlan0
#iface wlan0 inet dhcp
#pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant

Now once /etc/network/interfaces is properly configured lets ctrl-s to save then exit.

Now if all goes well you should be connected, lets find out!
sudo /etc/network/interfaces restart
ping [www.yahoo.com](www.yahoo.com) 
Enjoy 
defcon
[http://www.ubuntu-unleashed.com](http://www.ubuntu-unleashed.com)

---

### Post by stussy on 2009-01-11
> Now you should see a new wireless adaptor listed "wlan0, if not your fuqd and you need to ask for help!

I am fuqd,

```
root@ubuntu:~# sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

where do I ask for help?

---

### Post by winterlove on 2009-05-07
> **defconoii said:**
> The 2WIRE USB Adapter comes with 2Wire home portals, it has long plagued Ubuntu and Linux users alike, I have had one for quite a while and it has been collecting dust, to get this running on Ubuntu lets follow these directions:

Now what we must do is grab The drivers that are located in the root directory of the 2WIRE installation cdrom or wget them from my hosting:
wget [http://www.users.qwest.net/~choice240662796/WlanUIG.inf](http://www.users.qwest.net/~choice240662796/WlanUIG.inf)
wget [http://www.users.qwest.net/~choice240662796/WlanUIG.sys](http://www.users.qwest.net/~choice240662796/WlanUIG.sys)
then what we must do is sudo ndiswrapper -i WlanUIG.inf
Lets see if it loaded properly shall we?
type: 
$ ndiswrapper -l
wlanuig : driver installed
	device (1630:0005) present
Sweet! Its loaded now we are half way finished!

Then lets write module alias configuration for all devices:
sudo ndiswrapper -ma

Now lets write module install configuration for all devices:
sudo ndiswraper -mi

ok then finally lets load up ndiswrapper kernel module to see if it works!
sudo modprobe ndiswrapper
Now lets type:
[http://www.ubuntu-unleashed.com](http://www.ubuntu-unleashed.com)

Edit: 

here I get the following Message

WARNING: All config files need .conf: /etc/modprobe/ndiswrapper, it will be ignored in a future release.

I installed mandriva in my other computer and I just ha to do the 

sudo modprobe ndiswrapper and network manager connected automatically my usbport to the gateway and grabbed Internet. I didnt got the message Avove in mandriva... so I gess that message is what doesnt let me connect to internet in Ubuntu... how do I solve It.

[COLOR="Gray"]old part... 
Ok... I have to connect to a USB port for internet... like it was a ethernet port... until the part: 

modprobe ndiswrapper

everything is fine... the module is loaded... no new adaptor... how do I set USB as the port for the network...?
and how can I configure the network to take the Internet or local network from the USB port... Im using the windows xp driver for this... is a 2wire 2700HG gateway...[/COLOR]

Thanks...

---

### Post by noabody on 2009-07-19
I had a slightly different go at this today on Ubuntu Jaunty x64.  With the help of Puppy linux forum member Tempestuous I did the following to use native linux drivers instead of ndiswrapper.  First off I needed a development ready environment (see [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) ). I only did the first step

sudo apt-get install build-essential checkinstall

I then downloaded and extracted the latest drivers from linuxwireless.org

[http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)

I edited file p54usb.c in subfolder drivers/net/wireless/p54 and added the following to section:

	/* Version 1 devices (pci chip + net2280) */
	{USB_DEVICE(0x1630, 0x0005)},	/* ZCOM XG702B */

After that I did:

make
sudo make install
sudo make unload

Furthermore a firmware is required based on kernel version.  Uname -a reveals that my Jaunty is 2.6.28.13 so I went to [http://linuxwireless.org/en/users/Drivers/p54](http://linuxwireless.org/en/users/Drivers/p54) and downloaded the file for: 2.6.28 kernels and older; specially for 2.6.28; USB 1st generation (ISL3886 + net2280); 2.13.1.0.arm.0; required filename isl3890usb.

I know that looks weird but that's the section and filename (the filename isn't apparent because it's a link and shows up when you try to download).  Either rename the file upon download or later then copy it to /lib/firmware overwriting the original.

sudo cp isl3890usb /lib/firmware

dmesg suggests that the driver seeks out isl3886usb and then falls back to isl3890usb so you could probably name it isl3886usb as well.

After that I simply plugged in the adapter and used the Ubuntu networking wizards to set up the connection.


FYI:  This USB device is supported by Linux natively BUT it's vendor and device id's are not in the source code, that's all I changed.  In Windoze that information is stored plain text in the driver information file which, in this case, is wlanUIG.inf.  It reads like this:

[DeviceList.NTx86.5.1]
 %DCB_DESC_STR_XG302_CARDBUS%		= WLAN_DCB1.XP,        PCI\VEN_1260&DEV_3886&SUBSYS_00031630
 %DCB_DESC_STR_XG902_PCI%		= WLAN_DCB2.XP,        PCI\VEN_1260&DEV_3886&SUBSYS_00041630
 %WLAN_USB702_DESC_STR%                 = WLAN_USB1.XP,	       USB\VID_1630&PID_0005

I could download the Windoze device driver for any adapter and get it to work simply by adding the correct VID and PID (a dangerous proposition since I could load the wireless adapter using device drivers for say a webcam or just about anything).

Linux is not as easily manipulated as Windoze in this regard, I have to manually add the DEV/PID to the source code and recompile.  It's still not that hard but there is definitely more work required.  For those Windoze users with a NET2280+ISL3886 based adapter, the drivers for this one seem to be the newest available anywhere on the internet (dated 2007 with beta Vista support).  You can get the drivers here: [http://www.2wire.com/pages/driversanddocumentationsupport.php?did=14](http://www.2wire.com/pages/driversanddocumentationsupport.php?did=14) for awhile and edit the .inf file for your particular brand.

Some other notes are that I have been unable to find a Windoze 64-bit driver for the Prism54 adapters, only beta Vista support and no Windows 7 support.  I am free to compile 32 or 64 bit drivers for Linux based on the distribution and for Ubuntu in particular, once I setup my connection parameters, I can plug any wireless adapter in anywhere and it works.  In Windoze a wireless adapter's connection parameters are saved per slot, so simply moving a USB device from one slot to another requires a whole new profile.

---

### Post by jdp on 2009-07-24
I've had a 2wire 802.11g USB Wireless Adapter for a couple years and had found it useless in Linux.  Now I know better!  Have you submitted your changes to the devs to get this to be added to the next kernel release?

---

### Post by jdp on 2009-08-02
I took some time tonight to do the driver edit and add the USB ID of the 2wire device to the p54 driver file.  I confirm that this does work and is a simple fix that should be filed with the devs.  I dunno if anyone has yet, but if I don't hear back from some one in a while I'll see about doing it myself.

Such a simple fix!  Great job!

---

### Post by noabody on 2009-08-04
Hey jdp, I'm glad it worked for you.  I'm sort of a power user when it comes to operating systems but I'm no dev.  I did post a message to linuxwireless.org and would expect that support may be added to their future p54 driver releases.

I don't think this worked until kernel 2.6.28 since I couldn't get it to work in Puppy Linux kernel version 2.6.25.15.  It looks to me like the newer p54 driver was geared toward 2.6.28 and finally had enough bug fixes to get this particular adapter up and running.

I'm pretty oblivious when it comes to development and it never occurred to me to forward this to Ubuntu devs since that is like putting the information on the top branch of the tree.  Don't get me wrong, I want this to work out of the box in Ubuntu but I want it to work in every other Linux distro as well and I have no pull with linuxwireless at the bottom of the tree.

---

### Post by Nightsurfer on 2009-12-12
noabody, thank you for your clear, concise and comprehensive post on getting this 2wire adapter to work. I think I got within 98% of success, but I wonder whether my eeepc 900 32 bit (i386) running easy peasy 1.5 (ubuntu 9.04) with kernel 2.6.30.5-ep0 may be seeing things a little differently.

dmesg reports:

[ 1526.219934] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 1526.343679] usb 1-4: New USB device found, idVendor=1630, idProduct=0005
[ 1526.343688] usb 1-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 1526.344063] usb 1-4: configuration #1 chosen from 1 choice
[ 1526.621177] usb 1-4: firmware: requesting isl3886usb
[ 1586.620651] usb 1-4: (p54usb) cannot find firmware (isl3886usb)
[ 1586.620663] usb 1-4: firmware: requesting isl3890usb
[ 1646.630662] p54usb: probe of 1-4:1.0 failed with error -2
[ 1646.630786] usbcore: registered new interface driver p54usb

I downloaded the .arm file designated for 2.6.29 and above and copied it to /lib/firmware/ both as isl3886usb and isl3890usb to cover all options as 3886 is requested first I felt that this approach should cover all options and decrease activation times. As your original post is the only one which has got me anywhere close so far, I would appreciate any thoughts on this. regards and TIA.
NS.

---

