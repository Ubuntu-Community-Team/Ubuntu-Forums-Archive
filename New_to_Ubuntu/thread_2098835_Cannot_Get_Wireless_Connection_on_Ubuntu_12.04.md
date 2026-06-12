---
title: "Cannot Get Wireless Connection on Ubuntu 12.04"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by Kariotaki on 2012-12-27
Hello,

I'm a newbie to Linux but I managed to install Ubuntu 12.04 on an old Desktop Presario. Since there was no wireless card, I bought a wireless USB adapter (Mini USB 2.0 / 1.1 Wireless WiFi N LAN Adapter IEEE 802.11n 802.11g 802.11b - 943MiUSBMiF320).

The dealer said that the adapter is compatible with Linux.

I was not able to install the software from the CD (maybe the file is .exe?), but from what I ascertained, the driver that needs to be installed is the Realtek RTL8188CUS. 

As soon as I plug in the wireless adapter, the computer is able to detect wireless signals, but it cannot connect to them. When I go to network settings and try to establish a connection to my WiFi, the computer does not respond. 

Can anyone help?

---

### Post by BertN45 on 2012-12-27
Try this solution:

[http://askubuntu.com/questions/123937/rtl8188cus-wireless-usb-dongle-doesnt-work-unless-i-disable-wireless-security](http://askubuntu.com/questions/123937/rtl8188cus-wireless-usb-dongle-doesnt-work-unless-i-disable-wireless-security)

Instead of using the nano editor, you could use: sudo nautilus -> browse to the files you have to modify and open those files with the standard [COLOR="blue"]gedit[/COLOR] GUI editor.

---

### Post by ZippyUbu on 2012-12-27
Hi, Post the output of:

```
sudo lshw -C network
```For us to have a look anyway...

--
Zu

---

### Post by kurt18947 on 2012-12-27
I too would recommend the RealTek driver for that chipset.  I got mine from here:

[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false).

Select RTL8188CUS from the list.  Download and extract the files, keeping track of the folder where the extracted files are.  Navigate to that folder. One file should be install.sh.  I just type this command in a terminal:

```
sudo bash install.sh   
```and sit still for a minute:).  Do keep the folder with the Realtek files.  If you update and get a new image/kernel,  the wifi adapter will cease to work.  You'll need to rerun the script.  Do note that you need to do this in an account with sudo privileges.  Once you do it a time or two, it's a no-brainer and knowing how to extract and run a bash script is useful for other hardware as well.  I use a script to install Brother printers, it works great.

---

### Post by Kariotaki on 2012-12-27
Hi,

Here is what my system reads:
*-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:0b:81:87:dc:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated


I believe I have installed the Real Tek driver previously, but it always reads busy

---

### Post by squakie on 2012-12-27
Try:

sudo apt-get install build-essential

then:

follow this link:  [http://www.alexx.net/2012/06/adventures-in-wireless-ubuntu-1204.html](http://www.alexx.net/2012/06/adventures-in-wireless-ubuntu-1204.html)

---

### Post by BertN45 on 2012-12-27
> **Kariotaki said:**
> Hi,

Here is what my system reads:
*-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:0b:81:87:dc:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated


I believe I have installed the Real Tek driver previously, but it always reads busy

OK you have the wrong driver and you have to black list that one, so it is not loaded automatically. Unfortunately the drivers provided by Realtek do not work with the newest Ubuntu releases. This guy provides a script that will compile and install the correct driver for you and blacklist the erroneous one. You can find the script for Ubuntu 12.04/12.10 at the end of the page.

[http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux](http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux)

Copy/paste the script in a text file and save it as [COLOR="blue"]mwdinstall.sh[/COLOR] and run it using [COLOR="Blue"]sudo bash mwdinstall.sh[/COLOR] - note that it needs running after any kernel upgrade.

It is the automated version of: [http://askubuntu.com/questions/123937/rtl8188cus-wireless-usb-dongle-doesnt-work-unless-i-disable-wireless-security](http://askubuntu.com/questions/123937/rtl8188cus-wireless-usb-dongle-doesnt-work-unless-i-disable-wireless-security)

Please read the following instructions, which have been extracted from the complete script:
> # 
# This process may well work on other Ubuntu versions, other Linux distributions and also with other dongles based on the  Realtek RTL8188CUS chip - see notes in comment lines at end.
#
# The dongle seemed to work to some extent with the kernel driver as incorportated initially in Ubuntu and Lubuntu 12.04 or 12.10 but was at best very unstable. 
#
#If using  Lubuntu and other "lightweight" linux versions you may need first to install compile (gcc) and make functionality, e.g through
#        sudo apt-get build-essential 
# BUT in Lubuntu 12.10 build-essential has vanished. Only the following was needed:
#        sudo apt-get install gcc
# even though  a search for gcc with Synaptic implied that it was already present.
#
# This script needs to be **run again** whenever the Linux kernel has been updated - typically in some semi-automatic software updates.
# The kernel versions used in testing included 3.2.0-33 and 3.5.0-19 (3.2.0-23 up worked with earlier versions and probably will with this).
#
#################### GET THE DRIVER ##########################
# You need the latest driver installation package - use Ethernet or download elsewhere and copy using a USB stick or whatever.
# Get it from <[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/) > by selecting
#	Communications network ICs
#	Wireless LAN IC#s
#	WLAN NIC
#	IEEE 802.11b/g/n Single-Chip
#	Software
#then 
#	ticking RTL8188CUS
#	clicking Go
#	selecting the download site for the Unix/Linux package
#      unzipping the downloaded file
#
# The downloaded file used when preparing this note was
#	RTL8188C_8192C_8192D_USB_linux_v3.4.2_3727.20120404.zip
#
# Best not to have the dongle attached yet to avoid a reboot later.
#
# ##################### Unpack it  ########################
# (e.g. as folder RTL8188C_8192C_8192D_USB_linux_v3.4.2_3727.20120404)

################### Change into the resulting folder #####################
# e.g. cd RTL8188C_8192C_8192D_USB_linux_v3.4.2_3727.20120404
#and copy mwdinstall.sh (this script) into it.

################### Run this script ######################
# If you have done the above then running this script using, say, 
#                          sudo bash mwdinstall.sh
# should do the following:
#
# 1) Find and report the kernel version
# 2) Create or replace file blacklist-rtl8192 in  /etc/modprobe.d/blacklist.conf to disable the possibly wrongly selected Ubuntu supplied version.
# 3) Rename the said problematic driver to effectively disable it, just in case 
# 4) Run the install script you downloaded from Realtek. 


---

### Post by Kariotaki on 2012-12-28
Thanks for the advice BertN45, but I fear that I've done something wrong. After following the steps described, I still cannot get a wireless connection. 
Here is what my system reads:
description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:0b:81:87:dc:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated

I did not understand the cd command very well. I opened the folder RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105 and placed mwdinstall.sh inside. Then I proceeded with bash mwdinstall.sh, but I am still not able to connect to the available networks.

---

### Post by kurt18947 on 2012-12-29
> **Kariotaki said:**
> Thanks for the advice BertN45, but I fear that I've done something wrong. After following the steps described, I still cannot get a wireless connection. 
Here is what my system reads:
description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:0b:81:87:dc:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated

I did not understand the cd command very well. I opened the folder RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105 and placed mwdinstall.sh inside. Then I proceeded with bash mwdinstall.sh, but I am still not able to connect to the available networks.

What does the command

```
lsmod
```show?  One of the lines should show '8192cu'.  If it shows 'rtl8192cu'  that's the 'native' driver and will not work properly.  You should not have to place anything in the extracted RTL* folder.  There should be a  'install.sh' already present.  That's the script I execute &  it runs correctly.  Here are the contents of my download from Realtek after being extracted.  I renamed the folder to make typing easier and less error prone.
[ATTACH]229291[/ATTACH]

You may have to blacklist any rtl related modules in order for the module created by executing the script (should be 8192cu) to drive your device.

---

### Post by Kariotaki on 2012-12-29
Although the Wi-Fi didn't work yesterday, when I turned on the computer today, it booted a bit funny and voila... it suddenly recognized the wireless connection. Thanks to all for your advice and guidance!

---

### Post by Kariotaki on 2013-02-23
Problem suddenly recurred. I believe there was a generic kernel update. 

I am trying to reinstall the mwdinstall.sh file but the computer is telling me that no such file or directory exists.

xristaras@xristaras-linux:~$ sudo bash mwdinstall.sh
bash: mwdinstall.sh: No such file or directory

The original file is located in my documents folder. I can see the install.sh and mwdinstall.sh files. Why won't the system recognize them?

Can anyone please help?

---

### Post by Kariotaki on 2013-02-23
Still no luck. Trying to follow the instructions but it doesn't look like the computer even recognizes the driver anymore. Can anyone help?

rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.rtw_wlan_util.o.d
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Makefile
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Kconfig
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
./install.sh: line 32: syntax error near unexpected token `then'
./install.sh: line 32: `fiif [ "`uname -r |grep fc`" == "" ]; then'
xristaras@xristaras-linux:~/Documents/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo bash mwdinstall.sh

This script (mwdinstall.sh) is to
    Install a Solwise NET-WL-UMD-606N mini wireless dongle on Ubuntu 12.04 or 12.10
Before use please list it (cat mwdinstall.sh) and read the commented (#...) lines.
Have you done so and are now in the directory with the driver package etc.? (y/n): y
Thank you

The script is provided in the hope that it will be helpful, but no liability for any consequenses of use can be accepted. You have been warned. Feel free to adapt and/or share it but please do not make any charge to others for it.

Do you understand and accept the above? (y/n): y
You agreed

For information: the running kernel is version 3.2.0-38
The real work now starts. It will take a while.
When asked to select the card, enter the digit 1
Do you want to continue? (y/n): y
You agreed

We will now blacklist a problematic driver that the OS tries to use
This will not take immediate effect - needs e.g. a reboot

We will now disable it by name change as it sometimes seems to pop up again!
mv: cannot stat `/lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko': No such file or directory

About to start the main install process. Reply with 1 when asked which chipset is being used.
The process takes a while and may display a warning message or two before completing.
These are probably only warnings which the script deals with.
If more drastic fail see the notes in this script.

##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
	rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105.tar.gz
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/clean
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.tmp_rtw_wlan_util.o
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.rtw_wlan_util.o.d
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Makefile
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Kconfig
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
install.sh: line 32: syntax error near unexpected token `then'
install.sh: line 32: `fiif [ "`uname -r |grep fc`" == "" ]; then'

Above should end with an encouraging message. If so ignore any
warning messages. Plug in the dongle if necessary and try it.
Be patient waiting for the initial connection.
If it fails try rebooting.
xristaras@xristaras-linux:~/Documents/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo mwdinstall.sh
sudo: mwdinstall.sh: command not found
xristaras@xristaras-linux:~/Documents/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo bash mwdinstall.sh

This script (mwdinstall.sh) is to
    Install a Solwise NET-WL-UMD-606N mini wireless dongle on Ubuntu 12.04 or 12.10
Before use please list it (cat mwdinstall.sh) and read the commented (#...) lines.
Have you done so and are now in the directory with the driver package etc.? (y/n): y
Thank you

The script is provided in the hope that it will be helpful, but no liability for any consequenses of use can be accepted. You have been warned. Feel free to adapt and/or share it but please do not make any charge to others for it.

Do you understand and accept the above? (y/n): y
You agreed

For information: the running kernel is version 3.2.0-38
The real work now starts. It will take a while.
When asked to select the card, enter the digit 1
Do you want to continue? (y/n): y
You agreed

We will now blacklist a problematic driver that the OS tries to use
This will not take immediate effect - needs e.g. a reboot

We will now disable it by name change as it sometimes seems to pop up again!
mv: cannot stat `/lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko': No such file or directory

About to start the main install process. Reply with 1 when asked which chipset is being used.
The process takes a while and may display a warning message or two before completing.
These are probably only warnings which the script deals with.
If more drastic fail see the notes in this script.

##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
	rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105.tar.gz
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/clean
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.tmp_rtw_wlan_util.o
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.rtw_wlan_util.o.d
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Makefile
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Kconfig
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
install.sh: line 32: syntax error near unexpected token `then'
install.sh: line 32: `fiif [ "`uname -r |grep fc`" == " " ]; then'

Above should end with an encouraging message. If so ignore any
warning messages. Plug in the dongle if necessary and try it.
Be patient waiting for the initial connection.
If it fails try rebooting.
xristaras@xristaras-linux:~/Documents/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$

---

### Post by Kariotaki on 2013-02-23
Sorry for the trouble folks,

Managed to fix it. Wireless internet works again.

Apparently, I had to edit the name of the mdwinstall.sh file and list it as cat mdwinstall.sh

I do not remember doing this the last time and this was creating confusion for me.

---

### Post by Kariotaki on 2013-02-25
Hi Folks,

You helped me get my Real Tek usb wireless dongle working back in December. I am having some trouble again so I am taking the liberty of reaching out to you.

After the latest kernel update, I lost all connectivity. I followed directions and tried to reinstall the mwdinstall.sh file. After much trouble, I managed to reinstall by clicking on the actual file (which I had to rename to cat mwd install.sh for some reason, as per the directions in the terminal, otherwise it wouldn't run). It works but only per session. I must repeat the same process each time I shut down. 

When I try to install it with the sudo bash command, I get the message posted below. Perhaps I am not opening the terminal properly. I am very new to Linux and am not familiar with how to change directories in the terminal...

I appreciate any help you could offer so I don't have to keep installing this script each time I start the computer. 

[COLOR="Blue"]xristaras@xristaras-linux:~$ sudo bash
root@xristaras-linux:~# '/home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/cat mwdinstall.sh' 

This script (mwdinstall.sh) is to
    Install a Solwise NET-WL-UMD-606N mini wireless dongle on Ubuntu 12.04 or 12.10
Before use please list it (cat mwdinstall.sh) and read the commented (#...) lines.
Have you done so and are now in the directory with the driver package etc.? (y/n): y
Thank you

The script is provided in the hope that it will be helpful, but no liability for any consequenses of use can be accepted. You have been warned. Feel free to adapt and/or share it but please do not make any charge to others for it.

Do you understand and accept the above? (y/n): y
You agreed

For information: the running kernel is version 3.2.0-38
The real work now starts. It will take a while.
When asked to select the card, enter the digit 1
Do you want to continue? (y/n): y
You agreed

We will now blacklist a problematic driver that the OS tries to use
This will not take immediate effect - needs e.g. a reboot

We will now disable it by name change as it sometimes seems to pop up again!
mv: cannot stat `/lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko': No such file or directory

About to start the main install process. Reply with 1 when asked which chipset is being used.
The process takes a while and may display a warning message or two before completing.
These are probably only warnings which the script deals with.
If more drastic fail see the notes in this script.

bash: install.sh: No such file or directory

Above should end with an encouraging message. If so ignore any
warning messages. Plug in the dongle if necessary and try it.
Be patient waiting for the initial connection.
If it fails try rebooting.
root@xristaras-linux:~# sudo bash '/home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/cat mwdinstall.sh' 

This script (mwdinstall.sh) is to
    Install a Solwise NET-WL-UMD-606N mini wireless dongle on Ubuntu 12.04 or 12.10
Before use please list it (cat mwdinstall.sh) and read the commented (#...) lines.
Have you done so and are now in the directory with the driver package etc.? (y/n): y
Thank you

The script is provided in the hope that it will be helpful, but no liability for any consequenses of use can be accepted. You have been warned. Feel free to adapt and/or share it but please do not make any charge to others for it.

Do you understand and accept the above? (y/n): y
You agreed

For information: the running kernel is version 3.2.0-38
The real work now starts. It will take a while.
When asked to select the card, enter the digit 1
Do you want to continue? (y/n): y
You agreed

We will now blacklist a problematic driver that the OS tries to use
This will not take immediate effect - needs e.g. a reboot

We will now disable it by name change as it sometimes seems to pop up again!
mv: cannot stat `/lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko': No such file or directory

About to start the main install process. Reply with 1 when asked which chipset is being used.
The process takes a while and may display a warning message or two before completing.
These are probably only warnings which the script deals with.
If more drastic fail see the notes in this script.

bash: install.sh: No such file or directory

Above should end with an encouraging message. If so ignore any
warning messages. Plug in the dongle if necessary and try it.
Be patient waiting for the initial connection.
If it fails try rebooting.

[/COLOR]

---

