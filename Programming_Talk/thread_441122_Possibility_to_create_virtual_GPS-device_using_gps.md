---
title: "Possibility to create virtual GPS-device using gpsfake or gpspipe?"
date: 2007-05-12
forum: Programming Talk
---

### Post by MG_Blinker on 2007-05-12
Hi,
I'm just programming a GPS-application and therefore I'd like to create a virtual GPS-device using the data of a GPS test run (NMEA protocol). Thus, I want to avoid having to drive the track again and again.

Therefore, I have already tried the following:

gpsfake -i meinecapturedatei.txt
gpspipe - s /dev/ttyS0 -r

Those two commands work quite fine, the only problem is that there is no data arriving on ttyS0. I have already checked the ttyS0 interface using the hd command or by Cutecom.

Usage: gpspipe [OPTIONS] [server[:port]]

SVN ID: $Id: gpspipe.c 3185 2005-09-01 02:57:46Z esr $
-h show this help
-r Dump raw NMEA
-w Dump gpsd native data
-t time stamp the data
-s [serial dev] emulate a 4800bps NMEA GPS on serial port (use with '-r')
-n [count] exit after count packets
-V print version and exit

Does anyone have a hint for me? Or are there any other possibilities?

Thanks in advance.

---

### Post by marwouta23 on 2009-10-01
Hi,

I have a project about localisation using WSN and GPS.
I want to know if I can implement or use directly virtual GPS under NS-2 .

if you have an idea please forward it to me .
Thank you in advance.

---

### Post by Newton_Jose on 2010-09-22
Hi people,
I think you don't need to use gpspipe to do this.

Use only gpsfake. It will create a port in /dev/pts.

/dev/pts is a directory. We need find out what is the device, inside it, where 
gpsfake is send data to:

1) First step, see what device already up WHITOUT gpsfake running
# ls /dev/pst/
# 0  1  2  7  ptmx

2) Second step, start gpsfake and see what device show up
# gpsfake gps_file.nmea
# ls /dev/pst/
# 0  1  2  3  7  ptmx

As you can see /dev/pst/3 show up, and is the device with the nmea gps data.

So, with gpsfake still running, you only need to give the command:

# cat  /dev/pst/3 

to retrieve the data.

---

### Post by Newton_Jose on 2010-09-22
Another simpler way is use -p option in gpsfake:

# gpsfake -p nmea_rjibge.gps

It will send the data to stdout, i.e., the screen.

To eliminate the line with infomation about device and other things, and get a "pure" nmea data, gives:
# gpsfake -p nmea_rjibge.gps | grep -v 'class'

---

