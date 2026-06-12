---
title: "rtl-sdr driver on ubuntu 18.04 is not work ,install fail plz help :("
date: 2019-03-01
forum: New to Ubuntu
---

### Post by yujie666 on 2019-03-01
[COLOR=#000000]**[SIZE=3]Hello[/SIZE]**, [/COLOR][SIZE=3]**It can be successfully installed on ubuntu 16.04**[/SIZE][COLOR=#000000]

[/COLOR]
Install RTL-SDR
~ RTL_SDR ~
$ cd~
~$ sudo apt-get install build-essential
$ git clone git://git.osmocom.org/rtl-sdr.git
$ cd rtl-sdr
$ mkdir build
$ cd build
$ cmake ../ -DINSTALL_UDEV_RULES=ON
$ make
$ sudo make install
$ sudo ldconfig
$ cd ~
$ sudo cp ./rtl-sdr/rtl-sdr.rules /etc/udev/rules.d
$ sudo reboot
$ cd /etc/modprobe.d
$ sudo nano no-rtl.conf
Paste
             Blacklist dvb_usb_rtl28xxu
             Blacklist rtl2832
             Blacklist rtl2830
$ sudo reboot


[test] After inserting the dongle
$ rtl_fm -f 97.7e6 -M wbfm -s 200000 -r 48000 - | aplay -r 48k -f S16_LE
(The above will only complete the functions such as rtlfm, rtl-sdr, rtl-tcp, etc. To see the block again, gnuradio-companion needs the following OSMOSOM)



[SIZE=3][B]
But on ubuntu 18.04 is not ok...

When I execute gnuradio's rtl-sdr block, it appears these..


[/B][/SIZE]Loading: "/home/yujie/&#19979;&#36617;/download/FM_stereoReceiver.grc"
>>> Done


Generating: '/home/yujie/\xe4\xb8\x8b\xe8\xbc\x89/download/FM_stereoReceiver.py'


Executing: /usr/bin/python2 -u /home/yujie/&#19979;&#36617;/download/FM_stereoReceiver.py




(FM_stereoReceiver.py:3145): IBUS-WARNING **: 15:47:59.146: The owner of /home/yujie/.config/ibus/bus is not root!
gr-osmosdr v0.1.4-127-g4d83c606 (0.1.5git) gnuradio 3.7.13.4
built-in source types: file fcd rtl_tcp uhd sdrplay rfspace soapy redpitaya 
[32;1m[INFO] [UHD] [39;0mlinux; GNU C++ version 7.3.0; Boost_106501; UHD_3.11.0.HEAD-0-ga1b5c4ae
get_devices started
Device count: 0
get_devices end
Traceback (most recent call last):
  File "/home/yujie/&#19979;&#36617;/download/FM_stereoReceiver.py", line 261, in <module>
    main()
  File "/home/yujie/&#19979;&#36617;/download/FM_stereoReceiver.py", line 255, in main
    tb = top_block_cls()
  File "/home/yujie/&#19979;&#36617;/download/FM_stereoReceiver.py", line 148, in __init__
    self.rtlsdr_source_0 = osmosdr.source( args="numchan=" + str(1) + " " + '' )
  File "/usr/local/lib/python2.7/dist-packages/osmosdr/osmosdr_swig.py", line 1170, in make
    return _osmosdr_swig.source_make(*args, **kwargs)
RuntimeError: No supported devices found (check the connection and/or udev rules).

**My rtl-sdr can't hear the sound (FM)**

[SIZE=3]**Can someone help me? plz :(**[/SIZE]

---

