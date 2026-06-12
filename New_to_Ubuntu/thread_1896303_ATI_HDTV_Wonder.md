---
title: "ATI HDTV Wonder"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by swcrouch on 2011-12-16
I'm trying to install an ATI HDTV Wonder in mythbuntu 11.10

I found this on the mythtv wiki:
This card requires a firmware file (dvb-fe-nxt2004.fw1) for the demodulator, which can be obtained using the get_dvb_firmware perl script included in the kernel sources:

# cd /[kernel source directory]/Documentation/dvb/
# perl get_dvb_firmware nxt2004

Once the download is complete, place a copy of the firmware file in your /lib/firmware directory. (This directory may differ with some distros; consult your distro's documentation for the appropriate location).

Where exactly would I find my kernel source directory?  It's been about 10 years since I've looked at linux... please assume I know nothing.  All I remember is the ls command.  Thanks,

---

### Post by swcrouch on 2011-12-17
Did this:

sudo apt-get install linux-source
cd /usr/src
sudo tar xvjf linux-source-3.0.0.tar.bz2
cd linux-source-3.0.0/Documentation/dvb
sudo perl get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware/

---

### Post by swcrouch on 2011-12-19
The linuxtv.org wiki says to:

Within the file /etc/modules.conf(your system may have a different location such as /etc/modprobe.d/options), just add

options cx88xx card=34

I had added it as a line in /etc/modules, which did not work.  I added the file /etc/modprobe.d/options, and put the line in that new file, and it now works.

---

