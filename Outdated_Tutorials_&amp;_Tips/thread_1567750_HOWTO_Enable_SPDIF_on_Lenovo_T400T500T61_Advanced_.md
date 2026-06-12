---
title: "HOWTO: Enable SPDIF on Lenovo T400/T500/T61 Advanced Docking Station"
date: 2010-09-04
forum: Outdated Tutorials &amp; Tips
---

### Post by odedia on 2010-09-04
hi everyone,

This is my first post on the forums, and I wanted to share with you something that took me over 1.5 weeks to fix. hopefully, this will be helpful to someone out there.

I have a Lenovo T400 laptop which contains a Docking station with a SPDIF output built into it.

The SPDIF output worked great in Windows, but XBMC really stutters on Windows XP, so I tried Ubuntu 10.04. Although video was smooth as butter, the SPDIF connector simply didn't work no mater what I tried:

- I tried moving to OSS instead of ALSA
- I tried to remove Pulse
- I tried to upgrade to the latest version using the script at this URL: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Nothing worked.

I almost gave up, until I noticed this forum post:

[http://www.spinics.net/lists/alsa-devel/msg33651.html](http://www.spinics.net/lists/alsa-devel/msg33651.html)

So, what I did was:

1. Go through the upgrade script according to this URL: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)  BUT, stop after performing step #4! DO NOT compile yet.
2. replace the file under 
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/alsa-kernel/pci/hda/patch_conexant.c

with the file in the attachment (I already took the time to perform the comparison for you. NOTE: This is done against alsa version 1.0.23, if the file has changed in a later version, my file might not be updated, so please do the merge yourself according to the patch in the URL [http://www.spinics.net/lists/alsa-devel/msg33651.html](http://www.spinics.net/lists/alsa-devel/msg33651.html))

3. Now continue with step #5 and on.

After a reboot - you should have a working system. I had to go to the terminal and enter "alsamixer", and then to enable my SPDIF (press "M" if it is marked as "off" to unmute).

Hope this helps someone out there. I love open source :).

---

