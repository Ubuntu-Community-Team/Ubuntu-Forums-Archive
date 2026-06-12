---
title: "Recovering from crash"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by Derrick_Young on 2014-03-12
I have not used Linux/Unix in 15 years so my skills are a tad rusty but it is coming back to me and I am enjoying it.  

I am running virtualbox on a windows home server.  The Guest is Ubuntu Server 32 bit.

Through some stupidity of my own doing the disk the Virtual was running on ran out of space.  This caused the Guest system to crash and has caused some serious grief for me.

I moved the virtualbox files to a different disk.  created a new server using the existing VDI file and everything then booted back up.  I was however missing eth0, which some searches revealed was to be expected as a newly detected MAC address would have been present.  So I edited removed the device from the appropriate file and rebooted.  As it should it rediscovered the eth0 device and networking is back up and running.

The issue I am having is with Apache

I had 2 Virtual hosts setup in it and it is not recognizing them.  Everything is just going through to the default host.  I have check the files located in [COLOR=#000000][FONT=monospace]/etc/apache2/sites-available and the 2 virtuals are still there.
[/FONT][/COLOR]when I try and start the hosts using "sudo a2ensite domain.com" it states it is already running.  A restart of the Apache2 service does not yield any different results as well

What am I overlooking?

---

### Post by Derrick_Young on 2014-03-12
Manged to resolve this.

Really not sure how.

But when VM ran out of disk space I was doing an install of some modules php5-gd and imagemagick.

this has me thinking so I ran apt_get clean then upgrade.  in hopes it would tidy up anything.  Then a restart of apache and problem was resolved.

---

