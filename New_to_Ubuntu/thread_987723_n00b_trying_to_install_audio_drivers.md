---
title: "n00b trying to install audio drivers"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by TomServo1 on 2008-11-19
I tried to install a driver for the integrated audio on my Dimension 2350(because a driver for my USB headset doesn't exist).  I downloaded a Dell Alsa driver pack, then converted the .rpm to .deb with alien.
When I tried to install the .deb, I would get this message incessantly in the command line for about a minute:
```
chown: invalid user: `hulla:hulla'
```

followed by these errors:
```
Can't open /usr/share/hwdata/pcitable: No such file or directory.
Can't open /etc/sysconfig/hwconf: No such file or directory.
/var/lib/dpkg/info/dell-alsa-driver.postinst: 1071: dkms: not found
/var/lib/dpkg/info/dell-alsa-driver.postinst: 1089: dkms: not found
/var/lib/dpkg/info/dell-alsa-driver.postinst: 1089: dkms: not found
/var/lib/dpkg/info/dell-alsa-driver.postinst: 1089: dkms: not found
/var/lib/dpkg/info/dell-alsa-driver.postinst: 1091: chkconfig: not found
dpkg: error processing dell-alsa-driver (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dell-alsa-driver
Unable to install at /usr/share/perl5/Alien/Package/Deb.pm line 92, <GETPERMS> line 972.
	find dell-alsa-driver-0.9.0rc6 -type d -exec chmod 755 {} ;
	rm -rf dell-alsa-driver-0.9.0rc6
```

Basically, the install failed.  And now, I can't uninstall whatever was successfully installed.  When I open the Package Manager, I get this error:
```
E: The package dell-alsa-driver needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

How can I fix this problem?

---

### Post by saru411 on 2008-11-20
Can you install the drivers via System>Administration>Hardware Drivers?

---

### Post by TomServo1 on 2008-11-20
No, I basically couldn't install or uninstall anything.  But I figured it out.  There was a file the uninstall was trying to access that it couldn't for whatever reason.  When I deleted the file, it uninstalled without a hitch.  I found out that an alsa driver preinstalled with the system worked with my sound chip.  It kinda sucks that I can't use my Tritton headset, but I guess you can't have everything in the non-profit world.

---

