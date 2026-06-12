---
title: "Multi-Monitor Issue"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by agons on 2013-08-08
Hello everyone, I'm rather new to Ubuntu and I have only one issues so far. I have two monitor's, one is center 1920x 1080 while the other is on the right side horizontal; 1080x 1920. They both work,(showing video on the screen and what not) But every time i reboot I have to go into my admin control center for ATI and rearrange them to the proper formation. Upon restart the extra monitor is set in the OS at left side and upside down 1080 x1920 when my monitor is on the right side proper side up 1080x 1920. Its just a bit annoying every time i want to use my ubuntu machine i end up having to fix this. any ideas?

Im Currently running:
Ubuntu 12.04LTS
GPu: ATI HD 6970 
graphics drivers: ATI/AMD proprietary FGLRX graphics driver (post-release updates)

---

### Post by bsamim on 2013-08-11
I have the same issues basically. I have to usually move the display manager to the main monitor ( the only one that looks correct ) and just hit Apply again and that usually fixes it. The settings are correct in the Display manager it just needs to be re-applied. Its a bug in ubuntu or the driver and I am waiting for a fix.

---

### Post by ant2 on 2013-08-11
I have a similar issue with a dual monitor set-up with screens swapping being the default x screen. I have tried setting it correctly and saving the settings to xorg.conf but I still get things changing around upon rebooting. However, I am using NVidia proprietary driver and as I have the issue in both a Ubuntu and an Arch install (on the same box) so I had always attributed the problem to the NVidia driver but here seems to be a very similar issue with ATI. So now I'm thinking the issue lies elsewhere

---

### Post by The-Server-4dmin on 2013-08-11
I was having the same issue with three monitors, thus I am on windows with my six monitors now. :(

---

### Post by agons on 2013-08-12
I got it working thanks guys! in a combo of applying it in the cata control center over and over along with using the ubuntu built in configuration manager it finally stuck!

---

