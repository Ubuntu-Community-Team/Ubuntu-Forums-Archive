---
title: "Playing DVDs using vlc - I believe I have installed all packages needed"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by darkline on 2008-07-08
I am trying to use VLC (as i prefer vlc) to play dvds. If i cant get vlc working it doesnt matter if its another program.

I have installed all these packages ::-
totem-xine 
libxine1-ffmpeg 
libdvdread3 
libdvdcss2

and run /usr/share/doc/libdvdread3/install-css.sh

This is what happens when vlc is run - 
```

:~$ wxvlc dvd:///media/cdrom0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/h3n/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012a
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001c3
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000011a9
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002208e3
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0022093a
libdvdread: Elapsed time 3
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 18
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed - CRASHING!!!
wxvlc: vm.c:198: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
```

After opening with totem it comes up with an error "Could not read from resource"

Thanks for any help.

---

### Post by pofigster on 2008-07-08
Try removing totem-xine and libxine1-ffmpeg - the only things you should need for DVD playback is libdvdread3 and libdvdcss2

I don't know if it'll work, but uninstalling frivilous packages has worked for me.

---

### Post by Ryadt on 2008-07-08
Hi I think you need to install medibuntu.
Have a look at this;
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by darkline on 2008-07-08
Removing those two pakages seemed to work for most DVDs adn they now play fine on vlc.

However there is one DVD that doesnt work, its slightly scratched but works in my dvd player.

Im guessing that there is really nothing i can do about this?
If so it doesnt matter.

Thanks for the help!

---

### Post by stchman on 2008-07-08
> **darkline said:**
> I am trying to use VLC (as i prefer vlc) to play dvds. If i cant get vlc working it doesnt matter if its another program.

I have installed all these packages ::-
totem-xine 
libxine1-ffmpeg 
libdvdread3 
libdvdcss2

and run /usr/share/doc/libdvdread3/install-css.sh

This is what happens when vlc is run - 
```

:~$ wxvlc dvd:///media/cdrom0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/h3n/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012a
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001c3
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000011a9
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002208e3
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0022093a
libdvdread: Elapsed time 3
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 18
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed - CRASHING!!!
wxvlc: vm.c:198: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
```

After opening with totem it comes up with an error "Could not read from resource"

Thanks for any help.

I have a tutorial to get VLC and Ubuntu playing DVDs.

Install CODECs (32 bit, 64 bit has special instruction)
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Setup DVD CSS (extra step in Hardy)
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

You will be playing encrypted Hollywood DVDs in no time.

---

