---
title: "[SOLVED] cupsd is not running following package update"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by nirdo on 2008-12-02
Hi,
On 8.10 my cups server wouldn't start. I think it started happening after updating the CUPS package.
See below the output of the following commands:

nirdo@nirdo-desktop:~$ sudo /etc/init.d/cups status
Status of Common Unix Printing System: cupsd is not running.

nirdo@nirdo-desktop:~$ lpstat
lpstat: Unable to connect to server

nirdo@nirdo-desktop:~$ sudo /etc/init.d/cups start
 * Starting Common Unix Printing System: cupsd                                                                               cupsd: Child exited on signal 15!


/var/log/cups logs show:
No valid Listen or Port lines were found in the configuration file!


/etc/cups/cupsd.conf size is zero

---

### Post by kansasnoob on 2008-12-02
Do you have the "Proposed Updates" enabled?

There are some cupsys updates that are just NOT right in Proposed!

BTW there was a regression in HPLIP and I've quite often had to install hplip from the website to get hp printers to work properly in Intrepid.

---

### Post by nirdo on 2008-12-02
I don't have Proposed Updates enabled, just security and recommended.
Took your advice and tried to install HPLIP from the web. Seems that the installation thinks that the cups package dependency is missing:

> error: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.

So i tried to reinstall cups from Synaptic -> no change, HPLIP install still fails.
When i try to remove and install cups using apt-get, the install gives the following message:

> Setting up cups (1.3.9-2ubuntu3) ...
Reloading AppArmor profiles /sbin/apparmor_parser: Unable to replace "/usr/share/gdm/guest-session/Xsession".  Profile version not supported by Apparmor module
 Profile /etc/apparmor.d/gdm-guest-session failed to load
/sbin/apparmor_parser: Unable to replace "/usr/lib/cups/backend/cups-pdf".  Profile version not supported by Apparmor module
 Profile /etc/apparmor.d/usr.sbin.cupsd failed to load
: Failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.
 * Starting Common Unix Printing System: cupsd                                  cupsd: Child exited on signal 15!


---

### Post by nirdo on 2008-12-03
I've managed to successfully install cups and get the server running again after playing with AppArmor (deleting unsupported profiles and reloading AppArmor). I have installed HPLIP from the website and everything works well now. 
I still believe that there's a bug in the Intrepid upgrade or an an AppArmor update, that overlooks existing profiles

---

### Post by szirakitamas on 2008-12-11
Hi! Could You please help me? I have the same problem (after trying to install the HPLIP 2.8.10 from the HP website for the new Photosmart d5460)? What do You exactly mean: "deleting unsupported profiles and reloading AppArmor"? In which file? The /etc/apparmor.d? Thanks, Tamás

---

### Post by slambrick on 2008-12-11
> **nirdo said:**
> I've managed to successfully install cups and get the server running again after playing with AppArmor (deleting unsupported profiles and reloading AppArmor). I have installed HPLIP from the website and everything works well now. 
I still believe that there's a bug in the Intrepid upgrade or an an AppArmor update, that overlooks existing profiles

I have the same issue but also don't know what to do with AppArmor.
Please help.

---

### Post by szirakitamas on 2008-12-12
the biggest problem was that the / partition was filled up double amount of data.
temporarily i have solved it for myself: i purged all packages associated with hplip or cups, install most of them again, and the printer works. the problem was caused by installing the hplip-2.8.10 driver for my new photosmart d5460, and it was a bad decision. :) i installed this driver in VBox on Kubuntu, and it seems to be installed properly. i will check and see.

edit: finally i reinstall Ubuntu (without hplip-2.8.10 driver of course) because the improvement was temporarily.

---

