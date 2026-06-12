---
title: "Clamav &quot;outdated&quot; signatures"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by Swaphead on 2012-09-03
Hi, guys

I'm running Lubuntu 12.04 and use CLAMAV to check files that I load onto a USB stick 
for use in Windows.

When I noticed that the CLAMTK gui was showing "outdated signatures" I went into
the Synaptic Package Manager and upgraded CLAMAV, CLAMTK etc and rebooted.
The message was still showing.

I found this thread :
[http://ubuntuforums.org/showthread.php?t=1947436](http://ubuntuforums.org/showthread.php?t=1947436)

"sudo freshclam -v" did not produce any errors , like in the thread.

I checked the date on the files in var/lib/clamav and, although the dates were current,
I overwrote them with the files from clamav.net to be sure.

"sudo freshclam -v"  still does not produce any errors,
but I still see "outdated signatures" in the CLAMTK gui.

Am I up-to-date, or not?

Geoff

---

