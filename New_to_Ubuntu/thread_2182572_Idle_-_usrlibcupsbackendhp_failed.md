---
title: "Idle - /usr/lib/cups/backend/hp failed"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by schmitta on 2013-10-21
I get the message Idle - /usr/lib/cups/backend/hp failed and the printer does not work. I went to the admistration page ( [http://localhost:631/admin](http://localhost:631/admin) ) and there is no resume command. How do I get the printer to work?

---

### Post by tgalati4 on 2013-10-21
Look in /var/log/cups for error logs.  Why did the backend fail?  You might have to restart cups or reboot, but check the logs first and post anything that might be useful.  HP printer quality is generally poor, so you might have to reboot the printer if the printer's processor has locked up.

---

### Post by schmitta on 2013-10-22
Went to var/logs/cups/error and saw the following at the end. 

D [21/Oct/2013:17:25:50 -0400] [Job 38] Started filter /usr/lib/cups/filter/commandtops (PID 8194)
D [21/Oct/2013:17:25:50 -0400] [Job 38] Started backend /usr/lib/cups/backend/hp (PID 8195)
D [21/Oct/2013:17:25:50 -0400] [Job 38] STATE: +connecting-to-device
D [21/Oct/2013:17:25:50 -0400] [Job 38] prnt/backend/hp.c 745: ERROR: open device failed stat=12: hp:/par/HP_LaserJet_P2035?device=/dev/parport0
D [21/Oct/2013:17:25:50 -0400] [Job 38] Backend returned status 1 (failed)
D [21/Oct/2013:17:25:50 -0400] [Job 38] End of messages
D [21/Oct/2013:17:25:50 -0400] [Job 38] printer-state=3(idle)
D [21/Oct/2013:17:25:50 -0400] [Job 38] printer-state-message="/usr/lib/cups/backend/hp failed"
D [21/Oct/2013:17:25:50 -0400] [Job 38] printer-state-reasons=none

---

### Post by schmitta on 2013-10-22
Went to var/logs/cups/error and saw the following at the end. 

D [21/Oct/2013:17:25:50 -0400] [Job 38] Started filter /usr/lib/cups/filter/commandtops (PID 8194)
D [21/Oct/2013:17:25:50 -0400] [Job 38] Started backend /usr/lib/cups/backend/hp (PID 8195)
D [21/Oct/2013:17:25:50 -0400] [Job 38] STATE: +connecting-to-device
D [21/Oct/2013:17:25:50 -0400] [Job 38] prnt/backend/hp.c 745: ERROR: open device failed stat=12: hp:/par/HP_LaserJet_P2035?device=/dev/parport0
D [21/Oct/2013:17:25:50 -0400] [Job 38] Backend returned status 1 (failed)
D [21/Oct/2013:17:25:50 -0400] [Job 38] End of messages
D [21/Oct/2013:17:25:50 -0400] [Job 38] printer-state=3(idle)
D [21/Oct/2013:17:25:50 -0400] [Job 38] printer-state-message="/usr/lib/cups/backend/hp failed"
D [21/Oct/2013:17:25:50 -0400] [Job 38] printer-state-reasons=none

Powered on the printer and restarted ubuntu. The print queue was empty even though I had something to print in it.  Then printed two pages and got:

Idle - /usr/lib/cups/backend/hp failed

With the error logs:

E [22/Oct/2013:11:20:24 -0400] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [22/Oct/2013:11:20:24 -0400] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Hewlett-Packard-HP-LaserJet-P2035-Gray..' already exists
W [22/Oct/2013:11:20:24 -0400] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Hewlett-Packard-HP-LaserJet-P2035' already exists
E [22/Oct/2013:12:07:56 -0400] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [22/Oct/2013:12:08:03 -0400] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
W [22/Oct/2013:12:08:08 -0400] failed to CreateDevice: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

with /etc/cups/cupsd.conf

#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#


# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn


# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0


# Administrator user group...
SystemGroup lpadmin                                     <-- LINE 16




# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

NOTE THAT THIS USE TO WORK OK (SEVERAL DAYS AGO).

---

### Post by schmitta on 2013-10-23
Went to var/logs/cups/error and saw the following at the end. 

D [21/Oct/2013:17:25:50 -0400] [Job 38] Started filter /usr/lib/cups/filter/commandtops (PID 8194)
D [21/Oct/2013:17:25:50 -0400] [Job 38] Started backend /usr/lib/cups/backend/hp (PID 8195)
D [21/Oct/2013:17:25:50 -0400] [Job 38] STATE: +connecting-to-device
D [21/Oct/2013:17:25:50 -0400] [Job 38] prnt/backend/hp.c 745: ERROR: open device failed stat=12: hp:/par/HP_LaserJet_P2035?device=/dev/parport0
D [21/Oct/2013:17:25:50 -0400] [Job 38] Backend returned status 1 (failed)
D [21/Oct/2013:17:25:50 -0400] [Job 38] End of messages
D [21/Oct/2013:17:25:50 -0400] [Job 38] printer-state=3(idle)
D [21/Oct/2013:17:25:50 -0400] [Job 38] printer-state-message="/usr/lib/cups/backend/hp failed"
D [21/Oct/2013:17:25:50 -0400] [Job 38] printer-state-reasons=none

Powered on the printer and restarted ubuntu. The print queue was empty even though I had something to print in it. Then printed two pages and got:

Idle - /usr/lib/cups/backend/hp failed

With the error logs:

E [22/Oct/2013:11:20:24 -0400] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [22/Oct/2013:11:20:24 -0400] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Hewlett-Packard-HP-LaserJet-P2035-Gray..' already exists
W [22/Oct/2013:11:20:24 -0400] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Hewlett-Packard-HP-LaserJet-P2035' already exists
E [22/Oct/2013:12:07:56 -0400] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [22/Oct/2013:12:08:03 -0400] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
W [22/Oct/2013:12:08:08 -0400] failed to CreateDevice: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

with /etc/cups/cupsd.conf

#
#
# Sample configuration file for the CUPS scheduler. See "man cupsd.conf" for a
# complete description of this file.
#


# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn


# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0


# Administrator user group...
SystemGroup lpadmin <-- LINE 16




# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

NOTE THAT THIS USE TO WORK OK (SEVERAL DAYS AGO).

---

### Post by tgalati4 on 2013-10-23
This appears to be a parallel port printer--which means that it is probably several years old.  Try reconnecting the cable at both ends.  The machine probably needs cleaning inside and reseating of the internal connections.  CUPS and Linux in general does not tolerate wonky hardware.

There is not much you can do if the printer refuses to communicate.

---

### Post by schmitta on 2013-10-24
Found the problem! It was a connection problem after all! Thanks for all your help. Alvin....

---

