---
title: "How TO - Zydas ZD1211 on Edgy with WPA"
date: 2006-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by shof2k on 2006-10-30
**_HOW TO: Zydas ZD1211 wireless with automatic WPA_**

_Aim_
This is the Edgy version of my previous guide.  As before, I hope this helps you set up a WPA encrypted wireless network when using a ZD1211 based wireless card, such as the Safecom SWLU-5400 dongle.  It comes in 3 parts:
	Part 1 &#8211; Installing the module
	Part 2 &#8211; Installing wpa supplicant


_User level_
Intermedidate. This isn't meant to be a simple list of commands to type in to a terminal because networking has too many options for any one script to cover.  You may need to tweak some of the commands or files to your own system settings.

_Roadmap_
The kernel team are developing a kernel module for this card called ZD1211RW.  Expected to be fully functional in 2.6.18, this should mean that these cards will work &#8220;out of the box&#8221; with the packaged wpa_supplicant.  More details can be found at [http://zd1211.ath.cx/]("http://zd1211.ath.cx/")

_Prerequisites_
You can navigate around the file system using the terminal
You can copy and move files using the terminal
You can edit files from the terminal.
You can untar packages
You can follow bad how to's ;)
All downloaded files are assumed to be in /usr/src.  

_Part 1 &#8211; Installing the module_

1) With Edgy, the delivered wpasupplicant now works using the wext driver.  However I couldn't get the built in zd1211rw module to work.  To remove the module, open a terminal and type
```

sudo modprobe -r zd1211rw	

``` 

2)To stop the module from loading up on a reboot, blacklist this module by editing /etc/modprobe.d/blacklist and entering on a new line

```

blacklist zd1211rw

```

3) The following may not be essential, but it's worth installing to ensure better success with this and any future projects you might do. In a terminal type:
```

 sudo apt-get install build-essential kernel-package gcc libncurses5   libncurses5-dev libqt3-mt-dev wireless-tools libssl-dev 

```

4) Work out which version of the kernel you have by typing:
```

uname -r 

``` 

5) Obtain the correct headers and source for the kernel.  In my case I'm running 2.6.17-10-generic, so I need to get:
```

sudo apt-get install linux-headers-2.6.17-10 linux-headers-2.6.17-10-386 linux-headers-2.6.17-10-generic linux-headers-386 linux-headers-generic linux-source

``` 


6) Unpack the source and create a standard symbolic link.
```

cd /usr/src
sudo tar -xvjf linux-source-2.6.17.tar.bz2
sudo ln -s /usr/src/linux-headers-2.6.17-10 /usr/src/linux-headers
sudo ln -s /usr/src/linux-source-2.6.17 /usr/src/linux

``` 

7) Also make sure you have a link in /lib/modules/2.6.17-10-386/build pointing to /usr/src/linux-headers-2.6.17-10-386.  This should be already present, but if not type:
```

sudo ln -s /usr/src/linux-headers-2.6.17-10-386 /lib/modules/2.6.17-10-386/build

``` 


8.) In /usr/src, download a working version of the ZD1211 driver from [http://zd1211.ath.cx/download/]("http://zd1211.ath.cx/download/"). 
There are multiple versions of the driver and you may need to experiment with different drivers to get one that works for your particular dongle and kernel.  For me, the r77 worked.  
{Edit 5th Nov 2006.  Have upgraded to r83 as this is more stable and doesn't fill my log.  The instructions are identical for this package as well}

9) In /usr/src, untar the source package you selected and edit the Makefile to have the following options:
KERNEL_SOURCE=/usr/src/linux
ZD1211REV_B=0 (set this to 1 if you have a ZD1211B)

10) Compile the module by typing:
```

sudo make
sudo make install 

``` 

11) Copy the resulting zd1211.ko by typing
```

use sudo cp /usr/src/zd1211-driver-r77/zd1211.ko /lib/modules/2.6.17-10-386/build/drivers/usb/net/
[code]

12) Install the module using
[code]
sudo depmod 
sudo modprobe -v zd1211  

```

13) Now connect the dongle and type 
```

dmesg

```

You should see something like:
```

[17180336.828000] zd1211 - http://zd1211.ath.cx/ - r77
[17180336.828000] Based on www.zydas.com.tw driver version 2.5.0.0
[17180336.828000] usbcore: registered new driver zd1211

```

If you get any error codes here, you will need to go back to 8.) and use another driver package.

14) If you have an unsecured network, you should be able to start browsing. To check type:
```
sudo ifconfig 
```	to list all the active network connections 
```
sudo iwconfig 
``` 	to list the status of your wireless connection.
	
You may need to edit /etc/network/interfaces.  To help I've pasted my file below

```

auto lo
iface lo inet loopback

#iface eth0 inet static
#address 192.168.0.135
#netmask 255.255.255.0
#gateway 192.168.0.1

auto wlan0
iface wlan0 inet static
pre-up wpa_supplicant -Bw -i wlan0 -c  /etc/wpa_supplicant.conf -D wext
post-down killall -q wpa_supplicant
address 192.168.0.134
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid mySSID

```

Note I use static addressing, not DHCP.

If you go to SYSTEM-ADMINISTRATION-NETWORKING you can bring up the networking tool to manually disable your ethernet connection and set up wep encryption.  I found keeping only the wireless or wired interface active made my system more stable.

Note if you use a different kernel or recompile your kernel differently, you may well need to do this again.  It's worth posting the driver package that worked for you and the kernel/system used.


_Part 2 &#8211; Setting up WPA encryption_

Unless you're comfortable with the world and their dog also using your wireless network, you should really put some encryption on it.  WEP is trivial to do and trivial to break.  Currently WPA/PSK is much more secure.  

Luckily, the Edgy version of WPA suplicant is compatable with the ZD1211 chipset.  It does this by using the standard wireless extensions (wext) driver interface instead of the Zydas interface.


1) Create  /etc/wpa_supplicant.conf, changing the values in italics:

```

network={
		ssid = &#8220;network id&#8221;
		scan_ssid = 1
		pairwise=TKIP
		psk=&#8221;encryption key&#8221;
		key_mgmt=WPA-PSK
		proto=WPA
	}

```

where network id is your SSID, and encryption key is your router encryption password.

2) Set up your AP to be encrypted, then test the supplicant by typing:
```
	
sudo wpa_supplicant  -i wlan0 -c /etc/wpa_supplicant.conf -D wext -ddddd

```

and reading the output on the terminal for any error messages.  This took a few attempts with my keyboard becoming very slow as the connection was made.  If your connection is dropped repeatedly, you may need a different driver.

3) If you can connect OK, you can terminate the supplicant by typing CTRL+C, and set it in the background by typing into a terminal
```

sudo wpa_supplicant  -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas 

```

4) To have your wireless network come up automatically with wpasupplicant, edit  /etc/network/interfaces to my version above.

5) Then  restart your network, type
```

sudo /etc/init.d/networking restart

```

and hopefully wpa should now be working.........

Hope this helps :)

---

### Post by domino on 2006-10-30
Confirmed working on Edimax EW-7317Ug

Thanks for the how-to! Something is odd about Step 11 that may be misleading to some users. I unpacked the r77 driver to my desktop, not in the /usr/src/ directory. And I use 2.6.17-10-generic, so I don't see the point in copying the zd1211.ko to the /lib/modules/2.6.17-10-**386**/build/drivers/usb/net/ directory. I never boot to that kernel, in fact it's not even an option in grub... anymore :). or unless i'm misunderstanding why it should be copied to the /lib/modules/2.6.17-10-**386**/build/drivers/usb/net/ directory.

Again, thank you for a great easy to read tutorial.

---

### Post by shof2k on 2006-10-31
I'll update step 8.) to say you should download the driver source to /usr/src.

With regards to your second point, my installation of Edgy (beta) only had the 2.6.17-10-generic kernel.  The reason I copy the module to /lib/modules/2.6.17-10-386/... is a hang up from my previous work on Hoary, Breezy, and Dapper.  In theory, doing "make install" after compiling the module should copy it in, but I found I had to manually copy it over.  This  may well be something strange that I've been doing.

Roll on 2.6.18, and I can simply plug n play

---

### Post by domino on 2006-10-31
gotcha shof2k and thanks for the explanation. I can't give feedback on wpa because i use MAC filtering. but your tutorial works for open system though. Much easier than when i first originally got this edimax to work properly.

---

### Post by shof2k on 2006-11-03
No problems.  Be warned though just using MAC filtering really isn't secure these days.  You can spoof a MAC address via arp poisoning, allowing an attacker to become a 'man in the middle' when your on the network.  If you need anymore information, I could find a link to a site that explains it better than I can.

---

### Post by domino on 2006-11-04
It wasn't too hard to find it in *the* google :), so that wont be nessessary. Thanks for offering though.

---

### Post by domino on 2006-11-04
**sho2k,**
 Have you tried these drivers before?

[http://www.atheros.com/RD/ZyDAS/web_driver/ZD1211_USB/Linux/](http://www.atheros.com/RD/ZyDAS/web_driver/ZD1211_USB/Linux/)

---

### Post by gb5757870 on 2006-11-05
Great How-To. Thanks!

---

### Post by gb5757870 on 2006-11-05
Mmm, after creating the wpa_supplicant.conf (and populating with my network details), activating the encryption and running:
sudo wpa_supplicant  -i wlan0 -c /etc/wpa_supplicant.conf -D wext -ddddd

I get the following (blumberg is my network key):

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
Line 2: unknown network field 'ssid '.
Line 3: unknown network field 'scan_ssid '.
pairwise: 0x8
Line 5: Invalid PSK '******'.
Line 5: failed to parse psk '*******'.
key_mgmt: 0x2
proto: 0x1
Line 8: WPA-PSK accepted for key management, but no PSK configured.
Line 8: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Line 8: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request

---

### Post by shof2k on 2006-11-05
Could you paste a copy of /etc/wpa_supplicant.conf?  You should asterisk the PSK out as that isn't too important for debugging and giving away your PSK is the same as having no encryption.

---

### Post by locust on 2006-11-05
i got the same problem

```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
Line 2: unknown network field 'ssid '.
Line 3: unknown network field 'scan_ssid '.
pairwise: 0x8
Line 5: Invalid PSK '”ironlady”'.
Line 5: failed to parse psk '”ironlady”'.
key_mgmt: 0x2
proto: 0x1
Line 8: WPA-PSK accepted for key management, but no PSK configured.
Line 8: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Line 8: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request

```

Here is my /etc/wpa_supplicant.conf file

```

network={
                ssid = "xasis"
                scan_ssid = 1
                pairwise=TKIP
                psk=”******”
                key_mgmt=WPA-PSK
                proto=WPA
        }

```

any help would be greatly appreciated

---

### Post by shof2k on 2006-11-05
mmm that seems ok.  Are there any other lines in your /etc/wpa_supplicant.conf?  

Also what is the result of typing "dmesg|tail" in a terminal?

I thought this may be a simple typo, but it may be something else causing wpa supplicant to fail.

---

### Post by locust on 2006-11-05
no these are all the lines in my /etc/wpa_supplicant.conf  

Here is the result of "dmesg|tail"

```

[17179608.452000] Bluetooth: Core ver 2.8
[17179608.452000] NET: Registered protocol family 31
[17179608.452000] Bluetooth: HCI device and connection manager initialized
[17179608.452000] Bluetooth: HCI socket layer initialized
[17179608.480000] Bluetooth: L2CAP ver 2.8
[17179608.480000] Bluetooth: L2CAP socket layer initialized
[17179608.524000] Bluetooth: RFCOMM socket layer initialized
[17179608.524000] Bluetooth: RFCOMM TTY layer initialized
[17179608.524000] Bluetooth: RFCOMM ver 1.7
[17179612.256000] eth0: no IPv6 routers present

```

---

### Post by gb5757870 on 2006-11-05
My wpa_supplicant.conf as follows: (Since I live in a different country and no-one knows really who I am I didn't bother before with not putting my psk)

network={
		ssid = Priscilla
		scan_ssid = 1
		pairwise=TKIP
		psk=*******
		key_mgmt=WPA-PSK
		proto=WPA
	}


And a dmesg|tail results in:
[17179666.108000] zd1205: (exit) zd1205_init, /usr/src/zd1211-driver-r83/src/zd1205.c line 8570
[17179666.108000] usbcore: registered new driver zd1211b
[17179666.276000] zd1205: (enter) zd1205_open, /usr/src/zd1211-driver-r83/src/zd1205.c line 4353
[17179666.340000] zd1205: (exit) zd1205_open, /usr/src/zd1211-driver-r83/src/zd1205.c line 4436
[17179666.344000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179722.692000] zd1205: (enter) zd1205_close, /usr/src/zd1211-driver-r83/src/zd1205.c line 4896
[17179722.708000] zd1205: (exit) zd1205_close, /usr/src/zd1211-driver-r83/src/zd1205.c line 4962
[17179722.824000] zd1205: (enter) zd1205_open, /usr/src/zd1211-driver-r83/src/zd1205.c line 4353
[17179722.828000] zd1205: (exit) zd1205_open, /usr/src/zd1211-driver-r83/src/zd1205.c line 4436
[17179722.832000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
elvis@elvis-desktop:~$

---

### Post by catanzag on 2006-11-06
locust, sorry, maybe I'm wrong as you already know it, but what about line 5 error?

> **locust said:**
> i got the same problem

```

....
Line 5: Invalid PSK '”ironlady”'.
Line 5: failed to parse psk '”ironlady”'.
key_mgmt: 0x2
proto: 0x1
Line 8: WPA-PSK accepted for key management, but no PSK configured.
.....

```


did you put directly your ascii passphrase? the psk must be codified by essid; here an example by wieman01 in   [http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834).

type the following command in a terminal:

> 
```
wpa_passphrase <your_essid> <your_ascii_key>
```
Resulting in an output like...


```
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
}
```
Copy the "hex_key" (next to "psk=...") and replace <your_hex_key> in the "interfaces" files with it. 


regards

catanzag

---

### Post by gb5757870 on 2006-11-08
Dunno about locust but I followed the instructions from catanzag and I'm still getting the same error.

Err, any idea guys?

---

### Post by iorbell on 2006-12-04
Just wanted to say that this thread and how to is wonderful!! I have all my PC's here at home running Linux (always Ubuntu in the end, having tried many distros), and the one remaining nut I have not been able to crack is getting wireless working with my wpa setup. Until now that is...:)

Great thread. Ian

---

### Post by shof2k on 2006-12-05
Glad it helped :)

I'm afraid I'm not a pure linux techie.  This was really just publishing what I found out by trial and error, hoping that it made life easier for folks.

Personally I can't wait till the 2.6.18 kernel arrives with all of this built in, then I can "retire"

---

### Post by logos382 on 2006-12-29
Hi locust!
I've experimented same problem!
try to change your /etc/network/interfaces with something like this, work for me:

```

auto wlan0
iface wlan0 inet static
wpa-driver wext
wpa-conf managed
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key>
#wpa-conf /etc/wpa_supplicant.conf
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1

```

to made <your_hex_key> look at the post suggested by catanzag! in the same post I found this configuration settings and the work-around to restar your interface at startup!

P.S.
Thanks to shof2k for his how-to! (I never compilde driver by my self)
Thanks to wieman01 for is configuration setting!

---

### Post by logos382 on 2006-12-29
As I sayd before a followed the great how-to of shof2k! compiling end without error
My ZyAIR G-220 work fine. But after a while(1-5 hours), my nettraffic crashes. dmesg reports something like this:

```

[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] 1211_readl failed for 5 attempts...Very Serious<3>zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211: failed reg_urb
[17191401.116000] zd1211:USB ST Code = -19
[17191401.116000] zd1211_writel failed for 5 attempts

```

I tried it with the r83 and r80 both same problem.

Problem involving also USB because when the dongle crash i can't acces to my HDD connected via USB. (sopping in the middle of episode of Lost :evil: )

Anybody there who could help me?

---

### Post by scaryant on 2006-12-31
Thanks, great howto - I just love it when stuff works! :)

This worked for the 3Com USB WiFi Adapter 3CRUSB10075 (WL-545)

---

### Post by trippinnik on 2007-01-13
Anyone have any luck getting this to work under the 2.6.18 or 2.6.19 kernel?  I have it working in 2.6.17 but my custom kernel is only for the higher versions, I don't know why but it doesn't work when I got to 18 or 19. Also I thought the zd1211rw driver was supposed to work in those kernel versions.

---

### Post by shof2k on 2007-01-13
> **trippinnik said:**
> Anyone have any luck getting this to work under the 2.6.18 or 2.6.19 kernel?  I have it working in 2.6.17 but my custom kernel is only for the higher versions, I don't know why but it doesn't work when I got to 18 or 19. Also I thought the zd1211rw driver was supposed to work in those kernel versions.

When compiling the module, did you use the correct headers for the new kernel?  Also try using a later release of the kernel drivers.


I can't speak for the 2.6.18 kernel, but I'd assume the zd1211rw to be at Beta stage and still quite buggy. Hopefully Feisty will have a more stable incarnation.  If not, then I'll step into the breech ;)

---

### Post by trippinnik on 2007-01-13
Yeah, I have the headers cause I built them myself.  This time it wouldn't compile the drivers.  I have heard the zd1211rw drivers are still not that great, so I'd like to use this one and it worked for my custom kernel in 2.6.17.10 but I uninstalled it because I thought there was a different problem with the one I compiled.

---

### Post by trippinnik on 2007-01-13
I get this error:

sudo make
/lib/modules/2.6.19.2/build
/usr/src/zd1211-driver-r83
-I/usr/src/zd1211-driver-r83/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.19.2/build SUBDIRS=/usr/src/zd1211-driver-r83 modules
make[1]: Entering directory `/usr/src/linux-2.6.19.2'
  CC [M]  /usr/src/zd1211-driver-r83/src/zd1205.o
/usr/src/zd1211-driver-r83/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /usr/src/zd1211-driver-r83/src/zd1205.c:42:
/usr/src/zd1211-driver-r83/src/zd1205.h:1332: warning: type qualifiers ignored on function return type
/usr/src/zd1211-driver-r83/src/zd1205.h:1279: warning: ‘zd_readl’ declared inline after being called
/usr/src/zd1211-driver-r83/src/zd1205.h:1279: warning: previous declaration of ‘zd_readl’ was here
/usr/src/zd1211-driver-r83/src/zd1205.c: In function ‘zd1205_validate_frame’:
/usr/src/zd1211-driver-r83/src/zd1205.c:2809: warning: unused variable ‘len1’
/usr/src/zd1211-driver-r83/src/zd1205.c: In function ‘zd1205_translate_scan’:
/usr/src/zd1211-driver-r83/src/zd1205.c:7183: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘U32’
/usr/src/zd1211-driver-r83/src/zd1205.c:7183: warning: unknown conversion type character ‘,’ in format
/usr/src/zd1211-driver-r83/src/zd1205.c:7183: warning: spurious trailing ‘%’ in format
/usr/src/zd1211-driver-r83/src/zd1205.c: In function ‘zd1205_list_bss’:
/usr/src/zd1211-driver-r83/src/zd1205.c:7388: warning: format ‘%2d’ expects type ‘int’, but argument 2 has type ‘U32’
/usr/src/zd1211-driver-r83/src/zd1205.c:7388: warning: spurious trailing ‘%’ in format
/usr/src/zd1211-driver-r83/src/zd1205.c: At top level:
/usr/src/zd1211-driver-r83/src/zd1205.c:7527: warning: type qualifiers ignored on function return type
/usr/src/zd1211-driver-r83/src/zd1205.c:7608: warning: type qualifiers ignored on function return type
/usr/src/zd1211-driver-r83/src/zd1205.c:7697: warning: type qualifiers ignored on function return type
/usr/src/zd1211-driver-r83/src/zd1205.c:7713: warning: type qualifiers ignored on function return type
/usr/src/zd1211-driver-r83/src/zd1205.c: In function ‘CalculateQuality’:
/usr/src/zd1211-driver-r83/src/zd1205.c:10074: warning: unused variable ‘rxOffset’
make[2]: *** [/usr/src/zd1211-driver-r83/src/zd1205.o] Error 1
make[1]: *** [_module_/usr/src/zd1211-driver-r83] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19.2'
make: *** [all] Error 2

---

### Post by sputnik2012 on 2007-01-14
I've compiled the module to the source of the 2.6.17 kernel, which (from the ubuntu packeages) comes as 2.6.17.14-ubuntu1.  lsusb lists my dongle (a generic zydas unamed one). modprobe -v zd1211 works and the device is registered by dmesg.  I can even see it in administration -> device manager.
EDIT: Tried revison B by setting the flag in Makefile

Can't find /dev/wlan0 though.  I've done a make install in the zd1211 source directory, as well as ifdown eth0 before replugging the dongle.

/etc/network/interfaces lists wlan0 inet dhcp.

do I have to do a mknod /dev/wlan0 ? if so what are the minor and major numbers.


Any ideas?

Thanks,
       Rob.

---

### Post by shof2k on 2007-01-15
> **sputnik2012 said:**
> I've compiled the module to the source of the 2.6.17 kernel, which (from the ubuntu packeages) comes as 2.6.17.14-ubuntu1.  lsusb lists my dongle (a generic zydas unamed one). modprobe -v zd1211 works and the device is registered by dmesg.  I can even see it in administration -> device manager.
EDIT: Tried revison B by setting the flag in Makefile

Can't find /dev/wlan0 though.  I've done a make install in the zd1211 source directory, as well as ifdown eth0 before replugging the dongle.

/etc/network/interfaces lists wlan0 inet dhcp.

do I have to do a mknod /dev/wlan0 ? if so what are the minor and major numbers.


Any ideas?

Thanks,
       Rob.

. The zydas drivers were initially at /dev/eth1 then changed later to /dev/wlan0.  Try typing ifconfig into a terminal to see if the system has given you an interface node.

---

### Post by sputnik2012 on 2007-01-16
Thanks shof 2k.  Turns out the drivers are included in the kernel source. [http://www.ubuntuforums.org/showthread.php?t=49070&highlight=zd1201]("http://www.ubuntuforums.org/showthread.php?t=49070&highlight=zd1201")
doesn't include anything baout encryption though

---

### Post by shof2k on 2007-01-16
> **sputnik2012 said:**
> Thanks shof 2k.  Turns out the drivers are included in the kernel source. [http://www.ubuntuforums.org/showthread.php?t=49070&highlight=zd1201]("http://www.ubuntuforums.org/showthread.php?t=49070&highlight=zd1201")
doesn't include anything baout encryption though

That mentions the ZD1201 chipset.  I use the ZD1211 chipset.  I can't say if they are compatible or not.  That may well affect how encryption works.

---

### Post by sputnik2012 on 2007-01-18
EDI: Scrap.

Any way of getting the module to compile with 2.6.19 kernel

---

### Post by heri on 2007-01-18
THANK YOU !

Works perfectly with my 3Com USB WiFi Adapter 3CRUSB10075 on Dapper.
I am using the newest driver r83.

All the best.

---

### Post by shof2k on 2007-01-19
> **heri said:**
> THANK YOU !

Works perfectly with my 3Com USB WiFi Adapter 3CRUSB10075 on Dapper.
I am using the newest driver r83.

All the best.

Sweet as a biscuit.  That warm fuzzy feeling will last me all weekend ;)

I'm looking forward to retiring this guide when zd1211rw is released in Fiesty.

---

### Post by domcio on 2007-01-19
> **gb5757870 said:**
> Dunno about locust but I followed the instructions from catanzag and I'm still getting the same error.

Err, any idea guys?

Hi, you should remove unnecessary spaces from your configuration file, f.e. it should be:
```
ssid=Priscilla
scan_ssid=1
```
and not:
```
ssid = Priscilla
scan_ssid = 1
```

and you should also encrypt your psk just like catanzag said:
```
wpa_passphrase <your_essid> <your_ascii_key>
```

hope this helps,
domcio

---

### Post by trippinnik on 2007-01-23
Hi I had this card working but due to a recent reinstall I had to redo everything.  For some reason I can't get it to work.  I've got the headers and source for the kernel.  I built the module and installed it, but I am getting this error:
[17180567.848000] zd1205: (exit) zd1205_config, /usr/src/zd1211-driver-r83/src/zd1205.c line 2601
[17180567.848000] zd1205: (exit) zd1205_init, /usr/src/zd1211-driver-r83/src/zd1205.c line 8570

It looked like I was able to get it to find the AP from the command line before, but it doesn't connect.  

Also does anyone have any news on the zd1211rw?  
Thanks in advance!

---

### Post by traviesomono on 2007-01-23
Hi! I'm having the same problem:

wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant
network={
        ssid = "Networcilla"
        scan_ssid = 1
        pairwise=TKIP
        psk="A5001F29R4FA7B258E6E3939E5"
        key_mgmt=WPA-PSK
        proto=WPA
}

---

### Post by traviesomono on 2007-01-23
Sorry, ingnoer previous post, it was solved after reading an other time the full information. Thanks for your article.

---

### Post by trippinnik on 2007-01-24
First, thanks for the Howto!  I got my card working before thanks to this, and it means I can sit in my classroom at work and study to get a new job!  Anyway, one recent problem though.  Since I reinstalled Edgy recently I have to use the command dhclient periodically to connect and then reconnect.  Someone mentioned in another post they rolled back the driver, I've tried this but it hasn't helped.  Did something change recently?  Any ideas what could cause this?
I've also given the zd1211rw driver a try in the 2.6.19.1 kernel and 18, but I haven't gotten it to work yet.  I may try harder now.  has anyone had any luck with that?

---

### Post by shof2k on 2007-01-24
> **trippinnik said:**
>  Did something change recently?  
I couldn't say as I can't read the driver source.  I do recommend trying different versions till you find a "stable" module.  I use a static IP on my home LAN, so I haven't had the problem you're experiencing.


> I've also given the zd1211rw driver a try in the 2.6.19.1 kernel and 18, but I haven't gotten it to work yet.  I may try harder now.  has anyone had any luck with that?

I think someone tried it in this thread, but couldn't get it to work. zd1211rw sounds pretty alpha stage at the moment.  If I have a spare weekend, I will give it a try on Fiesty. If anyone can get it working, please post your results in this thread.

---

### Post by dc2447 on 2007-01-25
I can't get wlan0 to come up after loadinbg the driver:
> 
/usr/src/zd1211-driver-r83# dmesg | grep -i zd
[17262304.616000] usbcore: registered new driver zd1201
[17265175.784000] zd1211 - [http://zd1211.ath.cx/](http://zd1211.ath.cx/) - r83
[17265175.784000] usbcore: registered new driver zd1211


> root@dave-kubuntu:/usr/src/zd1211-driver-r83# ifup wlan0
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.
root@dave-kubuntu:/usr/src/zd1211-driver-r83# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

root@dave-kubuntu:/usr/src/zd1211-driver-r83#       

Any thoughts?

---

### Post by rytmisk on 2007-01-31
There are obviously problems with kernels above 2.6.17! I have tried lots of different things with my asus a9rp but only 2.17 will work. Have tried for hours now to get it working on faisty but to no avail. I have even tried linuxant... doesn't work either :( 

IT is the same here btw - it doesn't compile.

I would really like to be able to upgrade some day! Any hints?

Ketil

---

### Post by shof2k on 2007-02-01
> **rytmisk said:**
> There are obviously problems with kernels above 2.6.17! I have tried lots of different things with my asus a9rp but only 2.17 will work. Have tried for hours now to get it working on faisty but to no avail. I have even tried linuxant... doesn't work either :( 

IT is the same here btw - it doesn't compile.

I would really like to be able to upgrade some day! Any hints?

Ketil

Fiesty is still in development, so I expect there would be problems.  Personally, I don't upgrade until it's at RC4 or officially released.

My advice is to stick with Edgy or Dapper for now and have patience for Fiesty.  Conversely for those who can code and debug, perhaps getting zd1211rw is a worth task?

---

### Post by heri on 2007-02-04
> **heri said:**
> THANK YOU !

Works perfectly with my 3Com USB WiFi Adapter 3CRUSB10075 on Dapper.
I am using the newest driver r83.

All the best.

WOW .... I'm on Faisty Fawn Herd 3 now and glad to confirm that the dongle just WORKS OUT OF THE BOX ....!!!

WOW..

---

### Post by shof2k on 2007-02-04
> **heri said:**
> WOW .... I'm on Faisty Fawn Herd 3 now and glad to confirm that the dongle just WORKS OUT OF THE BOX ....!!!

WOW..

Is that with WPA out of the box too?  :D

---

### Post by heri on 2007-02-04
> **shof2k said:**
> Is that with WPA out of the box too?  :D

Well, I just tried it in the live cd mode, did not configure anything.

The adapter is still recognized as eth1... but it feels good when something just works .. :D

I think final version of Fiesty will be really a nice distro ......

All the best,

---

### Post by trippinnik on 2007-02-05
You don't need fiesty.  I just built the new 2.6.20 kernel which added the USB Id for my Planax version.  I am not sure if that's even necessary but the main thing that prevented me from getting in to work in the earlier versions was that I didn't grab the firmware and put it in the right place. 
Here's what I did:

I built the new kernel.  You can follow this guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

the module for the zd1211rw is included by default but you may want to customize your kernel while your compiling anyway.  

next grab the firmware from here:

[http://sourceforge.net/project/showfiles.php?group_id=129083&package_id=187875](http://sourceforge.net/project/showfiles.php?group_id=129083&package_id=187875)

follow the instructions from the included Readme, it says basically put the files in the /lib/firmware/zd1211 directory (you have to create the zd1211 directory)

Plug in the card and check dmesg.
should be all good.  I even have network manager going now and could pick up like 8 networks around my apartment.  I could really only find one of the before.  

Let me know how you guys do with this.  Don't worry compiling the kernel seems difficult but it just takes some time.  I prefer to use xconfig instead of menuconfig because it has more information about my choices.

---

### Post by DarthFrog on 2007-02-11
I did an "apt-get update && apt-get dist-upgrade" today, which installed the 2.6.17-11-generic kernel.   The kernel zd1211rw driver works with the wpa_supplicant wext driver just fine out of the box, no need for downloading & compiling source.

My wpa_supplicant.conf file:

network={
	ssid="Camp_Chaos"
	scan_ssid=1
	pairwise=TKIP
	key_mgmt=WPA-PSK
	proto=WPA
	#psk="******"
	psk=A_Long_Hex_String
}

My /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

pre-up  /sbin/wpa_supplicant -B -w -D wext  -i eth1 -c /etc/wpa_supplicant/wpa_supplicant.conf
post-up route add default gw 192.168.1.1
post-down killall -q wpa_supplicant

--
Cheers,
Rob

---

### Post by shof2k on 2007-02-13
Thanks for the update Rob.  My waters are feeling better that Feisty will give Zydas support out of the box.  

Once this is done, perhaps we can then do bluetooth

---

### Post by kir on 2007-06-15
Upgrading to Feisty caused my zd1211 to stop working, and now I fail to rebuild it (to reinstall) due to the "linux/congig.h - no such file or directory".

Is there different instructions for feisty?

Thanks,
Boris

-----------------------------------------------------------------------------------
UPDATE:
ZD1211 really works out-of-the box in Feisty.
The point is that after **upgrading** from Edgy one should:
- modprobe back the original zd1211rw
- remove 'blacklist zd1211rw' line from /etc/modprobe.d/blacklist

---

