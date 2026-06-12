---
title: "VLC: Hauppauge HVR-950"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-10-24
I have an Hauppauge HVR-950 Capture card.

lsusb gives

```
Bus 005 Device 029: ID 2040:6513 Hauppauge 

```

I open vlc, go to file>Open Capture Device
but then after that I don't know how to specify my device.
I think I need the entry in /dev or something. My question is, how do I tell vlc how to use my device

---

### Post by Zzl1xndd on 2008-10-24
I would recommend using TVtime, It is available from the add remove programs and is great for watching TV. I have found VLC doesn't work too well with TV capture cards.

---

### Post by lispwizard on 2009-05-04
To answer the original question (in Intrepid and Jaunty), you select a capture mode of DVB and then the adapter card to tune should be automatically filled in (in my case /dev/dvb/adapter0).  If it isn't, most likely you don't have the device's firmware.  There is a perl script called extract_xc3028.pl which will extract it from a windows driver file in /usr/src/linux-headers-2.6.28-11/Documentation/video4linux/. Once you've extracted it, you'll have to copy it (as root) to /lib/firmware.  You'll see that the firmware was loaded in the dmesg output after you plug in the device.

After that you need to pick the frequency of your station; for example, in Boston, WGBH is 503000000 so from the command line you could just type

vlc dvb:// --dvb-frequency=503000000 --program=3

to watch the HDTV stream and

vlc dvb:// --dvb-frequency=503000000 --program=4

to watch the SD stream.  (Note, if you set the frequency in the gui, even though it is labelled kHz, you really have to type to whole number (i.e. in Hz).

Instead of starting anew for each channel, you can create a channels.conf file load the dvb-utils package (you need universe enabled).  Then you can use the "scan" utility to create a channels.conf file for your area.  Then you can just type

vlc channels.conf

and your playlist will include all the stations.  You may have to edit out some marginal ones by hand, it is just a text file.

Hope that helps someone.

---

### Post by chrisj26 on 2009-06-23
lispwizard , do you know how to record from the command line? for say a given frequency to an external hard disk?

---

### Post by ONEother on 2010-01-08
Recently got one of these capture cards and I'm trying to record VHS to my hard drive.
The normal setup with my tv is the tv gets the vhs signal *and* the cable signal through the vhs.
As of now, I can't get scan to create channels.conf, and as a consequence I haven't the slightest clue how to get VLC -- or any player -- to display and record the input from the card.
Am I going about this a completely wrong way?

Scuse me for digging up an old thread :?

---

