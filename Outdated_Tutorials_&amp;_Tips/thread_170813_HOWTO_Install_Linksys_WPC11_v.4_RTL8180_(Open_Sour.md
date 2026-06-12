---
title: "HOWTO: Install Linksys WPC11 v.4/ RTL8180 (Open Source)"
date: 2006-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by monomaniacpat on 2006-05-05
First of all, I owe a debt of gratitude to [Linux Wireless LAN support](http://linux-wless.passys.nl) for providing an excellent listing of available open source drivers for Linux - something that should be everyone's first stop on route to wirelessness. Also, a big thank you to this forum for helping me resolve some very peculiar issues, which I am still not entirely sure I understand, but which you are free to look at [here](http://www.ubuntuforums.org/showthread.php?t=167026).

I must admit that I am still not an expert at this and don't entirely understand what I'm doing. But, the steps I am about to explain allowed me to access my wireless network, and this is partly designed for posterity, in case I ever have to re-install the drivers. Hopefully, it will also prove helpful for others.
[SIZE="2"]
--------------------------------------------------------------------------

Having visited the Wireless LAN support webpage, I followed a link to [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/) Following those instructions and not knowing what CVS was, I proceeded to download the tarball from sourceforge. However, having tried to make the files I came up with the following error:

```
/home/patrick/Downloads/rtl8180-0.21/r8180_core.c:3632: error: structure has no member named `pci_name'
```

A little bit of googling uncovered the fact the pci_dev structure no longer contains the slot_name member. Which essentially means the file it was looking for no longer exists. A little more googling led me to [this]("http://www.cwelug.org/cgi-bin/wiki.cgi?Wpc11v4#source") transcript. From this I learned that it was going to be necessary to acquire the drivers from source through CVS.

------------------------------------------------------------------------[/SIZE]

OK, the HOWTO part:

Preliminaries:

Download and install CVS either through synaptic or enter the following command in a terminal:

```
sudo apt-get install cvs
```

In order to make the relevant files later on you will need to have build-essential installed, either through synaptic or, again, in terminal:

```
sudo apt-get install build-essential
```

[SIZE="4"]I recall downloading another file when I was having trouble with the tarball, so it may be that you need that, too. If anyone has problems with any of the instructions, please let me know and I'll try and find out what you need.[/SIZE]

The download and installation:

Enter the following commands from a terminal:

```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/rtl8180-sa2400 login
```

Press enter when asked for a password.

```
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/rtl8180-sa2400 co -P rtl8180-sa2400-dev
```

Navigate to the directory where you downloaded the file (by default the one you are already in.)

```
cd rtl8180-sa2400-dev/
```

Now, make the drivers.

```
sudo make
```

Next, to load the modules permanently into the kernel (so that they will be inserted whenever the hardware is detected).

```
sudo make install
```

At this point you may need to restart your computer. Alternatively, if you'd rather insert the modules manually enter the following commands:

```
sudo insmod ./ieee80211_crypt-r8180.ko
sudo insmod ./ieee80211_crypt_wep-r8180.ko
sudo insmod ./ieee80211-r8180.ko
sudo insmod ./r8180.ko
```

OR (not tested)

```
sudo for I in "ieee80211_crypt-r8180.ko ieee80211_crypt_wep-r8180.ko ieee80211-r8180.ko r8180.ko" ; do modprobe $I ;
```

To check that they have been successfully inserted enter:

```
lsmod | grep r8180
```

Which should provoke this response:

```
r8180                  59276  0 
ieee80211_r8180        33668  1 r8180
ieee80211_crypt_wep_r8180     8064  0 
ieee80211_crypt_r8180     8324  2 ieee80211_r8180,ieee80211_crypt_wep_r8180
```

At this point it should simply be a case of going to network settings (System>Administration>Networking) and entering all your details under the newly created wireless device. However, you must be very certain about the settings entered here - a simple mistake can make it impossible to connect. In my case I put it on the wrong WEP key type (ASCII as opposed to Hex).

Hopefully, that should be it. However, to get a few more diagnostics and check whether your card is working, you can also enter:

```
ifconfig wlan0 up
iwlist wlan0 scan
```

Which should get your terminal to spew out the connection status of the wireless device and (hopefully) tell you what you're connected to.

```
wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:27:09:5E
                    ESSID:"Router_Name"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Quality=96/100  Signal level=-46 dBm  Noise level=-256 dBm
                    Encryption key:on
```

If this information is displayed you should have no problem connecting to your wireless network.

In order to make your device connect at startup, you need to edit /etc/network/interfaces (sudo gedit /etc/network/interfaces) to include the following information:

```
auto wlan0

iface wlan0 inet dhcp
wireless-essid Router_Name
wireless-key XXXX
```

Replacing "wlan0" with the name of your device (which you can find out by entering iwconfig in a terminal). Or, for a static IP:

```
iface wlan0 inet static
address 192.168.2.105
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1
```

Again, replacing IP's as appropriate. Of course, most of this terminal activity should be auto-filled by using the GUI, but this does allow us to make sure there are no mistakes.

------------------------------------------------------------------------

I've come to the conclusion that wireless threads are thin on the ground because every user will face different problems with the relevant packages they have installed, the distribution they are using, etc. But I hope that this thread will be useful for people as a starting point. If anyone has any problems, just PM me or suggest alterations here.

Yours,

mono.

---

