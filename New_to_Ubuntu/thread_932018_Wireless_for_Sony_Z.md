---
title: "Wireless for Sony Z"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by renkel on 2008-09-27
Hi folks,
I purchased a new Sony VGN-Z530N and installed UBUNTU hardy. 
There are two problems there:

1. Wireless doesn't work. I tried wicd, mad wifi, ndiswrapper, but nothing seems to work. No wireless networks are found.
This is my iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Hardware Drivers shows:
Intel(R) Wireless WiFi Link AGN driver for Linux
 
2. When rebooting, computer always hangs, when turning off computer often hangs.

Any help?
Peter.

---

### Post by david ly-gagnon on 2008-10-13
Hi Peter, 

I am glad you are writing about your experiences with Ubuntu and your Sony Z laptop. I also bought a Sony Z laptop a month ago, and I could not find anyone else blogging about their experience installing Ubuntu so far. 

To answer your first question, download Ubuntu 8.10(Intrepid Ibex) instead of 8.04 (hardy), and make sure you choose the 64 bit version. 2 reasons for doing this: first: wifi and network cards will both be recognized on installation; second: installing the 64 bit will recognize that the laptop has 4 Gig of Ram.

As for the reboot problem, I am still experiencing the same problem. I have installed Ubuntu 8.10 (x64) alpha 6 version, but haven't tried the beta version recently released. I have already filed for a bug report...

So, try the new beta release and let me know if that helped you:)

David

---

### Post by david ly-gagnon on 2008-10-13
Hello,

I just wanted to know if people have had similar results installing different version of Ubuntu of Sony Vaio Z series:

1. Ubuntu 8.04 (hardy x32): no wireless and no network
2. Ubuntu 8.10 (Intrepid Ibex x32): wireless and network recognized but only 2 Gb of ram is detected.
3. Ubuntu 8.10 (Intrepid Ibex x64): wireless and network detected, running 4Gb of ram, but computer hangs on reboot. Also FN keys not detected (for brightness), and seems like hard disk is making a tick sound very often. I believe fan is also running too often...

Thank you,

David

---

### Post by wcronen on 2008-10-21
> **david ly-gagnon said:**
> Hello,

I just wanted to know if people have had similar results installing different version of Ubuntu of Sony Vaio Z series:

3. Ubuntu 8.10 (Intrepid Ibex x64): wireless and network detected, running 4Gb of ram, but computer hangs on reboot. Also FN keys not detected (for brightness), and seems like hard disk is making a tick sound very often. I believe fan is also running too often...

Thank you,

David

Hi David,

I'm having exactly the errors you reported with the latest version of ubuntu beta 8.10 and all updates installed.

First my lan was not recognized but after updating to kernel 2.6.27-7 it's working fine.

My wlan is recognized but not working properly. I can connect to my wpa2 encrypted AP but the connection isn't working as it should. I run an endless ping for testing after a few minutes there is a connection for a few seconds (never more than 1 minute), then the connection get's lost, ... I don't know what I can try to resolve it. The problem is definitely a ubuntu/linux error as with windows vista there's no problem, so the AP must be ok.

Fn+F5/6 doesn't work and smartdimmer isn't also working.

The nvidia card is also not working. I've to use the intel card but this card works fine.

I can also report the "tick" sound of the harddisk.

If there are any solutions and ideas what I can try or test, please let it know.

Greetz
Walter

---

### Post by CrippledCanary on 2008-10-22
I have a SZ71 Vaio and Since Itrepid beta sometime the wlan has worked almost without any flaws. I will reinstall to 64bit after official release but is running 32bit right now.

I have pretty much everything up and running on my laptop, including nvidia, wlan, sound, dock.
What I still haven't been able to get up and running is the bluetooth. The device is recognised but I can't seem to get the "radio" part of it turned on (prolly somekind of vaio power saving feature).
And of course I don't have any control over the brightness either.

---

### Post by wcronen on 2008-10-22
Maybe the nvidia bug is only in the 64bit version of ubuntu?!

Do you have the display with 1600x900? Maybe it's a problem with the resolution?

---

### Post by david ly-gagnon on 2008-12-01
I have no clue if it is related to the x64 being installed. My current resolution is 1366 x 768 . NVIDIA is not installed yet, and I am hoping more people will report on experiencing ubuntu 8.10 with sony vgn-z series.

Does anyone else have tried ubuntu 8.10 with a sony Z series ???

---

### Post by dfacto on 2008-12-11
I have a z540 on 8.10 and have some things working well, and not on others.

Short version:
Not working: Nvidia, suspend, hibernate, stable wifi, most FN keys.
Working:     Everything else.

Long version:
Last I checked a few weeks ago, nvidia drivers were not working--this is an nvidia problem.  I suspect it is because of the dual-video card nature of the z-series (and other similarly configure laptops).  The intel video driver now works (there was a nasty corrupt-display bug but this is fixed in recent drivers).  Also note, I am using dual monitors with shared desktop.  For now, I am using only intel.  I did read in a forum that installing XP and deactivate/activate nvidia allowed things to work.  This is the most involved solution imaginable--short of opening the machine up and dropping pieces of doped sand into the appropriate area of the nvidia EEPROM core.  In other words, I have not, and will not, verify this "solution."

You should do is update the BIOS (goto sony.com) to fix the slow boot, no reboot problem, if you are experiencing it.  I have not tried to work on the suspend/hibernate issue.

The threads explain how to get wireless running, but I am experiencing a very troublesome periodic dropout with the inability to reconnect (using the self-patched intel drivers).  I believe the latest few kernels support the intel 5100 so you shouldn't need to compile from (patched) source as I did.  You will still probably experience the dropout problem, from what I have read.

Motioneye, sound, most everything else I can think of works well.

---

### Post by david ly-gagnon on 2008-12-12
Thanks dfacto, 

I have updated the Bios and the reboot problem is now solve. I can now reboot the computer from ubuntu without any problems.

I have the exact same model as you, Z540C to be precise, and was wondering if you run ubuntu on the NVIDIA card (SPEED) or the intel (STAMINA)?

I installed Ubuntu while the laptop was on speed mode and I only get a resolution 1360x768. 

Should I switch to Intel mode to get a better graphics until we get some appropriate drivers for NVIDIA?

thanks

David

---

### Post by jaikenone on 2008-12-16
I have Z530N with 8.10 installed.  I have the latest bios and have fixed the brightness problem with "xrandr --output LVDS --set BACKLIGHT_CONTROL legacy" and the gnome power manager brightness applet. I'm using the intel video card.  Setting the switch between stamina and speed makes no difference.  trying to use nvidia drivers hosed x windows.

what's not working:

brightness buttons
video out button
ms/sd card readers
head phones work but they don't turn off the speakers
built in mic

---

