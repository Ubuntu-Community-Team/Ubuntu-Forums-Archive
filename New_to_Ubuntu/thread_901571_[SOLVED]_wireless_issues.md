---
title: "[SOLVED] wireless issues"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by WastePotato on 2008-08-26
Hello All, 


I'm been having problems with my wireless card.

Vista has been extremely annoying recently, randomly cutting out and turning off my computer. When I try to restart again, Vista makes it to the Error Reporting Screen, and then proceeds to turn my laptop off again. It seems that the only way for this stop to to load my trusty Ubuntu LiveCD. The only problem with it is that it never correctly recognises my wireless card.

Take a look:

[http://fumpr.com/images/odgc7gf6ed229158jv.png](http://fumpr.com/images/odgc7gf6ed229158jv.png)



When I type: network-admin 

> ubuntu@ubuntu:~$ network-admin

(network-admin:9529): Gtk-WARNING **: Unknown property: GtkComboBox.items

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:11:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:04:a3:16
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:17:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0



When I type: iwconfig

> ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Anybody got any ideas? :confused:

Thanks.

---

### Post by gjoellee on 2008-08-26
bump*

---

### Post by nicedude on 2008-08-26
Yes you have an Atheros wifi adapter ( I think you have a AR5007 just like me ) and you need to use a newer madwifi driver for it to get it to work. If you are thinking of doing this with live CD I can't help. If you actually install Ubuntu ( dualboot so you can keep Vista ) then I wrote a guide on this adapter complete with a driver download.

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)


If/when you get stuck let me know via PM and I will try to help.

Goodluck

---

### Post by overdrank on 2008-08-26
> **gjoellee said:**
> bump*

I edited the title. :)

---

### Post by WastePotato on 2008-08-26
Wait... How did you do that? Are you God? :-D

Anyway. I decided not to dual boot. I figured that it would be too much trouble for me to repartition my already partitioned HD and mess around with the (I think it is the) Boot.ini configuration file.

Instead, I just used the Wubi installer that came on the CD and have installed Ubuntu inside Windows. I'm going to restart now and complete the installation. Then we can get down to business. :)



OMG. I JUST BECAME A REAL LINUX USER. \\:D/ UH OH. IS THAT A GOOD OR A BAD THING? I'M WORRIED NOW. :(

---

### Post by nicedude on 2008-08-26
Instead, I just used the Wubi installer that came on the CD and have installed Ubuntu inside Windows. I'm going to restart now and complete the installation. Then we can get down to business. 

Uh Wubi is not a real Linux install it is a way to use Linux inside of Windows, I would not recommend this to you, instead I would recommend a dual boot scenario where yes you will have to learn a little to get it done but I can tell you I tried this very day to help someone enable their AR5007 Atheros while in Wubi and it gave them errors I have not seen and as such I would say ( baring someone who knows wubi saying otherwise ) that it should be avoided and instead a true dualboot solution realized as then you would be a true linux user. 

just research vista & ubuntu dualboot and you will see it is not that hard.


Just trying to save you form pulling out your hair.

---

### Post by WastePotato on 2008-08-27
Is Wubi really that bad?

Now I'm really worried :(

---

### Post by WastePotato on 2008-08-28
Anyway, I've Wubi installed Ubuntu.

[http://fumpr.com/images/klncpsf0ckvwtb20pnig.png](http://fumpr.com/images/klncpsf0ckvwtb20pnig.png)

I've found that my wireless adapter is the Atheros AR5007EG Wireless Network Adapter. What should I do now?

nicedude, that tutorial looks pretty long. I heard there was a program called NDIS wrapper that would do everything automatically for me. 

I also saw this, but this is only for 802.11n deviees:

[http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for](http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for)

I'm so confused right now. :?

---

### Post by nicedude on 2008-08-28
Ok you will have problems with your adapter in Wubi with the madwifi driver, I just helped a guy yesterday that could not get his AR5007 to work in Wubi following my guide then I just helped him setup a dual boot with a real Ubuntu install ( Wubi is not real linux but virtual linux inside of the Windows OS ), then he used my guide again and bam it worked like a charm. 

I don't know if Ndiswrapper will work from within Wubi or not but I would not be supprised if it gives you problems as well ( Maybe someone who knows could chime in on that ). Ndiswrapper is not the best way to use your AR5007 inside Linux and it will only allow you to use simple wifi to connect to the internet, you will not be able to do any of the cool stuff like putting your card into monitor mode ( super stealthy mode to only sniff all data flying around you without transmitting anything and therefor invisibly ) or doing such cool things as raw packet injection for wifi hacking and penetration testing ( my favorite ) like the driver in my guide will allow you to be able to do. 

So if I was you and you like Ubuntu then research doing a dual boot setup and use Ubuntu for real and forget about Wubi. You will also get much better performance with a real install.

---

### Post by WastePotato on 2008-08-28
Ok. I'm convinced. I'll erase my current Ubuntu installation, repartition my HD and install Ubuntu with dual boot.

:biggrin:

---

### Post by nicedude on 2008-08-28
Thats the best medicine in this case. Good luck and feel free to PM me if you need any help :-)

---

### Post by WastePotato on 2008-08-28
In regard to partitioning my HD, should I use a GParted CD or just use the utility that came with Vista?

---

### Post by ugm6hr on 2008-08-28
Use the Vista partitioner to shrink Vista and leave empty space after it.

Then you can just use the "use largest continuous free space" option to install Ubuntu.

This is a well-documented how-to for your wifi: [http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

---

### Post by WastePotato on 2008-08-28
I've just attempted to use the Vista utility, but it will not allow me to create a space larger than 10GB, even though I don't have any files on the volume.

Take a look:

[http://fumpr.com/images/kfjgnnk17szwrkc6zht4.png](http://fumpr.com/images/kfjgnnk17szwrkc6zht4.png)

GParted then?

---

### Post by ugm6hr on 2008-08-28
> **WastePotato said:**
> GParted then?

Nope.

Vista will not work with less than 25GB (see the 8.7GB free space in C: ).

And GParted has been known to make a mess of Vista partitions (which I gather are slightly different than the traditional NT/XP NTFS partitions).

Your choice about partitions, but 10GB is enough for Ubuntu.  Or shrink the data partition too...

---

### Post by WastePotato on 2008-08-28
That's what I've been trying to do. Resize the Data partition. Vista only seems to be using 5GB of it, but wont let me have anymore. I want at least 15GB for Ubuntu.

---

### Post by ugm6hr on 2008-08-28
> **WastePotato said:**
> That's what I've been trying to do. Resize the Data partition. Vista only seems to be using 5GB of it, but wont let me have anymore. I want at least 15GB for Ubuntu.

Sorry - I'm an idiot :oops:

Did your computer come partitioned like this?  My Acer came with a similar setup - so I just deleted the "data" partition, and replaced it with Ubuntu.  If you have data stored on there - just move it elsewhere before deleting it.  You can recreate a new (smaller) data partition from GParted (or even a separate /home to share between Windows and Ubuntu in ext3 using fs-driver)

I would advise against resizing Vista partitions from GParted - it may not work (unless GParted has been fixed in the last year or so).

---

### Post by WastePotato on 2008-08-28
Yep. My computer came partition like this when I got it. I don't have any data on it, but Vista seems to be using it for something.

[http://www.fumpr.com/images/puad7p53qkyrwdmvkx9a.png](http://www.fumpr.com/images/puad7p53qkyrwdmvkx9a.png)

I may be getting a bigger HD soon. (120GB. Not much, but enough for me. :) )

---

### Post by tommcd on 2008-08-28
That extra drive is probably a backup drive. My Acer laptop came with a similar setup also. Acer installed their own backup utility (along with a lot of other bloat) that backed up data files. I erased the drive completely. The laptop now only has linux.
If this backup drive is not important to you, then just delete that partition from Vista's partition program; or you could probably use Gparted since you are just deleting it. Then use that space to install Ubuntu.

---

### Post by WastePotato on 2008-08-29
Well it took some playing around, but I finally managed to get Vista to give up some space.

[http://fumpr.com/images/t4pq2wqhpe71yh7oae.png](http://fumpr.com/images/t4pq2wqhpe71yh7oae.png)

Imma install Ubuntu now, wish me luck. :popcorn:

---

### Post by WastePotato on 2008-08-29
tommcd, I took your word for it and you where right. I deleted the drive and crossed my fingers and, to my suprise nothing happened!

By doing this, I was able to create a 2gb swap space, a 20gb partition for Ubuntu, and gave the extra space to Vista.

Thanks For the Advice!

---

### Post by WastePotato on 2008-08-29
nicedude, you where right all along.

Dual Boot was so easy, Ubuntu handled everything correctly and now I have the "GRUB Loader" (I think that's what it's called).

Thanks for the Advice!

---

### Post by WastePotato on 2008-08-29
It says to do this in terminal:

> sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)
cd ~
wget -O driver.tar.gz [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)
tar xf driver.tar.gz
cd madwifi-*
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci

But.... I don't have an internet connection in Ubuntu. Should I connect to the internet though my ethernet connection or download the file from within Vista and then put it on my USB drive?

---

### Post by ugm6hr on 2008-08-29
> **WastePotato said:**
> But.... I don't have an internet connection in Ubuntu. Should I connect to the internet though my ethernet connection or download the file rom within Vista and then put it on my USB drive?

Easiest to use ethernet cable.  If that's not possible, it can still be done (with a bit of difficulty).

---

### Post by WastePotato on 2008-08-29
OK. Later today, I'll go and connect my notebook to my router, download the driver and report back to tell you if it works.

:biggrin:

---

### Post by WastePotato on 2008-08-29
Back. I'm just about to try it out. I heard that the HAL in the restricted drivers manager might cause some problems with the install. Should I disable it beforehand?

---

### Post by WastePotato on 2008-08-29
Argh!

It doesn't work! Am I doing something wrong?

> lol@lol-PC:~$ sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)
[sudo] password for lol: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
lol@lol-PC:~$ cd ~
lol@lol-PC:~$ wget -O driver.tar.gz [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)
--17:59:37--  [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)
           => `driver.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,417,874 (4.2M) [application/x-gzip]

100%[====================================>] 4,417,874      1.96M/s             

17:59:40 (1.96 MB/s) - `driver.tar.gz' saved [4417874/4417874]

lol@lol-PC:~$ tar xf driver.tar.gz
lol@lol-PC:~$ cd madwifi-*
lol@lol-PC:~/madwifi-hal-0.10.5.6-r3835-20080801$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/lol/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.ko
  CC      /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.mod.o
  LD [M]  /home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools'
lol@lol-PC:~/madwifi-hal-0.10.5.6-r3835-20080801$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/lol/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.24-19-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.24-19-generic/net
make[1]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath'
make[1]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.24-19-generic/net
make[1]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
make[1]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
make[2]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
make[2]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
make[2]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
make[1]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
make[1]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.24-19-generic/net; \
	done
make[1]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
(export KMODPATH=/lib/modules/2.6.24-19-generic/net; /sbin/depmod -ae 2.6.24-19-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
		make -C $d install || exit 1; \
	done
make[2]: Entering directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/lol/madwifi-hal-0.10.5.6-r3835-20080801/tools'
lol@lol-PC:~/madwifi-hal-0.10.5.6-r3835-20080801$ echo ath_pci | sudo tee -a /etc/modules
ath_pci
lol@lol-PC:~/madwifi-hal-0.10.5.6-r3835-20080801$ sudo modprobe ath_pci
lol@lol-PC:~/madwifi-hal-0.10.5.6-r3835-20080801$ 


What did I do wrong?

Someone please help me, I'm desperate!

---

### Post by nicedude on 2008-08-29
Hey guy did you use the driver on my guides page? If not then that may be the problem, but also yes you have to deselect the restricted driver from managing any atheros things to keep it from conflicting. My guide works 100% if you can follow directions step by step so you may want to read it. I remove jockey the restricted driver manager from all my boxes as it is only of value if you can't do things yourself, and since it only manages wifi & graphics drivers for ATI & Nvidia it is pointless since you can use  envyng to manage the graphics and then manage your own madwifi driver ( or other brand if you have a broadcom etc ). So jockey is not at all needed in your system and actually can be confusing and screw stuff up if you try to load drivers and it does also.

---

### Post by WastePotato on 2008-08-29
Hey guys!

Everythings working now! I was just about to give up, as after 3 reboots, the madwifi driver was still failing to work, and then, out of boredom I typed:

> sudo iwlist scanning

And then all of the networks came up! So then I clicked the network Icon and surely enough, all of the networks came up! 

I Want to thank nicedude ,ugm6hr and tommcd for their continued and excellent support on this issue.

As a new user to Ubuntu, I was expecting that asking for help would lead to patronizing replies but this gives me hope that whenever I have an issue with Linux I can always turn to these forums for support.

Thanks Everyone! :KS  :popcorn:

---

