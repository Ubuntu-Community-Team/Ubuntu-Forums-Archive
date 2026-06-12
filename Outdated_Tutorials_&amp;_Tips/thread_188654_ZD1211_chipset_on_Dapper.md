---
title: "ZD1211 chipset on Dapper"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Jammy_Stuff on 2006-06-04
Unfortunately, once again the integrated support for the ZD1211 chipset doesn't work for many people. This however does not mean you can't get it to work. This guide explains how to get the newest version of the driver installed and working.

Fistly, remove the rubbish driver included with Ubuntu.

```
sudo modprobe -r zd1211
```

Then install build-essential (have the Dapper CD in the drive).

```
apt-get install build-essential
```

Open Synaptic and do a search for linux-headers, check all that appear and install them from the CD.

Download [http://zd1211.ath.cx/download/zd1211-driver-r77.tgz](http://zd1211.ath.cx/download/zd1211-driver-r77.tgz) and put it in your home directory.

Uncompress it.

```
tar zxvf zd1211-driver-r77.tgz
```

Go into the zd1211 driver directory.

```
cd ~/zd1211-driver-r77
```

If your adapter uses the ZD1211B chipset then you need to change the Makefile config.

```
sudo gedit Makefile
```

Look for ZD1211REV_B=0 and change it to ZD1211REV_B=1.

Now its just a case of compiling it all.

```
make clean
make
make install
```

Load the driver.

```
modprobe -v zd1211(zd1211b if you use the B chipset)
```

Remember to add zd1211(b) into your /etc/modules file.

Connect the interface.

```
sudo ifconfig wlan0 up
```

And connect to a network.

```
sudo iwconfig wlan0 essid <network name>
```

Restart the PC.

And that should be it. You can now configure the network further from the Network administation. I'm not sure if WPA/WEP works. Sorry if I missed anything out or got something wrong as I am doing this from memory.

Enjoy your move to Ubuntu.

---

### Post by domino on 2006-06-04
Thank you so much for this tut. Please rename the word mod[COLOR="Red"]e[/COLOR]probe to modprobe ;).

---

### Post by Jammy_Stuff on 2006-06-04
Thanks for letting me know about that mistake. Edited.

---

### Post by syadnom on 2006-06-04
very nice, works well. thanks

wonder why the included driver is crap?

---

### Post by flurl on 2006-06-04
wpa works for me.

make sure, you can connect to an unprotected network as described by the thread opener.

remove the wpa_supplicant package if installed:
```
sudo apt-get remove wpasupplicant
```

download the source for version 0.4.9 of wpa_supplicant from [http://hostap.epitest.fi/wpa_supplicant/]("http://hostap.epitest.fi/wpa_supplicant/").

you'll also need the openssl sources from [http://www.openssl.org/source/]("http://www.openssl.org/source/") (used the slightly old version 0.9.8a because i had it already, but i hope it works with the latest version too)

extract the sources:
```
tar -xzvf wpa_supplicant-0.4.9.tar.gz
tar -xzvf openssl-0.9.8b.tar.gz
sudo cp -R wpa_supplicant-0.4.9 /usr/src/wpasupplicant
sudo cp -R openssl-0.9.8b /usr/src/openssl
```



symlink the directory /usr/src/openssl/include to /usr/src/wpasupplicant/openssl
```
sudo ln -s /usr/src/openssl/include /usr/src/wpasupplicant/openssl
```

copy the file defconfig to .config
```
sudo cp /usr/src/wpasupplicant/defconfig /usr/src/wpasupplicant/.config
```

install wpa_supplicant
```
cd /usr/src/wpasupplicant
sudo make
sudo make install

```

create or edit the configuration file for wpa_supplicant /etc/wpa_supplicant.conf. mine looks like this:
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=0


network={
        ssid="daham"
        psk="XXX"
        proto=WPA
        key_mgmt=WPA-PSK
        scan_ssid=1
        pairwise=TKIP
}
```

start wpa_supplicant
```
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i wlan0 -D wext
```

this are the steps that made wpa_supplicant working for me. hope this may help someone else.

---

### Post by polo_step on 2006-06-05
[FONT="Courier New"]Thanks for this!

I was running 6.06 in "Live" mode the other night and mainly out of curiosity stuck in a 1211 USB dongle I had and to my surprise found that it appeared to immediately be working to some extent, finding, though not connecting to, my WPA network.

I experiment with numerous inexpensive wireless devices and have found that these Zydas  1211 and 1211b units usually get the job done reasonably well and can be the basis for [some interesting experiments.]("http://www.usbwifi.orcon.net.nz/");) Watching the results on the graphs in Network Stumbler, I found that I could get at least a ten decibel measurable boost using household whatnot as signal reflectors with these dongles.

Not long back, I got one of the [CompUSA WirelessG Adapters]("http://www.compusa.com/products/product_info.asp?product_code=333626&pfp=srch1"), which has the 1211 chip, for US$2.99 after rebate and an [Airlink101 AWLL3026]("http://airlink101.com/products/awll3026.html") unit, which is smaller, has a brilliant blue LED and uses the 1211b chip, for US$5.99 on sale.

In another local sale, I got an "active" USB extension cable for US$1.99, which is actually a single-outlet USB hub, which will extend useful USB connections to at least thirty feet from the computer without degradation, nor the loss from coax cable in a passive antenna.  The upshot of this is that one can have a roof-mounted, very high gain, active reflector WiFi system for almost nothing.

Getting these little devices integrated into Ubuntu with full native functionality (WPA/AES) would be a great boon!

[/FONT]

---

### Post by Shiroku on 2006-06-05
I have a Sitecom USB Wireless Adapter model wl-113 and I use Kubuntu


I followed the instruction and now if I run iwconfig there is a new "element" called **sit0** (I remember that when another boy used the usb wireless adapter there where also "sit0")

The screenshot:
[http://www.primadanoi.it/images/CANCELLAMI/7.png]("http://www.primadanoi.it/images/CANCELLAMI/7.png")

Now, I have to run "iwconfig sit0 essid <name>", it's correct?

I tryed:
(FRC is my network wireless name [set in the router])
iwconfig sit0 essid "FRC"
iwconfig sit0 essid 'FRC'
iwconfig sit0 essid FRC
iwconfig sit0 essid any

but it doesn't work...


If I run ```
dmesg | grep sit0
``` it says:
**sit0: Disabled Privacy Extensions**

When I reboot the sistem (because I post reply with windows....), when I reboot Kubuntu, if I run iwconfig there isn't sit0 and I reinstalled the driver....

However, I think that **sit0** is my usb adapter, infact when I installed Kubuntu on my friend's laptop whit my usb adapter plugged in, when I runned iwconfig there were sit0.
Then, I reinstalled Kubuntu on my friend's laptop without usb adapter, and if I run "iwconfig" there isn't sit0

PS:I'm a newbie

---

### Post by flurl on 2006-06-05
i doubt that sit0 is your wlan adapter. AFAIK are the sit* interfaces pseudo-interfaces for tunneling IPv6 throu IPv4.

are you sure the module is loaded correctly and your adapter is recognized?
open a second console and run:
```
 tail -f /var/log/messages
```

then load the module and plug-in your usb adapter

this is my output in /var/log/messages when loading the module and attaching my usb adapter (a trendnet TEW-429UB)
you should get something similar:
```

Jun  6 04:31:50 localhost kernel: [4382081.815000] zd1211 - http://zd1211.ath.cx/ - r77
Jun  6 04:31:50 localhost kernel: [4382081.815000] Based on www.zydas.com.tw driver version 2.5.0.0
Jun  6 04:31:50 localhost kernel: [4382081.816000] usbcore: registered new driver zd1211
Jun  6 04:32:18 localhost kernel: [4382109.551000] usb 1-2: new full speed USB device using uhci_hcd and address 6
Jun  6 04:32:18 localhost kernel: [4382109.784000] usb 1-2: reset full speed USB device using uhci_hcd and address 6
Jun  6 04:32:18 localhost kernel: [4382109.909000] Release Ver = 4802
Jun  6 04:32:18 localhost kernel: [4382109.909000] EEPORM Ver = 4330
Jun  6 04:32:18 localhost kernel: [4382109.931000] AiroHa AL2230RF
Jun  6 04:32:19 localhost kernel: [4382110.140000] AllowedChannel = 000107ff
Jun  6 04:32:19 localhost kernel: [4382110.140000] Region:48

```

---

### Post by sguart on 2006-06-07
again?!

at least the include driver actually loads without error, i thought they got zd1211 working with dapper...

glad that i got the zyxel p-330w from compusa and use it as a bridge and now my ubuntu box is connected via nic card...

shof2k should update his howto again to include the dapper instructions...

for some reason my gigafast adapter doesn't like the opensource driver, i had to get the driver source from zydas... i used the wpa_supplicant source from zydas too which added zd1211 support right in...  even after all that, it will lose the wireless connection after 30min of inactivity... i guess the driver is not working completely right... had to run background ping command to keep it up...

didn't know the wpa_supplicant supports the zd1211 via the -d wext switch...

anyway,

thanks for the updated info guys,

sg

---

### Post by MikeyC on 2006-06-07
Great guide Jammy Stuff - thanks - worth an inclusion in the Wiki.

Before I take the plunge and install Dapper on my Mandriva box, can you confirm that the build-essential and header stuff is on the CD?

I've downloaded the driver source already, but didn't want to get stuck with no internet connection and no way to compile a driver for one!

Cheers,

Mike

---

### Post by domino on 2006-06-07
I second the addition to the wiki, along with the wpa tut. Now the only problem I have is that vmware vnet(x) doesn't play nice with it.

---

### Post by Shiroku on 2006-06-07
this is my output:

root@kubuntu:~# tail -f /var/log/messages
Jun  7 22:16:11 kubuntu kernel: [4294971.866000] usbcore: deregistering driver zd1211
Jun  7 22:16:11 kubuntu kernel: [4294971.866000] ZD1211 802.11b/g USB WLAN driver removed
Jun  7 22:17:31 kubuntu exiting on signal 15
Jun  7 22:17:33 kubuntu syslogd 1.4.1#17ubuntu7: restart.
Jun  7 22:17:52 kubuntu kernel: [4295072.548000] ZD1211 802.11b/g USB WLAN driver v20050315 loaded
Jun  7 22:17:52 kubuntu kernel: [4295072.548000] (c) Willig, Yang, Zviskov et al.
Jun  7 22:17:52 kubuntu kernel: [4295072.548000] [http://zd1211.sourceforge.net/](http://zd1211.sourceforge.net/)
Jun  7 22:17:52 kubuntu kernel: [4295072.548000] usbcore: registered new driver zd1211
Jun  7 22:18:09 kubuntu kernel: [4295089.297000] sit0: Disabled Privacy Extensions
Jun  7 22:18:20 kubuntu kernel: [4295100.427000] usb 4-3: new high speed USB device using ehci_hcd and address 5

---

### Post by Shiroku on 2006-06-09
my usb wireless adapter is:
"Sitecom wl-113 **v1 002**"

May be this the problem?

---

### Post by Shiroku on 2006-06-09
I found this:
[http://rt2x00.serialmonkey.com/wiki/index.php/Hardware](http://rt2x00.serialmonkey.com/wiki/index.php/Hardware)

at the bottom of the page there is "**Sitecom WL113 V1-002**" but I don't know if it is USB....

---

### Post by shof2k on 2006-06-12
updated!  View the new one at [http://www.ubuntuforums.org/showthread.php?t=195259](http://www.ubuntuforums.org/showthread.php?t=195259)

---

### Post by domino on 2006-06-12
thanks for the update shof. Didn't want to clutter up your tutorial with this post :). Ps. It needs to be wikified!!

---

### Post by pkuijpers on 2006-06-13
[QUOTE=Jammy_Stuff]

Then install build-essential (have the Dapper CD in the drive).

```
apt-get install build-essential
```

[/QUOTE]

In addition to build-essential, I had to install te linux headers first to build the drivers:

```
apt-get install linux-headers-$(uname -r)
```

---

### Post by jarocooke on 2006-06-17
Cheers Jammy_Stuff.

I thought your post on how to set up ZD1211 chips on wireless devices was excellent, very easy to follow.

Again, many thanks
:D

---

### Post by drunken_sapo on 2006-07-01
Hi!
In the first place i want to thank you for this howto. This post was originally a question, but while I was writing I came up with the solution. I'm still posting here cause I think it would be useful to other people.
I've a Linksys WUSBF54G which has a zd1211 chipset. I'm using (k)ubuntu dapper with a 2.6.15-23-386 kernel. I was able to succesfully compile and load many versions of the module, but when I plug the stick, it is still recognized as a generic USB device in all cases. I was not sure what i've been missing, but i was pretty stuck right at that point, and i didnt have any error message to help me. It seemed that I was using the wrong driver. Thus I went once again to [http://zd1211.ath.cx/](http://zd1211.ath.cx/) and found that my stick was in UntestedWithRewrite state. So I followed the instructions there. that is adding the usb id to the listing in the driver's source code, and it worked neatly. 
Maybe its worth to mention that on the howto, to avoid losing many hours like in my case. In addition, I think that the reason why the original driver (the one packed with dapper) wasnt working was this one. Am i wrong?
Best regards,
Juan

Here was the output when it wasnt workin:

#modprobe -v  zd1211
insmod /lib/modules/2.6.15-23-386/net/zd1211.ko

#dmesg
[4297109.509000]  _____     ____    _    ____
[4297109.509000] |__  /   _|  _ \  / \  / ___|
[4297109.509000]   / / | | | | | |/ _ \ \___ \
[4297109.509000]  / /| |_| | |_| / ___ \ ___) |
[4297109.509000] /____\__, |____/_/   \_\____/
[4297109.509000]      |___/
[4297109.509000] zd1211 - version 2.14.0.0
[4297109.509000] usbcore: registered new driver zd1211

----> here I plug the stick
#dmesg
[4297047.435000] usb 5-1: new high speed USB device using ehci_hcd and address....

---

### Post by diogenes_3 on 2006-07-05
This was a very comprehensive guide. Being a relative Linux newbie I was able to work my way down the list step by step with barely the slightest confusions (apt-get wouldn't find the CD at first until I started and re-closed Synaptics, and the makes must be sudo make clean, sudo make, and sudo make install). Now the li'l blighter works blissfully, also with WEP turned on. Thanks a bundle!

---

### Post by domino on 2006-07-18
I have this annoying problem with losing connection to my network and usb2 stick when recycle my usb2 ext drive. I have to reboot the computer to get my network back up. The funny thing is, even if i unplug the wifi stick or restart networking i gnome, it's still not picking up the usb wlan stick. Anyone know what's going on and how to fix this annoyance? I'm runing dapper 6.06.

---

### Post by diogenes_3 on 2006-07-19
What a sad, sad world :-(

My network hummed along happily for a week, then deceased without any comment. I fear that an online update (rant: why are there so many of them?) has overwritten my changes. I will repeat the tutorial and hopefully get it back on line, since that is all I, the beginner, know to do, but that won't answer the question what happened and whether it'll happen again.

---

### Post by domino on 2006-07-22
Apparently i needed to reinstall the driver and compile it against the 2.6.15.26-686 kernel. i haven't thoroughly tested it since it's only my second reboot on this new compile. it has not locked up. I guess we will know in the next few hour/days.

diogenes_3, have yo tried recompiling and reinstalling the driver after the update?

As for my problem with loosing connection with the wlan stick after turngin off my ext USB drive, my dirty sulution is to disable wlan0 from Neworking Administrator, unplug the USB stick and re-enable wlan0 again. The goog thing is it doesn't lock up the system anymore.

---

### Post by diogenes_3 on 2006-07-26
Today I re-executed the tutorial (OK, I obviously didn't need to re-execeute each step, I understand *that* much :-)), and *presto*, the WLAN works again. But, how often will I have to do that? With Ubuntu annoyingly updating some snippet or other every other day, a kernel update is obviously just around the corner. I read something the other day that I "have to enter the changes I made into Synaptic", see if I can relocate that thread.

I am, admittedly, not at this machine every day, my other car is a Windows notebook...

---

### Post by domino on 2006-07-26
hell that's the most annoying thing about Linux in general. You have to remember to recompile some application/drivers to reflect the new kernel images, headers, etc. very annoying when you have had your OS running over 5 months and you have to remember what you installed. it's even more annoying if you have more than 2 computers and not always using them on a normal basis.

Things I have to update on every kernel upgrades are the wlan stick, ATI proprietary drivers, and my tv tuner card. And not all will work right after update update. So it's a good idea to lay back a few days or weeks till they get the problems resolved.

---

### Post by g3_400 on 2006-07-26
i'm a complete ubuntu newbie, just installed on my Apple G3. I like it so far, but i would like to connect to my wireless network. I'm sorry to say that I don't understand the instructions posted here for using my ZyDAS 1211B chipset wireless adapter with Ububntu 6.06. Cna anybody give me step-by-step instructions?

---

### Post by sidlinux on 2006-07-26
I'm running dapper drake with a Dell Inspiron 1100 using one of the Airlink with the zd1211 drivers.  

I did everything in the instructions that Jammy_Stuff posted, up to the part where you have to use "make" and wound up with an error :( which said 

"/lib/linux-2.6.15-26/build" (or whichever path it was) 

is not found.  Any suggestions on how to get the make working?  Thanks in advance.

Sidney

---

### Post by wormeyman on 2006-09-11
I have the same problem :(

---

### Post by wormeyman on 2006-09-14
Anyone have a clue how to fix the 

"
"/lib/linux-2.6.15-26/build" (or whichever path it was)

is not found. Any suggestions on how to get the make working? Thanks in advance.

"

---

### Post by Jammy_Stuff on 2006-09-14
I just installed on another PC and I've got the error now too. I have a feeling it is due to a missing symbolic link so I'll investigate it now.

---

### Post by KswP4RV on 2006-09-15
Install linux-headers for your kernel and then try running "make" again.

---

### Post by wormeyman on 2006-09-15
I do have the headers installed.
"
linux-headers-2.6.15-23-386
Linux kernel headers 2.6.15 on 386
"

---

### Post by KswP4RV on 2006-09-15
Strange, that error about some missing /lib/<kernel>/build directory was solved for me by installing the correct linux-headers package.

Can you post the output showing the error message?

---

### Post by Jammy_Stuff on 2006-09-16
Have you got both linux-headers-2.6.15-23-386 and linux-headers-2.6.15-23?

---

### Post by domino on 2006-09-16
Have you rescently upgraded the kernel? If so redo the instructions on the first page and it's important to restart.

---

### Post by wormeyman on 2006-09-16
> **Jammy_Stuff said:**
> Have you got both linux-headers-2.6.15-23-386 and linux-headers-2.6.15-23?

[http://wormeyman.com/img/screenshots/linux-headers-synapitc.png](http://wormeyman.com/img/screenshots/linux-headers-synapitc.png)

I think so 



eric@ubuntu:~$ sudo modprobe -r zd1211
Password:
eric@ubuntu:~$ apt-get install build-essential
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
eric@ubuntu:~$ sudo apt-get install build essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

[COLOR="Red"]I still had synaptic open and i checked an i have build-essential installed[/COLOR]
eric@ubuntu:~$ tar zxvf zd1211-driver-r77.tgz
zd1211-driver-r77/
zd1211-driver-r77/src/
zd1211-driver-r77/src/zdglobal.c
zd1211-driver-r77/src/zdhci.c
zd1211-driver-r77/src/zdglobal.h
zd1211-driver-r77/src/zdshared.c
zd1211-driver-r77/src/zddebug2.c
zd1211-driver-r77/src/zdhci.h
zd1211-driver-r77/src/zdmic.c
zd1211-driver-r77/src/WS11Ur.h
zd1211-driver-r77/src/zd1205_proc.c
zd1211-driver-r77/src/zdshared.h
zd1211-driver-r77/src/zdequates.h
zd1211-driver-r77/src/zdbuf.c
zd1211-driver-r77/src/zddebug2.h
zd1211-driver-r77/src/zdmic.h
zd1211-driver-r77/src/zdpci_hotplug.c
zd1211-driver-r77/src/zdhw.c
zd1211-driver-r77/src/zdsorts.h
zd1211-driver-r77/src/zd80211.h
zd1211-driver-r77/src/zdbuf.h
zd1211-driver-r77/src/zdpci_hotplug.h
zd1211-driver-r77/src/zdhw.h
zd1211-driver-r77/src/zdmmrx.c
zd1211-driver-r77/src/zdconfig
zd1211-driver-r77/src/pHash
zd1211-driver-r77/src/zdsynch.c
zd1211-driver-r77/src/zd1205.c
zd1211-driver-r77/src/zdpci_pcmcia.c
zd1211-driver-r77/src/zdcompat.h
zd1211-driver-r77/src/zdmmrx.h
zd1211-driver-r77/src/zdinlinef.h
zd1211-driver-r77/src/zdversion.h
zd1211-driver-r77/src/zd1205.h
zd1211-driver-r77/src/zdpci_pcmcia.h
zd1211-driver-r77/src/zdpsmon.c
zd1211-driver-r77/src/zdusb.h
zd1211-driver-r77/src/zd1211_wext.h
zd1211-driver-r77/src/WS11UPhR.h
zd1211-driver-r77/src/zdasocsvc.c
zd1211-driver-r77/src/zdpsmon.h
zd1211-driver-r77/src/zdutils.h
zd1211-driver-r77/src/menu_drv_macro.h
zd1211-driver-r77/src/zdtkipseed.c
zd1211-driver-r77/src/zdauthreq.c
zd1211-driver-r77/src/zdtypes.h
zd1211-driver-r77/src/zydas_common.h
zd1211-driver-r77/src/zdtkipseed.h
zd1211-driver-r77/src/zdapi.h
zd1211-driver-r77/src/WS11UPh.h
zd1211-driver-r77/src/zdpmfilter.c
zd1211-driver-r77/src/zdencrypt.c
zd1211-driver-r77/src/zd1211.c
zd1211-driver-r77/src/zdsm.h
zd1211-driver-r77/src/zddebug.c
zd1211-driver-r77/src/zdauthrsp.c
zd1211-driver-r77/src/zdos.h
zd1211-driver-r77/src/zdpmfilter.h
zd1211-driver-r77/src/zdencrypt.h
zd1211-driver-r77/src/WS11Ub.h
zd1211-driver-r77/src/zd1211.h
zd1211-driver-r77/src/zddebug.h
zd1211-driver-r77/src/WS11UPhm.h
zd1211-driver-r77/src/zdusb.c
zd1211-driver-r77/sta
zd1211-driver-r77/copying
zd1211-driver-r77/Makefile
zd1211-driver-r77/apdbg.c
eric@ubuntu:~$ cd ~/zd1211-driver-r77
eric@ubuntu:~/zd1211-driver-r77$ sudo gedit Makefile
[COLOR="Red"]I have a revision b chipset[/COLOR]
eric@ubuntu:~/zd1211-driver-r77$ make clean
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd
eric@ubuntu:~/zd1211-driver-r77$ make
/lib/modules/2.6.15-26-386/build
/home/eric/zd1211-driver-r77
-I/home/eric/zd1211-driver-r77/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211B
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/eric/zd1211-driver-r77 modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
eric@ubuntu:~/zd1211-driver-r77$

---

### Post by Jammy_Stuff on 2006-09-16
You need to install linux-headers-2.6.15-**26** and linux-headers-2.6.15-**26**-386

---

### Post by wormeyman on 2006-09-16
Ok but they don't seem to be available via synaptic?  i also tried:

eric@ubuntu:~$ sudo apt-get install linux-headers-2.6.15-26
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-26

---

### Post by Jammy_Stuff on 2006-09-17
I have a feeling that you may need internet access to get them as they wouldn't be on the CD or anything.

---

### Post by wormeyman on 2006-09-18
Hmm so i'd have to download them off the internet and not though ubuntu?


[http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-26](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-26)
[http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-26-386](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-26-386)

How would i go about installing them?

---

### Post by JAwuku on 2006-09-19
One thing that needs to be considered.

I have a Sitecom WL-113 USB wireless adaptor. There are actually two versions of this, one uses the ZD1211 chipset, and the other uses the Ralink RT73 chipset.

Both types of stick look identical, so you have to distinguish them by the serial number.

If it says WL-113 v1 ***001*** - it uses the ZD1211 chipset.

However, if like mine, it says WL-113 v1 ***002*** - this has an RT73 chipset.

There are linux drivers available for the RT73 chipset, from the Ralink website: [http://www.ralinktech.com/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralinktech.com/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz)

and the Ubuntu instructions for compiling:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29)

---

### Post by clandestino81 on 2006-09-20
In the [changelog]("http://www.kernelnewbies.org/LinuxChanges") of Linux kernel 2.6.18, the latest stable version, in the section "New driver" you can read:

> ZyDAS ZD1211 USB-WLAN driver: there are 60+ USB wifi adapters available on the market based on the ZyDAS ZD1211 chip, based on ZyDAS's own GPL driver, additionally, the firmware is redistributable and they have provided device specs. Kudos to ZyDAS. If you support "open hardware", you know what to do the next time you need a wifi adapter ;-) 

It means ZD1211 usb wireless devices will be supported by default with this kernel version, isn't it?

---

### Post by JeBeKe on 2006-09-21
Thanks for the beautiful howto ;) 
If I unplug and plug my zd1211 device, it's correctly detected and listed in 'lsusb'. I have access to the network :D 

During startup however, the device is not detected. Not even listed in lsusb.
I have to manually unplug and plug, before it's detected and working.

Any explanation?
Is the firmware downloaded after the usb-detection?
...

---

### Post by alanmzifa on 2006-10-02
Hi, I've been trying to get wireless working with my desktop on Ubuntu since first installing it 4 weeks ago (got a Ralink PCMCIA for laptop, now working). I've had to abandon trying to get my original USB wifi device (Netgear WG121) installed and from what I can see no-one has been sucessful with it hence my purchase of a [Safecom SWMULZ 5400]("http://safecom.cn/code/sub/category.asp?prdid=321&subcatid=41") which uses the ZD1211B chipset. Their website has an [up to date driver here]("http://safecom.cn/code/support/DMF.aspx?pid=321").


[I]
Can someone please help me with the instructions from the original post?[/I]

 I've seen a couple of threads and how-tos and this one seems to have less instructions (good) but I'm unsure I know how to properly carry out some of the steps described. I've tried searching but the search facility is poor to say the least so I just need a little bit of clarification as I haven't been able to fully clear up the areas of uncertainty. Anyway, I've already had some fumbled attempts which definitely didn't go to plan and have ended up completely re-installing Ubuntu to give me an untainted clean install.

thanks in advance.

Here's where I need clarification.

1/ I do a search for Linux headers and install them. ***Which ones?***
2/ edit the Makefile. The Makefile seems to have lines for both already. ***Do I really need to edit anything here?***
3/  compile it all. What is *it*? ***The makefile? Or other files as well? And I don't need to mention any files by name just [I]make clean, make, make install* in terminal? **[/I]
4/ Add ZD1211B into /etc/modules file. ***How do I do that?***


Again, thanks in advance for your help.

---

### Post by domino on 2006-10-09
Does anyone know if this works on edgy?

---

### Post by Peter76 on 2006-10-09
In Edgy it is sort of working out of the box. To bring it up I manually have to set my essid first and then run dhclient on it.

---

### Post by domino on 2006-10-09
Thanks for the reply Peter. I hope by the next release, the driver works without having to do any edits. Atm, "sort of working" wont work for a development box :).

---

### Post by domino on 2006-10-16
> **Peter76 said:**
> In Edgy it is sort of working out of the box. To bring it up I manually have to set my essid first and then run dhclient on it.

I have some good news for Edgy and I'll cross post this in the dev forum. I was able to get the dongle up and connected to the AP on every reboot without having to run dhclient every time. I first installed zd1211-driver-r83 which forced me to run dhclient every reboot. I downgraded to zd1211-driver-r77 and at first, even on reboot, the dongle would not activate. I had to manually enable it and set the static IP, gateway, and dns, then rebooted again. After that, wlan0 is up and running. I hope the network sticks and something don't breaking it any time soon.

---

### Post by diogenes_3 on 2006-12-02
Sadly, despite all reports in this thread that it should work in Edgy, it didn't for me. After upgrading, and later on after a clean install, my system  (with USB stick Sitecom WL-113) woke up once more without any network connection.

So I applied this trusted tutorial one more time. Sadly things seem to have changed, and some steps wouldn't quite work. (In the beginning, modprobe -r zd1211 told me it wasn't there so couldn't be removed, and in the end ifconfig wlan0 up told me there was nothing to go up with.) I heartily rebooted, and *presto!*, the WLAN was there anyway.

I wish my slight knowledge of Linux were sufficient to understand why...

---

### Post by trippinnik on 2007-01-23
Thanks for the comment about the dhclient command.  I need to do that now too!  I reinstalled and now I have to type that in to get a connection.  Why is this?  I really don't want to go back to an older version of a driver.

---

### Post by akajonesy on 2007-01-23
Ive been running on edgy and it works fine except I have to set essid and key in terminal (through iwconfig) after every boot.
Had it working flawlessly after installing Network-manager (through synaptic. No idea what the difference between that and what came w/edgy is. This is my first attempt at Linux), but I blew it all away through reinstalls (wanted to try Xubuntu and Kubuntu on clean installs. Liked Ubuntu the best on this comp) and I haven't had a chance to try again yet since the last reinstall.

---

### Post by Kjott21 on 2007-09-13
> **Jammy_Stuff said:**
> Unfortunately, once again the integrated support for the ZD1211 chipset doesn't work for many people. This however does not mean you can't get it to work. This guide explains how to get the newest version of the driver installed and working.

Fistly, remove the rubbish driver included with Ubuntu.

```
sudo modprobe -r zd1211
```

Then install build-essential (have the Dapper CD in the drive).

```
apt-get install build-essential
```

Open Synaptic and do a search for linux-headers, check all that appear and install them from the CD.

Download [http://zd1211.ath.cx/download/zd1211-driver-r77.tgz](http://zd1211.ath.cx/download/zd1211-driver-r77.tgz) and put it in your home directory.

Uncompress it.

```
tar zxvf zd1211-driver-r77.tgz
```

Go into the zd1211 driver directory.

```
cd ~/zd1211-driver-r77
```

If your adapter uses the ZD1211B chipset then you need to change the Makefile config.

```
sudo gedit Makefile
```

Look for ZD1211REV_B=0 and change it to ZD1211REV_B=1.

Now its just a case of compiling it all.

```
make clean
make
make install
```

Load the driver.

```
modprobe -v zd1211(zd1211b if you use the B chipset)
```

Remember to add zd1211(b) into your /etc/modules file.

Connect the interface.

```
sudo ifconfig wlan0 up
```

And connect to a network.

```
sudo iwconfig wlan0 essid <network name>
```

Restart the PC.

And that should be it. You can now configure the network further from the Network administation. I'm not sure if WPA/WEP works. Sorry if I missed anything out or got something wrong as I am doing this from memory.

Enjoy your move to Ubuntu.

Ok so I am trying to get my ZyDAS 1211 to work with Ubuntu 6.06. Is this still the proper procedure to follow? If so, the link to the driver takes you to 2 different files to download. One is labeled as firmware and the other is labeled as a memtool, which one do I want to use?

---

