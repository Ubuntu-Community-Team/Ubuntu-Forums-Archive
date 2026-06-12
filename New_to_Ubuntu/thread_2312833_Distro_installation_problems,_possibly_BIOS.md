---
title: "Distro installation problems, possibly BIOS?"
date: 2016-02-07
forum: New to Ubuntu
---

### Post by Thinaran on 2016-02-07
So here is my story.

The developers decided today to delete the Youtube plugin support for any Kodi version below 14.2. Not just stop supporting it, making it completely unusable. To get it back, I'd need to upgrade. Okay, after five years, sure. I upgraded to Gotham 13.1 last year because they killed Frodo support, but to get Kodi, I'll need to update my underlying OS, XBMCbuntu 12.something. However, updating via terminal doesn't work. I managed to upgrade my distro to 12.10 via Terminal, but that isn't really helpful. I found a tutorial for doing it via **do-release-upgrade**, but that just gave me over 9000 errors and ignores, I guess related to the sources.list? Adding repositories and apt-get updating didn't seem to help either. 

But okay, after five years, might as well do a clean install. Trakt will keep track of the watched episodes and my newest year of media is on a NAS. So I downloaded Kodibuntu 14, made a bootable drive using UNetbootin on my Macbook, stuck it in the computer (it's an Acer Inspire Revo), and it booted into XBMC. Hm oh yeah so I go into the BIOS, set it to boot from Removable drive first, and ... it boots into XBMC. I notice that under Harddisk, I can choose either the internal harddrive or the USB drive. I can't choose both, and the computer seems to ignore the Removable drive.

Booting a computer with the USB as the main harddrive just gives me a blank screen with a cursor. I downloaded the 32-bit version of Kodibuntu thinking that was the problem, but same result. I downloaded the regular Ubuntu 14.04 ISO, and still the same. I've tried using another USB drive, I've tried all three USB inputs. Nothing works. 

Has anyone seen this before?

---

### Post by Thinaran on 2016-02-07
Typical, as usual OSX was the problem. UNetbooting didn't make a proper MBR, downloading Syslinux and doing that manually actually let me boot from the USB. Currently in the Kodibuntu installer. :)

---

