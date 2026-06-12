---
title: "Howto: Working Nebula Digitv USB DVB-T receiver in Ubuntu 6.06 LTS"
date: 2006-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by polling on 2006-06-17
This howto describes how you can get your **Nebula uDigiTV USB** working with **Ubuntu 6.06 LTS**. It is an updated version of the howto that I posted in the Dapper Drake development forums. The instructions below have been tested and confirmed working on Ubuntu 6.06 LTS on 17th June 2006 using the latest 2.6.15-25-686 kernel.

[SIZE="5"]Problem[/SIZE]
The new Ubuntu 2.6.15 kernel ships with support for the Nebula usb device. However, it does not come with a Nebula firmware so you can't get a Nebula that's in cold-state (no firmware loaded) working. After installing the firmware, the Nebula Digitv module will still crash :( . Even when you connect a Nebula with a firmware already loaded (it is in warm-state), the Ubuntu shipped driver does not attach a frontend to it, making the device pretty useless ](*,) :

 	```
dvb-usb: found a 'Nebula Electronics uDigiTV DVB-T USB2.0)' in warm state.
	dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
	DVB: registering new adapter (Nebula Electronics uDigiTV DVB-T USB2.0)).
	dvb-usb: no frontend was attached by 'Nebula Electronics uDigiTV DVB-T USB2.0)'
	input: IR-receiver inside an USB DVB receiver as /class/input/input5
	dvb-usb: schedule remote query interval to 1000 msecs.
	dvb-usb: Nebula Electronics uDigiTV DVB-T USB2.0) successfully initialized and connected.
	usbcore: registered new driver dvb_usb_digitv
```

*So how do we solve this problem without much effort?* Well, continue reading below as I've managed to get my **Nebula uDigiTV USB working perfectly** on Ubuntu 6.06 LTS! The only thing it involves is recompiling the Nebula's kernel modules using the latest Video4Linux/DVB-T source.

[SIZE="5"]Resolution[/SIZE]

All commands below are assumed to be executed in a terminal from your home directory (unless otherwise stated).

First, download the latest Nebula firmware for Linux. This is from Patrick Boettcher, the guy who was kind enough to write most of the Nebula's Linux drivers last year.
	```
wget http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-digitv-02.fw

```
Copy the firmware to your kernel's firmware directory:
	```
sudo cp dvb-usb-digitv-02.fw /lib/firmware/$(uname -r)/
```

Install the Ubuntu build essentials (as we need to compile updated Nebula modules):
	```
sudo apt-get install build-essential
```

Install the kernel headers for your kernel:
	```
sudo apt-get install linux-headers-$(uname -r)
```

Install Mercurial (a version control tool to download the latest Video4Linux/DVB source):
	```
sudo apt-get install mercurial
```

Still in your home directory download the Video4Linux/DVB-T source:
 	```
hg clone http://linuxtv.org/hg/v4l-dvb
```

Now go into the downloaded directory:
	```
cd v4l-dvb
```

And configure how the v4l-dvb source compiles:
	```
make config
```
**Note:** if it comes up with errors on 'make config', you most likely need to install some additional bits and pieces to get the kernel to compile. Have a look at the output of 'make config' to see what's missing.

The 'make config' will ask you how to configure the Video4Linux/DVB-T source. Answer as follows:

```
#
# using defaults found in .config
#
*
* Linux Kernel Configuration
*
Enable drivers not supported by this kernel (VIDEO_KERNEL_VERSION) [N/y/?] (NEW)  n
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
      Nebula Electronics uDigiTV DVB-T USB2.0 support (DVB_USB_DIGITV) [N/m/?] (NEW) m
      TwinhanDTV Alpha/MagicBoxII, DNTV tinyUSB2, Beetle USB2.0 support (DVB_USB_VP7045) [N/m/?] (NEW) n
      TwinhanDTV StarBox and clones DVB-S USB2.0 support (DVB_USB_VP702X) [N/m/?] (NEW) n
      GENPIX 8PSK->USB module support (DVB_USB_GP8PSK) [N/m/?] (NEW) n
      Hauppauge WinTV-NOVA-T usb2 DVB-T USB2.0 support (DVB_USB_NOVA_T_USB2) [N/m/?] (NEW) n
      WideView WT-200U and WT-220U (pen) DVB-T USB2.0 support (Yakumo/Hama/Typhoon/Yuan) (DVB_USB_DTT200U) [N/m/?] (NEW) n
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
    NxtWave Communications NXT6000 based (DVB_NXT6000) [M/?] (NEW) m
    Zarlink MT352 based (DVB_MT352) [M/?] (NEW) m
    Zarlink ZL10353 based (DVB_ZL10353) [N/m/?] (NEW) n
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
```

Now type the following to start the build process:
	```
make

```
When completed install the modules with the following command:
	```
sudo make install
```
Reboot your machine and plug-in your Nebula USB device. If you do a 'dmesg' in a terminal it should come up with something like:

```
	dvb-usb: found a 'Nebula Electronics uDigiTV DVB-T USB2.0)' in cold state, will try to load a firmware
	dvb-usb: downloading firmware from file 'dvb-usb-digitv-02.fw'
	usb 4-3.1: USB disconnect, address 6
	dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
	usb 4-3.1: new high speed USB device using ehci_hcd and address 7
	usb 4-3.1: string descriptor 0 read error: -22
	usb 4-3.1: string descriptor 0 read error: -22
	dvb-usb: found a 'Nebula Electronics uDigiTV DVB-T USB2.0)' in warm state.
	dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
	DVB: registering new adapter (Nebula Electronics uDigiTV DVB-T USB2.0)).
	DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
	input: IR-receiver inside an USB DVB receiver as /class/input/input6
	dvb-usb: schedule remote query interval to 1000 msecs.
	dvb-usb: Nebula Electronics uDigiTV DVB-T USB2.0) successfully initialized and connected.
```

As you can see it now has a frontend attached and you're ready to start using your Nebula uDigiTV USB :D ! If your driver still does not register the frontend, try unplugging the Nebula for more than half a minute to get it into a cold state, then plug it back in again.

[I]**Note**: First see if you can get your Nebula working with the latest version of the Video4Linux/DVB-T source. If this does not work (new changesets might have broken Nebula support), you can try reverting to the version I used to write this howto by executing the following command in your v4l-dvb directory before 'make config':

```
hg revert -r 4103  
```

This will revert the repository to changeset 4103 that I used when writing this howto.[/I]

---

### Post by StolenNomenclature on 2006-08-25
When I try to obtain the firmware, i get:

barny@barny-desktop:~$ wget [http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-digitv-02.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-digitv-02.fw)
--10:02:35--  [http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-digitv-02.fw](http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-digitv-02.fw)
           => `dvb-usb-digitv-02.fw'
Resolving [www.wi-bw.tfh-wildau.de](www.wi-bw.tfh-wildau.de)... 194.95.44.33
Connecting to www.wi-bw.tfh-wildau.de|194.95.44.33|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:02:41 ERROR 404: Not Found.

Has he moved or perhaps the server is just down?

When I try the make, i get:

barny@barny-desktop:~/v4l-dvb$ make
make -C /home/barny/v4l-dvb/v4l
make[1]: Entering directory `/home/barny/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-26-386/build
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/barny/v4l-dvb/v4l'
make[1]: Entering directory `/home/barny/v4l-dvb/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-26-386/build
creating symbolic links...
echo srcdir
srcdir
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/barny/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /home/barny/v4l-dvb/v4l/tvmixer.o
/home/barny/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_ioctl':
/home/barny/v4l-dvb/v4l/tvmixer.c:90: error: storage size of 'va' isn't known
/home/barny/v4l-dvb/v4l/tvmixer.c:126: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/barny/v4l-dvb/v4l/tvmixer.c:126: error: (Each undeclared identifier is reported only once
/home/barny/v4l-dvb/v4l/tvmixer.c:126: error: for each function it appears in.)
/home/barny/v4l-dvb/v4l/tvmixer.c:141: error: 'VIDEO_AUDIO_BASS' undeclared (first use in this function)
/home/barny/v4l-dvb/v4l/tvmixer.c:143: error: 'VIDEO_AUDIO_TREBLE' undeclared (first use in this function)
/home/barny/v4l-dvb/v4l/tvmixer.c:154: error: 'VIDEO_AUDIO_MUTE' undeclared (first use in this function)
/home/barny/v4l-dvb/v4l/tvmixer.c:155: error: 'VIDIOCSAUDIO' undeclared (first use in this function)
/home/barny/v4l-dvb/v4l/tvmixer.c:159: warning: type defaults to 'int' in declaration of '_x'
/home/barny/v4l-dvb/v4l/tvmixer.c:161: warning: type defaults to 'int' in declaration of '_x'
/home/barny/v4l-dvb/v4l/tvmixer.c:161: warning: comparison of distinct pointer types lacks a cast
/home/barny/v4l-dvb/v4l/tvmixer.c:90: warning: unused variable 'va'
/home/barny/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_clients':
/home/barny/v4l-dvb/v4l/tvmixer.c:297: error: storage size of 'va' isn't known
/home/barny/v4l-dvb/v4l/tvmixer.c:343: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/barny/v4l-dvb/v4l/tvmixer.c:345: error: 'VIDEO_AUDIO_VOLUME' undeclared (first use in this function)
/home/barny/v4l-dvb/v4l/tvmixer.c:297: warning: unused variable 'va'
make[3]: *** [/home/barny/v4l-dvb/v4l/tvmixer.o] Error 1
make[2]: *** [_module_/home/barny/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/barny/v4l-dvb/v4l'
make: *** [all] Error 2

Any ideas? I am assuming this stage is not dependent on the firmware, which as you see i did not get.

Thanks.

---

### Post by StolenNomenclature on 2006-08-25
Can you or anyone explain why no distro ever seems to properly support DVB? There are always lots of bits missing. Wny should we have to recompile the kernel to obtain this support?

DVB should be available to all user of Linux, not just kernel hackers and IT specialists. 

I dont have to recompile the kernel to run Open Office, so why to watch DVB?

DVB has been around for years - i fear that by the time Linux gets support for it, it will be replaced by some other technology.

---

### Post by StolenNomenclature on 2006-08-25
After trying to follow your instructions with Ubuntu and failing, I rebooted to my Debian Etch installation, which uses a 2.6.16 kernel. Dmesg showed not only the detection of the tuner in a warm state, but attached the drivers and all the other stuff.

Fired up Synaptic and installed Kaffeine. Kaffeine detected the tuner, so I tried the channel scan. All the channels (in Australia) were detected.

I am now watching digital TV under Linux for the first time.

And didnt have to compile anything!

If only there was a Gnome app instead of having to use KDE.

---

### Post by mons on 2006-09-14
I have been watching TV with my Nebula USB for a while now using Kaffine mostly, but also MPlayer.

I can't get the remote control to work.  Does anyone know it is possible, and if so how?

---

### Post by StolenNomenclature on 2006-10-02
Can I ask which version of the tuner you have? Is it the early version, the one with a curved front?

If so, do you know what the name of the firmware file is that you use and where it is put?

Many thanks,

:cool:

---

### Post by mons on 2006-10-03
Hi,
Slightly curved front, yes.  There's no model number that I can see.  Only the name: digiTV USB 2.0.
I have the firmware under /lib/firmware/2.6.15-26-k7: dvb-usb-digitv-02.fw

Since posting this I have managed to get the volum control and the direct channel selection (actual channel, not ch+ and -) to work in Kaffeine.  Nothing else though.

In order to delete my XP partition I need the EPG and the rest of the buttons too :-)

Would be great if that was possible...


Mons

---

### Post by StolenNomenclature on 2006-10-04
Thanks for responding.

You say "slightly curved" - well maybe that sounds like the newer one. I didnt realise that the front of the new one is also curved - i thought it was straight.

Can you confirm if yours is the unit being displayed on the home page of the [http://www.nebula-electronics.com/](http://www.nebula-electronics.com/) web site? If so its the newer one.

Also, my version has a plug pack mains power supply, whearas I believe the new version gets its power from the usb port, so there is no external mains supply.

Thanks

---

### Post by mons on 2006-10-05
Hi,
Yes, it's the one on the picture with no other power supply other then the usb port itself, so yes, don't think there is any newer one yet.

How does the remote control for digiTV work anyway?  I mean, is the configuration hardcoded in the v4l dvb driver or is there a configuration file somewhere?

Mons

---

### Post by StolenNomenclature on 2006-10-18
Thanks.

Looks like im the only person in the whole world who bought the first one. You always get shat on by the companies when you buy their prototype units. Three times the price and half as good.

IT may not be bright yellow in colour but it sure is a lemon.

Sorry but cant help about the remote. No idea.

---

### Post by rknight73 on 2007-01-02
***************** THIS SOLUTION HAS BEEN TESTED ON EDGY EFT ONLY *****************

Working out how to configure the USB DIGITV remote control with the v4l-dvb drivers took me an age!!! There are all sorts of posts on the internet regarding ir-common and lirc which led me down the wrong path. On my system there is no ir-common module loaded and no bttv etc. modules. This solution does NOT use lirc either.

I am using Edgy Eft and the latest v4l-dvb drivers cloned from the linuxtv repository as described in the top post in this thread. I have the Nebula Electronics uDigiTV DVB-T USB2.0 receiver and the 55 key remote control.

Follow the steps in the top post and complete the make config stage.

Now go to the 

v4l-dvb/linux/drivers/media/dvb/dvb-usb directory

and open the digitv.c file in a text editor.

Scroll down until you find the following struct:

static struct dvb_usb_rc_key digitv_rc_keys[] = {
        { 0x5f, 0x55, KEY_0 },
        { 0x6f, 0x55, KEY_1 },
        { 0x9f, 0x55, KEY_2 },
        { 0xaf, 0x55, KEY_3 },
        { 0x5f, 0x56, KEY_4 },
        { 0x6f, 0x56, KEY_5 },
        { 0x9f, 0x56, KEY_6 },
        { 0xaf, 0x56, KEY_7 },
        { 0x5f, 0x59, KEY_8 },
        { 0x6f, 0x59, KEY_9 },
        { 0x9f, 0x59, KEY_TV },
        { 0xaf, 0x59, KEY_AUX },
        { 0x5f, 0x5a, KEY_DVD },
        { 0x6f, 0x5a, KEY_POWER },
        { 0x9f, 0x5a, KEY_MHP },     /* labelled 'Picture' */
        { 0xaf, 0x5a, KEY_AUDIO },
        { 0x5f, 0x65, KEY_F13 },
        { 0x6f, 0x65, KEY_INFO },     /* 16:9 */
        { 0x9f, 0x65, KEY_F14 },     /* 14:9 */
        { 0xaf, 0x65, KEY_E },
        { 0x5f, 0x66, KEY_EXIT },
        { 0x6f, 0x66, KEY_MENU },
        { 0x9f, 0x66, KEY_UP },
        { 0xaf, 0x66, KEY_DOWN },
        { 0x5f, 0x69, KEY_LEFT },
        { 0x6f, 0x69, KEY_RIGHT },
        { 0x9f, 0x69, KEY_ENTER },
        { 0xaf, 0x69, KEY_CHANNELUP },
        { 0x5f, 0x6a, KEY_CHANNELDOWN },
        { 0x6f, 0x6a, KEY_VOLUMEUP },
        { 0x9f, 0x6a, KEY_VOLUMEDOWN },
        { 0xaf, 0x6a, KEY_RED },
        { 0x5f, 0x95, KEY_GREEN },
        { 0x6f, 0x95, KEY_YELLOW },
        { 0x9f, 0x95, KEY_BLUE },
        { 0xaf, 0x95, KEY_SUBTITLE },
        { 0x5f, 0x96, KEY_F15 },     /* AD */
        { 0x6f, 0x96, KEY_TEXT },
        { 0x9f, 0x96, KEY_MUTE },
        { 0xaf, 0x96, KEY_REWIND },
        { 0x5f, 0x99, KEY_STOP },
        { 0x6f, 0x99, KEY_PLAY },
        { 0x9f, 0x99, KEY_FASTFORWARD },
        { 0xaf, 0x99, KEY_F16 },     /* chapter */
        { 0x5f, 0x9a, KEY_PAUSE },
        { 0x6f, 0x9a, KEY_PLAY },
        { 0x9f, 0x9a, KEY_RECORD },
        { 0xaf, 0x9a, KEY_F17 },     /* picture in picture */
        { 0x5f, 0xa5, KEY_KPPLUS },  /* zoom in */
        { 0x6f, 0xa5, KEY_KPMINUS }, /* zoom out */
        { 0x9f, 0xa5, KEY_F18 },     /* capture */
        { 0xaf, 0xa5, KEY_F19 },     /* web */
        { 0x5f, 0xa6, KEY_EMAIL },
        { 0x6f, 0xa6, KEY_PHONE },
        { 0x9f, 0xa6, KEY_PC },
};

(I've hacked around with this struct so it isn't quite the same as the original)

Now all you have to do is modify the KEY_ entry to whatever keyboard key you want the remote button to emulate. The KEY_ entries are mainly set to show which buttons they relate to on the remote. e.g. 0xaf, 0x95, KEY_SUBTITLE is the SubT button on the remote. 

However Ubuntu doesn't know what KEY_SUBTITLE means so you either have to define KEY_SUBTITLE to mean something to Ubuntu (I have no idea how you do this - via some keymap program?) or change KEY_SUBTITLE to a mapping that Ubuntu does understand.

e.g. I use the remote for mythtv and have changed KEY_EXIT to KEY_ESC (I guessed that this was the Ubuntu code for the Escape key!). Now when I press the exit button on the digitv remote the Escape key is emulated in Ubuntu. Use xev to track keypresses.  

Change all of the keys that you want to in the above struct and then save the file. One other useful entry I found in digitv.c was:

.rc_interval      = 1000

This sets the interval between keypresses for the remote. Currently this is 1000ms and is a little slow for my taste. For mythtv I found that a value of around 300 worked well. 

Follow the rest of the stages in the top post in this thread (make and make install) and reboot the machine.

I am no linux guru so this may be a bit of a hack but I hope it helps.

---

### Post by Köntzä on 2007-01-04
Is there really need for reboot after 'make install'?

I managed to get the newly made Nebula driver into use by first unloading the old module from the kernel with ```
sudo modprobe -r dvb-usb-digitv
```

Then I loaded the new module with ```
modprobe -r dvb-usb-digitv
```


**About editing digitv.c:**
From what I understood by looking at Linux's header file input.h, KEY_EXIT, KEY_TV, etc. are for those funky multimedia keyboards that have keys for those types of functionalities. I don't think there really is a need to edit this file, apart from changing the .rc_interval.

There was no life in the remote control until I updated the driver into the latest v4ldvb has to offer. I ran xev and was happy to see that most keys of the remote were identified. There was a problem, though: Ubuntu captured remote's power key and prompted me for a shutdown. And many keys were left entirely without an event.

While struggling to get the remote working (prior to updating the Nebula driver) I had tried a small daemon on offer at Ubuntu's repositories: inputlirc. This little daemon reads input from /dev/input/eventN (where N is a digit), and 'writes' it out on /dev/lircd. LIRC MUST NOT BE RUNNING ON THE SYSTEM, it won't coexist with inputlirc (AFAIK), but /dev/lircd has to exist. My remote control is on /dev/input/event3. What happens if it's on some other location? Event5? Starting inputlircd from /etc/init.d/inputlirc using /etc/default/inputlirc's defaults won't work...

Then I remembered how during my R/C struggles I had bumped into Garry Parker's Ubuntu/MythTV tips. He instructs how to make sure that a /dev/input-remote control has a static name. (See [his article]("http://parker1.co.uk/mythtv_tips.php"), look for 'Make the LIRC Device Static'.) To define a static name for the Nebula remote control my /etc/udev/rules.d/10-local.rules looks like this: ```
KERNEL=="event*",SYSFS{name}=="IR-receiver inside an USB DVB receiver",SYMLINK="input/irremote"
```

To match inputlirc and /dev/event/irremote, I edited /etc/default/inputlirc to look like the following:
```
EVENTS="/dev/input/irremote"
OPTIONS="-g -m 1"
```
EVENTS instruct inputlirc to use /dev/input/irremote as input. -g tells it to grab the events, and not to let them propagate through the rest of the system. -m 1 tells it to let through all events. Without option -m you won't get, e.g. keys 0-9 through.

I used Lirc packages irw app to verify that inputlirc transferred successfully the input event into /dev/lircd.

My current problem, after applying the tweaks related to inputlirc, is that VDR doesn't recognise keys 0-9, up-key, and some other keys. Does anyone have a comment as how to fix it?

---

### Post by rknight73 on 2007-01-04
OK I concede you don't have to reboot but that 45secs wasn't a big loss in my life ;).

You don't appear to have read my post properly:  

[I]There was no life in the remote control until I updated the driver into the latest v4ldvb has to offer. I ran xev and was happy to see that most keys of the remote were identified. There was a problem, though: Ubuntu captured remote's power key and prompted me for a shutdown. And many keys were left entirely without an event.
[/I]
I agree with the above. This is exactly what I did. Many keys ARE left entirely without an event and this is where altering the keycodes in DIGITV.C comes in. For instance if you change KEY_INFO in the DIGITV.C file to KEY_I then the Info button on the remote that wasn't doing anything as you mentioned above suddenly starts spitting out the character "I" when used in xev. It appears that the DIGITV module uses the event layer in exactly the same way as LIRC but you don't have to mess around with LIRC and static input device fixes etc.

Take the entry for KEY_INFO from digitv.c

{ 0x6f, 0x65, KEY_INFO }

0x6f, 0x65 is the equivalent of the value that irrecord (lirc program) will produce in lircd.conf for the Info button. Only the digitv module writer has already worked this value out for you.
KEY_INFO is the name you would give the key in lircd.conf. You would then use lircrc to bind KEY_INFO to an actual keyboard key. As we're not using lirc I just changed KEY_INFO to KEY_I (as linux already knows that KEY_I is "I"). If input.h contains the KEY_I definition then think of input.h as equivalent to lircrc. I don't know enough about this though so take it with a pinch of salt.

Another problem I had with using lirc is that in mythtv (can't comment on other programs) one remote control keypress was emulated twice. The control was jumping down 2 items in a menu rather than the desired one (when pressing the down key on the remote of course!). I believe this to be because both the digitv module and lirc use the same event layer process and 2 modules equals 2 reads of the process. That's my guess anyway!

The disadvantage of my method is that once you've hard-coded the buttons for a particular program then pressing e.g Info will always produce an "I" and therefore other programs have to work around this and offer a key config setup if you want Info to do something else.

Anyway mythtv is working beautifully for me using this method - if there is a more elegant way then I'd love to hear it. Maybe adding more mappings to input.h (thanks for pointing that out to me as I wondered where the definitions were held) so that KEY_INFO means something to linux rather than changing it in the DIGITV.c file.

Cheers,

Rich.

---

### Post by dvarsam on 2007-01-20
Hello!

[QUOTE=polling]This howto describes how you can get your **Nebula uDigiTV USB** working with **Ubuntu 6.06 LTS**...[/quote]

Can you please add a snapshot of your product "**Nebula uDigiTV USB**" on your original "HowTo" post?
It is always better to add a picture of the product you are talking about...

Thanks.

P.S.1> If you don't know how to do this:

1. visit the site: [www.photobucket.com](www.photobucket.com)

2. Create an account inside that site.

3. Upload your product's picture in that site.
Note: If you don't have a picture of your product, you can search for one in the internet.

4. Under the list of all your uploaded pictures:

a. Click on the right of the box named "IMG Code" & the text named "[I M G]http://i69.photobucket.com/albums/i58/your_account_name/your_picture's_name.png[/I M G]" will be selected.

b. Perform a copy (on the selected text) & paste it inside your original post.

---

### Post by mhakali on 2007-11-12
Same problem, using an ASUS P5W64 PRO and have tried a ASUS P5B deluxe.

Tell me if you reached any solution. :>

---

