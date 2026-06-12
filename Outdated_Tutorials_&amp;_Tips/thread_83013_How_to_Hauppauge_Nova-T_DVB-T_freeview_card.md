---
title: "How to Hauppauge Nova-T DVB-T freeview card"
date: 2005-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by fsman on 2005-10-27
i've read a lot of posts with people trying to get their Nova-t dvb (freeview in UK) working and perhaps going overboard with trying to configure Mythtv. here is what I did to get DVB-T up and running very easily in Breezy.

Firstly your card needs to have the phillips chipset SAA7146 plus either the TDA10045 or the TDA10046. See [http://www.linuxtv.org/wiki/index.php/WinTV-NOVA-T_PCI](http://www.linuxtv.org/wiki/index.php/WinTV-NOVA-T_PCI)

Now, you must ensure that the firmware for the card is loaded by hotplug. I found that sometimes my card would work, then crash and i would be stuck until i did the following.

Get a copy of the perl script get_dvb_firmware. Either from kernel source or download from [http://lists.suse.com/archive/suse-linux/2005-Aug/att-0622/](http://lists.suse.com/archive/suse-linux/2005-Aug/att-0622/)

then 

$ perl get_dvb_firmware xxxxx (where xxxxx is tda10045 or tda10046). my advice is to do both.
then copy the resulting file 45 and/or 46

$ sudo cp dvb-fe-tda10045.fw /usr/lib/hotplug/firmware/

then via synaptic install dvd-utils and gxine

then download the digital channel list (using your transmitter) and store for xine

$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace >~/.xine/channels.conf

Now lets watch digital tv!
From the applications menu select gxine and thern DVB from the menu. or command prompt 
$ gxine dvb:// 

for details to select channels, onscreen display, epg and recording of channels  take a look at :

[http://cvs.sourceforge.net/viewcvs.py/xine/xine-lib/doc/README.dvb?rev=1.10](http://cvs.sourceforge.net/viewcvs.py/xine/xine-lib/doc/README.dvb?rev=1.10)


Enjoy DVB without the complexity of mythtv (and no more windows to load the firmware)

---

