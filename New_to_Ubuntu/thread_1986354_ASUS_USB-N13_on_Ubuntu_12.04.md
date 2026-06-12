---
title: "ASUS USB-N13 on Ubuntu 12.04"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by stanifem on 2012-05-24
I'm completely new to installing in Ubuntu. I know very little terminal language.
When I plug in my Asus I can connect to a network, but the internet won't load anything. My ethernet is also broken so I have no network access on my computer until I get this resolve. I tried using wine to install the windows stuff and it crashed. I tried using lsusb and other such stuff. I'm not sure what the problem is.
anyone got any help.
thanks

---

### Post by lilmagnus on 2012-05-24
Welcome **stanifem**! Enjoy your stay!

Please check the following links for additional help. Apparently there are actually two different wireless chipsets in this adapter. Depends on which chipset as to which driver and set of instructions will work.

[http://ubuntuforums.org/showthread.php?t=1936246](http://ubuntuforums.org/showthread.php?t=1936246)
[http://ubuntuforums.org/showthread.php?p=11716409](http://ubuntuforums.org/showthread.php?p=11716409)

---

### Post by nidor on 2012-06-22
I've done a lot of search for the last 2 monthes and finally get the USB-N13 dongle work on 12.04!

Here's how:

1. Find the correct chipset of  your USB-N13 dongle. Mine is RT3072.
```

$ lsusb
Bus 002 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT3072]

```2. Download the corresponding driver from Ralink website. In this case, go to [URL="http://%3Cbr%20/%3E%0A%3Ca%20href=%22http://www.ralinktech.com/en/04_support/support.php?sn=501%22%20target=%22_blank%22%3Ehttp://www.ralinktech.com/en/04_support/support.php?sn=501%3C/a%3E"] 
[/URL][COLOR=DarkOrange][http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)[/COLOR] and download **RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB**

3. Untar the downloaded driver
```

$ cd Downloads/
$ tar -jxvf 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2

```Verify if the driver fits our chipset.
```

$ cd ~/Download/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/common/
$ cat rtusb_dev_id.c | grep Asus
    {USB_DEVICE(0x0B05,0x1784)}, /* Asus 3072 */

```The PID/VID fit what we found with lsusb in step 1.

4. Remove rt2800usb driver
```

$ sudo modprobe -r rt2800usb

```5. Prevent rt2800usb from loading after boot up (Any text editor will do. If you prefer gedit, just replace **vi** with **gedit**)
```

$ sudo vi /etc/modprobe.d/blacklist.conf

```add the following lines to this file
```

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

```6. Edit settings for WPA and Network Manager to work (Any text editor will do. If you prefer gedit, just replace **vi** with **gedit**)
```

$ cd ~/Download/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/
$ vi config.mk

```find the following part and change the 2 values from **n** to **y**
```

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=**y**


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**y**

```7. Make and install
```

$ cd ~/Download/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/
$ sudo make && sudo make install

```8. Reboot

9. It should work after reboot. You can use Network Manager to connect to your AP now.

10. You can check the driver status with the following commands
```

$ lsmod | grep rt5370
rt5370sta             730263  1 

$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:149550 (149.5 KB)  TX bytes:149550 (149.5 KB)

ra0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:feb1:72d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:284538040 (284.5 MB)  TX bytes:104338039 (104.3 MB)

$ iwconfig
lo        no wireless extensions.

ra0       Ralink STA  ESSID:"Your-AP-SSID"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: BC:AE:C5:C3:98:B1   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=83/100  Signal level:-52 dBm  Noise level:-76 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```Now I get steady 270Mb/s connection with **rt5370sta** (what we get after installation) to an AP of WPA2 security, instead of unstable 54Mb/s connection with** rt2800usb** driver which comes with 12.04.

I'm more than happy to share this information to this community. If you bumped into the same trouble I've been through, I wish this thread will be helpful to you.

---

### Post by Xpression28 on 2012-06-24
@nidor What directory are you in when you run the sudo make && sudo make install command?

---

### Post by nidor on 2012-06-25
> **Xpression28 said:**
> @nidor What directory are you in when you run the sudo make && sudo make install command?

@Xpression28, sorry I missed that. The directory is :
~/Download/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/

---

### Post by AnalogArsonist on 2012-06-30
Hi,

I'm using Debian and I have this same network adapter that continually logs on then logs off my network at a rate of about 1Hz. It looks like it's dropping RX packets but feels like a driver issue. Anyway I found your tutorial (thanks!) but I'm having a little trouble.

When I get to the make && make install section I get an error:

make -C /lib/modules/3.1.9+/build SUBDIRS=/boot/firmware/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux modules

make: *** /lib/modules/3.1.9+/build: No such file or directory. Stop.

make: *** [LINUX] Error 2

So, I manually created the directory so it gets one step further but now it give this error:

make[1]: Entering directory '/lib/modules/3.1.9+/build'
make[1]: *** No rule to make target 'modules'. Stop.
make[1]: Leaving directory '/lib/modules/3.1.9+/build'
make: *** [LINUX] Error 2

I also get some warnings saying makefile modification time is in the future because my system time is not set but not sure that has anything to do with it.

Do you understand what's going on? I sure don't! :confused:

Thanks, Ben

---

### Post by nidor on 2012-07-04
AnalogArsonist,

I'm not familiar with Debian. After googling for a while, I found that many people talking about these error messages in RPi forum.

[http://www.raspberrypi.org/phpBB3/viewtopic.php?f=66&t=6737&start=25](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=66&t=6737&start=25)

Wish you good luck!

---

### Post by AnalogArsonist on 2012-07-07
Hi again,

I was able to get the linux headers installed after some research. Then I followed your steps but I was getting a warning like this during the compile:

WARNING: Symbol version dump /lib/modules/3.1.9+/build/Module.symvers
	is missing; modules will have no dependencies and modversion s.

This prevented the module from loading properly and I was seeing this from dmesg and lsprobe, respectively:

rt5370sta: no symbol version for module_layout

FATAL: Error inserting rt5370sta (/lib/modules/3.1.9+/kernel/drivers/net/wireless/rt5370sta.ko): Invalid module format

So after some more research, I learned I needed to add the step 'make vmlinux' after the 'make_prepare' step. The module now appears to load and shows up in ifconfig. Hoping this might help.

Thanks, Ben

---

### Post by nidor on 2012-07-23
After a "Recommended Update" of linux kernel to 3.2.0-27-generic-pae, the magic trick failed... Missing those short happy days with a working WiFi dongle...

---

### Post by nidor on 2012-07-25
Don't know what went wrong, but I got it fixed by simply rebooting the AP, which is also an ASUS product, RT-N16.

The magic trick works still.

---

### Post by thinkpad20 on 2012-10-24
I recently received this guy, which I bought specifically because it was supposed to work with Linux, only to plug it in and... nothing](*,) So I'm trying to install the drivers (meaning I have to haul my desktop computer over to sit next to my wireless router). I was following the instructions laid out in [url = http://askubuntu.com/questions/168627/connecting-asus-usb-n13-wireless-adapter]this stack overflow question[/url], which is almost exactly the same as my situation. I followed the instructions there to the letter and got to the step where I run:

$ sudo bash install.sh
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/hal_init.c
[...truncated for space...]
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
cd cmd ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd crypto ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd debug ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd eeprom ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8712 ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd io ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd ioctl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mlme ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mp ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd pwrctrl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd recv ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd rf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd sta_mgt ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd xmit; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd efuse; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.2.0-23-generic/build M=/home/thinkpad20/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  CC [M]  /home/thinkpad20/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o
In file included from 

[truncated again...]

[_module_/home/thinkpad20/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'

So, an obscure "Error 2" derailed my installation. Any ideas?

---

