---
title: "[SOLVED] freecom usb dvb-t"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by lightnin on 2008-11-23
Hello all

so - I've had 7.10 loaded for a few months now.  and I've been without my freeview since then !

I have a usb freecom dvb-t , its a few years old and works well in windoze.

I have folled a few guides to try and get it working in linux, but still no joy :(

How do I find out which revision I have so I know which drivers to get ?

when I plug it in to the usb port, the system log is updated as follows

```
kernel: [  301.915147] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware
NetworkManager: <debug> [1227453531.844986] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_14aa_222_noserial'). 
firmware_helper[6253]: main: error loading '/lib/firmware/dvb-usb-wt220u-02.fw' for device '/class/firmware/3-6' with driver 'usb'
kernel: [  301.976255] dvb-usb: did not find the firmware file. (dvb-usb-wt220u-02.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
NetworkManager: <debug> [1227453531.974017] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_14aa_222_noserial_if0'). 
NetworkManager: <debug> [1227453532.086131] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_14aa_222_noserial_usbraw'). 
```

so - it seems the firmware file cannot be found ?

what might I be doing wrong ?

Thanks

---

### Post by Michael.Godawski on 2008-11-23
You can download the missing fw file here:
[http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)

it is the last one on the page. Now I have to do some research what to do with this file.:)

---

### Post by Michael.Godawski on 2008-11-23
Ok 

try to save the file into this directory;

**/lib/firmware/dvb-usb-wt220u-02.fw**

---

### Post by lightnin on 2008-11-23
thanks - I think I have 4 different firmwares  , I'll copy them all and see what happens :0

---

### Post by lightnin on 2008-11-23
as easy as that hey !  I had the file, but it hadn't copied to the firmware directory. I used the sudo command to let me have permission, now the dvb-t tuner works :D

thank you

not to get kafeine working error - dvb - client .... cant bind info socket!!!

whatever that means :confused:

I'll mark this one solved and make another thread for that

Thanks again

---

### Post by madsmaddad on 2008-11-27
My Kaffeine gives that every time, but then goes on to work. 

I had to set up the DVB-Stick using a configuration system that I got from 
[http://www.chandlerfamily.org.uk/files/firmware/](http://www.chandlerfamily.org.uk/files/firmware/)    

Have included instructions below. 

Then: 
sudo cp dvb-usb-wt220u-fc03 /lib/firmware/$(uname -r)/ 
And follow instructions here; 
[http://www.ubuntuforums.org/showthread.php?t=183297](http://www.ubuntuforums.org/showthread.php?t=183297) 
Ignoring first two lines, start from: 
sudo apt-get install build-essential 
Reboot, and the light should appear on USB stick 
stick. 
Install Kaffeine, if not already in installed 
and dvb-utils, open Kaffeine, choose DVB/Source 
Auto, if not supported, turn over rollover bar and 
choose you transmitter, 

The "antenna" provided is not a lot of good but with 
a normal indoor TV antennea I receive all free to air 
DVB channels and radio stations, Kaffeine also gives you 
a record facility  

And when you get a kernel upgrade, repeat all the process again!!! 
---------------------------------------------------

Just reinstalled under KDE Bianca 

The line sudo cp dvb-usb-wt220u-fc03.... 
Should read sudo cp dvb-usb-wt220u-fc03.fw... 

Alll references to dvb-usb-wt220u-fc03 should be 
dvb-usb-wt220u-fc03.fw 

In the Ubuntu link [http://ubuntuforums.org/showthread.php?t=183297](http://ubuntuforums.org/showthread.php?t=183297) 

Where is says "make install" this should be done as root 

i.e. sudo make install 

Also with new kernel, disconnect usb stick after compiling, and then plug in after reboot. 



Instructions from link above. 

You need to copy this to the firmware directory: 
Code:
sudo cp dvb-usb-wt220u-zl0353-01.fw /lib/firmware/$(uname -r)/
If you haven't already done so you need to install the application to allow you to build the modular driver for the freecom. First: 
Code:
sudo apt-get install build-essential
You will also need the tool to allow you to download the latest Video4Linux / DVB source: 
Code:
sudo apt-get install mercurial
and then you need the kernel headers: 
Code:
sudo apt-get install linux-headers-$(uname -r)
You will need to grab the v4l/dvb source: 
Code:
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
This will download the source to a new directory in your home folder, change to that directory: 
Code:
cd v4l-dvb
Now for the 'make' part, you need to configure the source for compilation: 
Code:
make config
You will then be asked a list of questions on how to configure the source, answer as follows. 
Code:
#
# using defaults found in .config
#
*
* Linux Kernel Configuration
*
*
* Multimedia devices
*
Video For Linux (VIDEO_DEV) [N/m/y/?] n
*
* Digital Video Broadcasting Devices
*
DVB For Linux (DVB) [Y/n/?] y
  DVB Core Support (DVB_CORE) [N/m/y/?] m
    *
    * Supported SAA7146 based PCI Adapters
    *
    *
    * Supported USB Adapters
    *
    Support for various USB DVB devices (DVB_USB) [N/m/?] (NEW) m
      Enable extended debug support for all DVB-USB devices (DVB_USB_DEBUG) [N/y/?] (NEW) n
      AVerMedia AverTV DVB-T USB 2.0 (A800) (DVB_USB_A800) [N/m/?] (NEW) n
      DiBcom USB DVB-T devices (based on the DiB3000M-B) (see help for device list) (DVB_USB_DIBUSB_MB) [N/m/?] (NEW) n
      DiBcom USB DVB-T devices (based on the DiB3000M-C/P) (see help for device list) (DVB_USB_DIBUSB_MC) [N/m/?] (NEW) n
      HanfTek UMT-010 DVB-T USB2.0 support (DVB_USB_UMT_010) [N/m/?] (NEW) n
      Conexant USB2.0 hybrid reference design support (DVB_USB_CXUSB) [N/m/?] (NEW) n
      Nebula Electronics uDigiTV DVB-T USB2.0 support (DVB_USB_DIGITV) [N/m/?] (NEW) n
      TwinhanDTV Alpha/MagicBoxII, DNTV tinyUSB2, Beetle USB2.0 support (DVB_USB_VP7045) [N/m/?] (NEW) n
      TwinhanDTV StarBox and clones DVB-S USB2.0 support (DVB_USB_VP702X) [N/m/?] (NEW) n
      GENPIX 8PSK->USB module support (DVB_USB_GP8PSK) [N/m/?] (NEW) n
      Hauppauge WinTV-NOVA-T usb2 DVB-T USB2.0 support (DVB_USB_NOVA_T_USB2) [N/m/?] (NEW) n
      WideView WT-200U and WT-220U (pen) DVB-T USB2.0 support (Yakumo/Hama/Typhoon/Yuan) (DVB_USB_DTT200U) [N/m/?] (NEW) m
    Technotrend/Hauppauge Nova-USB devices (DVB_TTUSB_BUDGET) [N/m/?] (NEW) n
    Technotrend/Hauppauge USB DEC devices (DVB_TTUSB_DEC) [N/m/?] (NEW) n
    Terratec CinergyT2/qanu USB2 DVB-T receiver (DVB_CINERGYT2) [N/m/?] (NEW) n
    *
    * Supported FlexCopII (B2C2) Adapters
    *
    Technisat/B2C2 FlexCopII(b) and FlexCopIII adapters (DVB_B2C2_FLEXCOP) [N/m/?] (NEW) n
    *
    * Supported BT878 Adapters
    *
    *
    * Supported Pluto2 Adapters
    *
    Pluto2 cards (DVB_PLUTO2) [N/m/?] (NEW) n
    *
    * Supported DVB Frontends
    *
    *
    * Customise DVB Frontends
    *
    *
    * DVB-S (satellite) frontends
    *
    ST STV0299 based (DVB_STV0299) [N/m/?] (NEW) n
    Conexant CX24110 based (DVB_CX24110) [N/m/?] (NEW) n
    Conexant CX24123 based (DVB_CX24123) [N/m/?] (NEW) n
    Philips TDA8083 based (DVB_TDA8083) [N/m/?] (NEW) n
    Zarlink VP310/MT312 based (DVB_MT312) [N/m/?] (NEW) n
    VLSI VES1893 or VES1993 based (DVB_VES1X93) [N/m/?] (NEW) n
    Samsung S5H1420 based (DVB_S5H1420) [N/m/?] (NEW) n
    *
    * DVB-T (terrestrial) frontends
    *
    Spase sp8870 based (DVB_SP8870) [N/m/?] (NEW) n
    Spase sp887x based (DVB_SP887X) [N/m/?] (NEW) n
    Conexant CX22700 based (DVB_CX22700) [N/m/?] (NEW) n
    Conexant cx22702 demodulator (OFDM) (DVB_CX22702) [N/m/?] (NEW) n
    LSI L64781 (DVB_L64781) [N/m/?] (NEW) n
    Philips TDA10045H/TDA10046H based (DVB_TDA1004X) [N/m/?] (NEW) n
    NxtWave Communications NXT6000 based (DVB_NXT6000) [M/?] (NEW) n
    Zarlink MT352 based (DVB_MT352) [M/?] (NEW) m
    Zarlink ZL10353 based (DVB_ZL10353) [N/m/?] (NEW) m
    DiBcom 3000M-B (DVB_DIB3000MB) [N/m/?] (NEW) n
    DiBcom 3000P/M-C (DVB_DIB3000MC) [N/m/?] (NEW) n
    *
    * DVB-C (cable) frontends
    *
    VLSI VES1820 based (DVB_VES1820) [N/m/?] (NEW) n
    Philips TDA10021 based (DVB_TDA10021) [N/m/?] (NEW) n
    ST STV0297 based (DVB_STV0297) [N/m/?] (NEW) n
    *
    * ATSC (North American/Korean Terrestrial/Cable DTV) frontends
    *
    NxtWave Communications NXT2002/NXT2004 based (DVB_NXT200X) [N/m/?] (NEW) n
    Oren OR51211 based (DVB_OR51211) [N/m/?] (NEW) n
    Oren OR51132 based (DVB_OR51132) [N/m/?] (NEW) n
    Broadcom BCM3510 (DVB_BCM3510) [N/m/?] (NEW) n
    LG Electronics LGDT3302/LGDT3303 based (DVB_LGDT330X) [N/m/?] (NEW) n
    *
    * Miscellaneous devices
    *
    LNBP21 SEC controller (DVB_LNBP21) [N/m/?] (NEW) n
    ISL6421 SEC controller (DVB_ISL6421) [N/m/?] (NEW) n
DABUSB driver (USB_DABUSB) [N/m/?] n
now we can build the kernel modules 
Code:
make
and install them 
Code:
make install
after this is done you should reboot the machine, plug in your freecom and you are ready to go. I used kaffine to test my card and it works pefectly. Im getting a strong signal from the SedburyB transmitter, even though Im in South Wales and using a cheapo aerial from B&Q in my loft!! (If anyone has proper frequency files for Wenvoe and Mendip I would be very grateful).

---

