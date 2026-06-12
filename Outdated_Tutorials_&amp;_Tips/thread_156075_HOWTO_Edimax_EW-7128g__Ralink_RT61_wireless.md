---
title: "HOWTO: Edimax EW-7128g / Ralink RT61 wireless"
date: 2006-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by ?@yk0&amp;^4 on 2006-04-06
RaLink RT61 Wireless chipset HOWTO for Ubuntu Breezy Badger
Written for Edimax EW-7128g wireless card (RT61 version) with a fresh Breezy install

This howto is a modified version of judgekaster's howto at [http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980). Hopefully it'll make installing this card easier for newbies like me... Many thanks to all those who have helped me!

Please note that at the time of writing (2006-04-06), Dapper Drake (Flight 6) does not work with this card (a driver is loaded but does not function correctly).


----------------


If you can't connect to the internet because your wireless card isn't working (!), try to connect using Ethernet (for example, Internet Connection Sharing from a PC or Mac that has a working connection, or direct connection into a router).


----------------


1) Check that you have an RT61 wireless card installed

Open a terminal window and type lspci -n

Somewhere in the list should be the numbers 1814:0301 or 1814:0302



2) Get driver source code from Ralink

Download this file
[http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz](http://www.ralinktech.com/drivers/Linux/2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz)



3) Extract the source code

In the terminal window, navigate to the directory you have downloaded the file to (e.g. type cd /home/yourusername/Desktop)

Extract the source code by typing the following into the terminal window and entering your password when requested:
sudo tar -xzf 2005_1230_RT61_Linux_STA_Drv1.0.3.0.tar.gz



4) Make sure you have the necessary tools to build the drivers

In the terminal window, type sudo apt-get install gcc-3.4 build-essential linux-headers-$(uname -r)

Type Y then Enter to accept and wait for the files to be downloaded.



5) Build the driver

In the terminal window, navigate to the extracted folder by typing the following:
cd RT61_Linux_STA_Drv1.0.3.0_200512230/Module

In the terminal window, type the following:
sudo cp Makefile.6 Makefile
sudo make all

Wait!



6) Copy files to a new location

In the terminal window, type the following:
sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT61STA
sudo cp *.bin /etc/Wireless/RT61STA/
sudo cp rt61sta.dat /etc/Wireless/RT61STA/



7) Copy the driver file to the modules directory and load it

In the terminal window, type the following:
sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/
sudo depmod
sudo modprobe rt61

The driver module should be loaded automatically every time you boot your machine...



8) Check that the driver was loaded

In the terminal window, type the following:
iwconfig

This should show some information for "ra0"

Exit the terminal by typing exit



9) Configure the card in the Networking application

Click on 'System > Administration > Networking'

Click on the 'Wireless connection' section and click 'Properties'

Click the checkbox next to 'Enable this connection' to enable the card

Enter the appropriate settings for your wireless network. It's probably best to try to get the card working without WEP first, so if possible, disable this on your wireless router.

Enter the appropriate IP settings for the connection (if you don't know these, you should probably set it to DHCP)

Click on the DNS tab and enter your wireless router's IP address (otherwise, you'll be able to ping IP addresses, but not domain names).

Click 'OK'



10) Test the network

Unplug whatever other connections you'd been using to connect to the internet, if any.

Try opening up a browser window and typing in [http://www.google.co.uk](http://www.google.co.uk)

If this doesn't work, try pinging your router (eg. type ping 10.0.0.2 into a terminal window) and then an external IP address (e.g. type ping 4.2.2.2). If this works but pinging [www.google.co.uk](www.google.co.uk) doesn't, your DNS settings are wrong.



11) Delete unnecessary files

Delete the downloaded file and extracted folder from your desktop.

You may need to use a terminal to do so (eg. type sudo rm -r /home/yourusername/Desktop/filename)



--------------------

Greg Swinford
Ubuntu Forums username: gregswinford

---

### Post by ?@yk0&amp;^4 on 2006-04-06
This is currently giving me some problems, I'll edit this howto once I've figured out what's happening. (The problem at the moment is that the driver causes the kernel to crash on boot).

Sorry!
Greg.

---

### Post by bruno321 on 2007-04-16
Hi, I'd like to inform that my Edimax EW-7128G worked out of the box with Kubuntu 6.10. I didn't have to do anything the OP mentioned. Perhaps the driver wasn't built in on 5.10, but it is on 6.10 (at least).

---

### Post by jogege on 2007-04-21
I have this exact same card working without any problem in Feisty fawn without any modifications. The only problem so far is that I have to manually configure the IP address since for some reason, DHCP does not work.

I have not also been able to get WPA to work but it connects to my WEP enabled wireless router without any problems whatsoever.

---

### Post by Agent86 on 2007-05-07
I was able to get my Edimax EW-7128G (V3.0) card up and running with DHCP and WPA-PSK/TKIP using the instructions at:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

The instructions are written for Edgy 6.10, but they worked on my Dapper 6.06 Xubuntu install. Nice to hear that things are more out-of-the-box in Feisty.

---

### Post by razta on 2008-03-31
This worked great with me. The only problem is that the link to the driver is different.  Im using ubuntu 7.04

Heres the updated link:
[http://www.ralinktech.com.tw/data/drivers/2007_1210_RT61_Linux_STA_v1.1.2.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2007_1210_RT61_Linux_STA_v1.1.2.0.tar.bz2)

---

### Post by dadec on 2008-06-26
hi

i'm a complete newbie to ubuntu and even linux in general, i've tried the steps outlined here for hardy heron but it doesn't work, can anyone help me with this?  thanks in advance!!

edit: i can get as far as the "make all" command where it wont build the module

---

### Post by dadec on 2008-06-26
ok so i got the wireless card to install but when i reboot into ubuntu it doesn't work unless i run the command

$sudo /sbin/ifconfig ra0 inet IP_ADDRESS up

and reconfigure network manager with the WPA password.

Does anyone know how to get this working automatically every time i boot up?

Thanks

---

### Post by Agent86 on 2008-06-26
I've installed Xubuntu Hardy (and run the Ubuntu Hardy LiveCD) on two machines equipped with the Edimax EW-7128g card/RT61 chipset, and one machine with the older RT2500 chipset. In all cases, all that was required to connect was clicking on the network icon in the panel, then clicking on the name of the network I wanted to connect to. If a key is required, a window will pop-up where you can enter your WEP or WPA key.

If you get a window after that requesting that you enter a password to encrypt your keyring, you can enter your login password, no password at all (insecure), or a separate password (you'll have to remember it - you must enter it every time you connect).

As far as I can see, Ralink chipset wireless is fully integrated with Hardy's Network Manager. No compiling or editing of text files is required - it all works out of the box.

---

### Post by dadec on 2008-06-27
I've tried using network manager but every time i reboot i have to enter in the wpa password again. Should this not be saved in network manager?

---

### Post by Agent86 on 2008-06-27
What flavor are you using: Xubuntu, Ubuntu, Kubuntu?

Are you using the Ralink drivers that come with *buntu or did you compile? In my experience, I haven't had to compile Ralink drivers since 6.06.

Do you have *buntu set to save your sessions on logout?

Does it keep asking for your WPA key, or your keyring password? The first time you entered your WPA key, did you immediately get asked to enter a keyring password? (you should have)

---

### Post by dadec on 2008-06-27
I'm using Ubuntu, I compiled the drivers downloaded from the Ralink site.  I'm not sure i'm using the right Network Manager, it never asked me for a keyring password when I first entered my WPA password.  I'm using the one in >System >Administration >Network

Thanks

---

### Post by Agent86 on 2008-06-28
Is there a reason you compiled the drivers? In my experience, the Edimax EW-7128g drivers that come with Hardy have been working flawlessly. IMO you shouldn't use compiled drivers if the standard modules work - you will have to recompile your drivers whenever your kernel is upgraded.

In a new Ubuntu install, the easiest way to access Network Manager is to simply left-click on the network icon near the upper-right corner of the screen - it looks like two computer monitors connected together.

If you're not sure that the standard drivers work, try booting a Hardy LiveCD. If you can get the LiveCD to connect, then you probably don't need the compiled drivers.

I don't know why it keeps asking for your WPA key. It could be some weirdness between the compiled drivers and Network Manager. Make sure that your sessions are being saved when you logout.

---

### Post by dadec on 2008-06-28
There were no drivers that came with my Hardy Heron, at least it didn't work out of the box.  I'm running the 64 bit version of Hardy, would it make any difference?  I'm asking because a friend also told me that the nVidia drivers don't work on 64 :confused:

---

### Post by Agent86 on 2008-06-28
The proper drivers should automatically load when you install Ubuntu.

Open a terminal, and enter the following command:

```
sudo lsmod
```Then post the results. In particular, we're looking for all lines that begin with "rt"

Also, if you have a LiveCD (usually the CD you installed Ubuntu from), boot from that CD, run the same command from a terminal and post those results here, too. Check to see if you can get your wireless to connect using Network Manager from the LiveCD.

---

### Post by dadec on 2008-06-28
Its ok, I installed the 32 bit version and it worked out of the box :)

---

### Post by melat0nin on 2008-08-28
Hello

I've just bought this card because I read it works well with Ubuntu.  Alas I can't get it to work.

I have been running 8.04.1 for a while now, and today I have put the new card in. Here is the output of sudo lsmod:

```

laurence@melat0nin:~$ sudo lsmod
[sudo] password for laurence: 
Module                  Size  Used by
isofs                  36388  1 
udf                    88612  0 
binfmt_misc            12808  1 
ipv6                  267780  16 
acpi_cpufreq           10796  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  2 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
af_packet              23812  8 
lp                     12324  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_seq_dummy           4868  0 
rt61pci                25472  0 
rt2x00pci              11264  1 rt61pci
rt2x00lib              22528  2 rt61pci,rt2x00pci
rfkill                  8592  1 rt2x00lib
snd_seq_oss            35584  0 
input_polldev           5896  1 rt2x00lib
snd_seq_midi            9376  0 
crc_itu_t               3072  1 rt2x00lib
snd_hda_intel         344728  3 
fglrx                1750468  27 
mac80211              165652  3 rt61pci,rt2x00pci,rt2x00lib
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               15112  1 mac80211
intel_agp              25492  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
eeprom_93cx6            3200  1 rt61pci
button                  9232  0 
agpgart                34760  2 fglrx,intel_agp
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36260  1 
evdev                  13056  3 
snd                    56996  17 snd_seq_dummy,snd_seq_oss,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_hwdep,snd_timer,snd_seq_device
parport                37832  2 lp,parport_pc
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
pcspkr                  4224  0 
ext3                  136712  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  4 
usb_storage            73664  1 
ata_generic             8324  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
libusual               19108  1 usb_storage
pata_acpi               8320  0 
r8169                  32900  0 
ata_piix               19588  3 
pata_jmicron            7040  0 
libata                159344  4 ata_generic,pata_acpi,ata_piix,pata_jmicron
scsi_mod              151436  5 sr_mod,sg,sd_mod,usb_storage,libata
uhci_hcd               27024  0 
ehci_hcd               37900  0 
usbcore               146028  6 usb_storage,usbhid,libusual,uhci_hcd,ehci_hcd
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
laurence@melat0nin:~$ 

```

So it looks as though the driver is installed.  But when I right-click the network icon in the panel and select Edit Wireless Networks, I don't see any in the list.

Also, when I go into network settings and select the properties for Wireless connection, I don't see any SSIDs in the drop-down box (despite the fact I know there are several wireless networks in the vicinity -- I'm connected on one now!).  I did see a list of SSIDs here once, but it hasn't come back.

Any thoughts?

EDIT: I'm able to connect to an unsecured WIFI network by entering its SSID manually into the Network Settings applet, and it works, but I still can't scan and see other networks, nor do I appear to be able to use WEP/WPA2 at the moment.

Any help much appreciated :)

---

### Post by melat0nin on 2008-08-28
I solved the problem by installing Wicd, which is a far better wireless network manager than the standard Gnome tools (IMO).  It detected all the local WiFi networks and connects to them (atuomatically), plus it supports encryption and even has a nice little tray icon which displays activity and signal strength.

Overall I'm very happy with it!

You can find it here:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

