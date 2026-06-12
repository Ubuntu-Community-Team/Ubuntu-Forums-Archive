---
title: "HOWTO: RT61 on Egdy Eft with WPA"
date: 2006-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by phq on 2006-11-10
This guide is for all Edgy users running a RT61 chipset WLAN card. If you follow all the steps described below, you should have running a WPA (WPA-PSK/TKIP) connection to your Access Point.
Please let me know if you have any suggestions or if something is wrong.
I've got everything running doing all these steps on a fresh and clean installation of Kubuntu Edgy Eft with standard options.

**1.) Download the latest original Ralink RT61 drivers from:** 
```
$> wget http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz

```
Note: I wrote the guide for 1.0.4.0, but it is no longer available for download. However, it should work with the new driver as well. If it does, please post that.
**2.) Compile the Module**
Install the kernel headers corresponding to your kernel (In most cases it should be installed by default, but it seems there are derivates which won't do that)
```
sudo apt-get install linux-headers-`uname -r`
```

```
$> tar xvfz RT61_Linux_STA_Drv1.0.4.0.tar.gz
$> cd RT61_Linux_STA_Drv1.0.4.0/Module/
$> cp -f Makefile.6 Makefile
$> make all
```

**3.) Get root**
```
$> sudo su
```

**4.) Prepare Config directory for the module**
```
#> mkdir -p /etc/Wireless/RT61STA/
#> cp *.bin /etc/Wireless/RT61STA/
#> cp rt61sta.dat /etc/Wireless/RT61STA/
```

**5.) Install Kernel Module**
```
#> cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/
#> depmod
```

**6.) Configure module via rt61sta.dat (use binary edit mode)**
```
#> vi -b /etc/Wireless/RT61STA/rt61sta.dat
```
See readme file in Modules directory for description.
For WPAPSK Authentification I've changed settings as following:
```
SSID=<SSID of Access Point>
NetworkType=Infra
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=<Secret WPA key>
```
NOTE: For some reason there seem to be problems if the WPA key is longer than 52 characters and/or contains non-alphanumeric characters.

**7.) Remove broken preinstalled Module**
> #> modprobe --remove rt61pci

**8.) Load module rt61**
```
#> modprobe rt61
```

**9.) Check whether device ra0 has been loaded**
```
#> iwconfig
```

**10.) Configure and test device**
```
#> ifconfig ra0 <IpAddress> netmask 255.255.255.0 up
#> ping <Access Point>
```

**Now everything SHOULD work! ;)**

Of course we want the device to be up after next reboot, so let's edit some more files:

** Edit modprobe and network config files**

**Add broken module to blacklist:**
```
#> echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
```

**Add the new module to module autostart**
```
#> echo 'rt61' >> /etc/modules

```
**and create an alias**
```
#> echo 'alias ra0 rt61' >> /etc/modprobe.d/aliases
```

**Now add the interface with your settings to /etc/network/interfaces**
```
#> vi /etc/network/interfaces
```

comment out the preconfigured wlan0 interface and add following lines (with your ips)
For a static IP address:
```
iface ra0 inet static
address <your ip>
netmask 255.255.255.0
gateway <ip of your access point>
auto ra0
```

If you want to use DHCP (thanks to neveceral):
```
iface ra0 inet dhcp
wireless-essid YOURESSID
auto ra0
```


**Reboot - Try - Be Happy! :-D **

---

### Post by RyanTMulligan on 2006-11-10
Your tutorial is missing an important step. You do not have people downloading the kernel headers anywhere.

---

### Post by techstop on 2006-11-10
The drivers were in Dapper, are they broken in Edgy? ie. why do you need to compile from source? Looks to be much the same instructions as found here;

[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

...apart from compiling the module.

---

### Post by zakhooi on 2006-11-11
> **techstop said:**
> The drivers were in Dapper, are they broken in Edgy? ie. why do you need to compile from source? Looks to be much the same instructions as found here;

[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

...apart from compiling the module.

Well for me the procedure in the first post DID work whereas the procedure in the other thread did not work for me.

So, thanks a lot!

---

### Post by poshmoggy on 2006-11-11
phq you are a star! For a week I've been following various guides, but none seemed to do the trick. Came across yours an hour ago and followed it to the letter. And now I have wireless again. Woohoo :)

---

### Post by Raubsau on 2006-11-11
I just can't get it working with WPA...

It worked fine without encryption, with WEP128bit, but not with WPA-PSK and I defenitly do not know where to look for the (i bet it's my human...) error.

Could anybody help me, please?
Greets, Raubsau (noob)

---

### Post by bodhi.zazen on 2006-11-12
Nice How-to 

This thread has been added to the UDSF wiki.

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by phq on 2006-11-12
Thanks for your replies and I'm glad I was able to help some of you guys!

Sure, this guide may contain similar steps as other guides, but I wanted to reflect exactly the steps I did to get it working on my machine. As i wrote this guide is especially for clean Edgy installations which requires some different steps than described in other guides (like blacklisting the rt61pci module and _not_ downloading any kernel headers).

---

### Post by phq on 2006-11-12
> **Raubsau said:**
> I just can't get it working with WPA...

It worked fine without encryption, with WEP128bit, but not with WPA-PSK and I defenitly do not know where to look for the (i bet it's my human...) error.

Could anybody help me, please?
Greets, Raubsau (noob)

tried the guide? ;)

---

### Post by Raubsau on 2006-11-12
Yes, that's what I did. Still it won't work :(

Or should I do the next clean install and try it again? It works fine without any encryption, but only a MAC filter for security? Too many bad kids around...

---

### Post by phq on 2006-11-12
Well, you should really use WPA at least ;) hum.. did you take the max 52 alphanum char thingie in account?

is the module loading?

what's the iwconfig output?

could you post your rt61sta.dat?

---

### Post by Biozid on 2006-11-12
Does it work with dhcp too?

---

### Post by Biozid on 2006-11-12
Finally everything works!! :D  I can confirm that this setup works with AES, TKIP and dhcp.

---

### Post by neveceral on 2006-11-13
> **phq said:**
> **Now add the interface with your settings to /etc/network/interfaces**
```
#> vi /etc/network/interfaces
```

comment out the preconfigured wlan0 interface and add following lines (with your ips)
```
iface ra0 inet static
address <your ip>
netmask 255.255.255.0
gateway <ip of your access point>
auto ra0
```

**Settings for DHCP **
```
iface ra0 inet dhcp
wireless-essid YOURESSID
auto ra0
```

---

### Post by phq on 2006-11-13
Thanks for the dhcp settings, I will add them to the howto.

---

### Post by dhanjel on 2006-11-14
I can't get this to work for some reason:

```
daniel@atlantis:~/RT61_Linux_STA_Drv1.0.4.0/Module$ make all
make -C /lib/modules/2.6.17-10-server/build SUBDIRS=/home/daniel/RT61_Linux_STA_Drv1.0.4.0/Module modules
make[1]: Entering directory `/lib/modules/2.6.17-10-server/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-server/build'
make: *** [all] Error 2
```

Any ideas?

---

### Post by Henry Rayker on 2006-11-15
when I do the iwconfig to check if the device is present, I get a ra0_ifrename...I can tell I'm close, but no device exists with that name...it seems to have a connection, though (the link light is blinking like crazy)

any ideas?

---

### Post by phq on 2006-11-15
> **dhanjel said:**
> I can't get this to work for some reason:

```
daniel@atlantis:~/RT61_Linux_STA_Drv1.0.4.0/Module$ make all
make -C /lib/modules/2.6.17-10-server/build SUBDIRS=/home/daniel/RT61_Linux_STA_Drv1.0.4.0/Module modules
make[1]: Entering directory `/lib/modules/2.6.17-10-server/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-server/build'
make: *** [all] Error 2
```

Any ideas?

Did you overwrite the Makefile by Makefile.6 first?

---

### Post by ww2 on 2006-11-15
Newbie question:

You have an wireless router connected to, say, a cable modem. When you are to define <your ip> following the howto, is it the external ip address (which, for me, is something like 201.xxx.xxx.xxx) provided by your ISP/cable modem or a custom internal ip address you want to define for your wireless adapter?

---

### Post by phq on 2006-11-15
> **ww2 said:**
> Newbie question:

You have an wireless router connected to, say, a cable modem. When you are to define <your ip> following the howto, is it the external ip address (which, for me, is something like 201.xxx.xxx.xxx) provided by your ISP/cable modem or a custom internal ip address you want to define for your wireless adapter?

A custom internal IP.

---

### Post by phq on 2006-11-15
> **Henry Rayker said:**
> when I do the iwconfig to check if the device is present, I get a ra0_ifrename...I can tell I'm close, but no device exists with that name...it seems to have a connection, though (the link light is blinking like crazy)

any ideas?

Could you post the complete output of iwconfig?

---

### Post by Henry Rayker on 2006-11-15
```
ra0_ifrename  RT61 Wireless  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

That's the output for the ra0_ifrename portion. I have a lo, eth0 and sit0 with "no wireless extensions." and my rausb0 device (it's just on so that I can post this; it doesn't matter if that device is on, in, or what have you).

---

### Post by phq on 2006-11-15
> **Henry Rayker said:**
> 
That's the output for the ra0_ifrename portion. I have a lo, eth0 and sit0 with "no wireless extensions." and my rausb0 device (it's just on so that I can post this; it doesn't matter if that device is on, in, or what have you).


I would suggest that you unload all other modules which use the card and reload the rt61. Did the module load correctly? What says lsmod|grep 'rt61' ?
If it works then, you also should blacklist the modules you have unloaded so there is no conflict.

---

### Post by dhanjel on 2006-11-15
> **phq said:**
> Did you overwrite the Makefile by Makefile.6 first?

Yup.

---

### Post by ww2 on 2006-11-15
Is RT61 the same as RT2561? (as in [RT2561T]("http://www.ralinktech.com/prod-2561.htm"))?

The three Ralink chipsets that have the 61 sufix are RT2561, RT2561S and RT2661 (see [http://www.ralinktech.com/prod.htm]("http://www.ralinktech.com/prod.htm")). Only the first two are relevant, I suppose, 'cause the last one is MIMO based and for cards in another price range.

If I'm right, why not just go ahead and call it RT2561?

Edit: by the way, the topic title says "Egdy" when it should be "Edgy".

---

### Post by Henry Rayker on 2006-11-15
name@computer:~$ lsmod | grep rt61
rt61                  257544  0 

is that correct loading? I'm just not certain. All I unloaded was rt61pci, as per your guide.

---

### Post by phq on 2006-11-16
> **dhanjel said:**
> Yup.

what's in your /lib/modules/2.6.17-10-server/build directory?

---

### Post by phq on 2006-11-16
> **ww2 said:**
> Is RT61 the same as RT2561? (as in [RT2561T]("http://www.ralinktech.com/prod-2561.htm"))?

The three Ralink chipsets that have the 61 sufix are RT2561, RT2561S and RT2661 (see [http://www.ralinktech.com/prod.htm]("http://www.ralinktech.com/prod.htm")). Only the first two are relevant, I suppose, 'cause the last one is MIMO based and for cards in another price range.

If I'm right, why not just go ahead and call it RT2561?
Well the driver supports those three cards you mentioned, so its easier to say rt61, also i find this calling i's more common.

> Edit: by the way, the topic title says "Egdy" when it should be "Edgy".
Yeah, nice typo :p

---

### Post by Henry Rayker on 2006-11-16
lib/module/'uname -r'/build directory contents

arch    drivers   include  kernel    mm              net       sound
block   firmware  init     lib       modules         scripts   usr
crypto  fs        ipc      Makefile  Module.symvers  security

not too sure how helpful that will be. :D

---

### Post by dhanjel on 2006-11-17
> **phq said:**
> what's in your /lib/modules/2.6.17-10-server/build directory?

linux-2.6.17-10-server -> /usr/src/linux-2.6.17-10-server

---

### Post by huygens on 2006-11-17
Ha cool!
Thanks a log for this effective howto. I got my wireless car working without a glitch.

I just wanted to point out a (typo) mistake in step 4. The code should be:
```
#> mkdir -p /etc/Wireless/RT61STA/
#> cp *.bin /etc/Wireless/RT61STA/
#> cp rt61sta.dat /etc/Wireless/RT61STA/
```As for DHCP, I'm not sure if the line "wireless-essid YOURESSID" is necessary or not.  I did not use it and it is working. I think this is redundant because there is already such an information in the file rt61sta.dat (see "SSID=<SSID of Access Point>")

Anyway, thanks a lot for this howto once more as you really deserve it!

Huygens

---

### Post by phq on 2006-11-18
> **dhanjel said:**
> linux-2.6.17-10-server -> /usr/src/linux-2.6.17-10-server

It seems you need the linux-headers package. Mine has been installed by default. Maybe the server installation won't that by default.
type ```
dpkg -l |grep 'headers'
```
In case it isn't installed, type
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by phq on 2006-11-18
> **huygens said:**
> Ha cool!
Thanks a log for this effective howto. I got my wireless car working without a glitch.

I just wanted to point out a (typo) mistake in step 4. The code should be:
```
#> mkdir -p /etc/Wireless/RT61STA/
#> cp *.bin /etc/Wireless/RT61STA/
#> cp rt61sta.dat /etc/Wireless/RT61STA/
```As for DHCP, I'm not sure if the line "wireless-essid YOURESSID" is necessary or not.  I did not use it and it is working. I think this is redundant because there is already such an information in the file rt61sta.dat (see "SSID=<SSID of Access Point>")

Anyway, thanks a lot for this howto once more as you really deserve it!

Huygens

Congrats! ;) Glad the guide helped out one more person.

Thanks for the info, just fixed the typo!

---

### Post by bf2mad on 2006-11-22
Hi,

Thanks for the tutorial.

I am having some problems, my iwconfig output is

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I have no lights on my card

I am using Ubuntu 6.10

Thanks

---

### Post by ffadmraven on 2006-11-22
Hi I just wanted to let you know that they have updated the driver to 1.1.0.0 from 1.0.4.0.  Just thought you would like to know.

---

### Post by phq on 2006-11-23
> **bf2mad said:**
> Hi,

Thanks for the tutorial.

I am having some problems, my iwconfig output is

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I have no lights on my card

I am using Ubuntu 6.10

Thanks

What's the output of "iwlist ra0 scan" and "ifconfig"?

---

### Post by phq on 2006-11-23
> **ffadmraven said:**
> Hi I just wanted to let you know that they have updated the driver to 1.1.0.0 from 1.0.4.0.  Just thought you would like to know.

Thanks, I've updated the link. Hope it still works with them ;) 

Aight the changes:

[V 1.1.0.0]
1.) **Support x64 platform**
2.) Support WMM-APSD
3.) Enhace IRQ with tasklet schedule (THREAD_ISR)
4.) Fix pci_map_single and pci_unmap_single unsync problem.
5.) Add A-band country region code #8(for W53),code #9(for J52) and code#10
6.) Enhance RTS/CTS frame for BG protection 
7.) Send disassocite event to Supplicant when AP turn off
8.) Display mixed mode (encryption&authentication) from get_site_survey

---

### Post by bf2mad on 2006-11-23
I am using 1.1.0.0 of the driver

iwlist ra0 scan
ra0       No scan results



ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:21:2E:4E  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe21:2e4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:444134 (433.7 KiB)  TX bytes:57257 (55.9 KiB)
          Interrupt:11 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:17:9A:7D:0F:DC  
          inet6 addr: fe80::217:9aff:fe7d:fdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

Thanks

---

### Post by bf2mad on 2006-11-23
I am no expert but I noticed that my eth0 and by ra0 in the results for ifconfig are both using Interrupt:11 is that ok?

---

### Post by goethe on 2006-11-23
Sorry, iwconfig says "no wireless extension" about ra0...  Any idea about this error? lsmod lists my rt61...What am I doing wrong?

---

### Post by ffadmraven on 2006-11-23
I also had this problem, but after I did a networking restart, it showed up in iwconfig with the wireless attributes.

---

### Post by goethe on 2006-11-24
Even a complete reboot didn't fix this problem. :(

---

### Post by Eigenwert on 2006-11-24
> **bf2mad said:**
> Hi,

Thanks for the tutorial.

I am having some problems, my iwconfig output is

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I have no lights on my card

I am using Ubuntu 6.10

Thanks

I had this same problem. Our router is set up to use WEP instead of WAP encryption, so I had to change the settings in the rt61sta.dat file.

EW

---

### Post by Bunti on 2006-11-24
Thanks for all the howto's. Previously they got my wireless rt61 up and running on dapper. Unfortunately, I can't seem to be able to get past the compiling stage on edgy. After 
> make all
I get the following errors:
> make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
make[1]: *** No rule to make target `rt61/RT61_Linux_STA_Drv1.1.0.0/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make: *** [all] Error 2

Thanks,
Bunti.

---

### Post by phq on 2006-11-25
> **Bunti said:**
> Thanks for all the howto's. Previously they got my wireless rt61 up and running on dapper. Unfortunately, I can't seem to be able to get past the compiling stage on edgy. After 

I get the following errors:


Thanks,
Bunti.

Did you install the kernel headers as described?

---

### Post by Bunti on 2006-11-25
Sorry, I should have mentioned that. First I tried installing the kernel headers for the generic kernel that edgy shipped with from ubuntu packages. I didn't have success there (same error) so I got an i386 kernel and headers from ubuntu packages. That didn't work either (same error). I hear that the install cd actually comes with the appropriate headers if you add it to your sources.list with apt-cdrom. Would it be worthwhile reinstalling ubuntu and installing the generic headers from the cd before trying again? Thanks very much for your assistance.

---

### Post by Bunti on 2006-11-25
OK. I reinstalled kubuntu edgy and the headers are installed by default, but I still get the same error message. I went and researched the contents of the headers in /usr/src. As follows:
> 
arch
block
crypto
drivers
firmware
fs
include
init
ipc
kernel
lib
Makefile
mm
modules
Module.symvers
net
scripts
security
sound
usr

Thanks for your help, but I'm not quite there yet.

---

### Post by Raubsau on 2006-11-26
> **Raubsau said:**
> Or should I do the next clean install and try it again? It works fine without any encryption, but only a MAC filter for security? Too many bad kids around...
OK, I did a clean new install and did nothing else but these steps. It works! Even my concern of a D-Link DWL-G650 (C3) wouldn't work on Dapper were unneccessary!
Summary:
D-Link DWL-G510 C2 will work on Ubuntu Edgy Eft with WPA-PSK.

---

### Post by Bunti on 2006-11-27
Nope, I did a clean install of kubuntu and the DWL G510 rev. C (chipset rt61) still does not work. I can't compile the module (see previous posts by me).

---

### Post by Bunti on 2006-11-27
Would it be worthwhile trying module-assistant ?

---

### Post by phq on 2006-11-27
> **Bunti said:**
> Would it be worthwhile trying module-assistant ?

Why not, give it a try.

Did you try to run make all as root? Maybe for some reason you don't have read access to this directory?

---

### Post by Raubsau on 2006-11-27
Bunti,

I did those steps right after booting up (ok I copied the .tar.gz from a usb-stick):
```
sudo apt-get install linux-headers-`uname -r`
cd ~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module
cp -f Makefile.6 Makefile
make all
sudo su
mkdir -p /etc/Wireless/RT61STA
cp *.bin /etc/Wireless/RT61STA
cp rt61sta.dat /etc/Wireless/RT61STA
cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net
depmod

```
I never experienced that sth. would stop on compiling.
I unpacked the .tar.gz on my Desktop via the standard application by doube-clicking and extrating the highlighted directory.
The I opened a terminal and did exactly those steps. I bet you could use that one as a script ;)

---

### Post by Proji on 2006-11-28
Hi, I have read your guide and it looks like the answer I have been searching for. I started all the steps on a fresh install of kubuntu 6.10, however I have encountered a stumbling block. The step about making the driver "make all" errors out every time. Originally it claimed it could not make the folder, so i made the build folder hoping this would work, below is an output of what i get back. 

```
STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/lib/modules/2.6.17-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-386/build'
make: *** [all] Error 2

```

Please could you help me get this step to work, I've spent weeks attempting to get wireless working with different versions of kubuntu and even tried Mandriva 2007 to no avail. 

Thanks in advance

---

### Post by Raubsau on 2006-11-28
I hope I don't get kicked for that, but I would like to privide you the .gz I used - because it is 1.0.4.0 !:-k

edit:
Should I never touch this running system or should I use the new 1.1.0.0 version? How would I do this upgrade? apt-get update won't do that!? ;)

---

### Post by Bunti on 2006-11-28
Proji, 
If you can bear slightly outdated packages, kubuntu dapper is a lot more rt61 friendly. There's still a howto for it somewhere on the forum. Basically, dapper ships with a module that works and all you have to do is write a few startup scripts and configure your network. That is covered by the howto. I use kubuntu edgy (I'm on windows at the moment because I can't get a network connection on edgy) also and it doesn't seem to work as well as ubuntu with regards to this card.

---

### Post by Bunti on 2006-11-28
I won't have time to try modules-assistant until after the weekend because I'll have to temporarily move my box to where it can get access to ethernet internet.

PS - Thanks for the tip Raubsau, but I used a 1.0.4.0 driver as that was the one that the link on the howto provided. I later tried it with the 1.1 driver, but had the same problem.

---

### Post by Raubsau on 2006-11-28
Really strange... what was your card's model?
Did you configure the ethernet or anything during install? I just left out the configuration. But that doesn't seem to be the problem, as you guys struggle with the make-thing...

---

### Post by Proji on 2006-11-28
yeah it's really weird how make won't work. there's no reason for it not to afaik, as i was working on a clean install, and all the gcc stuff was installed etc, i just get the feeling it doesn't like me :(

i might have to retry dapper, i dunno, if i could get it to work it'd make life much easier, save me spending an age booting windows up

---

### Post by Raubsau on 2006-11-28
offtopic: Well, I must say that I installed Dapper on an older Asus laptop and never experienced any problem - but that's another story for sleep-well and there isn't even a rt61 in it ;)

So it might be a try to use Dapper, I don't know why using Dapper should be a problem if you don't need Firefox 2.0 preinstalled - that's what I experienced. Beryl should be available for Dapper too, an upgrade from OOo 2.0.x to 2.0.4 might be an idea.

ontopic: What is your card's model?

---

### Post by Proji on 2006-11-28
my card is a belkin f5d7000 which i saw on the kubuntu forums as working out the box before i bought it. mine is obv based with the rt61 chipset. 

it's wierd, cos both dapper and edgy had the same basic issue, both would find the wireless network etc just not connect to it. 

i will try the older driver tomorrow when i get in from work, will post back letting you know how that went :)

---

### Post by Bunti on 2006-11-29
My card is a Netgear DWL G510 rev. C. It also is based on the rt61 chipset.
Just as an afterthought, when I get some time (I haven't even tried module-assistant yet) would it also be worthwhile trying a ubuntu install rather than a kubuntu install and seeing how that goes, even though theoretically the kernels are exactly the same?

---

### Post by mcdoogle on 2006-11-29
Thankyou very very much for writing this guide, without it I couldn't have installed my D-Link G510 (Rev. C2)! The rt61pci module was where I was going wrong..

---

### Post by hish on 2006-11-30
thank you so much for this guide! I struggled through four or five different guides and two different Xubuntu versions before I found this excellent how-to.

---

### Post by clauskalus on 2006-11-30
I've followed this guide, and i can't seem to get a connection.
The step where i was most confused, was step 10, where I had to write IpAdress and Access Point. Is there someway to get these values (I have got net connection via. cable, so maybe I could steal them from there?).
I followed the rest of the guide with no problems, but I can't seem to get a connection.

When i type the command "iwconfig ra0" i get the following output:

RT61 Wireless ESSID:" "
Mode:Auto  Frequency: 2.412 Ghz  Bit Rate=54 Mb/s
RTS thr:off  Fragment thr:off
Encryption key:0123-4567-89
Link Quality=0/100  Signal level: -121 dBm  Noise level:-111 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0

I notice that I should be informed of an ESSID, but I am not. The encryption key is also a little odd, what should i change in rt61sta.dat to get this correct?.
My data encryption type is WEP (I've configured this in rt61sta.dat), my Auth Type is open and my connection type is ESS. I'm kind of lost from here, and I've been struggling to get wireless since Breezy.

Claus

---

### Post by phq on 2006-11-30
> **clauskalus said:**
> 
The step where i was most confused, was step 10, where I had to write IpAdress and Access Point. Is there someway to get these values (I have got net connection via. cable, so maybe I could steal them from there?).


You need to set the ESSID and IP address of your AccessPoint via lan cable first. Also I strongly recommend to use WPA encryption, as WEP is outdated and unsecure.
After you have configured your A/P you can fill in the ESSID, etc.

In step 6 I have described which settings are important in the rt61sta.dat.

---

### Post by phq on 2006-11-30
> **mcdoogle said:**
> Thankyou very very much for writing this guide, without it I couldn't have installed my D-Link G510 (Rev. C2)! The rt61pci module was where I was going wrong..

> **hish said:**
> thank you so much for this guide! I struggled through four or five different guides and two different Xubuntu versions before I found this excellent how-to.

Glad, you had success with this guide! Have fun! 8)

---

### Post by clauskalus on 2006-11-30
Thanks for the answer.
I must admit, I have no idea how to get my access point, but i have found my IP and then written the ifconfig ra0 192.168...
Does it matter if i ping my Access point or not (step 10)

---

### Post by phq on 2006-11-30
> **clauskalus said:**
> Thanks for the answer.
I must admit, I have no idea how to get my access point, but i have found my IP and then written the ifconfig ra0 192.168...
Does it matter if i ping my Access point or not (step 10)

The ping is only to check whether you can reach your Access Point, to see if your connection is working.
However, you should first setup your Access Point (see User Manual).
Main Steps for setting up your AP:
- Set an IP Address
- Set an ESSID
- Set encryption/authorization type (WPA-PSK) and put the WPA Key you chose in your rt61sta.dat.

---

### Post by Raubsau on 2006-11-30
No, it is not necessary to ping your AP. It is just to proof your correct connection to your wireless LAN. So if you are able to ping it, we're getting a big step closer :)

Bunti, please try to install a Ubuntu. It should be no problem to "sudo apt-get install kubuntu-desktop" then. (Why would sb use KDE!? ;))

edit: For the case you choose to use WPA-PSK use "wpa_passphrase **ESSID_you_have_chosen** **code_you_have_chosen**" to make an encrypted version (I don't know how to name this) of your code. Put that encrypted code into your rt61sta.dat - Category "KEY". Maybe you want to post your rt61sta.dat?

---

### Post by phq on 2006-12-01
> **Bunti said:**
> My card is a Netgear DWL G510 rev. C. It also is based on the rt61 chipset.
Just as an afterthought, when I get some time (I haven't even tried module-assistant yet) would it also be worthwhile trying a ubuntu install rather than a kubuntu install and seeing how that goes, even though theoretically the kernels are exactly the same?

The flavor should play no role, I've used a clean Kubuntu installation as well.
Which kernel did you choose? 386 or generic? Maybe you try to compile the module in the wrong branch or something.

---

### Post by clauskalus on 2006-12-01
OK. Here's my rt61sta.dat: [http://paste.getlinuxhelp.org/32782](http://paste.getlinuxhelp.org/32782)
I have written SSID's and passwords everywhere I can get to it. The place that I'm crippling with is the IP and access point. Btw. I have no real networking experience, not even in windows, because my dad has set up the network.

---

### Post by deadspeak on 2006-12-01
got most of the way through but i'm having trouble editing the file, and what readme file does it refer to???
__________________

---

### Post by techstop on 2006-12-01
> **deadspeak said:**
> got most of the way through but i'm having trouble editing the file, and what readme file does it refer to???
__________________

You mean this in step 6?

> See readme file in Modules directory for description.

That's pretty straight forward isn't it? Uncompress the driver you downloaded from ralink in step 1. You will find a directory called "Modules", in that directory you will find a file called "readme" which contains information on the options in the configuration file "rt61sta.dat" in step 6. You need to enter your country code, wireless mode, encryption key and so on.

---

### Post by deadspeak on 2006-12-01
okay that me being a pratt and assuming that it should be more complicated. Now i am actually configuring the module, i having trouble just over writing the existing entries, with my network details?? it removes letters if i try a copy and paste, and if i try and navigate with the arrow key it adds extra lines and adds in A's and B's, can i just edit the file with a text editor like gedit?

---

### Post by techstop on 2006-12-01
> **deadspeak said:**
> okay that me being a pratt and assuming that it should be more complicated. Now i am actually configuring the module, i having trouble just over writing the existing entries, with my network details?? it removes letters if i try a copy and paste, and if i try and navigate with the arrow key it adds extra lines and adds in A's and B's, can i just edit the file with a text editor like gedit?

AFAIK you have to use vi as you need to edit in binary mode. You just need to read up on how vi works. Here are the basics;

-there are two modes; command and insert mode.
-command mode lets you save files, quit etc, insert mode lets you edit the text.
-to get into command mode, press "esc" twice
-to get into insert mode, press "i" when in command mode to insert text (before the cursor), or "a" to append text (after the cursor)
-when you have edited your file, you need to write the changes, and then quit
-to do this, from command mode (press "esc" twice), enter the following without the quotes;

":wq"

-":" tells vi that you are entering a command, "w" writes the changes (saves) and "q" quits vi
-these are the only commands you will need to edit your file, but you really should learn more about vi as a lot of times, gedit or similar wont be available, check this out;

[http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

---

### Post by Raubsau on 2006-12-02
deadspeak: just use "sudo nano ..." instead of "sudo vi -b ..."
For copy an paste, navigate to the line, remove what you what to change with Del oder Backspace, then click with you right Mouse Button and click on paste.

This is because you are editing in a Terminal. Optionally use "sudo gedit ..." ;)

OK, clauskalus, in line 019, did you enter your encrypted WPA password? Please fill in that piece an restart, then please post the result of the following terminal command:
```
ifconfig
```

---

### Post by Bunti on 2006-12-02
Thanks to everyone for their help, but I'm still having problems.
I did a clean install of ubuntu (not kubuntu) and followed the instructions in the guide from scratch. I still had the same problem when I got to the "make all" part as I got the following error:
> 
make all
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/bunti/edgy rt61/newstart/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `rt61/newstart/RT61_Linux_STA_Drv1.1.0.0/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2
bunti@bunti-desktop:~/edgy rt61/newstart/RT61_Linux_STA_Drv1.1.0.0/Module$ 
sudo make all
Password:
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/bunti/edgy rt61/newstart/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `rt61/newstart/RT61_Linux_STA_Drv1.1.0.0/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2
bunti@bunti-desktop:~/edgy rt61/newstart/RT61_Linux_STA_Drv1.1.0.0/Module$


I also tried module-assistant, but it did not have an option for installing the rt61 module. As the rtx00 modules are there, maybe the rt61 modules will make it there eventually too. 
Thanks again,
Bunti.

---

### Post by deadspeak on 2006-12-02
okay now i've done everything up to step 9 but when i try iwconfig i get
root@paul-desktop:/home/paul# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       no wireless extensions.

i've try a restart but still nothing, also if i go into networking under the admin menu there is nothing showing

more help PLEASE !!!!

---

### Post by Bunti on 2006-12-02
Can someone please attach a rt61.ko that they managed to compile please. If not, why do we have to compile everything ourselves?

---

### Post by The last Bert on 2006-12-02
I've followed this How-To, and it seems to have been mostly successful. When activated though, it claims to be receiving packets constantly, and can't actually ping the router. iwconfig gives:

```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:"NETGEAR"  
          Mode:Auto  Frequency:2.462 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=30/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```

ifconfig gives:
```
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:33:EB:7B  
          inet addr:10.13.37.13  Bcast:10.13.37.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe33:eb7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25254788 (24.0 MiB)  TX bytes:1047538 (1022.9 KiB)
          Interrupt:209 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17524 (17.1 KiB)  TX bytes:17524 (17.1 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:DE:29:D1  
          inet addr:10.13.37.1  Bcast:10.13.37.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fede:29d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:44 txqueuelen:1000 
          RX bytes:1661385 (1.5 MiB)  TX bytes:10524 (10.2 KiB)
          Interrupt:201 
```

doing iwlist ra0 scan gives:
```
ra0       No scan results
```

Apart from the last one, this looks ok, doesn't it?

Not too sure what I've done wrong, i think I followed all the steps correctly. Any help would be really appreciated, having the 'net on linux again would be awesome.

Thanks

Bert

---

### Post by Bunti on 2006-12-02
Can someone please attach their rt61.ko module. Please.....

---

### Post by jan-h on 2006-12-02
I've finally got my Belkin rt61 card working tonight using this howto and the latest cvs from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads")
since the Ralink one doesn't support Ad-Hoc mode (according to the release notes). 

Thanks for all the help. If anyone is using the serialmonkey driver the beta doesn't seem to work too well so go for the latest nightly tarball.

Bunti, I've attached my rt61.ko as a zipfile if it helps.

Ian

---

### Post by Bunti on 2006-12-02
Thankyou very very much. I'll report back on how well it works.

---

### Post by Bunti on 2006-12-02
Works beautifully with the rt61.ko you provided and *.bin from the 1.1 module specified in the updated howto. Thankyou very much. I think that an easier way to connect to the internet than all that ip stuff, though, is just:
> dhclient ra0

It's a lot less typing, especially if you use dhcp. Thankyou all very much.

---

### Post by phq on 2006-12-03
> **Bunti said:**
> Works beautifully with the rt61.ko you provided and *.bin from the 1.1 module specified in the updated howto. Thankyou very much. I think that an easier way to connect to the internet than all that ip stuff, though, is just:


It's a lot less typing, especially if you use dhcp. Thankyou all very much.

So, you've been successfull finally? ;) grats! Also working with WPA and stuff?

---

### Post by phq on 2006-12-03
> **The last Bert said:**
> I've followed this How-To, and it seems to have been mostly successful. When activated though, it claims to be receiving packets constantly, and can't actually ping the router. iwconfig gives:

Apart from the last one, this looks ok, doesn't it?

Not too sure what I've done wrong, i think I followed all the steps correctly. Any help would be really appreciated, having the 'net on linux again would be awesome.

Thanks

Bert

The output looks good so far.

You have set up 10.13.37.1 as your IP address. Could it be that this is the IP of you Access Point (Router)? Then you should change it to 10.13.37.10 or so and try again.

---

### Post by phq on 2006-12-03
> **deadspeak said:**
> okay now i've done everything up to step 9 but when i try iwconfig i get
root@paul-desktop:/home/paul# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       no wireless extensions.

i've try a restart but still nothing, also if i go into networking under the admin menu there is nothing showing

more help PLEASE !!!!

Did you check out that ESSID and WPA-Key are set up correctly in rt61sta.dat?

---

### Post by The last Bert on 2006-12-03
Ah. A n00b error :) Everything works fine now! Thank you so much, was really starting to miss 'buntu.

Interestingly, my wireless card still claims to be receiving packets at the rate of about 10 every second... Seems a bit bizarre, but at least it works.

Thanks again.

Bert

---

### Post by kebajonathan on 2006-12-03
Did anyone get the ra0 (rt2500) to work with Networkmanager / Kentworkmanager with WEP? Although the ra0 device is seen by knetworkmanager on my kubuntu box, it cannot connect to the router... Can you please help?

THX
Keba

---

### Post by phq on 2006-12-03
> **The last Bert said:**
> Ah. A n00b error :) Everything works fine now! Thank you so much, was really starting to miss 'buntu.

Interestingly, my wireless card still claims to be receiving packets at the rate of about 10 every second... Seems a bit bizarre, but at least it works.

Thanks again.

Bert

pleasure ;)

---

### Post by phq on 2006-12-03
> **kebajonathan said:**
> Did anyone get the ra0 (rt2500) to work with Networkmanager / Kentworkmanager with WEP? Although the ra0 device is seen by knetworkmanager on my kubuntu box, it cannot connect to the router... Can you please help?

THX
Keba

better get it working with wpa. I could not sleep well if my connection would run with wep ;)

---

### Post by kebajonathan on 2006-12-03
You're right but I'm forced to use WEP since there are some pcs around that have chipsets that don't support WPA. And the average laptop user can't get in just like this with WEP, although it's cracked in a matter of seconds.

So can you please help me? I travel a lot and I'd have to be able to connect to different networks (also unencryped)

THX

---

### Post by Raubsau on 2006-12-03
> **kebajonathan said:**
> You're right but I'm forced to use WEP since there are some pcs around that have chipsets that don't support WPA. And the average laptop user can't get in just like this with WEP, although it's cracked in a matter of seconds.

So can you please help me? I travel a lot and I'd have to be able to connect to different networks (also unencryped)

THX

Did you compile your driver? My suggestion: just leave alone any network manager and configure your net with the config files.

@Bunti: Strange, but nice :)

---

### Post by phq on 2006-12-03
> **kebajonathan said:**
> You're right but I'm forced to use WEP since there are some pcs around that have chipsets that don't support WPA. And the average laptop user can't get in just like this with WEP, although it's cracked in a matter of seconds.

So can you please help me? I travel a lot and I'd have to be able to connect to different networks (also unencryped)

THX

Well, I didn't try knetworkmanager, so dunno what's wrong there. Do you have some outputs of ifconfig/iwconfig?

---

### Post by clauskalus on 2006-12-03
Raubsau - I typed my password there from the beginning. Ifconfig ra0 gives:
ra0       Link encap:Ethernet  HWaddr 00:0E:8E:03:E6:D1  
          inet addr:192.168.1.141  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:8eff:fe03:e6d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

I've also noticed that this doesn't change when i go in and out of the access point range. Also, my wired network doesn't work unless i write ifconfig ra0 down in terminal. I dunno what I messed up.

---

### Post by Raubsau on 2006-12-03
clauskalus: I can't tell you what that thing with eth0 and ra0 is about, but I think your computer tries to connect to your gateway but doesn't know which network interface to use.

Anyway, in an earlier post you said you're using WEP as encryption, but your rt61sta.dat is configured for WPA-PSK with TKIP.
Is your myPASSWORD in line 019 the value you got out from wpa_passphrase? That is important!

Please make sure your AP is in WPA mode, otherwise there is no way to connect ;)

Do you know how to look up your encryption of your AP? ifdown ra0 and then browse to 192.168.1.1 or 192.168.1.100 - or better ask your father ;)

Then we'll see.

---

### Post by clauskalus on 2006-12-04
> **Raubsau said:**
> clauskalus: I can't tell you what that thing with eth0 and ra0 is about, but I think your computer tries to connect to your gateway but doesn't know which network interface to use.

Anyway, in an earlier post you said you're using WEP as encryption, but your rt61sta.dat is configured for WPA-PSK with TKIP.
Is your myPASSWORD in line 019 the value you got out from wpa_passphrase? That is important!

Please make sure your AP is in WPA mode, otherwise there is no way to connect ;)

Do you know how to look up your encryption of your AP? ifdown ra0 and then browse to 192.168.1.1 or 192.168.1.100 - or better ask your father ;)

Then we'll see.
Raubsau - What I know about my access point is:
It's a router
Its SSID is 3com
Its Data Encryption Type is WEP
Its Connection Type is ESS
Its Network Authentication Type is open

I've changed my rt61sta.dat to reflect this, as I did from the beginning (the reason I changed this in the rt61sta.dat file you got, is because I was told that it was unsafe to use WEP).
When I type ifdown ra0 in the terminal, I get the following:
Error for wireless request "Set Encode" (8B2A) :
     SET failed on device ra0 ; Network is down.
Error for wireless request "Set ESSID" (8B1A) :
     SET failed on device ra0 ; Network is down.

When I type ifdown ra0 the second time it says:
ifdown: interface ra0 not configured

---

### Post by Raubsau on 2006-12-04
Try a ifup ra0 then :)

---

### Post by deadspeak on 2006-12-06
okay seem to be getting there slowly, i now have this message

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

sit0      no wireless extensions.

the wireless is showing in the networking section under the admin menu, but it still does not appear in the gnome network manager applet, and i am still unable to connect to the wireless network.

please be generous and donate as much help as you can..

---

### Post by Baf on 2006-12-06
I'm running Dapper back at home, but I'll install Edgy once I get home and try this guide. I was wondering though about the kernel headers. Since I haven't gotten any connectivity through wireless, I don't have any Internet so I cant install the kernel headers like it is said to in the beginning of the guide. I will have the EdgyCD, and am wondering if I could do it through that? 

Also, I see the newest version of the driver supports x86_64. Everyones been successful with 64 bit? I've been trying to get this driver (older version I think) to work on Dapper through another guide on the forums but haven't had any luck. I was thinking that Edgy would have native support out of the box with this driver but I guess that isn't the case.

---

### Post by clauskalus on 2006-12-07
> **Raubsau said:**
> Try a ifup ra0 then :)
ifup ra0 just does a DHCPDISCOVER and doesn't find anyhthing.
I know that my computer can find the access point, because the wlan0 (before i started this guide) could find the access point (but not connect to it though, thats why i read this guide).
Maybe I'm fighting a lost cause here?

---

### Post by ultranoize on 2006-12-10
I need help. I followed the 9 steps and everything worked smoothly. Unfortunately step 10 is a bit hard to understand for me. Sorry completely new to Linux and to networking as well. I think i did type in the correct IP address which i got from running ifconfig (192.168.1.2 see below). I try to ping for example [www.google.com](www.google.com) and it does work but  that is because I still have the wired connection. I pull off the wire, try pinging again and nothing.  I have a WEP connection. My windows machine won't accept WPA (go figure!).
 
This is what I get after running ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:08:74:39:C4:30  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe39:c430/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1537 (1.5 KiB)  TX bytes:1784 (1.7 KiB)
          Interrupt:11 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1544 (1.5 KiB)  TX bytes:1544 (1.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:89:29:0A  
          inet6 addr: fe80::20e:2eff:fe89:290a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1505 errors:6 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000 
          RX bytes:126774 (123.8 KiB)  TX bytes:3096 (3.0 KiB)
          Interrupt:11 


The following is my rt61sta.dat:

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=SPP_MTB
NetworkType=Infra
Channel=0
AuthMode=WEPAUTO
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

and finally my /etc/network/interfaces:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth0


#iface wlan0 inet dhcp
#wireless-essid SPP_MTB
#wireless-key DD1533F316
#auto wlan0

#iface wmaster0 inet dhcp
#wireless-essid SPP_MTB
#wireless-key DD1533F316
#auto wmaster0

# New ra0 for rt61 driver
iface ra0 inet dhcp
wireless-essid SPP_MTB
wireless-key DD1533F316
auto ra0

The good thing is that the Link LED on the card is always on and every now and then the Activity LED blinks (whatever that means)
 

in advance thanks for the  help.

---

### Post by techstop on 2006-12-10
> **ultranoize said:**
> I need help. I followed the 9 steps and everything worked smoothly. Unfortunately step 10 is a bit hard to understand for me. Sorry completely new to Linux and to networking as well. I think i did type in the correct IP address which i got from running ifconfig (192.168.1.2 see below). I try to ping for example [www.google.com](www.google.com) and it does work but  that is because I still have the wired connection. I pull off the wire, try pinging again and nothing.  I have a WEP connection. My windows machine won't accept WPA (go figure!).
<SNIP>

From what I can see, you have you WEP key in both the rt61sta.dat file and the /etc/network/interfaces file, and they are different. You should only configure the key in the rt61sta.dat file. Comment out or delete these lines from /etc/network/interfaces;

wireless-essid SPP_MTB
wireless-key DD1533F316

and put the appropriate information in the .dat file (Step 6), pull down the interface and start it back up again, you should be in business then...

---

### Post by phq on 2006-12-11
Please check out whether your router accepts WPA encryption and configure it if possible, first on the router, then on your machine.

---

### Post by cirorodrigues on 2006-12-11
> **Bunti said:**
> Proji, 
If you can bear slightly outdated packages, kubuntu dapper is a lot more rt61 friendly. There's still a howto for it somewhere on the forum. Basically, dapper ships with a module that works and all you have to do is write a few startup scripts and configure your network. That is covered by the howto. I use kubuntu edgy (I'm on windows at the moment because I can't get a network connection on edgy) also and it doesn't seem to work as well as ubuntu with regards to this card.
 
I recompiled rt61.ko and replaced the one shipped with Dapper by this new module. The new module didn't work and I lost the old one :-?
Do you know any way to recover the original Dapper rt61 module either from cd or internet?

---

### Post by cirorodrigues on 2006-12-11
Just to complement previous email: I followed this how-to and recompiled rt61.ko successfully, based on driver version 1.1. I've changed rt61sta.dat file (as binary) with my settings, but when I tried to load the new rt61.ko modules I got "invalid module format".

---

### Post by ultranoize on 2006-12-11
> **techstop said:**
> From what I can see, you have you WEP key in both the rt61sta.dat file and the /etc/network/interfaces file, and they are different. You should only configure the key in the rt61sta.dat file. Comment out or delete these lines from /etc/network/interfaces;

wireless-essid SPP_MTB
wireless-key DD1533F316

and put the appropriate information in the .dat file (Step 6), pull down the interface and start it back up again, you should be in business then...

techstop, thanks for your help. I still can't get it to work. I have commented out the things you said in the interfaces file. The following is the rt61sta.dat file  that I have:

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=SPP_MTB
NetworkType=Infra
Channel=11
AuthMode=WEPAUTO
EncrypType=WEP
DefaultKeyID=1
Key1=DD1533F316
Key1Type=0
Key1Str=DD1533F316
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

I can't really see where the problem is. Where is it that I am supposed to type the WEP key? Is it under Key1 or Key1Str ??

---

### Post by ultranoize on 2006-12-11
I have a strange problem. I have done a ping test to various ip addresses (127.0.0.1 (lo), 192.168.2 (my wireless device) and 216.239.57.99 (which apparently is google because i type that ip address on firefox and a google page pops up.)). They all work fine, including the google one. My question is then what  can be wrong since I can't do ping -c 4 [www.google.com](www.google.com).  I know that this might be a problem with DNS. I've checked /etc/resolv.conf and i get

 nameserver 192.168.1.1

Is this correct?

I'm i any close to having a wireless connection working?

---

### Post by phq on 2006-12-12
> **ultranoize said:**
> I have a strange problem. I have done a ping test to various ip addresses (127.0.0.1 (lo), 192.168.2 (my wireless device) and 216.239.57.99 (which apparently is google because i type that ip address on firefox and a google page pops up.)). They all work fine, including the google one. My question is then what  can be wrong since I can't do ping -c 4 [www.google.com](www.google.com).  I know that this might be a problem with DNS. I've checked /etc/resolv.conf and i get

 nameserver 192.168.1.1

Is this correct?

I'm i any close to having a wireless connection working?

If your router's IP does not work, enter directly the nameservers of your provider.
Also you could try dhcp..

---

### Post by viuks on 2006-12-15
> **goethe said:**
> Sorry, iwconfig says "no wireless extension" about ra0...  Any idea about this error? lsmod lists my rt61...What am I doing wrong?

Same here...:(
Pls, if anybody has some ideas...

In Dapper I never inserted my essid namy. Everything just worked automaticly.

---

### Post by techstop on 2006-12-15
> **ultranoize said:**
> I can't really see where the problem is. Where is it that I am supposed to type the WEP key? Is it under Key1 or Key1Str ??

Sorry for the late reply....I don't use WEP, but I guess the key goes in Key1Str? Also, you have a WPA key in there too, maybe try deleting that line, or making it;

WPAPSK=

? Sorry, I really don't know. As above, does your router support WPA? If it does, use it, it is much more secure than WEP...

Does scanning show any channels? If it does, then it's just the key that isn't working, there is a guy here that could only get the card working with a key that is 13 characters long;

[http://www.ubuntuforums.org/showpost.php?p=1497956&postcount=169](http://www.ubuntuforums.org/showpost.php?p=1497956&postcount=169)

Hopefully someone that uses WEP will show up, or you can use WPA with your hardware...

---

### Post by tomjennings on 2006-12-16
> **phq said:**
> This guide is for all Edgy users running a RT61 chipset WLAN card. If you follow all the steps described below, you should have running a WPA (WPA-PSK/TKIP) connection to your Access Point....

**Reboot - Try - Be Happy! :-D **


I am happy! How did you know? :-) Thanks a million -- the RAlink driver works fine w/your hack. I've been battling the RAlink drivers for some time (mainly the still-buggy RT2570, USB). Long time SuSE user switched to ubuntu for my embedded linux automobile music player. SuSE getting too corporate for me.

Hardware:
VIA EPIA 5000 fanless (400MHz)
768M ram
xubuntu 6.10 edgy
CNET CWP-854 mini PCI card

---

### Post by noelferreira on 2006-12-16
thanks for the nice howto!

it almost worked in perfection for me. Everything is ok in my edgy amd64. 
However i can't configure my ' /etc/network/interfaces ' file. If i try to do that my system hang up on the next reboot. But if i delete the file everything works great. 
The only problem is that i have to manually bring up ra0 every start up. I just open a terminal console and type 'sudo dhclient ra0' and all works ok. 
I also tried to my a script to bring up it but i was not well sucedded. i wonder if you know any solution for my problem. 

some output that might help:

> dmesg | grep RT61
[   40.854561] RT61: Vendor = 0x1814, Product = 0x0302 
[  151.751515] RT61: RfIcType= 3

> dmesg | grep ra0
[  156.972041] ra0: no IPv6 routers present
[  806.303830] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !


thanks, 

noel ferreira

---

### Post by viuks on 2006-12-17
> **deadspeak said:**
> okay seem to be getting there slowly, i now have this message

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

..
Please, can You tell, how You gat awayfrom "ra0      no wireless extensions."  This is problem for me also.

---

### Post by dahen on 2006-12-18
Thank you! This worked great for my new D-Link DWL-G510 54Mbps PCI rev C.2.

Some questions:

1. What does the alias do? Is it only so I can modprobe ra0 just as rt61?
2. 'lsmod' shows lots of modules while /etc/modules show just a few. I guess there is automatic loading of the rest. Why can't rt61 be automatically loaded?

Suggested addition to guide:
* Perform an "update-pciids" which fetches the latest pci id list. It makes the output from "lspci" more accurate.
* Then do "lspci" to make sure that the adapter is really using a RT61 chipset.

---

### Post by PraysToPan on 2006-12-20
Hi Everyone,

After looking through this thread, I decided I wanted more flexibility for my connection options.  I'm using an SMC SMCWCB-GM PC card.  I find I get the best results with the [current CVS drivers from SerialMonkey]("http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz").  If you don't like the risk of the daily CVS snapshots, you can use the [beta drivers]("http://prdownloads.sourceforge.net/rt2400/rt61-1.1.0-b1.tar.gz?download").

You can build these drivers using the instructions in the first post.

If all has gone well at this point, you're ready to configure it.  The first step is to edit the file /etc/Wireless/RT61STA/rt61sta.dat.  The file must be edited as a binary file like so:
```
sudo vim -b /etc/Wireless/RT61STA/rt61sta.dat
```

Comment out everything _after_ the [Default] section.  This is done so that we don't have any initial access point configuration.  These option can be set by other means in the /etc/network/interfaces file.  This is what mine looks like:
```
# Copy this file to /etc/Wireless/RT61STA/rt61sta.dat
# This file is a binary file and will be read on loading rt2500.o module.

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
IEEE80211H=0
TxRate=0
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

# All parameters below can be set by iwconfig in the if-pre scripts
# if required or enabled here if you wish
# Anything enabled here will be used when EVEN the net interface is brought up
# this will undo any iwconfig pre-up settings.

#SSID=OFFICEWAPG
#NetworkType=Infra
#Channel=1
#AuthMode=SHARED
#EncrypType=WEP
#DefaultKeyID=1
#Key1Type=0
#Key1Str=
#Key2Type=0
#Key2Str=
#Key3Type=0
#Key3Str=
#Key4Type=0
#Key4Str=
#WPAPSK=abcdefghijklmnopqrstuvwxyz
#RTSThreshold=2312
#FragThreshold=2312
#PSMode=CAM
#RFMON=0

```

The final configuration step is to edit /etc/network/interfaces:
```
sudo vim /etc/network/interfaces
```

Here is an example based on the one I use:
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# Wired Ethernet
iface eth0 inet dhcp

# AP with WPA security using a preshared key
iface wpa inet dhcp      
pre-up iwconfig ra0 essid wpaap
pre-up iwpriv ra0 set NetworkType=Infra
pre-up iwpriv ra0 set AuthMode=WPAPSK #use WPA2PSK if needed
pre-up iwpriv ra0 set EncrypType=TKIP  #use AES instead if needed
pre-up iwpriv ra0 set WPAPSK="mywpakey"

# AP with no encryption or authentication
iface open inet dhcp
pre-up iwconfig ra0 essid openap
pre-up iwpriv ra0 set NetworkType=Infra
pre-up iwpriv ra0 set AuthMode=OPEN
pre-up iwpriv ra0 set EncrypType=NONE

# AP with WEP
iface wep inet dhcp
pre-up iwconfig ra0 essid wepap
pre-up iwpriv ra0 set NetworkType=Infra
pre-up iwpriv ra0 set AuthMode=SHARED
pre-up iwpriv ra0 set EncrypType=WEP
pre-up iwpriv ra0 set Key1=1111111111

```

To activate any of the networks in this configuration you would run:
```
sudo ifup ra0=*netname*
```
To bring down the network when you are done:
```
sudo ifdown ra0=*netname*
```
*netname* refers to the name you gave to your configuration in the /etc/network/interfaces file: 
```
iface wpa inet dhcp
```
*wpa* is the netname.  So to get your WPA configuration going, run:
```
sudo ifup ra0=wpa
```

OK, suppose you frequent a cafe and you want to set up a special network configuration just for it.  Since our cafe has an open access point, we'll copy the section in /etc/network/interfaces called *open*:
```
# AP at the cafe
iface cafe inet dhcp
pre-up iwconfig ra0 essid cafeap
pre-up iwpriv ra0 set NetworkType=Infra
pre-up iwpriv ra0 set AuthMode=OPEN
pre-up iwpriv ra0 set EncrypType=NONE
```

The only change we need to make to our new addition is this line:
```
iface open inet dhcp
```
becomes this line:
```
iface cafe inet dhcp
```
So to activate our settings at the cafe:
```
sudo ifup ra0=cafe
```
then:
> sudo ifdown ra0=cafe
when done.

I hope this finds a use for someone other then me!
Jon

---

### Post by Zhukov on 2006-12-21
Will it work in Master mode?

---

### Post by MeeMaw on 2006-12-21
Thanks SO MUCH for the great how-to!!!
I had been battling this in Dapper and had completely ruined it, so I wiped it and installed Edgy, then followed the how-to and it worked! I'm using WEP, but will soon be changing to WPA.
The only glitch I found was when I did iwconfig..... I had followed everything to the letter but it still said "No wireless extensions" but after I re-booted, it worked just fine.

Thanks again,      MeeMaw    :-D

---

### Post by PraysToPan on 2006-12-21
Hi all,

I was just bitten by the lack of response from DHCP servers.  Looking through the modules loaded by the rt61.ko module, af_packet.ko is loaded at some point after rt61.ko.  So what I did was:
```
sudo ifconfig ra0 down
sudo modprobe -r rt61
sudo modprobe -r af_packet
sudo modprobe rt61

```

Then do what ever you need to to start your connection again.

Jon

---

### Post by warri0r on 2006-12-25
this is relly a cool post, i m new to linux as well as to this community too.

bunch of thanks to PHQ

at first i messed up with editing the dat file as i used vi editor,later i tried editing with nano and gedit it worked awesome.

but now i got a problem , i can connect to my router and evry thing works fine inside my network ,even i can access my router configurations. the problem is i cant get connected to the internet using ubuntu. i m sure tat my router is connected to Internet but i cant access frm my system.

in short:

my router is connected to the internet as well as my system is also connected to the router but i cant access the internet frm my system.

plz anyone help me as i m new to linux. i ll b thankful :)

---

### Post by techstop on 2006-12-25
> **warri0r said:**
> 
in short:

my router is connected to the internet as well as my system is also connected to the router but i cant access the internet frm my system.

plz anyone help me as i m new to linux. i ll b thankful :)

Welcome to the ubuntu forums! 

If you can connect wirelessly from your system to the router, you are 99% of the way there. I'd say it is just a DNS issue. From the command line, try these two commands;

```

ping 64.233.167.99
```

```
ping google.com
```

If you get results from the first command, but not the second (eg. cannot find host or similar), then it means your system does not know what the DNS server on your network is. Can you post the contents of your /etc/network/interfaces file?

---

### Post by warri0r on 2006-12-25
thank you for replying me sir

this is the data i got sir

warri0r@warri0rs:~$ ping -c 2 64.233.167.99
PING 64.233.167.99 (64.233.167.99) 56(84) bytes of data.
64 bytes from 64.233.167.99: icmp_seq=1 ttl=250 time=429 ms
64 bytes from 64.233.167.99: icmp_seq=2 ttl=250 time=460 ms

--- 64.233.167.99 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 429.669/444.917/460.166/15.263 ms


warri0r@warri0rs:~$ ping google.com
ping: unknown host google.com



Interfaces file contents:



auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface ra0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1
auto ra0



kindly for ur information sir:

 i hav configured my router DNS to opendns.com service. i dont know whether i hav configured any dns ip in my ubuntu system

---

### Post by techstop on 2006-12-25
I guess 192.168.1.1 is your wireless router? Is the router also a modem? If so, were you able to access the internet with other operating systems or other computers? Or do you have some other network config? 

eg. here is my network;

internet->modem->linux gateway->switch->wireless access point

the linux gateway has an ip address of 192.168.0.1, so that is the address I put in the /etc/network/interfaces file as the gateway address. The ip address of the wireless router is not used. If I used that address instead, I would get the DNS issues you describe.

---

### Post by warri0r on 2006-12-25
hope this ll be the answer for ur questions sir

i m having a huawei router sir which can be bridged so tat it ll act as a modem.

but i hav configured the tat (192.168.1.1) as a router and it act as my gateway

my connection model:

192.168.1.3(my system) ----> 192.168.1.1 (router)----- > internet

i hav only one system inside my network currently 

i hav a windows XP and ubuntu 6.10 running

the windows is working well for years and tat is wat i m switching my OS to reply u sir.

i turned off the DHCP in my router as i use to configure it manually in my system. my system IP is 192.168.1.3

i hav configured my DNS on my router to openDNS.com service and itw working gr8

if i m missing something in the answer for our question means , please specify tat sir

---

### Post by Haim on 2006-12-25
Following the howto to the letter worked for me (would have been first time if not for my typos!)

Brilliant, have read lots of stuff, and struggled to tie together with my limited linux know-how.  Great christmas present!!

Cheers

Haim

---

### Post by techstop on 2006-12-25
> **warri0r said:**
> hope this ll be the answer for ur questions sir

i m having a huawei router sir which can be bridged so tat it ll act as a modem.

but i hav configured the tat (192.168.1.1) as a router and it act as my gateway

my connection model:

192.168.1.3(my system) ----> 192.168.1.1 (router)----- > internet

i hav only one system inside my network currently 

i hav a windows XP and ubuntu 6.10 running

the windows is working well for years and tat is wat i m switching my OS to reply u sir.

i turned off the DHCP in my router as i use to configure it manually in my system. my system IP is 192.168.1.3

i hav configured my DNS on my router to openDNS.com service and itw working gr8

if i m missing something in the answer for our question means , please specify tat sir

please stop calling me sir, you're making me nervous! :D 

I must admit I don't know what the problem is now. In your windows setup, do you have 192.168.1.1 as the DNS server, or the OpenDNS server IP addresses? (properties of your connection, then properties of the tcp/ip, there is a dialog page that you specify to obtain an ip address automatically, or use the following address - which you will be using if you don't have dhcp. then down the bottom of the dialog you have to specify the dns server, hope all this makes sense)

---

### Post by warri0r on 2006-12-25
thanks a bunch for spending your precious time in solving my problm sir 

i m just 18 yrs old, struggling to be a master in computer security field. i just want to respect ppl helping me all the way to achieve my goal :mrgreen: 

i hav configured my windows system with the same opendns service as on my router. but as far as i know "its the router tat fetches the dns requests", i cant conclude this statement as you ppl may be right sir.

if u need me to configure the dns address in my system too means please tell me where i can add those ip addresses

---

### Post by techstop on 2006-12-25
> **warri0r said:**
> thanks a bunch for spending your precious time in solving my problm sir 

i m just 18 yrs old, struggling to be a master in computer security field. i just want to respect ppl helping me all the way to achieve my goal :mrgreen: 

i hav configured my windows system with the same opendns service as on my router. but as far as i know "its the router tat fetches the dns requests", i cant conclude this statement as you ppl may be right sir.

if u need me to configure the dns address in my system too means please tell me where i can add those ip addresses

OK, from what I understand, you have turned off DHCP on the router? So you will need to add the following to another file, /etc/resolv.conf

```
nameserver 208.67.222.222
```

I think I have that address correct for the OpenDNS server? That line tells your system where to find the DNS server.

I think that might even work!

EDIT: Add another line for any extra DNS servers you need

---

### Post by warri0r on 2006-12-25
awesome it is woking gr8888!

thanks a bunch for your kind help sir

i didnt find the file you specified but i added the dns ip's to system--->administration ---->networking

i entered the ip addresses in the dns server tab, now its working gr8

once again thanks a lot sir

now moving to the graphic card section to fix my Nvidia fx 5200  :mrgreen:

---

### Post by techstop on 2006-12-25
> **warri0r said:**
> awesome it is woking gr8888!

thanks a bunch for your kind help sir

i didnt find the file you specified but i added the dns ip's to system--->administration ---->networking

i entered the ip addresses in the dns server tab, now its working gr8

once again thanks a lot sir

now moving to the graphic card section to fix my Nvidia fx 5200  :mrgreen:

Ahhh, good to hear. Can I suggest Automatix to install the drivers for your nvidia card?

---

### Post by warri0r on 2006-12-25
> **techstop said:**
> Ahhh, good to hear. Can I suggest Automatix to install the drivers for your nvidia card?

oops .. that would be a gr8test help for me sir, still searching.... i dont know abt automatix , but i do know a little bit abt x-window system :mrgreen:

---

### Post by techstop on 2006-12-25
> **warri0r said:**
> oops .. that would be a gr8test help for me sir, still searching.... i dont know abt automatix , but i do know a little bit abt x-window system :mrgreen:

[Automatix]("http://getautomatix.com/") is an addon for ubuntu that easily installs things like video card drivers, extra fonts, codecs and other useful addons that aren't included by default. It's very easy, and automatically adds required repositories. I used it to install my nvidia 6600GT and it worked perfectly. Cheers.

[http://getautomatix.com/](http://getautomatix.com/)

---

### Post by warri0r on 2006-12-25
> **techstop said:**
> [Automatix]("http://getautomatix.com/") is an addon for ubuntu that easily installs things like video card drivers, extra fonts, codecs and other useful addons that aren't included by default. It's very easy, and automatically adds required repositories. I used it to install my nvidia 6600GT and it worked perfectly. Cheers.

[http://getautomatix.com/](http://getautomatix.com/)

woohoo..... tats relly a worth info. i ll try tat and comment to u sir

thanks a lot for u r kind help:mrgreen:

---

### Post by cirorodrigues on 2006-12-26
Finally I have my DWL-G510 wifi card working properly (WPAPSK-TKIP) with native Dapper RT61 driver. I didn't use the new RT61 v1.1 driver. I got it, but at end I used the one shipped with Dapper. What I did:
1) downloaded drivers and firmware from ralink website as described above in other posts.
2) created /etc/Wireless/RT61STA/.
3) copied firmware files (*.bin) and rt61sta.dat to this folder.
4) edited rt61sta.dat with vi, accordingly to readme file included in drivers package, adjusting to my own settings (WPAPSK, TKIP, keys, channel and SSID).
5) edited /etc/network/interfaces, commenting all references to wlan, ath interfaces (which refers to others wifi networks). I've added the following commands at end of file:
auto ra0
iface ra0 inet dhcp
6) rebooted
7) verified with ifconfig: I got IP from access point
 verified with iwconfig: ssid, wpa, etc were all ok (loaded from rt61sta.dat)

Note: I couldn't make Gnome Network-Manager to work with wifi. I think it's because of wpapsk setting. But I'll not cry for this...

Hope this help others. There's some light at end of tunnel...

---

### Post by rhys2 on 2006-12-27
Worked fine with D LInk DWL G30 e2 v5
Location of ralink files has moved to  /ralink/data so check out ralinktech.com before downloading tar.
It would perhaps be easier for noobies like me to use gedit rather than vi to edit interfaces and .dat files.
This "how to" should be part of the UBUNTU wiki wireless guide.
Thanks

---

### Post by trichards57 on 2006-12-31
A great HowTo.  Finally my laptop is on the internet!!!  Only thing I might suggest adding is a note at step 10 (Configure and test the Device).  If, after manually setting the IP address, the ping fails, try running dhclient.  This solved the problem for me.

Once again, brilliant guide! :D

---

### Post by Analord on 2007-01-03
nice howto.

Anyone got kismet up and running with this module ?

If yes pls post your kismet.conf :)
Thx

---

### Post by Fantomius on 2007-01-03
> **deadspeak said:**
> okay now i've done everything up to step 9 but when i try iwconfig i get
root@paul-desktop:/home/paul# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       no wireless extensions.

i've try a restart but still nothing, also if i go into networking under the admin menu there is nothing showing

more help PLEASE !!!!


Does anybody have the solution to this problem? I can see I'm not the only one having this problem.

By the way: Consider that I'm new to linux and that my errors might be stupid and that I need easy/detailed help :)

---

### Post by Guranic on 2007-01-03
Great HowTo! Thanks. My A-link wl54pc (rt61) is working perfectly. Later post in this thread showed another howto helping with multiple networks. That is indeed what you need with laptop, right? I'm just asking is it possible to control connections with kubuntu (or ubuntu) networkmanager if I'll comment out those things after "default" part. Or maybe I just try it..

---

### Post by Guranic on 2007-01-03
Nope. Won't work like I wanted to... Kubuntu networkmanager won't actually connect at all. I have other application called "Wireless Assistant", it can connect the network though.. But it does not have network profiles. (or haven't I found them)  So I just commented out those things after "default" part in /etc/Wireless/RT61STA/rt61sta.dat (like told before in this thread), I left uncommented some parts, like channel, country, wireless mode etc. but I took out keys and encryption methods. I'm using generally WEP-encrypted or open accesspoints so this would be better than editing the binaryfile with vi every time I want to change to another network. If somebody knows better solution, let me know. Thanx.

---

### Post by zadatak on 2007-01-06
Okay, tried this with a Gigabyte GN-WP01GS on a fresh install of Kubuntu Edgy and the system locked up soon after:

```
#> ifconfig ra0 192.168.1.5 netmask 255.255.255.0 up
```

Now the system locks up at boot on "initializing network interfaces"

EDIT:sorry, it says "*configuring* network interfaces"

---

### Post by Frak on 2007-01-07
Press Ctrl+C to skip the process.

---

### Post by zadatak on 2007-01-07
> **Frak said:**
> Press Ctrl+C to skip the process.

Does nothing, still locked up. After a few seconds this message comes up:

BUG: soft lockup detected on CPU#0!

---

### Post by zadatak on 2007-01-07
Okay, now i'm very confused. Sometimes, (like 5% of the time) it boots up fine and networking works perfectly. But most of the time the system locks up at boot.

Interestingly, if i take out the antenna (so the card gets no signal) everything boots up fine, and if i put the antenna back in after it boots, networking works perfectly too. :-?

---

### Post by dakakri on 2007-01-07
i got the same problem, but know that I have sucessfully have done pretty mutch the same prosidure with an older driver verstion.

Apperently the 1.1.0.0 does not work. Someone got a link to the 1.0.4.0 drivers or a new howto?

---

### Post by Thebear on 2007-01-07
I was getting along okay until step 6 where I have to use the vi editor.  I had previously tried to get my rt61 up and running on Dapper Drake using the guide items suggested by judgekaster and while I was ultimately unsuccesful I did not have any problems editing the binary file rt61sta.dat with the vi editior.  This time after making the changes I try to save with the :w command and the changes will not save because the file is read only.  I then try to save with :!w as suggested but still no luck. The message when I try to exit with the :q command or :!q dosn't seem to matter is " no changes since last save" something to that affect.  

I can make all the changes I want but I can't seem to get the editor to quit and save and I always end up with a swap file that needs to be removed, before I can try again. 

Can anyone help me with this problem? 

The bear

---

### Post by Frak on 2007-01-07
replace vi with gedit, way easier to use. Vi is a terminal text editor, that at least for me, took forever to learn.

---

### Post by techstop on 2007-01-07
> **Frak said:**
> replace vi with gedit, way easier to use. Vi is a terminal text editor, that at least for me, took forever to learn.

That would be the *easy* way out, but is not necessarily a solution. Everyone should learn vi!

@ Thebear, if it is being opened as readonly, then you should do;

```

**sudo** vi -b /etc/Wireless/RT61STA/rt61sta.dat
```

at step 6. Then you will be able to edit, and write and quit with ":wq"

---

### Post by Frak on 2007-01-07
> **techstop said:**
> That would be the *easy* way out, but is not necessarily a solution. Everyone should learn vi!

I'll learn vi when my life depends on it.

---

### Post by Martin_Blank on 2007-01-08
Thanks for the How-to, eveything worked great. I did have to add 'dns-nameservers <dns address>' to the interfaces file, but other than that, worked like a charm!

---

### Post by Thebear on 2007-01-08
> **techstop said:**
> That would be the *easy* way out, but is not necessarily a solution. Everyone should learn vi!

@ Thebear, if it is being opened as readonly, then you should do;

```

**sudo** vi -b /etc/Wireless/RT61STA/rt61sta.dat
```

at step 6. Then you will be able to edit, and write and quit with ":wq"

Thanks Techstop

That did solve my problem and the vi editor was no trouble after that.  

I wonder if you could help me a little further

I have checked the file rt61sta.dat and all is well, but when I run iwconfig ra0  and all others show "no wireless extensions" they showed up fine when I was in Dapper?  It seems my device Linksys wmp54g is not loaded.  I loaded the driver using ndiswrap from the windows cd that came with the card.

Any ideas?  

the bear

---

### Post by i386DX on 2007-01-08
I used this howto to install the RT61-driver, which worked (i think...)
then I followed [this](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html) tutorial to install networkmanager/WPA.

Now I think that networkmanager doesn't recognize my wireless networkcard. When I click on the network manager icon I don't get I screen like this:

[img]http://www.debianadmin.com/images/wpa/2.png[/img]

I only see 'wired network'
there are no wireless networks found (that's ok at this moment, because there are no wireless networks at this place) but I think I should see Connect to other wireless network and Create new in the menu or does networkmanager work like that?

ifconfig gives:
```

ra0       RT61 Wireless  ESSID:""
           Mode: Auto  Frequency:2.412 Ghz    Bit Rate=54Mb/s
           RTS thr:off    Fragment thr:off
           Link Quality=0/100    Signal level:-121 dBm     Noise Level:-111 dBm
           Rx invalid nwid:0   Rx invalid crypt:0     Rx invalid frag:0
           Tx excessive retries:0    Invalid misc:0     Missed beacon:0

```

iwlist ra0 list
```

ra0      No scan results

```

I'm not sure if there's anything wrong (i don't have a wireless connection at this place), but I want to be sure that it works when I enter a network. Everything looks normal, but I think I should see Connect to other wireless network and Create new Wireless Network in the networkmanager menu even there's no wireless network available?

---

### Post by techstop on 2007-01-08
> **Thebear said:**
> Thanks Techstop

That did solve my problem and the vi editor was no trouble after that.  

I wonder if you could help me a little further

I have checked the file rt61sta.dat and all is well, but when I run iwconfig ra0  and all others show "no wireless extensions" they showed up fine when I was in Dapper?  It seems my device Linksys wmp54g is not loaded.  I loaded the driver using ndiswrap from the windows cd that came with the card.

Any ideas?  

the bear

This HOWTO is written so you don't need to use ndiswrapper. ndiswrapper is a "hack" that lets you use windows drivers if there aren't any native linux ones. It's far better to use native linux drivers if they are available. In the case of RT61 based wireless cards, there are good native drivers. So, if you have a wireless card based on the RT61 chipset, you should uninstall ndiswrapper and start the howto from the beginning again.

---

### Post by Thebear on 2007-01-09
Okay, I have redone the HOWTO several times now, I have uninstalled ndiswrapper and gone through the process with the correct native drivers.  My problem seems to occur when compiling the module in step 2 

Here is the output of my terminal at that step. There seems to be a number of error messages and warnings. 

--------------------------


wayne@wayne-desktop:/tmp/RT61_Linux_STA_Drv1.1.0.0/Module$ sudo make all
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/tmp/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:227: warning: ‘device’ is used uninitialized in this function
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.o
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c: In function ‘STAMlmePeriodicExec’:
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c:744: warning: unused variable ‘RxSignal’
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c: In function ‘AsicSetRxAnt’:
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c:5455: warning: ‘R77’ may be used uninitialized in this function
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c: In function ‘RadarDetectionStop’:
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c:5893: warning: ‘R66’ may be used uninitialized in this function
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c: In function ‘AsicAdjustTxPower’:
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c:4346: warning: ‘BbpR1’ may be used uninitialized in this function
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c: In function ‘AsicSwitchChannel’:
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/mlme.c:3666: warning: ‘BbpReg’ may be used uninitialized in this function
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/connect.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/sync.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/assoc.o
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/assoc.c: In function ‘link_status_handler’:
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/assoc.c:817: warning: embedded ‘\0’ in format
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/assoc.c:841: warning: embedded ‘\0’ in format
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/auth.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/auth_rsp.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_data.o
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_data.c: In function ‘RTMPSendRTSCTSFrame’:
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_data.c:1865: warning: unused variable ‘IrqFlags’
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_data.c: In function ‘RTMPHardTransmit’:
/tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_data.c:2047: warning: unused variable ‘IrqFlags’
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_init.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/sanity.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_wep.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_info.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/eeprom.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_tkip.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/wpa.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/md5.o
  CC [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_task.o
  LD [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rt61.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rt61.mod.o
  LD [M]  /tmp/RT61_Linux_STA_Drv1.1.0.0/Module/rt61.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'

lspci say 

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
02:0a.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
02:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:0c.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
root@wayne-desktop:/tmp/RT61_Linux_STA_Drv1.1.0.0/Module# 

iwconfig says 

root@wayne-desktop:/tmp/RT61_Linux_STA_Drv1.1.0.0/Module# iwconfig
lo        no wireless extensions.

ra0       no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

There is no light action on my card either 

Thebear

---

### Post by Frak on 2007-01-09
Use the serial monkey driver, I can't seem to get the 1.1.0.0 driver working, but the serial monkey one works fine, nightly snapshot, not beta.

EDIT:
The Rutil one is the GUI for using the rt61-1.1.0-b1.tar.gz

---

### Post by tom-g on 2007-01-10
The serial monkey drivers should already be present. Here is what I did to get my card up and running with WPA-PSK.

Just for information:
 "uname -a"
Linux <I won't tell>  2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux


"sudo lspci -v" returned the following output:
00:0c.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: RaLink Unknown device 2561
        Flags: bus master, slow devsel, latency 32, IRQ 11
        Memory at de000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [40] Power Management version 2

"lsmod | grep rt"
rt61pci                37632  0 
80211                 175880  2 rate_control,rt61pci
crc_itu_t               3200  1 rt61pci


1. Create the file /etc/wpa_supplicant/wpa_supplicant.conf with the following contents ( sudo vi ...):

ap_scan=1

network={
       ssid="<your id>"
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP CCMP
       psk="<your plain text password>"
       priority=2
}

2. "sudo ifconfig wlan0 up" and check with "sudo iwlist scan" if card sees the AP.

3. "sudo wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf -i wlan0 -Dwext" 

The card should now be associated.

4. sudo dhclient wlan0

Now if everything works, It's time to make things permanent:

5. Edit the file /etc/network/interfaces (sudo vi ...). Mine looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
        wpa-driver wext
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto wlan0

That's it.

I had the same problems with NetworkManager. Just didn't work. Didn't have time to find out why.

---

### Post by Thebear on 2007-01-10
Okay so mines says 

Linux (......) 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

Does that make sense 

The bear

---

### Post by Thebear on 2007-01-10
And the sudo lspci -v  showed 

02:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Linksys Unknown device 0055
        Flags: bus master, slow devsel, latency 32, IRQ 177
        Memory at feaf0000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [40] Power Management version 2

I noticed that it says unknown device 0055  rather than 2561  does this mean it may not be an rt61 chipset? 

thebear

---

### Post by techstop on 2007-01-10
Well, the first line of your lspci suggests it's an RT61 card. Your errors in step 2 suggest that the module is not compiling properly. I really don't think that changing to the serialmonkey driver will fix those compilation issues, *plus* this is a HOWTO for RT61 cards using official drivers not serialmonkey drivers. Additionally, you won't need to use WPA supplicant as that is taken care of by the .dat configuration file.

Have you installed the linux headers for your kernal? See this post by the author of the HOWTO...

[http://www.ubuntuforums.org/showpost.php?p=1774337&postcount=32](http://www.ubuntuforums.org/showpost.php?p=1774337&postcount=32)

Try that, if you haven't got the headers installed, install them (see instructions in post linked to above) and try again.

Also, be sure you are not using network manager. It is not required and has been known to break the functionality. See this section of the thread linked to below (these instructions are for Dapper, but illustrate the problems that using the network tool can have);

> Some additional notes:

(a) Do not use the "Networking" tool (network-admin). You will get a lock-up at boot time at the point where the network interfaces are bieng configured. If you have used the Networking tool, you will have to comment out the entries in the file "/etc/network/interfaces." to do this:

[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

Hopefully the author of this howto might step in soon to help? :-k

---

### Post by Thebear on 2007-01-11
It seems to me anyway that the headers are loaded 

wayne@wayne-desktop:~$ dpkg -l |grep 'headers'
ii  libx11-dev                                 1.0.3-0ubuntu4                       X11 client-side library (development headers
ii  linux-headers-2.6.17-10                    2.6.17.1-10.34                       Header files related to Linux kernel version
ii  linux-headers-2.6.17-10-generic            2.6.17.1-10.34                       Linux kernel headers for version 2.6.17 on x
ii  linux-headers-generic                      2.6.17.10                            Generic Linux kernel headers
ii  x11proto-core-dev                          7.0.7-1                              X11 core wire protocol and auxiliary headers

I have just recently switched from Dapper to Edgy hoping that that could help solve the problem. 

While in Dapper I was one of those people that used the HOWTO by Judgekaster and got all the way to the end and kept getting the "No DHCPOFFERS Received" problem.  The proposed iwpriv solution yielded nothing as well.  


I ran into the network tool problem a also . 

Perhaps I shuld just reinstall edby and start again ? 

Thebear

---

### Post by techstop on 2007-01-11
Someone has posted their compiled module back here;

[http://ubuntuforums.org/showpost.php?p=1837733&postcount=82](http://ubuntuforums.org/showpost.php?p=1837733&postcount=82)

Maybe you could try using that?

I just tried downloading the ralink drivers but their site appears to be down. I am at a loss now, someone knowledgeable will show up soon I'm sure!

EDIT: I think I may have found something here;

[http://ubuntuforums.org/showpost.php?p=1747321&postcount=54](http://ubuntuforums.org/showpost.php?p=1747321&postcount=54)

When you installed Edgy, was it an upgrade from Dapper, or a clean install? It is possible that you have some old files left in the modules folder which are interfering.

---

### Post by tom-g on 2007-01-11
It was a fresh install. The only thing I installed after the initial install was NetworkManager (which did not work). No compiles, nothing. The driver came with my distribution. I verified than this is the serial monkey driver.

---

### Post by techstop on 2007-01-11
> **tom-g said:**
> The driver came with my distribution. I verified than this is the serial monkey driver.

Wait, this guide requires you to download the official ralink driver from their website, it is not for the serialmonkey driver. I'm confused...

EDIT: I was replying to thebear in the post above this one....

---

### Post by tom-g on 2007-01-11
To TheBear:

enter "lsmod | grep rt". If you get anything with rt61pci then then serial monkey drivers should be there. One file is in /lib/module/kernel/drivers/network/wireless/ra2x00 (or something close to that. I am currently at work and don't have my system to check): rt61pci.ko. The firmware for the card is somewhere in /lib/firmware.

Correct paths:
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/firmware/2.6.17-10-generic/rt25*

---

### Post by tom-g on 2007-01-11
> **techstop said:**
> Wait, this guide requires you to download the official ralink driver from their website, it is not for the serialmonkey driver. I'm confused...

EDIT: I was replying to thebear in the post above this one....

sorry, I noticed that too late. I had already pushed the button.

---

### Post by Thebear on 2007-01-11
mine was a fresh install also 

I will try the remedies that you both suggest later tonight. 

the link to the ralink drivers on the HOWTO does not work but I could get the newest drivers by just searching the ralink site. 

They did not work for me whowever 

I will look to see if the serial monkey drivers are there , I had trouble loading them 
I can't remeber right now what the problem was but I will let you know later.

the bear

---

### Post by tom-g on 2007-01-11
> **Thebear said:**
> 

the link to the ralink drivers on the HOWTO does not work but I could get the newest drivers by just searching the ralink site. 

They did not work for me whowever 

the bear

Just make sure to get rid of the installed drivers from the ralink site. Should be something like rt61 if the file was rt61.ko. Check this with the lsmod command I gave earlier.

Tom

---

### Post by tom-g on 2007-01-11
> **techstop said:**
> Wait, this guide requires you to download the official ralink driver from their website, it is not for the serialmonkey driver. I'm confused...


Just to clarify the confusion. The very first post by phq stated the included driver is broken. At least for my installation and card this is not the case. The serial monkey driver works fine for my card.

Tom

---

### Post by Thebear on 2007-01-13
To tom-g,
    You are correct the serial monkey driver and firmware are loaded where you said they were. 
I also removed the rt61.ko file. 

Now what do I do. 

Thebear

---

### Post by techstop on 2007-01-13
Perhaps discussion of the serialmonkey driver could continue in a separate thread? It's off-topic now.

---

### Post by tom-g on 2007-01-13
> **Thebear said:**
> To tom-g,
    You are correct the serial monkey driver and firmware are loaded where you said they were. 
I also removed the rt61.ko file. 

Now what do I do. 

Thebear

Please try following the steps I posted in my first post. If it works all is well:

1. Create the file /etc/wpa_supplicant/wpa_supplicant.conf with the following contents ( sudo vi ...):

ap_scan=1

network={
ssid="<your id>"
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
group=TKIP CCMP
psk="<your plain text password>"
priority=2
}

2. "sudo ifconfig wlan0 up" and check with "sudo iwlist scan" if card sees the AP.

3. "sudo wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf -i wlan0 -Dwext"

The card should now be associated.

4. sudo dhclient wlan0

Now if everything works, It's time to make things permanent:

5. Edit the file /etc/network/interfaces (sudo vi ...). Mine looks like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto wlan0

---

### Post by tom-g on 2007-01-13
> **techstop said:**
> Perhaps discussion of the serialmonkey driver could continue in a separate thread? It's off-topic now.

I don't see where this is off topic. Please read the title of the thread. Anyway I'm just trying to help.

---

### Post by techstop on 2007-01-13
> **tom-g said:**
> I don't see where this is off topic. Please read the title of the thread. Anyway I'm just trying to help.

I know you are trying to help.

However, this howto is for using the official driver, without using wpa supplicant. It is off-topic because you are discussing the serialmonkey driver and using wpa supplicant. To this point, all posts have been in relation to the official drivers and this howto. Are you suggesting that instructions on how to use a different procedure be included in this thread? It makes searching for answers difficult because there will be two procedures, two sets of problems, and two sets of people looking for help. It's too messy.

If you like, you could start your own howto thread on getting an RT61 card working with serialmonkey drivers and wpa supplicant, but it is off-topic in this thread because the procedure is *significantly different*. You are not changing a step here or there, but the entire procedure!

---

### Post by tom-g on 2007-01-13
> **techstop said:**
> I know you are trying to help.

However, this howto is for using the official driver, without using wpa supplicant. It is off-topic because you are discussing the serialmonkey driver and using wpa supplicant. To this point, all posts have been in relation to the official drivers and this howto. Are you suggesting that instructions on how to use a different procedure be included in this thread? It makes searching for answers difficult because there will be two procedures, two sets of problems, and two sets of people looking for help. It's too messy.

If you like, you could start your own howto thread on getting an RT61 card working with serialmonkey drivers and wpa supplicant, but it is off-topic in this thread because the procedure is *significantly different*. You are not changing a step here or there, but the entire procedure!

I don't agree. Things like that have to be looked at in context. Especially if as in this case the thread orginator has stated that the delivered drivers are broken.

---

### Post by Thebear on 2007-01-13
anyone

I have made a number of attempts to get this HOWTO to work.  using almost all the drivers that are mentioned. 

Do I need to worry about my past attempts leaving remnants behind 

If so is there any way I can clean out and start again. 

The bear

---

### Post by techstop on 2007-01-13
> **Thebear said:**
> anyone

I have made a number of attempts to get this HOWTO to work.  using almost all the drivers that are mentioned. 

Do I need to worry about my past attempts leaving remnants behind 

If so is there any way I can clean out and start again. 

The bear

Did you try using the precompiled module I linked to above? If so, what errors did you get?

---

### Post by Thebear on 2007-01-13
Techstop,

     I am not sure what you mean by precompiled module when I followed the link i found another link to how to download daily serial monkey tars and a zip file containing a rt61.ko.  Is this the precompiled module you refer to. Should I load that zip file into a particular directory and then what? 

The bear

---

### Post by techstop on 2007-01-13
Sorry about that, it's the wrong link. Let me find the right one...

EDIT: My apologies, I had my wires crossed with the link to the module above, I will have to go searching again, let me get back to you...

---

### Post by techstop on 2007-01-18
Thebear, sorry to take a while to get back to you. Very busy doing stuff for other people. Anyway....

I decided to have a go installing the RT61 drivers on my gf's system. She has an RT61 card (D-Link PCI card), but uses ethernet normally. Guess what? I get *exactly* the same errors when compiling the module as you do! Also, when doing "iwconfig" I get "no wireless extensions found" etc... ](*,) 

I did a bit of searching, and came across this command;

```
 sudo ifup ra0
```

let it do its thing, then try;

```
iwconfig
```

```
kirsten@kjs:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       no wireless extensions.

.....

kirsten@kjs:~$ sudo ifup ra0
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; Network is down.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:13:46:e8:a4:c8
Sending on   LPF/ra0/00:13:46:e8:a4:c8
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.195 -- renewal in 17098 seconds.
kirsten@kjs:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       RT61 Wireless  ESSID:"MYSSID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:9A:66:B6:99   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=91/100  Signal level:-48 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Success!!!! :mrgreen: 

Can you please try and let me know if it works or not for you? For one reason or another, the ra0 interface was not "up" for either of us at step 9. You bring it up with the command above. It's actually working, but you're not getting the expected result at the "iwconfig" step of the HOWTO. Have you actually gone past that step? ie from step 10 onwards? I setup my "/etc/network/interfaces" file after I got the "no wireless extensions found" error at step 9 and before I did that "ifup ra0" command. I'm not sure what implications this has for bringing the interface up each boot.

Please let me know how you go. Cheers.

BTW: I followed the HOWTO exactly up until step 9 didn't work. ie. I used the ralink drivers.

---

### Post by Frak on 2007-01-18
Hey could you, technically speaking, replace WPA with WEP if that is what we are using?

---

### Post by lukew on 2007-01-18
> **Frak said:**
> Hey could you, technically speaking, replace WPA with WEP if that is what we are using?



There are some entries for WEP in 

```
#> vi -b /etc/Wireless/RT61STA/rt61sta.dat
```

You need to put in the encrypted key and the key number.

Luke

---

### Post by bill.albertson on 2007-01-19
I need help finding the necessary EXTRA packages to install for this build.  ](*,) 

The build of the kernel module fails for me at step 2:
```
bill@bill-desktop:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$ cp -f Makefile.6 Makefile
bill@bill-desktop:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$ make all
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/bill/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
bill@bill-desktop:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$ sudo make all
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/bill/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
bill@bill-desktop:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$
```
I have installed **build-essential** and **linux kernel headers for 'uname -r'**.  The problem is that make wants a directory I know nothing about, and was not created or populated by either build-essential nor the kernel headers.  Do I also need the linux source package, or some other developer package for the rt61 kernel module build, then?

Also, the rt61.ko driver posted to this forum does NOT work for the current default kernel (2.6.15-27-386 with gcc-4.0), I get a **fatal error inserting rt61: Invalid module format.**  Probably because it was compiled for a completely different type of kernel (586 SMP gcc-4.1), using a different version of gcc.  Anyone can run a 'modinfo rt61' vs a 'modinfo rtc' to see what I mean.

---

### Post by techstop on 2007-01-19
> **bill.albertson said:**
> I need help finding the necessary EXTRA packages to install for this build.  ](*,) 

The build of the kernel module fails for me at step 2:

<SNIP>

I have installed **build-essential** and **linux kernel headers for 'uname -r'**.  The problem is that make wants a directory I know nothing about, and was not created or populated by either build-essential nor the kernel headers.  Do I also need the linux source package, or some other developer package for the rt61 kernel module build, then?

Also, the rt61.ko driver posted to this forum does NOT work for the current default kernel (2.6.15-27-386 with gcc-4.0), I get a **fatal error inserting rt61: Invalid module format.**  Probably because it was compiled for a completely different type of kernel (586 SMP gcc-4.1), using a different version of gcc.  Anyone can run a 'modinfo rt61' vs a 'modinfo rtc' to see what I mean.

My kernel is 2.6.17-10-generic but yours seems to be an earlier version? You are running edgy right? If you are running dapper, I had success with this howto;

[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

```
kirsten@kjs:~$ modinfo rt61
filename:       /lib/modules/2.6.17-10-generic/kernel/drivers/net/rt61.ko
author:         Paul Lin <paul_lin@ralinktech.com>
description:    RT61 Wireless Lan Linux Driver
license:        GPL
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
srcversion:     4EF93805FB7B2CC0B57D92B
```

```
kirsten@kjs:~$ modinfo rtc
modinfo: could not find module rtc
kirsten@kjs:~$
```

What have you got in your /lib/modules directory? I have a folder matching my current kernel version.

---

### Post by Thebear on 2007-01-19
Techstop,
       Sorry but that remedy did not work.  It sounded like we were so close to.   But Perhaps the output will give you another clue. 

wayne@wayne-desktop:~$ iwconfig
lo        no wireless extensions.

ra0       no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wayne@wayne-desktop:~$  sudo ifup ra0
Ignoring unknown interface ra0=ra0.

The bear

BTW

this follows step 9 just like you

---

### Post by techstop on 2007-01-19
> **Thebear said:**
> Techstop,
       Sorry but that remedy did not work.  It sounded like we were so close to.   But Perhaps the output will give you another clue. 

wayne@wayne-desktop:~$ iwconfig
lo        no wireless extensions.

ra0       no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wayne@wayne-desktop:~$  sudo ifup ra0
Ignoring unknown interface ra0=ra0.

The bear

BTW

this follows step 9 just like you

So, start at step 8 to load the module first;

```
modprobe rt61
```

Then;

```
sudo ifup ra0
```

Any luck? Can you also post your /etc/network/interfaces file?

---

### Post by Thebear on 2007-01-19
Techstop, 
    Went back to step 8 again with a fresh boot, and then when I ran ifup ra0 ti starts to work but the machine keeps hanging up and freezing before it can complete. 

The first time it went through only one DHCP search and the second time six. 


BTW - ect/network/interfaces file reads 

iface ra0- inet dhcp
wireless-essid b1test00
wireless-key s:thebearwpa

that all seems correct.

Also my wired connection is no longer working. 

I am writing this now on my windows laptop. 

The bear

---

### Post by techstop on 2007-01-19
> **Thebear said:**
> Techstop, 
    Went back to step 8 again with a fresh boot, and then when I ran ifup ra0 ti starts to work but the machine keeps hanging up and freezing before it can complete. 

The first time it went through only one DHCP search and the second time six. 


BTW - ect/network/interfaces file reads 

iface ra0- inet dhcp
wireless-essid b1test00
wireless-key s:thebearwpa

that all seems correct.

Also my wired connection is no longer working. 

I am writing this now on my windows laptop. 

The bear

I don't think your /etc/network/interfaces file is correct; you have your key in there, which is supposed to be in the configuration file "/etc/Wireless/RT61STA/rt61sta.dat" plus you are missing the line

```
auto ra0
```

...and also there is an extra hyphen after ra0 which isn't needed.

Try changing your file so it reads;

```
iface ra0 inet dhcp
wireless-essid b1test00
auto ra0
```

...plus whatever is there for your other interfaces. Here is the file from my gf's pc;

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

iface ra0 inet dhcp
wireless-essid MYSSID
auto ra0
```

See how you go. I think we are almost there!

---

### Post by bill.albertson on 2007-01-20
Well, this would explain some of my issues... I am running 6.06 LTS, Dapper....sigh.  I don't know how I got it into my head that I was running Edgy.  Well, back to the drawing board.

---

### Post by techstop on 2007-01-20
> **bill.albertson said:**
> Well, this would explain some of my issues... I am running 6.06 LTS, Dapper....sigh.  I don't know how I got it into my head that I was running Edgy.  Well, back to the drawing board.

Try the link I posted above, it's a pretty similar procedure.

---

### Post by Thebear on 2007-01-20
Techstop, 
   Thanks for all of your help so far, but I am sitll having mysterious problems. 

I set my interfaces to match your gf's but the system would still hang up.  The mouse would freeze and the terminal would not respond. 

I even went so far as to reinstall edgy and start all over again with the HOWTO. 

When I got to Step 8 . Just I had ra0  plus all the others showing up with "no wireless extensions" 

I then tried the  sudo ifup rao - and got the message "Ignoring unknown interface ra0=ra0.
" just like last time.  I went back to install the module rt61 with modprobe ret61 which worked before but no dice "still the same message" 

Then I looked at the interfaces file and saw no mention of ra0.  so I added the lines 

iface ra0 inet dhcp
wireless-essid b1test00
auto ra0

and commented out the wlan0 lines

Then when I ran sudo ifup ra0 it starts to run, but hangs up the system again freezes. 

Even though I completely reinstalled. 

I hope this gives you some clues.

But I am still patientily plugging away. 

Thebear

---

### Post by Thebear on 2007-01-21
Techstop 
here is the kernel  message buffer for clues
wayne@wayne-desktop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000027fc0000 (usable)
[17179569.184000]  BIOS-e820: 0000000027fc0000 - 0000000027ff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000027ff8000 - 0000000028000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 639MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 163776
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 159680 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000ff980
[17179569.184000] ACPI: RSDT (v001 D845HV WN84510A 0x20010914 MSFT 0x00001011) @ 0x27ff0000
[17179569.184000] ACPI: FADT (v001 D845HV HV84510A 0x20010914 MSFT 0x00001011) @ 0x27ff1000
[17179569.184000] ACPI: MADT (v001 D845HV HV84510A 0x20010914 MSFT 0x00001011) @ 0x27fe2ec0
[17179569.184000] ACPI: SSDT (v001 D845HV HV84510A 0x00000001 MSFT 0x0100000b) @ 0x27fe2f28
[17179569.184000] ACPI: DSDT (v001 D845HV HV84510A 0x00000006 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:0 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 28000000:d6c00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1395.697 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.664000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.668000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.700000] Memory: 639336k/655104k available (1910k kernel code, 15264k reserved, 1070k data, 308k init, 0k highmem)
[17179570.700000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.780000] Calibrating delay using timer specific routine.. 2795.21 BogoMIPS (lpj=5590426)
[17179570.780000] Security Framework v1.0.0 initialized
[17179570.780000] SELinux:  Disabled at boot.
[17179570.780000] Mount-cache hash table entries: 512
[17179570.780000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.780000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.780000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179570.780000] CPU: L2 cache: 256K
[17179570.780000] CPU: Hyper-Threading is disabled
[17179570.780000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[17179570.780000] Checking 'hlt' instruction... OK.
[17179570.796000] SMP alternatives: switching to UP code
[17179570.796000] Freeing SMP alternatives: 16k freed
[17179570.796000] checking if image is initramfs... it is
[17179571.792000] Freeing initrd memory: 5564k freed
[17179571.792000] ACPI: Core revision 20060707
[17179571.792000] ACPI: Looking for DSDT ... not found!
[17179571.796000] CPU0: Intel(R) Pentium(R) 4 CPU 1400MHz stepping 0a
[17179571.796000] Total of 1 processors activated (2795.21 BogoMIPS).
[17179571.796000] ENABLING IO-APIC IRQs
[17179571.796000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.940000] Brought up 1 CPUs
[17179571.940000] migration_cost=0
[17179571.940000] NET: Registered protocol family 16
[17179571.940000] EISA bus registered
[17179571.940000] ACPI: bus type pci registered
[17179571.940000] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=2
[17179571.940000] PCI: Using configuration type 1
[17179571.940000] Setting up standard PCI resources
[17179571.948000] ACPI: Interpreter enabled
[17179571.948000] ACPI: Using IOAPIC for interrupt routing
[17179571.948000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.948000] PCI: Probing PCI hardware (bus 00)
[17179571.952000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[17179571.952000] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[17179571.952000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.952000] Boot video device is 0000:01:00.0
[17179571.952000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.952000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.956000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.956000] ACPI: Power Resource [FDDP] (off)
[17179571.960000] ACPI: Power Resource [URP1] (off)
[17179571.960000] ACPI: Power Resource [URP2] (off)
[17179571.960000] ACPI: Power Resource [LPTP] (off)
[17179571.964000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.964000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179571.964000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.964000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.964000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.964000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.964000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.964000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179571.964000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.964000] pnp: PnP ACPI init
[17179571.972000] pnp: PnP ACPI: found 13 devices
[17179571.972000] PnPBIOS: Disabled by ACPI PNP
[17179571.972000] PCI: Using ACPI for IRQ routing
[17179571.972000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.976000] PCI: Bridge: 0000:00:01.0
[17179571.976000]   IO window: disabled.
[17179571.976000]   MEM window: fc900000-fe9fffff
[17179571.976000]   PREFETCH window: e4600000-f46fffff
[17179571.976000] PCI: Bridge: 0000:00:1e.0
[17179571.976000]   IO window: d000-dfff
[17179571.976000]   MEM window: fea00000-feafffff
[17179571.976000]   PREFETCH window: f4700000-f47fffff
[17179571.976000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.976000] NET: Registered protocol family 2
[17179572.016000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.016000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179572.016000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179572.020000] TCP: Hash tables configured (established 131072 bind 65536)
[17179572.020000] TCP reno registered
[17179572.020000] audit: initializing netlink socket (disabled)
[17179572.020000] audit(1169382994.020:1): initialized
[17179572.020000] VFS: Disk quotas dquot_6.5.1
[17179572.020000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.020000] Initializing Cryptographic API
[17179572.020000] io scheduler noop registered
[17179572.020000] io scheduler anticipatory registered
[17179572.020000] io scheduler deadline registered
[17179572.020000] io scheduler cfq registered (default)
[17179572.020000] isapnp: Scanning for PnP cards...
[17179572.384000] isapnp: No Plug & Play device found
[17179572.460000] Real Time Clock Driver v1.12ac
[17179572.460000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.460000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.460000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.464000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.464000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.464000] mice: PS/2 mouse device common for all mice
[17179572.464000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.464000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.464000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.468000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179572.468000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.468000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.468000] EISA: Probing bus 0 at eisa.0
[17179572.468000] EISA: Detected 0 cards.
[17179572.472000] TCP bic registered
[17179572.472000] NET: Registered protocol family 1
[17179572.472000] NET: Registered protocol family 8
[17179572.472000] NET: Registered protocol family 20
[17179572.472000] Using IPI No-Shortcut mode
[17179572.472000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.472000] Freeing unused kernel memory: 308k freed
[17179573.696000] Capability LSM initialized
[17179573.784000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179573.784000] ACPI: Getting cpuindex for acpiid 0x2
[17179574.936000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[17179574.936000] ICH2: chipset revision 18
[17179574.936000] ICH2: not 100% native mode: will probe irqs later
[17179574.936000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179574.936000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[17179574.936000] Probing IDE interface ide0...
[17179575.228000] hda: FUJITSU MPF3102AT, ATA DISK drive
[17179575.900000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.908000] Probing IDE interface ide1...
[17179576.648000] hdc: MATSHITA CD-RW CW-7585, ATAPI CD/DVD-ROM drive
[17179576.984000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.000000] hda: max request size: 128KiB
[17179577.020000] hda: 20015856 sectors (10248 MB) w/512KiB Cache, CHS=19857/16/63, UDMA(33)
[17179577.020000] hda: cache flushes not supported
[17179577.020000]  hda: hda1 hda2 < hda5 >
[17179577.088000] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179577.088000] Uniform CD-ROM driver Revision: 3.20
[17179577.504000] usbcore: registered new driver usbfs
[17179577.504000] usbcore: registered new driver hub
[17179577.504000] USB Universal Host Controller Interface driver v3.0
[17179577.504000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 169
[17179577.504000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179577.508000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179577.508000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179577.508000] uhci_hcd 0000:00:1f.2: irq 169, io base 0x0000ef40
[17179577.508000] usb usb1: configuration #1 chosen from 1 choice
[17179577.508000] hub 1-0:1.0: USB hub found
[17179577.508000] hub 1-0:1.0: 2 ports detected
[17179577.612000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 177
[17179577.612000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[17179577.612000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[17179577.612000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[17179577.612000] uhci_hcd 0000:00:1f.4: irq 177, io base 0x0000ef80
[17179577.612000] usb usb2: configuration #1 chosen from 1 choice
[17179577.612000] hub 2-0:1.0: USB hub found
[17179577.612000] hub 2-0:1.0: 2 ports detected
[17179577.844000] Attempting manual resume
[17179577.912000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179577.912000] EXT3-fs: write access will be enabled during recovery.
[17179577.956000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179578.108000] usb 2-2: configuration #1 chosen from 1 choice
[17179578.112000] hub 2-2:1.0: USB hub found
[17179578.116000] hub 2-2:1.0: 4 ports detected
[17179578.424000] usb 2-2.1: new low speed USB device using uhci_hcd and address 3
[17179578.560000] usb 2-2.1: configuration #1 chosen from 1 choice
[17179578.764000] usb 2-2.2: new low speed USB device using uhci_hcd and address 4
[17179578.912000] usb 2-2.2: configuration #1 chosen from 1 choice
[17179578.956000] usbcore: registered new driver hiddev
[17179578.972000] input: Logitech USB Mouse as /class/input/input0
[17179578.976000] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1f.4-2.1
[17179578.992000] input: Microsoft Microsoft Internet Keyboard as /class/input/input1
[17179578.992000] input: USB HID v1.10 Keyboard [Microsoft Microsoft Internet Keyboard] on usb-0000:00:1f.4-2.2
[17179579.016000] input: Microsoft Microsoft Internet Keyboard as /class/input/input2
[17179579.016000] input: USB HID v1.10 Device [Microsoft Microsoft Internet Keyboard] on usb-0000:00:1f.4-2.2
[17179579.016000] usbcore: registered new driver usbhid
[17179579.016000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179579.492000] kjournald starting.  Commit interval 5 seconds
[17179579.496000] EXT3-fs: recovery complete.
[17179579.496000] EXT3-fs: mounted filesystem with ordered data mode.
[17179593.984000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.992000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179594.164000] Floppy drive(s): fd0 is 1.44M
[17179594.204000] FDC 0 is a post-1991 82077
[17179594.216000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.220000] agpgart: Detected an Intel i845 Chipset.
[17179594.224000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179594.516000] parport: PnPBIOS parport detected.
[17179594.516000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179594.848000] hw_random hardware driver 1.0.0 loaded
[17179594.884000] input: PC Speaker as /class/input/input3
[17179595.972000] ts: Compaq touchscreen protocol output
[17179596.472000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 185
[17179596.472000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179597.144000] intel8x0_measure_ac97_clock: measured 56190 usecs
[17179597.144000] intel8x0: clocking to 48000
[17179597.144000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179597.144000] RT61: Vendor = 0x1814, Product = 0x0301 
[17179597.208000] 8139too Fast Ethernet driver 0.9.27
[17179597.208000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179597.208000] eth0: RealTek RTL8139 at 0xe88e0c00, 00:40:05:84:67:92, IRQ 185
[17179597.208000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179597.268000] Loading module: rt61pci - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[17179597.364000] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179597.404000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179597.624000] RT61: RfIcType= 3
[17179597.676000] lp0: using parport0 (interrupt-driven).
[17179597.740000] Adding 441748k swap on /dev/disk/by-uuid/6279ff30-95eb-4042-bee7-5162658f142e.  Priority:-1 extents:1 across:441748k
[17179597.828000] EXT3 FS on hda1, internal journal
[17179598.500000] NET: Registered protocol family 17
[17179600.684000] f1:35:f2:1a:ce:01:e4:79:e3:e4:75:1b:4c:db:2b:17:
[17179600.684000] f0:50:3f:2a:e2:af:c9:5b:
[17179600.684000] 24:52:3e:eb:d2:39:19:4e:
[17179600.688000] 8c:9d:a5:0b:a3:21:14:3c:40:a6:1c:be:f2:27:69:eb:
[17179600.688000] 8e:c1:69:87:ce:7e:c8:7f:
[17179600.688000] 08:7d:e2:26:4a:c9:1b:4e:
[17179601.652000] NET: Registered protocol family 10
[17179601.652000] lo: Disabled Privacy Extensions
[17179601.652000] IPv6 over IPv4 tunneling driver
[17179603.592000] ACPI: Power Button (FF) [PWRF]
[17179603.592000] ACPI: Power Button (CM) [PBTN]
[17179603.816000] ibm_acpi: ec object not found
[17179603.860000] pcc_acpi: loading...
[17179608.524000] apm: BIOS not found.
[17179608.856000] 15:d4:71:2c:d2:da:56:a8:b1:bb:5c:e5:dd:9b:75:92:
[17179608.856000] 3d:03:68:20:ba:c9:ed:97:
[17179608.856000] e0:61:45:1c:03:51:23:4f:
[17179612.168000] eth0: no IPv6 routers present
[17179612.236000] ra0: no IPv6 routers present
[17179612.880000] 54:2d:e7:75:ca:ec:e4:86:07:a5:0c:68:76:11:86:26:
[17179612.880000] 70:3e:60:c4:df:a3:12:b4:
[17179612.880000] af:d8:3f:40:a3:bd:57:f9:
[17179612.884000] 2c:7a:3d:32:c7:4c:72:00:0e:7e:d4:2e:e2:73:ed:2b:
[17179612.884000] 9a:6c:16:c7:f9:fb:4b:0e:
[17179612.884000] 16:96:98:23:4c:19:a8:81:
[17179614.956000] Bluetooth: Core ver 2.8
[17179614.956000] NET: Registered protocol family 31
[17179614.956000] Bluetooth: HCI device and connection manager initialized
[17179614.956000] Bluetooth: HCI socket layer initialized
[17179615.004000] Bluetooth: L2CAP ver 2.8
[17179615.004000] Bluetooth: L2CAP socket layer initialized
[17179615.036000] Bluetooth: RFCOMM socket layer initialized
[17179615.036000] Bluetooth: RFCOMM TTY layer initialized
[17179615.036000] Bluetooth: RFCOMM ver 1.7
[17179642.992000] 10:8a:7e:88:e8:94:b7:41:39:09:ea:73:bd:29:85:35:
[17179642.992000] 5c:d7:04:eb:6b:7d:d4:8a:
[17179642.992000] a0:8f:c2:95:b3:64:68:65:
[17179673.412000] 2c:c5:ec:b7:f1:7b:ad:80:e4:e9:ec:49:66:a7:f5:d8:
[17179673.412000] 89:e6:7a:70:33:68:f9:4c:
[17179673.412000] 65:09:15:d8:a6:02:c4:e0:

---

### Post by Thebear on 2007-01-21
Techstop

In order to stop the freezing problem I commented out the entry for eth0 in the etc/network/interfaces file, assuming that having two possibly active connections may be causing the freezing.  It worked and the freezing problem stopped. 

I then reran <sudo ifup ra0> and it ran this time and configured the ra0

so here is the iwconfig output

wayne@wayne-desktop:~$ iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:"b1test00"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:A3:69:C3:A2   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level:-59 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

wayne@wayne-desktop:~$ 

When I look at the system/administration/networking 
it shows the wireless ra0 as active and configured and the eth0 as not configured. 

I have attached the screen shot. 

So all should be working, but I can't access the internet without the cable plugged in. 



The bear

---

### Post by Thebear on 2007-01-21
Sorry forgot to attach the screenshot

---

### Post by shackleton on 2007-01-21
@phq: Thanks man, worked like a charm!

---

### Post by techstop on 2007-01-21
> **Thebear said:**
> Techstop 
here is the kernel  message buffer for clues

[17179597.268000] Loading module: rt61pci - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).



Well, it looks like you're loading the rt61pci module which should be blacklisted. (See second step of Step 10). Maybe try finishing the howto, reboot, enable your eth0 again and reboot.

I have to admire your persistence in getting your wireless card working!

---

### Post by LordMau on 2007-01-21
Here's my error at the make step:
```
make: *** /lib/modules/2.6.17-10-generic/build: No such file or directory.   
```
What's missing on my system <sorry this looks noobish>?

thanks!

---

### Post by bill.albertson on 2007-01-22
> **LordMau said:**
> Here's my error at the make step:
```
make: *** /lib/modules/2.6.17-10-generic/build: No such file or directory.   
```
What's missing on my system <sorry this looks noobish>?

thanks!

I have had the same problem.  Thankfully, the ONE file that you would be missing probably can be found already on your system, under /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2600/rt61.k0.  All of the other files are binaries and the dat file that come in the package, precompiled.

Unfortunately, I have also had zero luck getting the original source from ralink to compile.  Packages **build-essential** and **kernel headers** for current kernel version have not allowed me to compile, even though these are all that "should" be needed.  I even tried installing the **linux source** package as well.  

There is something not installed, and nobody can tell me what it is either- though there have been plenty of guessers who do have it installed, but don't know that it wasn't created by loading the former mentioned packages.  None of the former packages I mention (and you can check this under synaptic, by selecting each package's properties) actually create or install to the missing directory that make desires so badly.  

So, you might want to try the default kernel module that isn't mentioned clearly in the directions.  I found this reference somewhere in between pages 11 and 15 after my third read of one of these threads, and after much coffee.  :roll: 

Oh, and don't forget to read all of the notes before you START.  ALL of the notes.  Like the one about commenting out anything that might show up in /etc/network/interfaces, or you will be doing brain surgery by hooking up you drive to another system to comment out all references to ra0 in the interfaces file.  Otherwise, bad things happen, like your system not working, even when you boot up in failsafe mode.

---

### Post by rascal on 2007-01-22
I'm having trouble compiling the driver as well. I'm using feisty, kernel-headers and build-essential are installed. This is what I get when i type "make all":

```
make -C /lib/modules/2.6.20-5-386/build SUBDIRS=/home/simo/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-5-386'
  CC [M]  /home/simo/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/simo/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/simo/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/simo/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/home/simo/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/simo/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/simo/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-5-386'
make: *** [all] Error 2

```

In Edgy the driver compiles just fine.

---

### Post by Thebear on 2007-01-22
Lord Mau

The files that the HOWTO point to are no longer there,  they are located at 

[www.ralinktech.com](www.ralinktech.com)  

They are on the support page under linux, just click on the rt2561/rt61 and the files will down load and extract to /tmp

then start the HOWTO  at step two and tar the file. 

Should work from there. 

Not for me but for you probably. 

The BEAR

---

### Post by Thebear on 2007-01-22
Lord mau,
    Please note the current file on the server is 

rt61_Linux_STA_Drv1.1.0.0.tar.gz

like the original file not 

rt61_Linuz_STA_Drv1.4.0.0.tar.gz  as in the bulk of the HOWTO you have to change the commands to reflect that. 

The bear

---

### Post by Thebear on 2007-01-22
STill trying to get this HOWTO to work for me. 

All seems to be correct 
rt61pci is blacklisted, etc, etc, 

when I run dmesg

I keep getting this message within the kernel log

ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !

The driver I am using is rt61_Linux_STA_Drv1.1.0.0 from the ralinktech.com website. 

Does anyone have a different driver to try, this one just does not seem to work for me. 

the bear

---

### Post by techstop on 2007-01-23
> **Thebear said:**
> STill trying to get this HOWTO to work for me. 

All seems to be correct 
rt61pci is blacklisted, etc, etc, 

when I run dmesg

I keep getting this message within the kernel log
[B]
ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver ![/B]

The driver I am using is rt61_Linux_STA_Drv1.1.0.0 from the ralinktech.com website. 

Does anyone have a different driver to try, this one just does not seem to work for me. 

the bear

I get that line as well. Nothing to worry about as far as I can see. Can you please post your **entire** /etc/network/interfaces file? I had the same error "unknown interface ra0=ra0" on a dapper install, and I fixed it by editing the interfaces file.

> **bill.albertson said:**
> 

Unfortunately, I have also had zero luck getting the original source from ralink to compile.  Packages **build-essential** and **kernel headers** for current kernel version have not allowed me to compile, even though these are all that "should" be needed.  I even tried installing the **linux source** package as well.  

There is something not installed, and nobody can tell me what it is either...<SNIP>

Again, you don't need this howto if you are indeed running dapper. There is a built-in driver that you can use (which works!) and you don't need to compile anything. I posted the link for the dapper howto earlier, which is here again; scroll down to the section beginning with;

> (b) rt61 in Dapper

Ubuntu 6.06 (Dapper Drake) comes with the rt61 driver. However, you will still have to copy the firmware files to /etc/Wireless/RT61STA.

[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

Or, have you installed edgy now?

---

### Post by Thebear on 2007-01-23
Techstop

Yes here is my entire interfaces file

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#wlan0 inet dhcp

iface ra0 inet dhcp
wireless-essid b1test00
auto ra0

When I follow the Howto I get to step  8  then step 9 and then instead of completing step 10   I skip it and  run the sudo ifup rap command.  At that time I get the ""unknown interface ra0=ra0"   that you mentioned. 

I then carry on with the HOWTO and then run the "sudo ifup ra0 " just after using the vi editor to update the etc/network/interfaces files as you see above. 

Just like you I can't get sudo ifup ra- to work until I modify the file.  

Also if I forget to comment out the wlan0 i get system freeze. 

Anyway is that the procedure you follow or am I missing something. 

The bear

---

### Post by LordMau on 2007-01-23
> **bill.albertson said:**
> I have had the same problem.  Thankfully, the ONE file that you would be missing probably can be found already on your system, under /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2600/rt61.k0.  All of the other files are binaries and the dat file that come in the package, precompiled.


I believe that file exists under dapper installs only. I recall that my prev dapper system worked right away after installing the .bin files needed by the rt61 card. In edgy there is no .../rt2600 folder, and as such rt61.ko file, only there is rt61pci.ko file that seems broke hence this thread.

As an aside its mind boogling to think that up to now the official rt61 driver is still broken. You'd think the working file as detailed in this thread should be in the official repos by now, considering the dapper one worked fine. ](*,) 

> **Thebear said:**
> Lord Mau

The files that the HOWTO point to are no longer there,  they are located at 

[www.ralinktech.com](www.ralinktech.com)  

They are on the support page under linux, just click on the rt2561/rt61 and the files will down load and extract to /tmp

then start the HOWTO  at step two and tar the file. 

Should work from there. 

Not for me but for you probably. 

The BEAR

Yep got all that. The thing is the makefile seems to look for a /build folder as indicated in the error message:

```
make: *** /lib/modules/2.6.17-10-generic/build: No such file or directory.
```

but i don't have a build folder or file in that directory. Hence my question if I have a missing package that was overlooked in my dis-upgrade to edgy. build-essential etc are all installed as per the instructions.

Anyway I took a shortcut instead. Seems that someone already posted a working rt61.ko in this thread. I used that and now my wireless works, albeit for now without WPA or WEP even hehe. Don't even use the rt61sta.dat for now.

---

### Post by techstop on 2007-01-24
> **Thebear said:**
> 
When I follow the Howto I get to step  8  then step 9 and then instead of completing step 10   I skip it and  run the sudo ifup rap command.  At that time I get the ""unknown interface ra0=ra0"   that you mentioned. 

I then carry on with the HOWTO and then run the "sudo ifup ra0 " just after using the vi editor to update the etc/network/interfaces files as you see above. 

Just like you I can't get sudo ifup ra- to work until I modify the file.  

Also if I forget to comment out the wlan0 i get system freeze. 

Anyway is that the procedure you follow or am I missing something. 

The bear

I really don't know now. I am completely out of ideas. In fact, I have got the wireless card running without doing any of step 10, so I really don't know. Your setup seems to be the same as me. If I find out anything, I will be sure to let you know. Sorry we couldn't get it working... ](*,)

---

### Post by Thebear on 2007-01-24
Thanks Techstop
 
I admire your persistence in continuing to try to help me. 

Let me know if you can think of anything. 

I also seem to be plagued with a lot of freeze ups as well so there is something wrong, I may try the wireless card in another machine just to check to see if it is functioning properly.

Bye for now

---

### Post by gooba on 2007-01-26
I got my dlink DWL G510 working with a fresh install of edgy using wpa_supplicant using the following guide [http://www.strangeparty.com/2006/11/26/getting-a-wmp56g-pci-wifi-card-working-under-debian-etch/](http://www.strangeparty.com/2006/11/26/getting-a-wmp56g-pci-wifi-card-working-under-debian-etch/)
edgy loaded the rt61pci driver by default and it just worked. hope this helps others.
The only problem I have is using ftp over my lan drops the network after about 10 minutes and i have to reboot to make it work again. does anyone have any ideas about it?

 iwconfig 
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"xxxxxxxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:50:6A:73   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:17:9A:BE:58:4F  
          inet addr:192.168.2.121  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:febe:584f/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2771531 (2.6 MiB)  TX bytes:499087 (487.3 KiB)
          Base address:0x1000 

wmaster0  Link encap:UNSPEC  HWaddr 00-17-9A-BE-58-4F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x1000

---

### Post by almax00 on 2007-01-28
i followed the original how-to and eventually got my gigabyte rt61 based pci card to work. i got to step 9 and got "no wireless extensions" as others got. i poked around and found in: /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless some remenants of the default installed drivers so i deleted anything that looked remotely like rtXXXX and rtlXXXX. (having deleted the files i can't list exact names). i did modprobe rt61 again. i rebooted and/or restarted the network (/etc/init.d/networking restart) AFTER configuring the rt61sta.dat file.

Sun Jan 28 /etc/Wireless/RT61STA:$ cat rt61sta.dat
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=NETGEAR
NetworkType=Managed
Channel=auto
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=**see below**
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

note you have to use the following in konsole to get your WPAPSK: (DO use the single quotes)
Sun Jan 28 /etc/Wireless/RT61STA:$ wpa_passphrase 'your_ssid' 'your_secret_password' should return:
network={
        ssid="your-ssid'
        #psk="your_secret_password"
        psk=enter_the_long_string_of_numbers/letters_after_WPAPSK_in_rt61sta.dat
}

i am now trying to find a way to monitor my network, ie signal strength, networks available, etc.
does anyone know how to do this? i tried kwirelessmonitor and kwavecontrol and got "device error" as if they couldn't see the network.

good luck to all. i am on a fresh install of kubuntu edgy

---

### Post by NoWhereMan on 2007-01-28
if you (you, people with rt61) still have noapic in your kernel parameters, remove it or the driver will fail to work

bye

---

### Post by Thebear on 2007-01-30
How does one go about removing noapic from the kernel parameters.  Where do you find the kernel parameters. 

thebear

---

### Post by NoWhereMan on 2007-01-31
if you do not know how to do it you probably don't have to. If you have, you are supposed to have added yourself that parameter to the kernel

btw is in /boot/grub/menu.lst (do not edit that file if you don't know what you're doing)

bye

---

### Post by adrianj on 2007-02-02
Great instructions!

I got my Belkin F5D7010yy (ver 6000yy) Wireless G Network Card working following your guide.

---

### Post by adrianj on 2007-02-02
Great instructions!

I got my Belkin F5D7010yy (ver 6000yy) Wireless G Network Card working on 6.10 following your guide.

---

### Post by BeachBum on 2007-02-02
@ phq - Thanks for the howto, it is so close to working!

I've been playing with this driver for quite some time on Edgy, and have noted the following:

If after 
> modprobe rt61
you see
> ra0     no wireless extensions.
try running
> sudo ifconfig ra0 up

I was under the impression ifconfig ra0 up was the same as ifup ra0, however it doesn't seem to be the case; ifconfig ra0 up seems to activate the interface while ifup ra0 attempts to assign IP via DHCP.  

I've been following the serialmonkey drivers closely because of the master mode support, but both the legacy and rt2x00 drivers are too immature for my machine :confused:.

I am currently trying to setup ra0 as ad-hoc, in this manner:

Internet -> [eth0 - workstation - ra0] -> laptops

The issue I'm having is that this driver/ my configuration seems hit or miss; last night the driver was working well; iwconfig showed the correct mode, essid, and iwlist from the workstation and laptops saw the essid.  I brought the interface up and down a few times, and now the driver does not retain the essid; iwconfig shows the essid as blank :confused:.  I have regularly cycled removing the module and loading using the following commands:
> 
ifconfig ra0 down
modprobe -r rt61
modprobe rt61
ifconfig ra0 up

The result is the following:

#iwconfig
ra0       RT61 Wireless  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 76:E4:76:B0:7B:2E   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

#ifconfig
ra0       Link encap:Ethernet  HWaddr 00:0E:2E:5E:7B:9E  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe5e:7b9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:28 dropped:28 overruns:0 carrier:0
          collisions:54 txqueuelen:1000 
          RX bytes:2190931 (2.0 MiB)  TX bytes:7839 (7.6 KiB)
          Interrupt:50 

Here are a few configs:
#interfaces
auto ra0
iface ra0 inet static
address 192.168.1.1
netmask 255.255.255.0
        wireless-mode           ad-hoc
        wireless-essid          thinkcentre
        wireless-channel        6

#rt61sta.dat
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=thinkcentre
NetworkType=Adhoc
Channel=6
AuthMode=OPEN
EncrypType=NONE
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789

Anyone have any suggestions?

---

### Post by SunshineSmile on 2007-02-04
Hi folks.

Read through the entire thread, and have some questions. I can't get my wifi up either. 

I am using the D-Link DWL G510 (same as cirorodrigues on page 14). I follow the original instructions, using the **RT61_Linux_STA_Drv1.1.0.0.tar.gz**, that I found on the ralinktech page.

It takes me all the way to the **iwconfig** step without problems. iwconfig shows no extensions.

So I type *sudo ifconfig ra0 up* like BeachBum above suggested. Iwconfig now lists up some data for ra0. However, when disabling my ethernetcable, I am unable to get online.

I need a **strategy to get me further**. I have done all the steps in the original post. 
- should I try the **serialmonkey** approach?
- do I have to clean up the mess I have created now, and how do I do that? Re-install?

```
vi -b /etc/Wireless/RT61STA/rt61sta.dat

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=FoxhoundNetwork
NetworkType=Infra
Channel=1
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=here I typed in my wpa-psk key
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
"/etc/Wireless/RT61STA/rt61sta.dat" 34 lines, 481 characters
```

```
root@foxhound:/home/me# iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:"FoxhoundNetwork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:5C:08:91   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:2793-BE84-3065-A85C-A3F1-F262-8A18-AC08-58CE-FD9A-5714-E56D-DFC6-7E32-6695-BEC6
          Link Quality=100/100  Signal level:-30 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

---

### Post by SunshineSmile on 2007-02-04
I got it working. I am not sure how, but I did the following: 

1) Downloaded the RT61_Firmware zip file from ralink. Unzipped onto desktop. No idea if that had anything to do with it.

2) Edited the "/etc/network/interfaces" file. Added the lines:

```

auto ra0
iface ra0 inet dhcp

```

Restarted the machine.

Now I am one happy son of a b.. 

And I even started learning Vi.

Thank u all.

---

### Post by techstop on 2007-02-04
> **SunshineSmile said:**
> I got it working. I am not sure how, but I did the following: 

1) Downloaded the RT61_Firmware zip file from ralink. Unzipped onto desktop. No idea if that had anything to do with it.

2) Edited the "/etc/network/interfaces" file. Added the lines:

```

auto ra0
iface ra0 inet dhcp

```

Restarted the machine.

Now I am one happy son of a b.. 

And I even started learning Vi.

Thank u all.

I'd say it's step 2 that's responsible. It is part of the howto after all.

---

### Post by stormfrog on 2007-02-05
Great Guide! It was simple enough to follow and I _almost_ have my wlan up and running.

I can ping my wlan router and even ping my gateway server. I cannot however reach beyond to the internet.  I have been at this for hours now and I am simply clueless as to what causes this! I have two other computers that uses the wlan router and gateway already so I these two has to be correctly configured.

In other words there has to be something with the laptap / RT61 card wlan(?).

This is my current setup:

latptop < - WLAN - >  wlan router < - cable -> gateway < - cable - > internet
192.168.1.142           192.168.1.2               192.168.1.1                    f00

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11166 (10.9 KiB)  TX bytes:11166 (10.9 KiB)

ra0       Link encap:Ethernet  HWaddr 00:19:5B:6D:2F:FA  
          inet addr:192.168.1.142  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe6d:2ffa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15086 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:104 txqueuelen:1000 
          RX bytes:1949038 (1.8 MiB)  TX bytes:257564 (251.5 KiB)
          Interrupt:11

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 ra0

cat /etc/resolv.conf 
domain mir.fallman.org
nameserver 172.16.3.3

rt61sta.dat 
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=nethernet
NetworkType=Infra
Channel=0
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=secretpassword
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

```

Any ideas what can be causing this? I can, as I wrote, ping the gateway and all local IPs. But somehow I cant get out! And I have had numerous different computers hooked up to the local network - both wired an wireless, neither has ever before had any issues getting out on the internet. So this has to do with my Ubuntu laptop I am truing to configure now somehow.

Thanks! Id be extremely grateful for any replies!


----------------------------------------------------------------

The day after I posted this I booted up and suddenly nothing works at all anymore!

Yesterday I managed to get LAN access by deleting some stuff from routing but I am not sure. Route is what I suspect is what is causing mischief.

My route looks like this:

```

192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 ra0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ra0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

The "default" is something I added because it was supposed to help. But now it comes back everytime I restart ra0 even thou I have done a "sudo route del default"x2

Detailed Rotuing with "route -nNvee -FC"
```

KKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface    MSS   Window irtt
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0     0     0      0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ra0      0     0      0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ra0      0     0      0
Kernel IP routing cache
Source          Destination     Gateway         Flags Metric Ref    Use Iface    MSS   Window irtt  TOS HHRef HHUptod     SpecDst
192.168.1.142   192.168.1.1     192.168.1.1           0      0        2 eth0     1500  0      0     0   -1    0     192.168.1.142
192.168.1.142   192.168.1.1     192.168.1.1           0      0        0 eth0     1500  0      0     0   -1    0     192.168.1.142
192.168.1.142   192.168.1.3     192.168.1.3           0      0        0 eth0     1500  0      0     0   -1    0     192.168.1.142
192.168.1.142   192.168.1.3     192.168.1.3           0      0        7 eth0     1500  0      0     0   -1    0     192.168.1.142
192.168.1.142   172.16.3.3      192.168.1.1           0      0        3 ra0      1500  0      0     0   2     0     192.168.1.142
192.168.1.142   192.168.1.142   192.168.1.142   l     0      0       14 lo       16436 0      0     0   2     1     192.168.1.142
192.168.1.142   172.16.3.3      192.168.1.1           0      0        2 ra0      1500  0      0     0   -1    0     192.168.1.142

```

Do they look right?

Some more wlan info:

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:2.437 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=87/100  Signal level:-52 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**iwgetid**
```
ra0       ESSID:""
```


**iwlist ra0 scan** *(nethernet is my wlan)*
```
ra0       Scan completed :
          Cell 01 - Address: 00:17:9A:9F:88:E4
                   *cut*
          Cell 02 - Address: 00:0F:CB:9F:47:86
                   *cut*
          Cell 03 - Address: 00:17:9A:67:DD:83
                   *cut*
          Cell 04 - Address: 00:60:B3:99:D6:36
                   *cut*
          Cell 05 - Address: 00:17:9A:F1:F8:95
                    ESSID:"nethernet"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s
          Cell 06 - Address: 00:0F:B5:25:8F:F2
                   *cut*
          Cell 07 - Address: 00:17:9A:F3:67:D3
                   *cut*
```


**iwlist ra0 freq**
```
ra0       13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.437 GHz (Channel 6)
```


**iwlist ra0 bitrate**
```
ra0       unknown bit-rate information.
          Current Bit Rate=54 Mb/s
```

**sudo ifup | ifdown ra0** *(only with sudo gives these errors)*
```
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ra0 ; Network is down.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; Network is down.
```

Yesterday LAN worked and I was connected through the wlan router. Today nothing works. I havent changed the settings beside messed with around with the *route* command. So the rest of the settings should be right ... or?

I would so much appreciate some light on this because I am completely and utterly clueless.

Regards, Stormfrog


----------------------------------------------------------------------------------------------------


SOLVED!!!


I have solved my issue and now internet works perfectly. As I suspected it was the route that was the bad guy. But since route is deduced from /etc/network/interfaces upon networking restart how can I change them? Actually it was my gf who realized it had to be an issue with the router after all. It worked with windows, but I suspect linux is alot more specific with its settings since support is still so low in this area.

Anyway, apperantly we had set the router WAN gateway adress to point at the Gateway servers internal ip (which normally works as the gw on a wired connection). For wlan to work however this had to be changed to the routers IP. An /etc/init.d/networking restart later and voila! Everything worked.

I dont know if this helps anyone but I believe it to be sound advice to check out your routing tables if all else fails and your wlan seems completely haywire.

Again, THANKS SO MUCH FOR THIS GUIDE!!! =)

---

### Post by viuks on 2007-02-06
Hi!
Please, can anybody help me yo get out of this mess. I reinstalled edgy, end now I can not get my wifi working. i dont use any encription, and my router is with default settings. ifconfog gives me out
```
eth0      Link encap:Ethernet  HWaddr 00:11:5B:EB:D7:F8  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:feeb:d7f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:858424 (838.3 KiB)  TX bytes:154235 (150.6 KiB)
          Interrupt:201 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:882 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25662 (25.0 KiB)  TX bytes:25662 (25.0 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0E:2E:86:96:D9  
          inet6 addr: fe80::20e:2eff:fe86:96d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:215 errors:0 dropped:2 overruns:2 frame:2
          TX packets:694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14768 (14.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:193 

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.17.1  Bcast:172.16.17.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.166.1  Bcast:172.16.166.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```An I have no idea where theese vmnet items I got.

My interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ra0
iface ra0 inet dhcp
```And .dat file:
```
# Copy this file to /etc/Wireless/RT61STA/rt61sta.dat
# This file is a binary file and will be read on loading rt2500.o module.

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
IEEE80211H=0
TxRate=0
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

# All parameters below can be set by iwconfig in the if-pre scripts
# if required or enabled here if you wish
# Anything enabled here will be used when EVEN the net interface is brought up
# this will undo any iwconfig pre-up settings.

SSID=dlink
NetworkType=Infra
#Channel=1
AuthMode=SHARED
EncrypType=WEP
#DefaultKeyID=1
#Key1Type=0
#Key1Str=
#Key2Type=0
#Key2Str=
#Key3Type=0
#Key3Str=
#Key4Type=0
#Key4Str=
#WPAPSK=abcdefghijklmnopqrstuvwxyz
#RTSThreshold=2312
#FragThreshold=2312
PSMode=CAM
#RFMON=0
```

---

### Post by raydekok on 2007-02-06
i use feisty who can help me?

---

### Post by tomjennings on 2007-02-06
I am getting 
RT61: RfIcType= 3
followed by

BUG: soft lockup detected CPU#0!

and a kernel lockup when I have ra0 confiuration info in /etc/network/interfaces! Very repeatable. 

I suspect the problem is related to deferred boot-time scripts.

My system is a headless server in the trunk of my car (umm, no fun to debug from there!). I use an autologin user that invokes wifi link management (using wireless tools) and another that runs a music player. 

autologin launches user shell on $tty1 pretty quickly after boot, and  I get syslog messages peeing on the console after the autologin user has started all the scripts:

* Starting system log...
* Starting kernel log...
Message from syslogd@hornet at time and date
hornet kernel: [xxx.xxx] RT61: RfIcType= 3
 * Starting powernowd
 * Starting OpenBSD Secure Shell Server
 * blah blah blah
* Running local boot scripts (/etc/rc.local)

I would guess that the deferred startup junk is somehow interfering with the driver.

With ra0 config in /etc/network/interfaces, if I login and sudo REALLY QUICK and rmmod rt61, I do not get any lockup or panic -- so it definitely is a problem with the rt61 kernel module.

Since my scripts explicitly manage the wifi link, I don't need config in that file; I put it there for belt-and-suspenders reliability (eg. if my script fails, I have my home AP info installed at boot time). I can live without that.

tomj


[QUOTE=noelferreira;1895484]thanks for the nice howto!

it almost worked in perfection for me. Everything is ok in my edgy amd64. 
However i can't configure my ' /etc/network/interfaces ' file. If i try to do that my system hang up on the next reboot. But if i delete the file everything works great. 

some output that might help:

> dmesg | grep RT61
[   40.854561] RT61: Vendor = 0x1814, Product = 0x0302 
[  151.751515] RT61: RfIcType= 3

> dmesg | grep ra0
[  156.972041] ra0: no IPv6 routers present
[  806.303830] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !

---

### Post by stormfrog on 2007-02-07
> **phq said:**
> 
**6.) Configure module via rt61sta.dat (use binary edit mode)**
```
#> vi -b /etc/Wireless/RT61STA/rt61sta.dat
```
See readme file in Modules directory for description.
For WPAPSK Authentification I've changed settings as following:
```
SSID=<SSID of Access Point>
NetworkType=Infra
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=<Secret WPA key>
```


I am curious as to why you have to specify AP, authentication and key in the NIC driver? This works and I finally have network access. But it is very troublesome to change configuration between different networks as laptops tend to be somewhat mobile :)

If I remove the network specific data from the rt61sta.dat and enter it into "interfaces" file the AP is not recognised and I cant establish a working connection.

Is there any way to solve this issue?

Thanks again!

---

### Post by techstop on 2007-02-07
> **stormfrog said:**
> I am curious as to why you have to specify AP, authentication and key in the NIC driver? This works and I finally have network access. But it is very troublesome to change configuration between different networks as laptops tend to be somewhat mobile :)

If I remove the network specific data from the rt61sta.dat and enter it into "interfaces" file the AP is not recognised and I cant establish a working connection.

Is there any way to solve this issue?

Thanks again!

This is discussed in detail [here]("http://ubuntuforums.org/showpost.php?p=1910477&postcount=116") in this thread.

---

### Post by raydekok on 2007-02-08
for dapper use this it works fine

[http://ubuntu.lupine.me.uk/dists/dapper/main/](http://ubuntu.lupine.me.uk/dists/dapper/main/)

great this is what we need.

---

### Post by ultranoize on 2007-02-09
I'm posting this just to provide (hopefully) some help to the newbies like me out there. Today I updated my computer with the main update being the kernel (i think) from 2.6.17-10-386 to 2.6.17-11-386. As soon as I restarted the computer I had lost my wireless. 
So here's how I fixed it. Its just as simple as downloading the headers again, making the module, copying the .ko file to the corresponding directory, modprobing, iwconfig and finally reboot. 

In short you just  have to go through the following steps of the HOWTO: 2, 5, 6, 8, reboot, and now you should be wireless again. !!!

---

### Post by bunnny on 2007-02-10
Hi
I have this "soft lock on cpu#0!" problem.
It acures when I run iwconfig ra0 up, dhclient ra0 or anything that tries to activate the network.

I have followed the original guide on my xubuntu 6.10

What should I try, what to do?

---

### Post by warri0r on 2007-02-11
> **bunnny said:**
> Hi
I have this "soft lock on cpu#0!" problem.
It acures when I run iwconfig ra0 up, dhclient ra0 or anything that tries to activate the network.

I have followed the original guide on my xubuntu 6.10

What should I try, what to do?

Same problem here :(

it works when i restart my router but dont think router is the culprit

plz help

**config:**

rt61 chipset (linksys wmp54g wireless card)

installed the driver with the guide provided in this post

---

### Post by warri0r on 2007-02-12
~bump

sorry, someone plz help regarding this :(

---

### Post by Analord on 2007-02-12
Regarding bug above.

Had the same thing "soft lock on cpu#0" after fsck in recovery mode.
No ubuntu no term no nothin. Just stuck on statement above
So, i booted puppy linux, commented out everything added in this guide regarding the module. Rebooted. Worked fine.
Then, i tried to modprobe rt61, added again all mentioned in this guide and make /etc/init.d/networking restart. That freezed the computer.
Then i tried to restart the ruter via power switch, that worked fine. So try restarting the wifi ruter and reboot. Worked for me.
Why is that happening ? :)
I'm using Zyxel ruter, canyon wf511 wifi card, edgy.

Edit : Also, i bought new thermal paste for proc. :)

---

### Post by stormfrog on 2007-02-15
> **PraysToPan said:**
> Hi Everyone,

After looking through this thread, I decided I wanted more flexibility for my connection options.  I'm using an SMC SMCWCB-GM PC card.  I find I get the best results with the [current CVS drivers from SerialMonkey]("http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz").  If you don't like the risk of the daily CVS snapshots, you can use the [beta drivers]("http://prdownloads.sourceforge.net/rt2400/rt61-1.1.0-b1.tar.gz?download").

You can build these drivers using the instructions in the first post.


* CUT *

when done.

I hope this finds a use for someone other then me!
Jon

Hi, this sounds like a good idea. I tried your suggestion and now I cant even boot my computer anymore.

The first thing that happend after I reconfigured and did a /etc/init.d/network restart is that the lights on my RT61 wnic pcmcia went out. ra0=f00 just tells me there is nothing such to start. I then rebooted my computer and it went from the Ubuntu loginscreen to show:

"kill: Could not kill pid '1732': No such process"

My computer and WLAN was working perfectly before (although with the fuss of having to poke around in the driver rt61 dat every day when I move between APs).

Could someone please help me get out of this mess. I am clueless as to what is happening. Removing the wlan-card doesnt help either. I would be very grateful for suggestions as how to solve this.

---

### Post by whayong on 2007-02-17
I'm trying to work on my wireless card but can't get past the first step, loL!  It says, 

```
wget http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz
--00:26:16--  http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz
           => `RT61_Linux_STA_Drv1.1.0.0.tar.gz'
Resolving www.ralinktech.com... 65.36.233.111
Connecting to www.ralinktech.com|65.36.233.111|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
00:26:16 ERROR 404: Not Found.
```

---

### Post by Frak on 2007-02-17
> **whayong said:**
> I'm trying to work on my wireless card but can't get past the first step, loL!  It says, 

```
wget http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz
--00:26:16--  http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz
           => `RT61_Linux_STA_Drv1.1.0.0.tar.gz'
Resolving www.ralinktech.com... 65.36.233.111
Connecting to www.ralinktech.com|65.36.233.111|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
00:26:16 ERROR 404: Not Found.
```
That would be because they took that one down, use this instead

```
wget http://www.ralinktech.com/ralink/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz
```

---

### Post by Unseelie on 2007-02-17
> **ultranoize said:**
> I'm posting this just to provide (hopefully) some help to the newbies like me out there. Today I updated my computer with the main update being the kernel (i think) from 2.6.17-10-386 to 2.6.17-11-386. As soon as I restarted the computer I had lost my wireless. 
So here's how I fixed it. Its just as simple as downloading the headers again, making the module, copying the .ko file to the corresponding directory, modprobing, iwconfig and finally reboot. 

In short you just  have to go through the following steps of the HOWTO: 2, 5, 6, 8, reboot, and now you should be wireless again. !!!

um, as someone who only has the wireless internet connection (no other way to connect to intrawebs) how would i get the headers?

---

### Post by Phophos on 2007-02-21
Hiya,

Not sure if this has been previously discussed, but I think it needs bringing up anyway:

I tried this guide last night in Edgy in order to get my LinkSys wireless card working. I followed the steps to the letter but to no avail - the wireless wouldn't work.

Then when I rebooted, to test if it just needed a reboot to work, I had nothing. No wireless connection, and even my eth0 wired connection wouldn't connect to my router.

This is majorly bad news. I did a bit of fiddling to see if I could get the thing working, but again, nothing.

Very frustrated. A bit of a showstopper, to be honest, since I need the interwebs to use my box. Is there any way to totally reverse this walkthrough and get my wired connection back?

Any help would be most gratefully received.

Phophos.

---

### Post by lukew on 2007-02-24
PHQ, thanks it worked a trea; first time and no problems. However i had to reboot before my network came up; the initial raising of the network did not work.

Thanks again PHQ!

---

### Post by lukew on 2007-02-24
> **lukew said:**
> PHQ, thanks it worked a trea; first time and no problems. However i had to reboot before my network came up; the initial raising of the network did not work.

Thanks again PHQ!

Woops. forgot to say I am in EDGY.

---

### Post by diana.artemis on 2007-02-24
Being a complete noob, I failed totally to get my wi-fi working with Edgy on my dual-boot laptop. 

Then I followed this HowTo slavishly, and now my wi-fi works.  (Three cheers for PHQ!!!)  But it only works for about ten minutes.  Then the system freezes and the only solution is to power down the laptop.

I have no idea how to troubleshoot this problem.  Are there any log files anywhere that might indicate what's happening when the system freezes?  I'd be grateful for advice about where to look.  Or advice about what might be causing the freeze, if anyone's had similar experiences.

---

### Post by researchsci on 2007-02-25
Okay, here is my question/concern with this. Once I get it what I believe is a completely correct install, I look up my network devices, and it is gone where as before it was there. Also, isn't there a way I can just scan for available ssid's to use instead of having to type it in by hand? Thanks for your help.

---

### Post by omegahelix on 2007-02-25
Hey all.  I'm trying to get WPA-PSK/TKIP working :confused:.  It's a linksys card and router and I have the latest Edgy packages.  I had wpa_supplicant installed (it would give me wireless for about 5-10 minutes) but I have removed that and the rt61pci driver.  I can get the rt61 driver 1.1.0.0 to load and I can get it to show up in ifconfig and iwconfig.  The problem is  if I have an /etc/Wireless/RT61STA/rt61sta.dat file out there the driver will make the system  crash (completely unresponsive) when I do ifconfig.  If I move the config file it won't crash but I will have a blank SSID in iwconfig.  I tried configuring with iwpriv but when I get to the WPAPSK = "my password" command it hangs.

Here is my rt61sta.dat file:

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=omegahelix
NetworkType=Infra
Channel=11  #the router is on this channel
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=  #tried putting my router password here, didn't help
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=my_password
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

I have tried with DefaultKeyID, KeyXType and KeyXStr commented out and with channel set to zero (0) and to "auto".  I also tried replacing my text password with the passkey output of wpa_passphrase...none worked.  Please help.  Thanks!

---

### Post by omegahelix on 2007-02-27
Hello? :(

---

### Post by Barrakketh on 2007-02-28
> **omegahelix said:**
> Hello? :(

For some odd reason, the driver will randomly freeze my PC only when I initially load it (after a kernel update/fresh install).  It has never done that in normal operation, and works perfectly fine after I restart.  Have you tried just restarting your PC with the configuration file in-place and see if it works?

---

### Post by lukew on 2007-02-28
> **omegahelix said:**
> Hey all.  I'm trying to get WPA-PSK/TKIP working :confused:.  It's a linksys card and router and I have the latest Edgy packages.  I had wpa_supplicant installed (it would give me wireless for about 5-10 minutes) but I have removed that and the rt61pci driver.  I can get the rt61 driver 1.1.0.0 to load and I can get it to show up in ifconfig and iwconfig.  The problem is  if I have an /etc/Wireless/RT61STA/rt61sta.dat file out there the driver will make the system  crash (completely unresponsive) when I do ifconfig.  If I move the config file it won't crash but I will have a blank SSID in iwconfig.  I tried configuring with iwpriv but when I get to the WPAPSK = "my password" command it hangs.

Here is my rt61sta.dat file:

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=omegahelix
NetworkType=Infra
Channel=11  #the router is on this channel
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=  #tried putting my router password here, didn't help
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=my_password
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

I have tried with DefaultKeyID, KeyXType and KeyXStr commented out and with channel set to zero (0) and to "auto".  I also tried replacing my text password with the passkey output of wpa_passphrase...none worked.  Please help.  Thanks!

What do you mean by your outer password? You are putting in your "passphrase". I could not get this working in dapper unless my passphrase was hex.

```
wpa_passphrase 'your_essid' 'your_ascii_key'
```

Luke

---

### Post by omegahelix on 2007-02-28
> **lukew said:**
> What do you mean by your outer password? You are putting in your "passphrase". I could not get this working in dapper unless my passphrase was hex.

```
wpa_passphrase 'your_essid' 'your_ascii_key'
```

Luke

I should not have said "router password".  I have an ascii password that I use for my TKIP key.  I tried putting that in the Key1Str field instead of the WPA_PSK field but it didn't help.  I'll give the wpa_passphrase command another try.  Thanks.

Barrakketh, I tried just rebooting and it freezes at boot time, unfortunately.

---

### Post by stormfrog on 2007-03-01
> **Barrakketh said:**
> For some odd reason, the driver will randomly freeze my PC only when I initially load it (after a kernel update/fresh install).  It has never done that in normal operation, and works perfectly fine after I restart.  Have you tried just restarting your PC with the configuration file in-place and see if it works?

It seems these drivers are completely unstable. It does the same on my system and is reported to the same on most systems. I really would not recommend anyone to install it. If you have a wlan NIC with ralink chip your best solution is to get a refund and buy a card that actually is supported by Ubuntu. Ralinks drivers are horribly messed up anyways. Etc, a company that creates drivers where you have to specify encryption mode (among other things) in the driver dat file?!!!. Thats even more retarded than ATi's drivers. :}

Althou, if someone eventually finds a solution for them I would be interested in how.

---

### Post by DaveAK on 2007-03-02
I have to admit that I only read the OP and just wanted to add my thanks!  It worked perfectly for me, and connected to my Belkin router with WPA-PSK flawlessly first time.

---

### Post by whayong on 2007-03-02
I've got a problem.  here's what I get when I try to blacklist:

```
*******@srx77:~$ echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
```

what am I doing wrong?

---

### Post by diana.artemis on 2007-03-02
Try 

*******@srx77:~$ sudo echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist

(you need root permissions to do this)

---

### Post by whayong on 2007-03-02
That actually didn't work, but guess who's posting this wirelessly?  Woooohoooooo!

Here's what I did:

I followed this how to:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29)
which to my knowledge is the same as this how to.

When i got to the part of blacklisting, I had some problems so I used nautilus and went to /etc/modprobe.d/blacklist and addedd "blacklist rt61pci" (without the quotation marks) to the last line and followed the rest of the how to.

For the record, my wireless card is a MSI MP54G5 mPCI card.  lspci lists it as RaLink RT2561/RT61 rev B 802.11g.

This is on a Vaio PCG-SRX77 laptop 20 GB HD 384 MB RAM. Ubuntu 6.10

I hope this info will be usefull to others just as this how to was usefull to me.  It only took me 1 month and 6 fresh installs to get the wireless working. lol!

Thanks to the great people on this forum and to the OP for the help.

---

### Post by bestiarosa on 2007-03-02
Hi phq,
I'm struggling to get the drivers of my RT61 wireless compiled. I have a fresh Edgy Eft installation without Internet access so I'm downloading packages from  another computer and saving them on a USB card to install them on my Ubuntu computer. So, when you type ```
sudo apt-get install linux-headers-`uname -r`
``` which are exactly the packages Ubuntu downloads?
I've already installed gcc-4.1, the latest build-essentials, linux-headers-2.6.17-10 and linux-headers-2.6.17-11 (latest) but if I try to make all it's forever telling me > make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `DWG-510'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2
If I type ```
./Config
``` I get this error:> -------------------- Ralink RT61 Station Configuration -------------------- 

  Linux kernel source directory [/usr/src/linux-2.6.17-10-generic]: 
 
Linux source tree '/usr/src/linux-2.6.17-10-generic' is incomplete or missing!

Configuration failed

Do you have an idea about what I can be missing? I've described my problem as well in this post here: [http://ubuntuforums.org/showthread.php?t=374485](http://ubuntuforums.org/showthread.php?t=374485)

---

### Post by whayong on 2007-03-02
Not sure if this is in the realm of being off topic or not but how do I get this to work with multiple AP's?  I was able to connect at home via WPA and DHCP.  But at work, we use WEP via static.  I created a new profile in settings>administration/networks and entered the WEP and static IP info but can't connect here at work.  Is it possible that setting the .dat in vi editor is prohibiting me from connecting to another AP other then the one I specified?

---

### Post by whayong on 2007-03-03
Alright, I got the wireless card to connect to an AP at school with DHCP and no security.  I just need to try it at work which has WEP and static IP. 

All I did was edited the /etc/Wireless/RT61STA/rt61sta.dat and removed the values I entered for the SSID, encyption type, password, etc......  Baisically, I edited the file back to it's "unedited version" and I can now connect to other AP's.

---

### Post by mesmerize on 2007-03-15
I have a desktop with Ubuntu 6.10 and Windows Xp and a laptop with Xp. I connect to the Internet through the ethernet card to the cable modem (it's not wifi). I have created and ad-hoc lan in windows to connect the laptop to Internet. I'd do the same with Ubuntu, so I'd not have to boot windows to do that.
I have the linksys wmp54g v4.1 and I think it's properly configurated.

---

### Post by George M. Harkin on 2007-03-16
> **stormfrog said:**
> It seems these drivers are completely unstable. It does the same on my system and is reported to the same on most systems. I really would not recommend anyone to install it. If you have a wlan NIC with ralink chip your best solution is to get a refund and buy a card that actually is supported by Ubuntu. Ralinks drivers are horribly messed up anyways. Etc, a company that creates drivers where you have to specify encryption mode (among other things) in the driver dat file?!!!. Thats even more retarded than ATi's drivers. :}

Althou, if someone eventually finds a solution for them I would be interested in how.

The drivers seem to be working fine for me. My only issue is that NetworkManager does not want to manage it. I'm looking into fixing that now.

So, great card, with great linux support. More than you can ask from Dell.

---

### Post by Phophos on 2007-03-16
Ahh, ignore my last post - this is now working in 32-bit Edgy. I followed this walkthrough with a little help from some other areas too.

If anyone is having problems here, [http://www.ubuntuforums.org/printthread.php?t=132980&pp=75](http://www.ubuntuforums.org/printthread.php?t=132980&pp=75) is bloomin' marvellous. The scripts to place in init.d work rather well.

The main little twist is using iwpriv instead of iwconfig. No clue as to why this works, but by Jove it does.

One point, I've not yet tested it with WPAPSK, only WEP. This is plenty secure for my neighbourhood though - they're not really out of the Stone Age around here, or even past dial-up...

Anyway! More tips:

[LIST=1]
[*]Look around at all of the walkthroughs you can! Also, if you don't understand something, man it or ask in the IRC channels.
[*]After following any procedure such as this, don't ever use the GUI managers that come as standard again, or you'll break things...
[*]Download rtutilt. It's handy!
[*]Learn how to use vim before you attempt to fix that rt61sta.dat, or stuff starts breaking.
[/LIST]

I'm posting this wirelessly after a week of trying. The most important point? Never give up! Giving up hope is for the weak!

In the meantime, I hope y'all sort your RT61 problems out.

The Phopsynator.

---

### Post by Andrew MacDonald on 2007-03-18
If you're having trouble downloading the driver try here:

[http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz](http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz)

---

### Post by new_pingu on 2007-03-18
Thanks PH,
I have been trying to connect using my wireless card for weeks with no luck. followed your guide and was up with an hour. A well written step by step for RT61.

Best Regards
New_pingu   :)

---

### Post by Andrew MacDonald on 2007-03-19
If you are using a post-2.6.18 kernel the driver supplied by ralink won't compile. get_wireless_stats has been removed from netdevice.h as discussed here:
[http://www.linuxquestions.org/questions/showthread.php?t=529973](http://www.linuxquestions.org/questions/showthread.php?t=529973)

Instead, get the latest cvs tarball from:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)
and follow the same method.

---

### Post by lime4x4 on 2007-03-22
do i still need t load the proper drivers yet

00:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI

this is on a fresh install of edgy after running the lspci command. I can't connect wirelessly yet.just trying to figure if i still need to compile the newer drivers if edgy already detects the card properly

---

### Post by Frak on 2007-03-24
I created a HOWTO: and a script to install the driver automatically for anybody who needs it, I've tested it and it works fine.
[http://ubuntuforums.org/showthread.php?p=2344944#post2344944](http://ubuntuforums.org/showthread.php?p=2344944#post2344944)
Hopefully this will help.

---

### Post by zophiel on 2007-03-25
Has anyone tried using the rt61 to turn the installation into a router?

namely this:

[http://www.ubuntuforums.org/showthread.php?t=376283]("http://www.ubuntuforums.org/showthread.php?t=376283")

I tried the iwconfig ra0 mode master
and it gave the predictable:

# iwconfig ra0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Invalid argument.

here is the relevant iwconfig:ra0       RT61 Wireless  ESSID:""  
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

anyone know?

---

### Post by sbyrne on 2007-03-25
Thanks PHQ,

         I am continually amazed at how easy it is to get support for even the more esoteric problems.  I used your guide and had wireless in less than 15 minutes.  I have had no success whatsoever with the ndiswrapper approach under any configuration :( 

I am now using WPA to connect to an Airport Extreme.  The guide worked the first time on a relatively clean edgy 6.10 install.

I have given up trying to get my on-board BCM4316 working with any of the every suggested fix and simply use a Netgear WG111v2 plugged into a USB port on my Dell XPS m140.  Worked almost immediately after plugging it in.  Now if only I can get that to work with WPA....

---

### Post by BeachBum on 2007-03-25
> **zophiel said:**
> 
Has anyone tried using the rt61 to turn the installation into a router?

namely this:

[http://www.ubuntuforums.org/showthread.php?t=376283]("http://www.ubuntuforums.org/showthread.php?t=376283")

I tried the iwconfig ra0 mode master
and it gave the predictable:

# iwconfig ra0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ra0 ; Invalid argument.


The RaLink driver does not support master mode; you'd need the rt2x00 serialmonkey driver, which is still beta software.

---

### Post by radio_flyer on 2007-03-26
I have to agree with stormfrog. I'm surprised that so many people are having success with this HOWTO. The system I'm installing this on is an AMD Sempron with 32-bit Edgy. I successfully compiled and installed the rt61.ko module from the latest 1.1.0.0 sources from Ralink. At first iwconfig showed the ra0 link up but I couldn't get a DHCP IP address assignment. A few minutes later the kernel froze solid. Rebooting the system produced a blank screen. Attempts to reboot in 'safe mode' resulted in 'soft lockup detected on CPU#0'. I eventually had to boot using my Gentoo rescue CD and remove the rt61 module from /etc/modules and the ra0 interface from /etc/network/interfaces (the latter because of the 'ra0 rt61' alias BTW) before Ubuntu would boot back up.

I find this whole wireless situation really disappointing. I've been using Linux for a decade (currently running Gentoo on my primary system) so I'm no stranger to the issues involved with OSS and Linux. However, I'm building this new system for my niece and wanted something easy to use and as GUI-driven as possible. I shopped carefully, bought hardware I knew had good Linux support, and choose Ubuntu for it's ease-of-use and automagic installation. Overall the out-of-the-box experience has been great. Except for the wireless connection. Heck, the box even says 'Linux drivers included' on it. Of course, if I try to modprobe those I get symbol mismatch errors. So I do the source compile thing using code direct from the manufacturer web site. And my system freezes so solid I have to revert to my beyond-noob skills to rescue it. That is really sad. 

I will get this thing working eventually (probably with a different manufacturer's card) but it pains me to see Linux getting SO close to being a real OS option for the average PC user and yet fail so miserably on a few key items. Walk into a coffee shop with Mac OSX, scroll through the list of access points and connect. Fire up your office WinXP, enter the office SSID and WPA2 password and hit enter. So simple. That day still seems a long way off for Linux.

---

### Post by radio_flyer on 2007-03-26
Now I'm really surprised this is working so well for so many people. Here's a bug report from the serialmonkey site:

[http://sourceforge.net/tracker/index.php?func=detail&aid=1687350&group_id=107832&atid=648844](http://sourceforge.net/tracker/index.php?func=detail&aid=1687350&group_id=107832&atid=648844)

which indicates that the rt61 driver has issues with an SMP kernel (like Ubuntu's.) Yeah, I know this is the rt61 thread not serialmonkey, but read the whole report. It appears to be the 1.1.0.0 rt61 driver, not the serialmonkey one, that hangs.

---

### Post by Junge on 2007-03-26
Hi,

I think the tutorial works fine, so that's great. When I come to the end and assign an ip with ifconfig I can actually ping my wireless router.

Except i'm wondering about two things:

1) How doe I get it to start at boot? Because the echo command doesn't seem to work. Each time the computer boots I have to load the module and assign an ip with ifconfig, even though the router is DHCP.

2) The internet still doesn't work?

Grtz,

Jeroen
(newbie)

---

### Post by Frak on 2007-03-26
Have you tried iwpriv? Instead of iwconfig?
just use
```
man iwpriv
```

---

### Post by Junge on 2007-03-27
> **Frak said:**
> Have you tried iwpriv? Instead of iwconfig?
just use
```
man iwpriv
```

It worked with that! Made a auto startup script to. Many thnx!

---

### Post by tictacman on 2007-04-01
How are you supposed create a passphrase that's less than 52 characters long?  Every time I type wpa_passphrase myssid mypassword not matter how short mypassword is it always creates a string larger than 52 characters.

---

### Post by Andrew MacDonald on 2007-04-01
I believe the passphrase should be your ASCII password. At least that's what I have in my rt61sta.dat file.

---

### Post by tictacman on 2007-04-02
I've just managed to get the card working after spending the whole weekend trying. I know this going over old ground but I thought I would post exactly what I did to get it working, in the hope it might benefit other rt61 victims. Following the guide on pg1 word for word did not work for me, and I tried several different drivers.

I'm using kubuntu 6.10 with the latest updates and the serial monkey driver which I downloaded  (rt61-cvs-2007040123).  First off I tried to get the card working without encyrption.I installed the driver as page1 of the howto instructed except copying makefile.6 to makefile as there wasn't makefile.6 and ignoring the encyrption settings. My user defined setting in rt6sta.dat looked like this:

SSID=mdkgroup
NetworkType=OPEN
Channel=8
PSMode=CAM

Everything else commented out with #.  

In /etc/network/interface I kept the entry for ra0 simple:

auto ra0
iface ra0 inet dhcp

When I booted into recovery mode it worked, when I loaded up into kde it failed.  I figured out that it was my mobo's fault because it has  via graphics (k8mm3 - via k8m800+vt82374/823475 + chipset).  I found a workaround by going into /etc/X11/xorg.conf and under the via driver adding the option: Option "DisableIRQ" "true" and also adding irqpoll to the default kernel line in /boot/grub/menu.lst.  After this everything working well.  The card now connected everytime.

However when I tried setup wpapsk as per instructions (except keeping network type as OPEN) it failed miserably.  This time I commented the ra0 section  in /etc/network/interface. I tried removing the module so I could add it again, but the system said ra0 busy.  I commented out the rt61 entry in /etc/module so it wouldn't load on boot. Shut the system down rebooted in recovery mode, removed the module.


modprobe --remove
depmod -a
modprobe rt61
dhclient ra0

Bam!! it worked.  Just a case now of creating a script to load the card at boot.

The last section of the rt61sta.dat without the commented out lines now looks like this.:

SSID=notworkgroup
NetworkType=OPEN
Channel=8
AuthMode=WPAPSK
WPAPSK=forbiddenfruit
PSMode=CAM

---

### Post by ep2011 on 2007-04-02
This didn't work for me, so heres what I did to make it work perfectly.

**1.) Download the latest original Ralink RT61 drivers from:** 
```
$> wget http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz

```
Note: I wrote the guide for 1.0.4.0, but it is no longer available for download. However, it should work with the new driver as well. If it does, please post that.
**2.) Compile the Module**
Install the kernel headers corresponding to your kernel (In most cases it should be installed by default, but it seems there are derivates which won't do that)
```
sudo apt-get install linux-headers-`uname -r`
``` 
[COLOR="Red"]^^ Did NOT need to do.[/COLOR]

```
$> tar xvfz RT61_Linux_STA_Drv1.0.4.0.tar.gz
$> cd RT61_Linux_STA_Drv1.0.4.0/Module/
$> cp -f Makefile.6 Makefile
$> make all
```

**3.) Get root**
```
$> sudo su
```

**4.) Prepare Config directory for the module**
```
#> mkdir -p /etc/Wireless/RT61STA/
#> cp *.bin /etc/Wireless/RT61STA/
#> cp rt61sta.dat /etc/Wireless/RT61STA/
```

**5.) Install Kernel Module**
```
#> cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/
#> depmod
```

**6.) Configure module via rt61sta.dat (use binary edit mode)**
```
#> vi -b /etc/Wireless/RT61STA/rt61sta.dat
```
ENTER FOLLOWING:

```
[Default]
NetworkType=Infra
AuthMode=SHARED
EncrypType=WEP
DefaultKeyID=1
Key1=<KEY>
SSID=<WIRELESS SSID>
```

**7.) Remove broken preinstalled Module**


**8.) Load module rt61**
```
#> modprobe rt61
```

** Edit modprobe and network config files**

**Add broken module to blacklist:**
```
#> echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
```

**Add the new module to module autostart**
```
#> echo 'rt61' >> /etc/modules

```
**and create an alias**
```
#> echo 'alias ra0 rt61' >> /etc/modprobe.d/aliases
```

** Create file named StartWifi.sh in /etc/init.d/**
```
#!/bin/sh
sudo modprobe --remove rt61pci
sudo modprobe rt61
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<KEY>
sudo iwpriv ra0 set SSID=<WIRELESS SSID>
sudo dhclient ra0

```

** Enter the following terminal commands **
```

sudo chmod 0755 /etc/init.d/StartWifi.sh
sudo ln -s /etc/init.d/STartWifi.sh /etc/rc2.d/S90StartWifi.sh

```

**Reboot - Try - Be Happy! :-D **

Now, If you do a kernel update do the following:

copy rt61.ko from /lib/modules/(OLD KERNEL)/kernel/drivers/net to /lib/modules/(NEW KERNEL)/kernel/drivers/net

then run the following terminal command:
```
 sudo depmod 
```

And that should be it!!!

I did not make this up myself, I took some of the info from this post, some from another post, and some from help from very nice people in IRC.

---

### Post by Dj Delta9 on 2007-04-14
:guitar: YES!  SUCCESS!  Thank you so much!  This has taken me an entire week to figure out since Im noobtastic, but now all is well in the universe!  I can go on with my life.=D>

---

### Post by ultranoize on 2007-04-19
Has anyone upgraded to Feisty yet?  I've thought about doing it but if it means that the wireless is not going to work then i'd rather not.  Any suggestions?  I read here [http://ubuntuforums.org/showthread.php?t=408987]("http://ubuntuforums.org/showthread.php?t=408987") something about not being able to use WAP. Is this true?

Any suggestions???

---

### Post by Frak on 2007-04-19
> **ultranoize said:**
> Has anyone upgraded to Feisty yet?  I've thought about doing it but if it means that the wireless is not going to work then i'd rather not.  Any suggestions?  I read here [http://ubuntuforums.org/showthread.php?t=408987]("http://ubuntuforums.org/showthread.php?t=408987") something about not being able to use WAP. Is this true?

Any suggestions???
I was unable to connect to any network, let alone see any network.

---

### Post by sunburst01 on 2007-05-20
Following this howto, seems to work ok, on my freshly installed 2.6.20-15 Feisty Fawn system with Lynksys wmp54g and BT Wireless service. One deviation from the procedure...

My "make all" did not work when building the driver as downloaded from ralinktech.com. I had to comment out one line (197) in file  RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c to get it to build:

#if WIRELESS_EXT >= 12
//    net_dev->get_wireless_stats = RT61_get_wireless_stats;
    net_dev->wireless_handlers = (struct iw_handler_def *) &rt61_iw_handler_def;
#endif

The wireless.h file on my system has been changed to remove get_wireless_stats.

Aside from that, procedure works fine. My rt61sta.dat file reads:

[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=BTHomeHub-181B
NetworkType=Infra
Channel=0
AuthMode=OPEN
EncrypType=WEP
DefaultKeyID=1
Key1Type=hexadecimal
Key1Str=.......... (my 10 digit hex key entered in here)
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

Hope this helps!
Ciao...

---

### Post by gatoruss on 2007-06-01
I have been wrestling with wifi and Feisty for over a week.  Everything worked fine until I upgraded to 7.04!

Well, after some tinkering, I have gotten the wifi to work following the tutorial mentioned in post #4 of  [this thread]("http://http://ubuntuforums.org/showthread.php?t=415693"), as modified by post #1.  However, it only boots up manually and I cannot get wifi to fire up on start up...I need to manually launch every time I boot up?"  But it does not fire up wifi on start up....any suggestions?

---

### Post by hanspb on 2007-08-29
I'm bringing this thread up again.
I have a machine with Fluxbuntu (based on Ubuntu Dapper drake) and the rt61 wireless. Previously my network has had WEP encryption. Back then everything worked fine and I had my network connection working. I recently changed that to WPA-PSK. Now, I tried to change the setup for this Fluxbuntu-machine to use WPA-PSK. What I did was the following:

-Changed to WPA-PSK in /etc/wireless/RT61STA/rt61sta.dat according to this guide.

-In /etc/network/interfaces I commented out the unused interfaces and I added

```

 iface ra0 inet dhcp
 wireless-essid <MYESSID>
 auto ra0

```

Then I tested the setup with 

```
ifup ra0
```

All worked fine, I got on the net like a piece of cake. Ok, reboot to see that it works like it should...

BANG!

The #¤%& machine won't boot! it hangs on "starting ra0" and I don't get any further!:(
Can anybody help me? Obviously I need to use a live CD to fix this, but what should I do?

Also, at the same time this happened, I lost my wireless connection on my laptop, which I had running in order to read this guide while working. Now I can't connect to the wireless network, neither in Ubuntu (Feisty) nor in Windows (it's a dual-boot system):(
Cabled network is fine.

Hans Petter

---

### Post by woZa on 2007-09-12
Thanks for the HOWTO... Seems to have got my card up and running... Only issue I am now having is that I can't see the base station when scanning...

```
sudo iwlist ra0 scan
```
```
ra0       Scan completed :
          Cell 01 - Address: 00:14:7F:57:1C:4B
                    ESSID:"BTHomeHub-E488"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address: 00:14:C1:04:C1:50
                    ESSID:"USR9108"
                    Mode:Managed
                    Channel:11
                    Encryption key:off
                    Bit Rates:0 kb/s
          Cell 03 - Address: 00:13:49:A0:BA:EE
                    ESSID:"ZyXEL"
                    Mode:Managed
                    Channel:6
                    Encryption key:off
                    Bit Rates:0 kb/s
```

Great. Only those are my neighbours - mine is not showing up. It is an apple airport extreme base station. I have tried turning off ALL security on it and it still won't show up in the scans.

```
iwconfig
```
```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off

```

```
cat /etc/Wireless/RT61STA/rt61sta.dat
```
```
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=Wireless
NetworkType=Infra
Channel=0
AuthMode=WPAPSK
EncrypType=TKIP
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=myplaintextpassword
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0
```

Anyone any ideas about this?

Oh. And I am running a fresh install of feisty 7.04...

Thanks
Alex

---

### Post by googlah on 2007-10-26
The link to the actual driver at Ralinktech.com seem to be down. Can't get further without this.. :)

Thanks for a nice How-to anyway, just hope this helps. ^^

---

### Post by Frak on 2007-10-26
> **googlah said:**
> The link to the actual driver at Ralinktech.com seem to be down. Can't get further without this.. :)

Thanks for a nice How-to anyway, just hope this helps. ^^
Newer versions of Ubuntu have the RT61 driver module already.

---

### Post by vilwarin on 2008-09-15
finishing this howto didn't connect me yet, I had to do one more step independent whether you compile the module yourself or use the new module rt61pci included in hardy.

network-manager  only cause trouble, I removed it
wicd  looked promising but was also not able to connect me
iwconfig  could not connect me either
iwpriv  same here
rt61sta.dat  RAlinks config method also lead in a cul-de-sac

what finally did the trick was using the RALink Utility Tools (rutilt). Using this tool I finally can connect to my Access Point. Get it from the standard package list by typing

```
apt-get install build-essential rutilt
```

and find it in

```
Applications > Internet > RUtilt WLAN Manager
```
(hardy)

good luck
vilwarin

---

### Post by wamubu on 2008-10-07
Latest driver version: 
[1.2.2.2 @ 7/23/2008](http://www.ralinktech.com.tw/data/drivers/2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2) 902kB
[1.2.2.2 Doc](http://www.ralinktech.com.tw/data/drivers/ReleaseNote-RT61STA-v1122.txt)

---

### Post by omax on 2008-11-01
Hi and thank you for an excellent guide!

Though I'm having some troubles, because after a few hours of uptime the network crashes. iwconfig does not show that I'm connected to my AP but ifconfig still shows my internal IP.

Here's the error code when I try to restart networking:

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          ioctl[SIOCSIWMODE]: Network is down
Could not configure driver to use managed mode
SIOCADDRT: No such process
Failed to bring up ra0.
                                                                         [ OK ]
t$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          




ioctl[SIOCSIWENCODEEXT]: Network is down
ioctl[SIOCSIWENCODEEXT]: Network is down
ioctl[SIOCSIWENCODEEXT]: Network is down
ioctl[SIOCSIWENCODEEXT]: Network is down
SIOCADDRT: No such process
Failed to bring up ra0.
                                                                         [ OK ]


$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/ra0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

ioctl[SIOCSIWAP]: Network is down
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
SIOCADDRT: No such process
Failed to bring up ra0.
                                                                         [ OK ]

```

Dmesg from the time of crash and trying to restart networking:
```
[ 2051.421375] e2:1a:09:be:b3:44:5f:1b:82:79:82:c0:05:e9:15:02:
[ 2051.421391] d8:a0:05:0e:89:da:b7:4a:
[ 2051.421394] e0:f7:3e:90:01:eb:ff:65:
[ 5654.032581] 06:1a:85:07:99:d2:2a:5c:76:d3:30:77:f4:71:7f:a5:
[ 5654.032592] 11:fb:78:99:e2:31:55:87:
[ 5654.032595] 6f:9f:02:01:3d:75:3e:94:
[ 5657.031476] 06:1a:85:07:99:d2:2a:5c:76:d3:30:77:f4:71:7f:a5:
[ 5657.031486] 11:fb:78:99:e2:31:55:87:
[ 5657.031489] 6f:9f:02:01:3d:75:3e:94:
[ 9256.667820] 5a:61:00:fb:29:4d:4d:2a:61:90:a2:1d:ed:85:34:27:
[ 9256.667829] 26:a1:9a:c7:c5:a3:2e:3b:
[ 9256.667832] b1:ba:ea:46:1f:e5:f4:a1:
[ 9259.650342] 5a:61:00:fb:29:4d:4d:2a:61:90:a2:1d:ed:85:34:27:
[ 9259.650355] 26:a1:9a:c7:c5:a3:2e:3b:
[ 9259.650359] b1:ba:ea:46:1f:e5:f4:a1:
[ 9262.649764] 5a:61:00:fb:29:4d:4d:2a:61:90:a2:1d:ed:85:34:27:
[ 9262.649777] 26:a1:9a:c7:c5:a3:2e:3b:
[ 9262.649781] b1:ba:ea:46:1f:e5:f4:a1:
[12862.277547] 24:90:d2:9e:d9:67:ed:d1:f3:4a:62:42:95:85:01:fa:
[12862.277557] d7:f9:8e:27:48:47:45:fa:
[12862.277560] bb:0b:24:30:c4:6a:51:41:
[12942.258465] Before wrapper, AuthMode=7, wepStatus=6, pCipher=6, gCipher=4, IEEE8021X=0
[12942.258473] After wrapper, the AuthMode=7! wepStatus=6!
[12942.904273] RT61: RfIcType= 3
[12946.007071] Before wrapper, AuthMode=0, wepStatus=1, pCipher=1, gCipher=1, IEEE8021X=0
[12946.007077] After wrapper, the AuthMode=7! wepStatus=6!
[12946.115317] ReqVarIELen=36! RespIELen=120!
[12946.115323] infoLen=343!
[12946.115338] wext_notify_event_assoc():AssocInfo=
[12946.115340] 	ASSOCINFO(ReqIE0100000fac020100000fac040100000fac020000 RespIEff000000000000000000000000000000000000000000dd1a00904c340807050000000f00000000000000000000000000000030180100000fac020200000fac02000fac040100000fac020000dd1a0050f20101000050f20202000050f2020050f20401000050f202)!
[12946.115346] ra0 (WE) : Wireless Event too big (343)
[12946.388562] c3:65:1b:44:21:49:65:7e:ea:13:87:2c:75:58:9a:19:
[12946.388572] 00:00:00:00:00:00:00:00:
[12946.388575] 00:00:00:00:00:00:00:00:
[12946.388614] 24:90:d2:9e:d9:67:ed:d1:f3:4a:62:42:95:85:01:fa:
[12946.388622] d7:f9:8e:27:48:47:45:fa:
[12946.388627] bb:0b:24:30:c4:6a:51:41:
[12953.509193] ra0: no IPv6 routers present
[12969.226399] Before wrapper, AuthMode=7, wepStatus=6, pCipher=6, gCipher=4, IEEE8021X=0
[12969.226406] After wrapper, the AuthMode=7! wepStatus=6!
[12969.935980] RT61: RfIcType= 3
[12976.912359] Before wrapper, AuthMode=0, wepStatus=1, pCipher=1, gCipher=1, IEEE8021X=0
[12976.912366] After wrapper, the AuthMode=7! wepStatus=6!
[12976.932449] ReqVarIELen=36! RespIELen=120!
[12976.932454] infoLen=343!
[12976.932470] wext_notify_event_assoc():AssocInfo=
[12976.932471] 	ASSOCINFO(ReqIE0100000fac020100000fac040100000fac020000 RespIEff000000000000000000000000000000000000000000dd1a00904c340807050000000f00000000000000000000000000000030180100000fac020200000fac02000fac040100000fac020000dd1a0050f20101000050f20202000050f2020050f20401000050f202)!
[12976.932477] ra0 (WE) : Wireless Event too big (343)
[12980.023802] ra0: no IPv6 routers present
[12989.962312] Before wrapper, AuthMode=7, wepStatus=6, pCipher=6, gCipher=6, IEEE8021X=0
[12989.962319] After wrapper, the AuthMode=7! wepStatus=6!
[12989.977579] ReqVarIELen=36! RespIELen=120!
[12989.977586] infoLen=343!
[12989.977601] wext_notify_event_assoc():AssocInfo=
[12989.977602] 	ASSOCINFO(ReqIE0100000fac020100000fac040100000fac020000 RespIEff000000000000000000000000000000000000000000dd1a00904c340807050000000f00000000000000000000000000000030180100000fac020200000fac02000fac040100000fac020000dd1a0050f20101000050f20202000050f2020050f20401000050f202)!
[12989.977608] ra0 (WE) : Wireless Event too big (343)
[12991.314335] Before wrapper, AuthMode=7, wepStatus=6, pCipher=6, gCipher=6, IEEE8021X=0
[12991.314341] After wrapper, the AuthMode=7! wepStatus=6!
[12991.895662] RT61: RfIcType= 3
[12993.933879] Before wrapper, AuthMode=0, wepStatus=1, pCipher=1, gCipher=1, IEEE8021X=0
[12993.933886] After wrapper, the AuthMode=3! wepStatus=1!
[12994.536898] RT61: RfIcType= 3
[12995.233538] Before wrapper, AuthMode=0, wepStatus=1, pCipher=1, gCipher=1, IEEE8021X=0
[12995.233545] After wrapper, the AuthMode=3! wepStatus=1!
[12995.825391] RT61: RfIcType= 3
[12996.477280] Before wrapper, AuthMode=0, wepStatus=1, pCipher=1, gCipher=1, IEEE8021X=0
[12996.477288] After wrapper, the AuthMode=3! wepStatus=1!
[12997.056009] RT61: RfIcType= 3
[12997.701039] Before wrapper, AuthMode=0, wepStatus=1, pCipher=1, gCipher=1, IEEE8021X=0
[12997.701046] After wrapper, the AuthMode=3! wepStatus=1!
[12998.312059] RT61: RfIcType= 3
[12999.408292] Before wrapper, AuthMode=0, wepStatus=1, pCipher=1, gCipher=1, IEEE8021X=0
[12999.408299] After wrapper, the AuthMode=3! wepStatus=1!
[12999.993904] RT61: RfIcType= 3
[13010.453626] ra0: no IPv6 routers present

```

Has anyone had any similar problems? What could be wrong?

---

