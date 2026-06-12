---
title: "More atheros wireless woes"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Geoff! on 2008-08-20
I made the switch to Ubuntu from XP in July. I am using an Acer Aspire 3050 running a AR242x 802.11abg Wireless PCI Express Adapter. Obviously there were initial wireless problems. Which I solved using Madwifi, with help from this website-[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html")

Up until several days ago this worked just fine. However something happened. My wireless stopped working completely. And the links in that article, it seems, are outdated. In turn, I tried rfincher's post here [http://ubuntuforums.org/showthread.php?t=795984&page=13]("http://ubuntuforums.org/showthread.php?t=795984&page=13") but to no avail. The terminal returned this:
> [QUOTE]geoffrey@geoffrey-laptop:~$ wget [http://madwifi-hal-0.10.5.6-r3835-20080810.tar.gz](http://madwifi-hal-0.10.5.6-r3835-20080810.tar.gz)
--02:36:49--  [http://madwifi-hal-0.10.5.6-r3835-20080810.tar.gz/](http://madwifi-hal-0.10.5.6-r3835-20080810.tar.gz/)
           => `index.html'
Resolving madwifi-hal-0.10.5.6-r3835-20080810.tar.gz... failed: Name or service not known.
geoffrey@geoffrey-laptop:~$ tar xvf madwifi-hal-0.10.5.6-r3835-20080810.tar.gz
tar: madwifi-hal-0.10.5.6-r3835-20080810.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
geoffrey@geoffrey-laptop:~$ cd madwifi-hal-0.10.5.6-r3835-20080801
bash: cd: madwifi-hal-0.10.5.6-r3835-20080801: No such file or directory
geoffrey@geoffrey-laptop:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
geoffrey@geoffrey-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
geoffrey@geoffrey-laptop:~$ sudo modprobe ath_pci[/QUOTE]

Now I'm all sorts of confused. I've been at this for a few hours on and off and I'm about stumped. I certainly don't want to make the switch back to Windows but I need to able to connect to the internet. If any one can offer some help to get my wireless working again, it will be greatly appreciated.

---

### Post by pmsumner on 2008-08-20
```
geoffrey@geoffrey-laptop:~$ wget http://madwifi-hal-0.10.5.6-r3835-20080810.tar.gz
--02:36:49-- http://madwifi-hal-0.10.5.6-r3835-20080810.tar.gz/ => `index.html'
Resolving madwifi-hal-0.10.5.6-r3835-20080810.tar.gz... failed: Name or service not known.
```

This is where it all went wrong, the first step.  You're trying to download from the wrong place.

You should replace the http://madwifi..... with:

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)

So:
```

wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz

```

And go again.

---

### Post by Geoff! on 2008-08-20
I tried your suggestion but to no avail. I entered this:
```
sudo apt-get update && sudo apt-get install build-essential
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
tar xvf madwifi-hal-0.10.5.6-r3835-20080810.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo make
sudo make install
sudo modprobe ath_pci
sudo reboot
```

And received this: 
```
geoffrey@geoffrey-laptop:~$ wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
--14:23:50--  http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
           => `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz.3'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,417,874 (4.2M) [application/x-gzip]

100%[====================================>] 4,417,874    684.42K/s    ETA 00:00

14:23:57 (611.58 KB/s) - `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz.3' saved [4417874/4417874]

geoffrey@geoffrey-laptop:~$ tar xvf madwifi-hal-0.10.5.6-r3835-20080810.tar.gz
tar: madwifi-hal-0.10.5.6-r3835-20080810.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
geoffrey@geoffrey-laptop:~$ cd madwifi-hal-0.10.5.6-r3835-20080801
geoffrey@geoffrey-laptop:~/madwifi-hal-0.10.5.6-r3835-20080801$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools'
geoffrey@geoffrey-laptop:~/madwifi-hal-0.10.5.6-r3835-20080801$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.24-16-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.24-16-generic/net
make[1]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath'
make[1]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.24-16-generic/net
make[1]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
make[1]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.24-16-generic/net
make[2]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
make[2]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.24-16-generic/net
make[2]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
make[2]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.24-16-generic/net
make[2]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
make[2]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.24-16-generic/net
make[2]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
make[1]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
make[1]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.24-16-generic/net; \
	done
make[1]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
(export KMODPATH=/lib/modules/2.6.24-16-generic/net; /sbin/depmod -ae 2.6.24-16-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
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
make[2]: Entering directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/geoffrey/madwifi-hal-0.10.5.6-r3835-20080801/tools'
geoffrey@geoffrey-laptop:~/madwifi-hal-0.10.5.6-r3835-20080801$ sudo modprobe ath_pci
geoffrey@geoffrey-laptop:~/madwifi-hal-0.10.5.6-r3835-20080801$ sudo reboot
```

Which I'm pretty sure all went wrong around this point:

```
geoffrey@geoffrey-laptop:~$ tar xvf madwifi-hal-0.10.5.6-r3835-20080810.tar.gz
tar: madwifi-hal-0.10.5.6-r3835-20080810.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
```

I'm pretty sure the answer is quite simple. I'm just too inexperienced to see it.

---

### Post by pmsumner on 2008-08-20
OK, you're getting places

```

14:23:57 (611.58 KB/s) - `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz.3' saved [4417874/4417874]

geoffrey@geoffrey-laptop:~$ tar xvf madwifi-hal-0.10.5.6-r3835-20080810.tar.gz
tar: madwifi-hal-0.10.5.6-r3835-20080810.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

```

Look at the file name the wget command saved:
```
madwifi-hal-0.10.5.6-r3835-20080801.tar.gz.3
```

And the file that tar is expecting:
```
madwifi-hal-0.10.5.6-r3835-20080810.tar.gz
```

Spot the 3 on the end?  You've tried this a few times already, and the wget command has already saved the file 3 times (once without any numbers after it, 2nd time with a .1 after it, 3rd time with a .2 and 4th time with a .3).

Easiest way to proceed is probably to delete all the previous downloads and start again.

```
rm ~/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz*
```

Another option is just to rename the file and continue from the "tar xvf" bit:

```
mv madwifi-hal-0.10.5.6-r3835-20080801.tar.gz.3 madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

Hope that helps

---

### Post by Geoff! on 2008-08-20
I went with your first suggestion and removed them. I doubled checked to make sure the code was consistent and entered:

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
tar xvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo make
sudo make install
sudo modprobe ath_pci
sudo reboot
```

It seems that I now have the ability to connect through wireless. When I go through System>Administration>Network, Wireless Connections actually appears now. Which is progress for sure. However, it doesn't seem to be picking up my home wireless router. Any thoughts?

---

### Post by pmsumner on 2008-08-21
Whoohoo!
In the terminal, if you type: ```
iwconfig ath0
``` Can you copy/paste the response?

(This command shows the wireless config for 'ath0' which should be your wireless network interface)

If it says something like "ath0 does not exist" can you type:
```
lsmod | grep ath_
```
And copy/paste the results here.

(This command lists the modules loaded by the kernel and shows only the modules with 'ath_' in their name).

---

### Post by Geoff! on 2008-08-21
Alright, the results of iwconfig ath0:

```
geoffrey@geoffrey-laptop:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

...and for kicks:

```
geoffrey@geoffrey-laptop:~$ lsmod | grep ath_
ath_rate_sample        16128  1 
ath_pci               249016  0 
wlan                  236272  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               305376  3 ath_rate_sample,ath_pci

```

---

### Post by pmsumner on 2008-08-22
Fabulous!  We now know that your wireless card is recognised, and that the modules have been built and loaded correctly.

Next is to get the thing connected.  I cheated at this, I downloaded and installed wicd to do this for me as I was really frustrated at this point.  Someone else will have to tell you how to do it any other way.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) is wicd's home.  Look at the download page for instructions on how to install in Ubuntu.

---

### Post by Geoff! on 2008-08-22
Alright, I've completed downloading the Wicd manager. Unfortunately it isn't recognizing any wireless signals. Quite baffling. I tried troubleshooting, yet nothing is yield results. Any thoughts?

---

### Post by pmsumner on 2008-08-22
Sorry, at this point I can't help any further.  Someone else will have to step in to sort you out!

---

### Post by wally the duck on 2009-04-06
I've put on fresh install of Jaunty (beta) on a Compaq CQ60 210US with atheros wifi card. I turned off the bluetooth service (system monitor) and wireless now works perfectly with the out-of the-box Jaunty drivers. I had tried for 2 days to get it going and could not. Either turning off bluetooth did it or something changed overnight in the repositories and updated after my install.
The blue light stays orange, but everything still works.

---

