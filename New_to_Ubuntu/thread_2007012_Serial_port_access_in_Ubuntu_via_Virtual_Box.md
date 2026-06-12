---
title: "Serial port access in Ubuntu via Virtual Box"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by sjalickee on 2012-06-20
I am running  Ubuntu 11.10 as a guest on Windows 7 through VM (VirtualBox 4.0) and am trying to access a serial port collecting NMEA (ASCII) data - I have tried to monitor the port using minicom and GtkTerm but have a feeling I am missing something basic.  My pc has a 1 native serial port and I can see the data coming in using PuTTY (and I do disconnect before trying to connect on ubuntu).
Really appreciate this form - have helped with plenty of other issues!

---

### Post by lkraemer on 2012-06-20
You need the Download & Install of of VirtualBox that supports USB, if you are going to use a USB to Serial Adapter.
You also need to set up a couple of Serial Ports in VirtualBox.  I don't have any Legacy Serial Ports on my Laptop,
so I can't tell you the specifics................

Then read this Posting #2:
[http://ubuntuforums.org/showthread.php?t=1810760&highlight=com1](http://ubuntuforums.org/showthread.php?t=1810760&highlight=com1)
and this Posting #6: (for USB to Serial Adapter)
[http://ubuntuforums.org/showthread.php?t=1356750&highlight=com1](http://ubuntuforums.org/showthread.php?t=1356750&highlight=com1)
Also:
[http://ubuntuforums.org/showthread.php?t=2006760](http://ubuntuforums.org/showthread.php?t=2006760)
to manage your Groups & Permissions.

It should explain what you need to look for.  GTKTerm works good, I've used it lots.

You might also find this site interesting:
[http://www.lammertbies.nl/comm/cable/RS-232-spy-monitor.html](http://www.lammertbies.nl/comm/cable/RS-232-spy-monitor.html)


lk

---

### Post by sjalickee on 2012-06-20
It is not a USB to Serial but I now think the problem is with my VB
I know I am getting the data into my host windows7 maching b/c I use putty to see it but when I try to add a serial port in VB I get the following error:

*Failed to open host device ‘\dev\ttyS0’**(VERR_PATH_NOT_FOUND)*[I]Unknown error creating VM (VERR_PATH_NOT_FOUND).

[/I]I checked and I am already in group 'dialout' 
Should I change the permissions of ttyS0?

---

### Post by lkraemer on 2012-06-21
Since your HOST is Win 7, and that is what is running VirtualBox, you need to SLOWLY read "Section 3.9 Serial Ports" in the VirtualBox Manual starting on Page 51.

It explains that you need to create a Virtual Serial Port in VirtualBox, then attach it to the HOST (ie. COM1 in Win7....NOT /dev/ttySx) and all communications will be routed to the HOST's Port, from the Guest OS.  So, in GTKTerm you can then try /dev/ttySx or use a symbolic link to get your data routed to the Virtual Serial Port.  I'd start with a looped back (Null Modem Cable) with TX tied to RX to do my testing, if I were you.  If you can type characters in Ubuntu's GTKTerm, and get them to echo back to the GTKTerm Window (from GTKTerm to VBox to Win 7 COM1 then looped back to Win 7 COM1 to VBox to GTKTerm) then you are on the way to proceed.

My Debian 6 /dev/ttyS0 Permissions are set to:
> 
crw-rw---- 1 root dialout 4, 64 Jun 21 11:54 /dev/ttyS0


lk

---

