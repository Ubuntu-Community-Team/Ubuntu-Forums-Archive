---
title: "wireless connection"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by leilton on 2012-03-30
Yes, this has probably been discussed before, but having now spent three days trying to get a connection, got a bit impatient, and decided to post now.

Have, on my brand new laptop, (no windows), Ubuntu, Xubuntu and Kubuntu.

Now in my innocents, assumed that as all three end in Ubuntu, procedure would be same.

Can someone explain what the secret is to connecting to Wireless via Kubuntu, because no matter what I do, it will not happen.   As a second thought, why does it keep changing my Key on the security page, or am I missing something and being a bigger idiot than I usually am.

Please before I lose my hair (already silver in colour), someone tell me what I am doing wrong.

Sorry if this is a repeat of someone else question, but my last hope

:confused:

---

### Post by Jake5 on 2012-03-30
So in the terminal or Konsole, type in ```
sudo lshw -c Network
``` copy (ctrl+shift+C in the terminal) and paste the results here so we can see what kind of hardware you are running. Do the same for ```
iwconfig
```

---

### Post by Jake5 on 2012-03-30
The output of ```
rfkill list all
``` will help too.

---

### Post by leilton on 2012-04-03
> **Jake5 said:**
> So in the terminal or Konsole, type in ```
sudo lshw -c Network
``` copy (ctrl+shift+C in the terminal) and paste the results here so we can see what kind of hardware you are running. Do the same for ```
iwconfig
```

[B]edward@edward-AMILO-PRO-V2030:~$ sudo lshw -c Network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0000000-d0001fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:40:ca:de:c8:9b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.1.33 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:2000(size=256) memory:d0002c00-d0002cff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:6d:fa:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

edward@edward-AMILO-PRO-V2030:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

:confused:

I apologise for the delay in answering your prompt reply, Mubuntu does not appear to want to work on my system, taken me three days to get it pass the 28% update mark, and certainlythe edit pages on same are no way similar to those on other Ubuntu Systems.

Best I could do copy and paste wise, never having done same before in Linux, trust it makes sense to you.

Again my apologise


[/B]

---

### Post by Jake5 on 2012-04-03
k, try this:```
sudo ifconfig wlan0 up
```
That should enable your wireless network!
Be sure to restart the computer and make sure its a permanent solution.

---

### Post by jwaipouri on 2012-04-03
Hi, 
I just installed 10:04 on an HP Mini, in order to do it I installed it on an HDD in my Acer, because the mini wouldn't USB boot.
After putting the HDD in the Mini, I found the wireless and ethernet do not work.

I got the following in the terminal: 

desirae@desirae:~$ iwconfig

lo no wireless extensions


eth0 no wireless extensions


wlan0 IEEE 802.11bg ESSID:off/any
      Mode:Managed Access Point: Not-Associated Tx-Power=20dBm
      Retry  long limit:7  RTS thr:off   Fragment thr:off
      Power Management:off

desirae@desirae:~$ rfkill list all
0: phy0: wireless LAN
        Soft blocked: no
        Hard blocked: no
deisrae@desirae:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory

Obviously because I can't get it online, I'm trying to work with my own computer's internet and then transferring files by usb stick to the HP.

any further ideas for me?

---

### Post by Jake5 on 2012-04-03
Have you tried the last code without using the "sudo" command

---

### Post by Jake5 on 2012-04-03
Maybe take a look here...post #18 should help. [click here]("http://ubuntuforums.org/showthread.php?t=1946445&page=2")

---

### Post by bkratz on 2012-04-03
> **Jake5 said:**
> Maybe take a look here...post #18 should help. [click here]("http://ubuntuforums.org/showthread.php?t=1946445&page=2")


Why would post 18 help?  The op has a Broadcom device which does not use the mentioned driver.

---

### Post by Jake5 on 2012-04-03
Good point, I didn't notice the difference, sorry. Perhaps this is where the extent of my knowledge ends. Perhaps you could take over bcratz, I will sit back and try to learn something. I was only trying to help because no one else had made it here yet.

---

### Post by jwaipouri on 2012-04-03
Thanks for your thoughts, I realised after a lot of messing around that the wlan was working, so I connected and then used the hardware driver utility to find the appropriate driver.

I can be a bit slow sometimes:)
works great, although the wireless icon still shows no connection even when there is.

---

### Post by bkratz on 2012-04-03
> **Jake5 said:**
> Good point, I didn't notice the difference, sorry. Perhaps this is where the extent of my knowledge ends. Perhaps you could take over bcratz, I will sit back and try to learn something. I was only trying to help because no one else had made it here yet.


From the pages of 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers)

Since Ubuntu 11.04 **Natty Narwhal** additional installation of the package **firmware-b43-installer** can be helpful and/or necessary, respectively: 
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```This should be done with an operational ethernet connection.  It will probably be necessary to reboot after downloading.  Disconnect ethernet and 


```
sudo iwlist scan
```

and see what comes up!

---

### Post by bkratz on 2012-04-03
So it is working now?

---

### Post by troymius on 2012-04-03
In general it seems that the broadcom wifi cards cause more trouble than others. 

It does not answer why kubuntu specifically wont connect while other *buntus do of course.

On my Dell mini (also a broadcom card) I ended up using wicd by the way.

---

### Post by jwaipouri on 2012-04-03
Tried as suggested, with following result:

desirae@desirae:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
[sudo] password for desirae: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer


PLease note that although I have wireless connectivity the icon in the corner shows no connection.

---

### Post by jwaipouri on 2012-04-03
> **bkratz said:**
> So it is working now?

Yes but with faulty front end icons

---

### Post by leilton on 2012-04-04
> **Jake5 said:**
> k, try this:```
sudo ifconfig wlan0 up
```That should enable your wireless network!
Be sure to restart the computer and make sure its a permanent solution.


SIOCSIFFLAGS: No such file or directory

answer to above suggestion is shown.

Beyond me, why it will work on wired but not wireless is a joke.

Perhaps time to give up with Mubuntu and try something else.

Thanks for help so far.

:confused:

---

### Post by leilton on 2012-04-04
> **bkratz said:**
> From the pages of 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers)

Since Ubuntu 11.04 **Natty Narwhal** additional installation of the package **firmware-b43-installer** can be helpful and/or necessary, respectively: 
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```This should be done with an operational ethernet connection.  It will probably be necessary to reboot after downloading.  Disconnect ethernet and 


```
sudo iwlist scan
```and see what comes up!

edward@edward-AMILO-PRO-V2030:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.8 kB of archives.
After this operation, 139 kB of additional disk space will be used.
Get:1 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric/main b43-fwcutter i386 1:014-9 [16.5 kB]
Get:2 [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric/multiverse firmware-b43-installer all 1:014-9 [3,272 B]
Fetched 19.8 kB in 0s (22.7 kB/s)            
Selecting previously deselected package b43-fwcutter.
(Reading database ... 122146 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a014-9_i386.deb) ...
Selecting previously deselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a014-9_all.deb) ...
Processing triggers for man-db ...

Setting up b43-fwcutter (1:014-9) ...
Setting up firmware-b43-installer (1:014-9) ...
This card work with newer 5.10.56.27.3 firmware. Trying to install it.
--2012-04-04 12:37:44--  [http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2)
Resolving mirror2.openwrt.org... 46.4.11.11
Connecting to mirror2.openwrt.org|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1596823 (1.5M) [application/x-bzip2]
Saving to: `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2'

100%[======================================>] 1,596,823    103K/s   in 16s     

2012-04-04 12:38:01 (97.2 KB/s) - `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2' saved [1596823/1596823]

broadcom-wl-5.10.56.27.3/driver/
broadcom-wl-5.10.56.27.3/driver/Makefile
broadcom-wl-5.10.56.27.3/driver/aiutils.c
broadcom-wl-5.10.56.27.3/driver/bcmsrom.c
broadcom-wl-5.10.56.27.3/driver/bcmutils.c
broadcom-wl-5.10.56.27.3/driver/hnddma.c
broadcom-wl-5.10.56.27.3/driver/hndpmu.c
broadcom-wl-5.10.56.27.3/driver/include/
broadcom-wl-5.10.56.27.3/driver/include/UdpLib.h
broadcom-wl-5.10.56.27.3/driver/include/aidmp.h
broadcom-wl-5.10.56.27.3/driver/include/arminc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcdc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aes.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aeskeywrap.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bcmccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bn.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/ccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/des.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/dh.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/hmac_sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md5.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/passhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/prf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rc4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rijndael-alg-fst.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha1.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/tkhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdefs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdevs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmendian.h
broadcom-wl-5.10.56.27.3/driver/include/bcmnvram.h
broadcom-wl-5.10.56.27.3/driver/include/bcmotp.h
broadcom-wl-5.10.56.27.3/driver/include/bcmparams.h
broadcom-wl-5.10.56.27.3/driver/include/bcmperf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmrobo.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_fmt.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_tbl.h
broadcom-wl-5.10.56.27.3/driver/include/bcmstdlib.h
broadcom-wl-5.10.56.27.3/driver/include/bcmutils.h
broadcom-wl-5.10.56.27.3/driver/include/bcmwifi.h
broadcom-wl-5.10.56.27.3/driver/include/bitfuncs.h
broadcom-wl-5.10.56.27.3/driver/include/dmemc_core.h
broadcom-wl-5.10.56.27.3/driver/include/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/igs/
broadcom-wl-5.10.56.27.3/driver/include/epivers.h
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.in
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.prev
broadcom-wl-5.10.56.27.3/driver/include/etioctl.h
broadcom-wl-5.10.56.27.3/driver/include/flash.h
broadcom-wl-5.10.56.27.3/driver/include/flashutl.h
broadcom-wl-5.10.56.27.3/driver/include/hndarm.h
broadcom-wl-5.10.56.27.3/driver/include/hndchipc.h
broadcom-wl-5.10.56.27.3/driver/include/hndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/hnddma.h
broadcom-wl-5.10.56.27.3/driver/include/hndgige.h
broadcom-wl-5.10.56.27.3/driver/include/hndjtagdefs.h
broadcom-wl-5.10.56.27.3/driver/include/hndmips.h
broadcom-wl-5.10.56.27.3/driver/include/hndpci.h
broadcom-wl-5.10.56.27.3/driver/include/hndpmu.h
broadcom-wl-5.10.56.27.3/driver/include/hndsoc.h
broadcom-wl-5.10.56.27.3/driver/include/linux_gpio.h
broadcom-wl-5.10.56.27.3/driver/include/linux_osl.h
broadcom-wl-5.10.56.27.3/driver/include/linuxver.h
broadcom-wl-5.10.56.27.3/driver/include/min_osl.h
broadcom-wl-5.10.56.27.3/driver/include/mips33_core.h
broadcom-wl-5.10.56.27.3/driver/include/mips74k_core.h
broadcom-wl-5.10.56.27.3/driver/include/mipsinc.h
broadcom-wl-5.10.56.27.3/driver/include/ndiserrmap.h
broadcom-wl-5.10.56.27.3/driver/include/nicpci.h
broadcom-wl-5.10.56.27.3/driver/include/osl.h
broadcom-wl-5.10.56.27.3/driver/include/pci_core.h
broadcom-wl-5.10.56.27.3/driver/include/pcicfg.h
broadcom-wl-5.10.56.27.3/driver/include/pcie_core.h
broadcom-wl-5.10.56.27.3/driver/include/proto/
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11e.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.1d.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmeth.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmevent.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmip.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmtcp.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eap.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eapol.h
broadcom-wl-5.10.56.27.3/driver/include/proto/ethernet.h
broadcom-wl-5.10.56.27.3/driver/include/proto/vlan.h
broadcom-wl-5.10.56.27.3/driver/include/proto/wpa.h
broadcom-wl-5.10.56.27.3/driver/include/rts/
broadcom-wl-5.10.56.27.3/driver/include/rts/crc.h
broadcom-wl-5.10.56.27.3/driver/include/sbchipc.h
broadcom-wl-5.10.56.27.3/driver/include/sbconfig.h
broadcom-wl-5.10.56.27.3/driver/include/sbgige.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndarm.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/sbhnddma.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndpio.h
broadcom-wl-5.10.56.27.3/driver/include/sbmemc.h
broadcom-wl-5.10.56.27.3/driver/include/sbpcmcia.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdio.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdpcmdev.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsocram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsprom.h
broadcom-wl-5.10.56.27.3/driver/include/sflash.h
broadcom-wl-5.10.56.27.3/driver/include/siutils.h
broadcom-wl-5.10.56.27.3/driver/include/trxhdr.h
broadcom-wl-5.10.56.27.3/driver/include/typedefs.h
broadcom-wl-5.10.56.27.3/driver/include/wlc_ethereal.h
broadcom-wl-5.10.56.27.3/driver/include/wlioctl.h
broadcom-wl-5.10.56.27.3/driver/include/wllmacctl.h
broadcom-wl-5.10.56.27.3/driver/linux_osl.c
broadcom-wl-5.10.56.27.3/driver/nicpci.c
broadcom-wl-5.10.56.27.3/driver/nvram_stub.c
broadcom-wl-5.10.56.27.3/driver/sbutils.c
broadcom-wl-5.10.56.27.3/driver/siutils.c
broadcom-wl-5.10.56.27.3/driver/siutils_priv.h
broadcom-wl-5.10.56.27.3/driver/wl_apsta/
broadcom-wl-5.10.56.27.3/driver/wl_apsta/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_dbg.h
broadcom-wl-5.10.56.27.3/driver/wl_export.h
broadcom-wl-5.10.56.27.3/driver/wl_iw.c
broadcom-wl-5.10.56.27.3/driver/wl_iw.h
broadcom-wl-5.10.56.27.3/driver/wl_linux.c
broadcom-wl-5.10.56.27.3/driver/wl_linux.h
broadcom-wl-5.10.56.27.3/driver/wlc_key.h
broadcom-wl-5.10.56.27.3/driver/wlc_pub.h
broadcom-wl-5.10.56.27.3/nas_exe.o
broadcom-wl-5.10.56.27.3/shared/
broadcom-wl-5.10.56.27.3/shared/Makefile
broadcom-wl-5.10.56.27.3/shared/UdpLib.c
broadcom-wl-5.10.56.27.3/shared/bcmcvar.h
broadcom-wl-5.10.56.27.3/shared/bcmtimer.h
broadcom-wl-5.10.56.27.3/shared/ctype.c
broadcom-wl-5.10.56.27.3/shared/linux_timer.c
broadcom-wl-5.10.56.27.3/shared/netconf.h
broadcom-wl-5.10.56.27.3/shared/opencrypto.h
broadcom-wl-5.10.56.27.3/shared/rte_timers.c
broadcom-wl-5.10.56.27.3/shared/shutils.c
broadcom-wl-5.10.56.27.3/shared/shutils.h
broadcom-wl-5.10.56.27.3/shared/wl.c
broadcom-wl-5.10.56.27.3/shared/wl_linux.c
broadcom-wl-5.10.56.27.3/shared/wlutils.h
broadcom-wl-5.10.56.27.3/wl_exe.o
This file is recognised as:
  ID         :  FW15
  filename   :  wl_prebuilt.o
  version    :  508.1084
  MD5        :  490d4e149ecc45eb1a91f06aa75be071
Extracting b43/ucode19.fw
Extracting b43/lp0initvals14.fw
Extracting b43/ucode16_lp.fw
Extracting b43/ucode16_sslpn.fw
  ucode revision: 1084
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/sslpn2bsinitvals17.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/ucode16_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/sslpn2initvals17.fw
Extracting b43/ucode4.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ucode17.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/pcm4.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/pcm5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/ucode20.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
edward@edward-AMILO-PRO-V2030:~$ 

:confused:

Still zilch.

Thanks anyway

---

### Post by lkraemer on 2012-04-04
Leilton,
Now that you have the Firmware installed, select SYSTEM -> ADMINISTRATION
and click on Hardware Drivers.  Toggle it once and see if you have Wireless. If that doesn't work try once more.  It should now work.

If it still doesn't work try :
```

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

```
OR
```

sudo /etc/init.d/networking restart

```
Then try to ping [www.yahoo.com](www.yahoo.com) from a Terminal Window (Console)
```

ping -c 3 www.yahoo.com

```

Also, Rght Click & then Left Click on the Networking Icon in the Upper Right Panel (Menu Bar) 
and make sure Wifi & Wired are ENABLED.


lk

---

### Post by leilton on 2012-04-05
> **lkraemer said:**
> Leilton,
Now that you have the Firmware installed, select SYSTEM -> ADMINISTRATION
and click on Hardware Drivers.  Toggle it once and see if you have Wireless. If that doesn't work try once more.  It should now work.

If it still doesn't work try :
```

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

```OR
```

sudo /etc/init.d/networking restart

```Then try to ping [www.yahoo.com]("http://www.yahoo.com") from a Terminal Window (Console)
```

ping -c 3 www.yahoo.com

```Also, Rght Click & then Left Click on the Networking Icon in the Upper Right Panel (Menu Bar) 
and make sure Wifi & Wired are ENABLED.


lkdward@edward-AMILO-PRO-V2030:~$ sudo /etc/init.d/networking start
[sudo] password for edward: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start networking
networking stop/waiting
edward@edward-AMILO-PRO-V2030:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
edward@edward-AMILO-PRO-V2030:~$ ping -c 3 [www.yahoo.com](www.yahoo.com)
PING eu-fp3.wa1.b.yahoo.com (87.248.122.122) 56(84) bytes of data.
64 bytes from ir1.fp.vip.ch1.yahoo.com (87.248.122.122): icmp_req=1 ttl=51 time=124 ms
64 bytes from ir1.fp.vip.ch1.yahoo.com (87.248.122.122): icmp_req=2 ttl=51 time=91.1 ms
64 bytes from ir1.fp.vip.ch1.yahoo.com (87.248.122.122): icmp_req=3 ttl=51 time=86.3 ms

--- eu-fp3.wa1.b.yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2740ms
rtt min/avg/max/mdev = 86.313/100.655/124.531/16.996 ms
edward@edward-AMILO-PRO-V2030:~$ 



Results of suggestions are shown, not in very good order I'm afraid, at this time of night not at my best.

Still wonder if it is the fact that the Manage Configuration pages are not those shown on other Ubuntu and for some reason it keeps changing my Device MAC address and Key.

Give it one more day, then out it comes.

Silly question, and I hesitate to ask, (why I'm on absolute beginners page, is it possible to copy and paste an example of the configure. pages, and when I check Connection Pages show wireless and wired,but wireless says waiting for authorization.

Any Help?

Thanks a bunch for all you have done so far.   Certainly lost without you chaps helping.


:confused:

---

### Post by wildmanne39 on 2012-04-05
Hi, I have been watching this thread from the beginning and if no one minds I would like to help.

Please post the output of the following commands by just copy and paste into the terminal for accuracy:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

Thanks

---

### Post by leilton on 2012-04-06
[QUOTE=wildmanne39;11820791]Hi, I have been watching this thread from the beginning and if no one minds I would like to help.

Please post the output of the following commands by just copy and paste into the terminal for accuracy:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
``````
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```by clicking on new reply and click # and paste the information between the brackets.
Thank you

Thanks[edward@edward-AMILO-PRO-V2030:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux edward-AMILO-PRO-V2030 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
edward@edward-AMILO-PRO-V2030:~$ lspci -nnk | grep -iA2 net
00:06.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
        Subsystem: Gemtek Technology Co., Ltd Device [17f9:0006]
        Kernel driver in use: b43-pci-bridge
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
        Subsystem: Fujitsu Technology Solutions Device [1734:109b]
        Kernel driver in use: via-rhine
edward@edward-AMILO-PRO-V2030:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
edward@edward-AMILO-PRO-V2030:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
edward@edward-AMILO-PRO-V2030:~$ lsmod
Module                  Size  Used by
via                    45249  2 
drm                   192226  3 via
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
joydev                 17393  0 
snd_via82xx            24720  2 
gameport               15060  1 snd_via82xx
snd_via82xx_modem      18377  5 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
b43                   318816  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
pcmcia                 39822  0 
mac80211              272785  1 b43
serio_raw              12990  0 
snd                    55902  21 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14115  3 snd_via82xx,snd_via82xx_modem,snd_pcm
i2c_viapro             12969  0 
soundcore              12600  1 snd
cfg80211              172392  2 b43,mac80211
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35854  0 
via_rhine              27413  0 
firewire_core          56937  1 firewire_ohci
pata_via               13359  0 
sata_via               13534  3 
crc_itu_t              12627  1 firewire_core
ssb                    50682  1 b43
video                  18908  0 
edward@edward-AMILO-PRO-V2030:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:14:A5:6D:FA:46

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        00:40:CA:DE:C8:9B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             80.58.61.250
    DNS:             80.58.61.254


edward@edward-AMILO-PRO-V2030:~$ sudo iwlist scan
[sudo] password for edward: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

]
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55 

Hope this is what you asked for.


Does appear that I'm taking up a lot of peoples time and effort just to get a wireless connection that works on any other Ubuntu set up.

My thanks as always for your help

---

### Post by leilton on 2012-04-06
> **leilton said:**
> [QUOTE=wildmanne39;11820791]Hi, I have been watching this thread from the beginning and if no one minds I would like to help.

Please post the output of the following commands by just copy and paste into the terminal for accuracy:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan
``````
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```by clicking on new reply and click # and paste the information between the brackets.
Thank you

Thanks[edward@edward-AMILO-PRO-V2030:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux edward-AMILO-PRO-V2030 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
edward@edward-AMILO-PRO-V2030:~$ lspci -nnk | grep -iA2 net
00:06.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
        Subsystem: Gemtek Technology Co., Ltd Device [17f9:0006]
        Kernel driver in use: b43-pci-bridge
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
        Subsystem: Fujitsu Technology Solutions Device [1734:109b]
        Kernel driver in use: via-rhine
edward@edward-AMILO-PRO-V2030:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
edward@edward-AMILO-PRO-V2030:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
edward@edward-AMILO-PRO-V2030:~$ lsmod
Module                  Size  Used by
via                    45249  2 
drm                   192226  3 via
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
joydev                 17393  0 
snd_via82xx            24720  2 
gameport               15060  1 snd_via82xx
snd_via82xx_modem      18377  5 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
b43                   318816  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
pcmcia                 39822  0 
mac80211              272785  1 b43
serio_raw              12990  0 
snd                    55902  21 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14115  3 snd_via82xx,snd_via82xx_modem,snd_pcm
i2c_viapro             12969  0 
soundcore              12600  1 snd
cfg80211              172392  2 b43,mac80211
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
firewire_ohci          35854  0 
via_rhine              27413  0 
firewire_core          56937  1 firewire_ohci
pata_via               13359  0 
sata_via               13534  3 
crc_itu_t              12627  1 firewire_core
ssb                    50682  1 b43
video                  18908  0 
edward@edward-AMILO-PRO-V2030:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:14:A5:6D:FA:46

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        00:40:CA:DE:C8:9B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.33
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             80.58.61.250
    DNS:             80.58.61.254


edward@edward-AMILO-PRO-V2030:~$ sudo iwlist scan
[sudo] password for edward: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

]
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55 

Hope this is what you asked for.


Does appear that I'm taking up a lot of peoples time and effort just to get a wireless connection that works on any other Ubuntu set up.

My thanks as always for your help


ps.   Just noticed that when I open manage connection, unable to check the wireless enable box.   Have I done something stupid.

By the by, was 11.04 this bad, if not, maybe I'll download same and get rid of this 11.10 which is a pain in the butt.

---

### Post by wildmanne39 on 2012-04-06
Hi, it shows a hard block that usually means that the switch on your computer is off, make sure it is on then see if it works if not run:
```
sudo unblock all
```
then check it with:
```
rfkill list all
```
All commands that begin with sudo requires you to enter your user password but it will not show it in the terminal as you type it so just hit enter after you have typed your password.

Please try this command again:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etork | tail -n55
```
I really need to see the output.

Please post the information here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

