---
title: "(Un)installation Error coming &amp; going"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by mglennpooh on 2011-10-25
I recently tried to uninstall my Wubi Ubuntu 11.10 as prelude to Easy Transfer / WAIK Labs we're doing in my Microsoft 7 Configuration Cert Course and I keep getting the following error message after I try to reinstall & reboot ...
                
                          Loop-mounted file systems already present

                           The selected partition ( partition 2 of
                        /var/lib/devices/=dev=sda ) already contains
                             the following file system images:

                                /ubuntu/disks/root.disk

                        Please uninstall these before trying again

...When I boot back into Win7 I find C:\Ubuntu contains a file /ubuntu/disks/root.disk
so I scram the whole folder but no luck on the retry.

PS - I finally got another wubi to install but when I type sudo fdisk -l , I get three disks, one 298GB, and two (virtual) around half a gig each. I assume the smaller of the two is the remnant which failed to uninstall. I also limitted the install to 10 GB but my Win7 Control Panel lists Ubuntu as 23GB total. I've got more space than I know what to do with right now but I suspect there are others with disks under a 100GB who might profit from a relevant solution here.

---

### Post by kemtnbkr on 2011-10-26
Personally, I have never tried wubi, so I can't help much from experience.  
However, I have seen lots of people having lots of odd issues with wubi; in the end it often seems easier to just do a dualboot install, or boot Ubuntu from a live USB or CD rather than using wubi.

But of course that wouldn't work if you need to have Windows and Ubuntu running at the same time.  It is possible to boot a copy of Windows that is installed to the HD from within an Ubuntu session, but it looked harder than was really worth it.  The thread is here: [http://ubuntuforums.org/showthread.php?t=984437]("http://ubuntuforums.org/showthread.php?t=984437") if you're interested.  This is a bit outdated, but supposedly works with Windows 7 too.  

Sorry I wasn't of more assistance, at least you got a free bump :)

---

