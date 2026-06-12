---
title: "[SOLVED] &amp;quot;Could not connect to the master backend server&amp;quot; after applied update"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Elijah2104 on 2008-11-02
Hi, I wonder if you can help.

I allowed Mythbuntu to install the following updates on the 1st November

> Commit Log for Sat Nov  1 14:42:21 2008

Upgraded the following packages:
apt (0.7.9ubuntu17) to 0.7.9ubuntu17.1
apt-utils (0.7.9ubuntu17) to 0.7.9ubuntu17.1
libgtk2.0-0 (2.12.9-3ubuntu4) to 2.12.9-3ubuntu5
libgtk2.0-common (2.12.9-3ubuntu4) to 2.12.9-3ubuntu5
linux-headers-2.6.24-21 (2.6.24-21.42) to 2.6.24-21.43
linux-headers-2.6.24-21-generic (2.6.24-21.42) to 2.6.24-21.43
linux-image-2.6.24-21-generic (2.6.24-21.42) to 2.6.24-21.43
linux-libc-dev (2.6.24-21.42) to 2.6.24-21.43
linux-source-2.6.24 (2.6.24-21.42) to 2.6.24-21.43
tzdata (2008h-0ubuntu0.8.04) to 2008h-0ubuntu0.8.04.1
xkb-data (1.1~cvs.20080104.1-1ubuntu6) to 1.1~cvs.20080104.1-1ubuntu8
xserver-xorg-video-intel (2:2.2.1-1ubuntu13.6) to 2:2.2.1-1ubuntu13.7


ever since, I have been unable to connect to the backend.  The same problem occurs whether I use the computers fixed IP (assigned through my router) or whether I use 127.0.0.1.  (At the moment the client and sever are on the same computer although I will need to change back to the fixed IP to use a remote client in the future).

The version of Mythbuntu I'm running is

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"


When executing the front end through the terminal I get the following output

> 2008-11-02 16:39:33.929 Using runtime prefix = /usr
2008-11-02 16:39:34.468 XScreenSaver support enabled
2008-11-02 16:39:34.469 DPMS is active.
2008-11-02 16:39:34.470 Empty LocalHostName.
2008-11-02 16:39:34.470 Using localhost value of MMPC
2008-11-02 16:39:34.488 New DB connection, total: 1
2008-11-02 16:39:34.495 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:39:34.498 Closing DB connection named 'DBManager0'
2008-11-02 16:39:34.506 Primary screen 0.
2008-11-02 16:39:34.507 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:39:34.509 Using screen 0, 1360x768 at 0,0
2008-11-02 16:39:34.525 New DB connection, total: 2
2008-11-02 16:39:34.526 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:39:34.530 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-02 16:39:34.534 Enabled verbose msgs:  important general
2008-11-02 16:39:34.686 Unable to parse themeinfo.xml for glass-wide
2008-11-02 16:39:34.686 The theme (glass-wide) is missing a themeinfo.xml file
2008-11-02 16:39:34.956 Unable to parse themeinfo.xml for glass-wide
2008-11-02 16:39:34.956 The theme (glass-wide) is missing a themeinfo.xml file
2008-11-02 16:39:35.386 No theme dir: /home/andrew/.mythtv/themes/blue
2008-11-02 16:39:35.387 Primary screen 0.
2008-11-02 16:39:35.388 Using screen 0, 1360x768 at 0,0
2008-11-02 16:39:35.390 No theme dir: /home/andrew/.mythtv/themes/blue
2008-11-02 16:39:35.392 Switching to square mode (blue)
2008-11-02 16:39:35.443 Using the Qt painter
2008-11-02 16:39:35.445 JoystickMenuClient Error: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
2008-11-02 16:39:35.445 lirc init success using configuration file: /home/andrew/.mythtv/lircrc
2008-11-02 16:39:37.045 Loading from: /usr/share/mythtv/themes/blue/base.xml
2008-11-02 16:39:37.110 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-02 16:39:37.138 Registering Internal as a media playback plugin.
2008-11-02 16:39:37.209 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-02 16:39:37.240 Failed to run 'cdrecord --scanbus'
2008-11-02 16:39:37.243 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-11-02 16:39:37.248 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-11-02 16:39:37.269 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-11-02 16:39:37.317 No theme dir: /home/andrew/.mythtv/themes/blue
2008-11-02 16:39:39.513 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-02 16:39:39.513 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-11-02 16:39:40.020 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-02 16:39:40.023 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-11-02 16:39:42.294 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-02 16:39:42.294 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2008-11-02 16:39:44.647 Deleting UPnP client...

Of course, this now means that I can't watch TV, or any existing recordings and I cannot make new recordings either.

I have connected to MySQL using the password used by MythTV and it appeared to work (except I cannot find the instructions on how to check again, so if you'd like to post some I'll make extra sure).

If anyone is able to help I will be most grateful, so far using MythTV has been superb.

Thanks in advance

---

### Post by NT4usB on 2008-11-02
Do you have phpmyadmin installed? I use it to access and manage mysql. Runs in your browser. 

The command to connect but I don't recall any of the commands from there except they all begin with backslash \ 
like 
\quit 
to end session...```
mysql -u root -p
```

---

### Post by Elijah2104 on 2008-11-02
> **NT4usB said:**
> Do you have phpmyadmin installed? I use it to access and manage mysql. Runs in your browser. 

The command to connect but I don't recall any of the commands from there except they all begin with backslash \ 
like 
\quit 
to end session...```
mysql -u root -p
```

No, I don't have phpmyadmin.  So what do I need to do in the database to sort it out?  Do you think that is where the problem is?  (I guess it must be if it's the master backend! :) )

I found the command I used to connect to it before, using the password set in Mythfrontend and it was.

```
mysql -u mythtv -p
```

Of course, I still don't know what to do with it when I'm in there...

---

### Post by fenian on 2008-11-02
What is the output if you run the command...

> ps -p `cat /var/run/mythtv/mythbackend.pid`

Also can you post the contents of the log file at...

> more /var/log/mythtv/mythbackend.log

---

### Post by fenian on 2008-11-02
If you are getting the errors "No Upnp backends found" or "cannot log onto database"
try reconfiguring the mythtv database with the command...

> sudo dpkg-reconfigure mythtv-database

---

### Post by Elijah2104 on 2008-11-03
> **fenian said:**
> What is the output if you run the command...



Also can you post the contents of the log file at...

The output from

```
ps -p `cat /var/run/mythtv/mythbackend.pid` 
```

is

> 5944 ?        00:00:00 mythbackend <defunct>

and the log file...

> 2008-11-01 06:56:07.931 Reschedule requested for id -1.
2008-11-01 06:56:07.996 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 06:58:32.254 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 07:00:02.157 MainServer::HandleAnnounce Monitor
2008-11-01 07:00:02.162 adding: MMPC as a client (events: 0)
2008-11-01 07:01:14.511 Reschedule requested for id -1.
2008-11-01 07:01:14.574 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 07:08:34.293 Reschedule requested for id -1.
2008-11-01 07:08:34.359 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 07:10:02.196 MainServer::HandleAnnounce Monitor
2008-11-01 07:10:02.202 adding: MMPC as a client (events: 0)
2008-11-01 07:13:32.299 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 07:14:00.126 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 07:14:00.132 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 07:14:29.204 Reschedule requested for id -1.
2008-11-01 07:14:29.275 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 07:19:10.573 Reschedule requested for id -1.
2008-11-01 07:19:10.640 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 07:20:02.238 MainServer::HandleAnnounce Monitor
2008-11-01 07:20:02.242 adding: MMPC as a client (events: 0)
2008-11-01 07:22:06.705 Reschedule requested for id -1.
2008-11-01 07:22:06.774 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 07:26:09.233 Reschedule requested for id -1.
2008-11-01 07:26:09.296 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 07:28:32.345 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 07:28:39.266 Reschedule requested for id -1.
2008-11-01 07:28:39.561 Scheduled 15 items in 0.3 = 0.23 match + 0.06 place
2008-11-01 07:30:02.362 MainServer::HandleAnnounce Monitor
2008-11-01 07:30:02.366 adding: MMPC as a client (events: 0)
2008-11-01 07:33:57.271 Reschedule requested for id -1.
2008-11-01 07:33:57.574 Scheduled 15 items in 0.3 = 0.24 match + 0.07 place
2008-11-01 07:39:14.971 Reschedule requested for id -1.
2008-11-01 07:39:15.264 Scheduled 15 items in 0.3 = 0.23 match + 0.06 place
2008-11-01 07:40:02.399 MainServer::HandleAnnounce Monitor
2008-11-01 07:40:02.406 adding: MMPC as a client (events: 0)
2008-11-01 07:43:32.392 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 07:44:07.144 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 07:44:07.148 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 07:46:08.939 Reschedule requested for id -1.
2008-11-01 07:46:09.006 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 07:50:02.454 MainServer::HandleAnnounce Monitor
2008-11-01 07:50:02.462 adding: MMPC as a client (events: 0)
2008-11-01 07:51:06.401 Reschedule requested for id -1.
2008-11-01 07:51:06.464 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 07:55:08.516 Reschedule requested for id -1.
2008-11-01 07:55:08.583 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 07:58:32.433 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 08:00:02.588 MainServer::HandleAnnounce Monitor
2008-11-01 08:00:02.593 adding: MMPC as a client (events: 0)
2008-11-01 08:00:26.600 Reschedule requested for id -1.
2008-11-01 08:00:26.670 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:02:58.144 Reschedule requested for id -1.
2008-11-01 08:02:58.207 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 08:05:44.586 Reschedule requested for id -1.
2008-11-01 08:05:44.660 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:10:02.625 MainServer::HandleAnnounce Monitor
2008-11-01 08:10:02.634 adding: MMPC as a client (events: 0)
2008-11-01 08:11:02.426 Reschedule requested for id -1.
2008-11-01 08:11:02.716 Scheduled 15 items in 0.3 = 0.23 match + 0.06 place
2008-11-01 08:13:32.479 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 08:14:14.160 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 08:14:14.164 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 08:15:04.037 Reschedule requested for id -1.
2008-11-01 08:15:04.103 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:20:02.656 MainServer::HandleAnnounce Monitor
2008-11-01 08:20:02.658 adding: MMPC as a client (events: 0)
2008-11-01 08:21:06.794 Reschedule requested for id -1.
2008-11-01 08:21:06.858 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 08:26:09.307 Reschedule requested for id -1.
2008-11-01 08:26:09.372 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:28:32.522 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 08:30:02.696 MainServer::HandleAnnounce Monitor
2008-11-01 08:30:02.702 adding: MMPC as a client (events: 0)
2008-11-01 08:31:09.863 Reschedule requested for id -1.
2008-11-01 08:31:09.929 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:36:07.652 Reschedule requested for id -1.
2008-11-01 08:36:07.716 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:40:02.745 MainServer::HandleAnnounce Monitor
2008-11-01 08:40:02.750 adding: MMPC as a client (events: 0)
2008-11-01 08:41:05.858 Reschedule requested for id -1.
2008-11-01 08:41:05.925 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:43:32.566 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 08:43:53.563 Reschedule requested for id -1.
2008-11-01 08:43:53.628 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:44:20.176 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 08:44:20.179 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 08:49:11.657 Reschedule requested for id -1.
2008-11-01 08:49:11.724 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:50:02.777 MainServer::HandleAnnounce Monitor
2008-11-01 08:50:02.782 adding: MMPC as a client (events: 0)
2008-11-01 08:54:28.208 Reschedule requested for id -1.
2008-11-01 08:54:28.272 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 08:58:32.608 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 08:59:48.344 Reschedule requested for id -1.
2008-11-01 08:59:48.413 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:00:02.818 MainServer::HandleAnnounce Monitor
2008-11-01 09:00:02.826 adding: MMPC as a client (events: 0)
2008-11-01 09:02:56.428 Reschedule requested for id -1.
2008-11-01 09:02:56.491 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 09:10:02.882 MainServer::HandleAnnounce Monitor
2008-11-01 09:10:02.890 adding: MMPC as a client (events: 0)
2008-11-01 09:10:23.922 Reschedule requested for id -1.
2008-11-01 09:10:23.989 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:13:13.620 Reschedule requested for id -1.
2008-11-01 09:13:13.684 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:13:32.656 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 09:14:23.185 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 09:14:23.191 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 09:16:06.291 Reschedule requested for id -1.
2008-11-01 09:16:06.357 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:20:03.021 MainServer::HandleAnnounce Monitor
2008-11-01 09:20:03.026 adding: MMPC as a client (events: 0)
2008-11-01 09:21:07.738 Reschedule requested for id -1.
2008-11-01 09:21:07.805 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:25:11.836 Reschedule requested for id -1.
2008-11-01 09:25:11.904 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:28:32.697 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 09:30:02.061 MainServer::HandleAnnounce Monitor
2008-11-01 09:30:02.066 adding: MMPC as a client (events: 0)
2008-11-01 09:30:29.624 Reschedule requested for id -1.
2008-11-01 09:30:29.922 Scheduled 15 items in 0.3 = 0.23 match + 0.07 place
2008-11-01 09:36:51.175 Reschedule requested for id -1.
2008-11-01 09:36:51.238 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 09:40:02.104 MainServer::HandleAnnounce Monitor
2008-11-01 09:40:02.111 adding: MMPC as a client (events: 0)
2008-11-01 09:41:04.845 Reschedule requested for id -1.
2008-11-01 09:41:04.913 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:43:32.743 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 09:44:24.200 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 09:44:24.207 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 09:46:05.755 Reschedule requested for id -1.
2008-11-01 09:46:05.823 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:50:02.305 MainServer::HandleAnnounce Monitor
2008-11-01 09:50:02.309 adding: MMPC as a client (events: 0)
2008-11-01 09:51:07.439 Reschedule requested for id -1.
2008-11-01 09:51:07.506 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:54:36.250 Reschedule requested for id -1.
2008-11-01 09:54:36.318 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 09:58:05.223 Reschedule requested for id -1.
2008-11-01 09:58:05.289 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 09:58:32.786 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 10:00:02.393 MainServer::HandleAnnounce Monitor
2008-11-01 10:00:02.401 adding: MMPC as a client (events: 0)
2008-11-01 10:01:11.769 Reschedule requested for id -1.
2008-11-01 10:01:11.842 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:04:31.507 Reschedule requested for id -1.
2008-11-01 10:04:31.575 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:08:42.246 Reschedule requested for id -1.
2008-11-01 10:08:42.313 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:10:02.567 MainServer::HandleAnnounce Monitor
2008-11-01 10:10:02.573 adding: MMPC as a client (events: 0)
2008-11-01 10:11:19.918 Reschedule requested for id -1.
2008-11-01 10:11:19.987 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:13:32.836 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 10:13:58.263 Reschedule requested for id -1.
2008-11-01 10:13:58.336 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:14:31.210 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 10:14:31.219 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 10:18:10.317 Reschedule requested for id -1.
2008-11-01 10:18:10.618 Scheduled 15 items in 0.3 = 0.24 match + 0.06 place
2008-11-01 10:20:02.661 MainServer::HandleAnnounce Monitor
2008-11-01 10:20:02.665 adding: MMPC as a client (events: 0)
2008-11-01 10:21:05.677 Reschedule requested for id -1.
2008-11-01 10:21:05.759 Scheduled 15 items in 0.1 = 0.01 match + 0.07 place
2008-11-01 10:24:33.037 Reschedule requested for id -1.
2008-11-01 10:24:33.103 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 10:28:32.888 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 10:30:02.768 MainServer::HandleAnnounce Monitor
2008-11-01 10:30:02.773 adding: MMPC as a client (events: 0)
2008-11-01 10:31:28.737 Reschedule requested for id -1.
2008-11-01 10:31:28.808 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:35:10.517 Reschedule requested for id -1.
2008-11-01 10:35:10.583 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:40:02.855 MainServer::HandleAnnounce Monitor
2008-11-01 10:40:02.858 adding: MMPC as a client (events: 0)
2008-11-01 10:41:09.492 Reschedule requested for id -1.
2008-11-01 10:41:09.564 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:43:32.939 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 10:44:35.223 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 10:44:35.228 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 10:45:44.453 Reschedule requested for id -1.
2008-11-01 10:45:44.525 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:50:02.936 MainServer::HandleAnnounce Monitor
2008-11-01 10:50:02.941 adding: MMPC as a client (events: 0)
2008-11-01 10:51:26.185 Reschedule requested for id -1.
2008-11-01 10:51:26.252 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:55:15.117 Reschedule requested for id -1.
2008-11-01 10:55:15.187 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 10:58:32.990 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 11:00:02.076 MainServer::HandleAnnounce Monitor
2008-11-01 11:00:02.081 adding: MMPC as a client (events: 0)
2008-11-01 11:00:32.948 Reschedule requested for id -1.
2008-11-01 11:00:34.287 Scheduled 15 items in 1.3 = 1.27 match + 0.07 place
2008-11-01 11:03:47.194 Reschedule requested for id -1.
2008-11-01 11:03:47.260 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 11:06:57.851 Reschedule requested for id -1.
2008-11-01 11:06:57.917 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 11:10:02.128 MainServer::HandleAnnounce Monitor
2008-11-01 11:10:02.134 adding: MMPC as a client (events: 0)
2008-11-01 11:12:14.768 Reschedule requested for id -1.
2008-11-01 11:12:14.832 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 11:13:33.038 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 11:14:39.233 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 11:14:39.239 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 11:16:22.439 Reschedule requested for id -1.
2008-11-01 11:16:22.505 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 11:19:11.603 Reschedule requested for id -1.
2008-11-01 11:19:11.669 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 11:20:02.168 MainServer::HandleAnnounce Monitor
2008-11-01 11:20:02.170 adding: MMPC as a client (events: 0)
2008-11-01 11:22:48.873 Reschedule requested for id -1.
2008-11-01 11:22:48.941 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 11:28:33.086 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 11:29:57.282 Reschedule requested for id -1.
2008-11-01 11:29:57.346 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 11:30:02.267 MainServer::HandleAnnounce Monitor
2008-11-01 11:30:02.273 adding: MMPC as a client (events: 0)
2008-11-01 11:33:44.376 Reschedule requested for id -1.
2008-11-01 11:33:44.439 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 11:36:59.217 Reschedule requested for id -1.
2008-11-01 11:36:59.278 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 11:40:02.330 MainServer::HandleAnnounce Monitor
2008-11-01 11:40:02.337 adding: MMPC as a client (events: 0)
2008-11-01 11:41:12.628 Reschedule requested for id -1.
2008-11-01 11:41:12.691 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 11:43:33.131 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 11:44:34.362 Reschedule requested for id -1.
2008-11-01 11:44:34.425 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 11:44:42.246 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 11:44:42.251 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 11:49:18.566 Reschedule requested for id -1.
2008-11-01 11:49:18.629 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 11:50:02.368 MainServer::HandleAnnounce Monitor
2008-11-01 11:50:02.373 adding: MMPC as a client (events: 0)
2008-11-01 11:54:35.006 Reschedule requested for id -1.
2008-11-01 11:54:35.070 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 11:58:33.173 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 11:58:49.523 Reschedule requested for id -1.
2008-11-01 11:58:49.816 Scheduled 15 items in 0.3 = 0.23 match + 0.06 place
2008-11-01 12:00:02.500 MainServer::HandleAnnounce Monitor
2008-11-01 12:00:02.505 adding: MMPC as a client (events: 0)
2008-11-01 12:01:23.129 Reschedule requested for id -1.
2008-11-01 12:01:23.193 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 12:04:05.587 Reschedule requested for id -1.
2008-11-01 12:04:05.649 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 12:10:02.643 MainServer::HandleAnnounce Monitor
2008-11-01 12:10:02.646 adding: MMPC as a client (events: 0)
2008-11-01 12:11:07.156 Reschedule requested for id -1.
2008-11-01 12:11:07.219 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 12:13:33.219 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 12:14:49.254 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 12:14:49.259 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 12:15:48.007 Reschedule requested for id -1.
2008-11-01 12:15:48.071 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 12:20:01.253 Reschedule requested for id -1.
2008-11-01 12:20:01.568 Scheduled 15 items in 0.3 = 0.24 match + 0.08 place
2008-11-01 12:20:02.657 MainServer::HandleAnnounce Monitor
2008-11-01 12:20:02.662 adding: MMPC as a client (events: 0)
2008-11-01 12:24:05.184 Reschedule requested for id -1.
2008-11-01 12:24:05.244 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 12:28:33.261 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 12:30:02.709 MainServer::HandleAnnounce Monitor
2008-11-01 12:30:02.713 adding: MMPC as a client (events: 0)
2008-11-01 12:30:37.125 Reschedule requested for id -1.
2008-11-01 12:30:37.370 Scheduled 15 items in 0.2 = 0.19 match + 0.06 place
2008-11-01 12:35:54.912 Reschedule requested for id -1.
2008-11-01 12:35:54.983 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 12:40:02.823 MainServer::HandleAnnounce Monitor
2008-11-01 12:40:02.825 adding: MMPC as a client (events: 0)
2008-11-01 12:41:07.204 Reschedule requested for id -1.
2008-11-01 12:41:07.269 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 12:43:33.311 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 12:44:52.270 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 12:44:52.275 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 12:47:35.849 Reschedule requested for id -1.
2008-11-01 12:47:35.912 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 12:50:02.861 MainServer::HandleAnnounce Monitor
2008-11-01 12:50:02.865 adding: MMPC as a client (events: 0)
2008-11-01 12:51:05.536 Reschedule requested for id -1.
2008-11-01 12:51:05.596 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 12:58:33.358 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 12:58:47.554 Reschedule requested for id -1.
2008-11-01 12:58:47.617 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:00:02.885 MainServer::HandleAnnounce Monitor
2008-11-01 13:00:02.889 adding: MMPC as a client (events: 0)
2008-11-01 13:01:55.267 Reschedule requested for id -1.
2008-11-01 13:01:55.329 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:04:45.498 Reschedule requested for id -1.
2008-11-01 13:04:45.559 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:07:41.958 Reschedule requested for id -1.
2008-11-01 13:07:42.040 Scheduled 15 items in 0.1 = 0.02 match + 0.06 place
2008-11-01 13:10:02.923 MainServer::HandleAnnounce Monitor
2008-11-01 13:10:02.925 adding: MMPC as a client (events: 0)
2008-11-01 13:13:33.404 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 13:14:04.182 Reschedule requested for id -1.
2008-11-01 13:14:04.247 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:14:54.278 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 13:14:54.284 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 13:18:17.437 Reschedule requested for id -1.
2008-11-01 13:18:17.725 Scheduled 15 items in 0.3 = 0.23 match + 0.05 place
2008-11-01 13:20:01.957 MainServer::HandleAnnounce Monitor
2008-11-01 13:20:01.961 adding: MMPC as a client (events: 0)
2008-11-01 13:21:06.898 Reschedule requested for id -1.
2008-11-01 13:21:06.961 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:24:38.885 Reschedule requested for id -1.
2008-11-01 13:24:38.946 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:28:33.445 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 13:30:01.986 MainServer::HandleAnnounce Monitor
2008-11-01 13:30:01.989 adding: MMPC as a client (events: 0)
2008-11-01 13:31:11.386 Reschedule requested for id -1.
2008-11-01 13:31:11.451 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:33:56.228 Reschedule requested for id -1.
2008-11-01 13:33:56.288 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:40:02.018 MainServer::HandleAnnounce Monitor
2008-11-01 13:40:02.021 adding: MMPC as a client (events: 0)
2008-11-01 13:40:31.434 Reschedule requested for id -1.
2008-11-01 13:40:31.496 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:43:33.489 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 13:44:45.930 Reschedule requested for id -1.
2008-11-01 13:44:45.993 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:44:54.287 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 13:44:54.295 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 13:50:02.038 MainServer::HandleAnnounce Monitor
2008-11-01 13:50:02.045 adding: MMPC as a client (events: 0)
2008-11-01 13:51:10.002 Reschedule requested for id -1.
2008-11-01 13:51:10.066 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:56:24.453 Reschedule requested for id -1.
2008-11-01 13:56:24.513 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 13:58:33.536 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 13:59:52.558 Reschedule requested for id -1.
2008-11-01 13:59:52.621 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:00:02.042 MainServer::HandleAnnounce Monitor
2008-11-01 14:00:02.045 adding: MMPC as a client (events: 0)
2008-11-01 14:03:02.041 Reschedule requested for id -1.
2008-11-01 14:03:02.105 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:05:57.755 Reschedule requested for id -1.
2008-11-01 14:05:57.829 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 14:10:02.086 MainServer::HandleAnnounce Monitor
2008-11-01 14:10:02.093 adding: MMPC as a client (events: 0)
2008-11-01 14:11:05.657 Reschedule requested for id -1.
2008-11-01 14:11:05.721 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:13:33.582 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 14:14:54.841 Reschedule requested for id -1.
2008-11-01 14:14:54.904 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:14:59.298 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 14:14:59.304 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 14:18:03.711 Reschedule requested for id -1.
2008-11-01 14:18:03.775 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:20:02.127 MainServer::HandleAnnounce Monitor
2008-11-01 14:20:02.129 adding: MMPC as a client (events: 0)
2008-11-01 14:21:11.397 Reschedule requested for id -1.
2008-11-01 14:21:11.463 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:25:01.184 Reschedule requested for id -1.
2008-11-01 14:25:01.246 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:28:12.506 Reschedule requested for id -1.
2008-11-01 14:28:12.566 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:28:33.624 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 14:30:02.180 MainServer::HandleAnnounce Monitor
2008-11-01 14:30:02.185 adding: MMPC as a client (events: 0)
2008-11-01 14:31:25.583 Reschedule requested for id -1.
2008-11-01 14:31:25.645 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:37:00.930 Reschedule requested for id -1.
2008-11-01 14:37:00.992 Scheduled 15 items in 0.1 = 0.01 match + 0.05 place
2008-11-01 14:40:02.284 MainServer::HandleAnnounce Monitor
2008-11-01 14:40:02.289 adding: MMPC as a client (events: 0)
2008-11-01 14:43:33.671 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 14:44:34.186 Reschedule requested for id -1.
2008-11-01 14:44:34.285 Scheduled 15 items in 0.1 = 0.04 match + 0.06 place
2008-11-01 14:45:05.307 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 14:45:05.312 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 14:49:23.607 Reschedule requested for id -1.
2008-11-01 14:49:23.673 Scheduled 15 items in 0.1 = 0.01 match + 0.06 place
2008-11-01 14:50:02.445 MainServer::HandleAnnounce Monitor
2008-11-01 14:50:02.449 adding: MMPC as a client (events: 0)
2008-11-01 14:51:30.104 Using runtime prefix = /usr
2008-11-01 14:51:30.205 Empty LocalHostName.
2008-11-01 14:51:30.235 Using localhost value of MMPC
2008-11-01 14:51:30.322 New DB connection, total: 1
2008-11-01 14:51:30.362 Connected to database 'mythconverg' at host: localhost
2008-11-01 14:51:30.363 Closing DB connection named 'DBManager0'
2008-11-01 14:51:30.375 Connected to database 'mythconverg' at host: localhost
2008-11-01 14:51:30.384 New DB connection, total: 2
2008-11-01 14:51:30.405 Connected to database 'mythconverg' at host: localhost
2008-11-01 14:51:30.429 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 15:05:39.814 Using runtime prefix = /usr
2008-11-01 15:05:39.915 Empty LocalHostName.
2008-11-01 15:05:39.944 Using localhost value of MMPC
2008-11-01 15:05:40.085 New DB connection, total: 1
2008-11-01 15:05:40.089 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:05:40.114 Closing DB connection named 'DBManager0'
2008-11-01 15:05:40.116 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:05:40.123 New DB connection, total: 2
2008-11-01 15:05:40.132 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:05:40.171 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 15:09:10.726 Using runtime prefix = /usr
2008-11-01 15:09:10.730 Empty LocalHostName.
2008-11-01 15:09:10.738 Using localhost value of MMPC
2008-11-01 15:09:10.761 New DB connection, total: 1
2008-11-01 15:09:10.770 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:09:10.773 Closing DB connection named 'DBManager0'
2008-11-01 15:09:10.774 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:09:10.777 New DB connection, total: 2
2008-11-01 15:09:10.778 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:09:10.784 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 15:09:10.808 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:09:10.831 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:42:32.475 Using runtime prefix = /usr
2008-11-01 15:42:32.481 Empty LocalHostName.
2008-11-01 15:42:32.485 Using localhost value of MMPC
2008-11-01 15:42:32.502 New DB connection, total: 1
2008-11-01 15:42:32.535 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:42:32.539 Closing DB connection named 'DBManager0'
2008-11-01 15:42:32.540 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:42:32.544 New DB connection, total: 2
2008-11-01 15:42:32.545 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:42:32.550 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 15:42:32.572 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:42:32.581 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:42:32.583 DVBChan(3:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:42:32.586 DVBChan(4:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-01 15:42:33.868 Main::Registering HttpStatus Extension
2008-11-01 15:42:33.869 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-01 15:42:33.870 Enabled verbose msgs:  important general
2008-11-01 15:42:33.887 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 15:42:41.319 MainServer::HandleAnnounce Monitor
2008-11-01 15:42:41.716 adding: MMPC as a client (events: 0)
2008-11-01 15:42:41.717 MainServer::HandleAnnounce Monitor
2008-11-01 15:42:41.717 adding: MMPC as a client (events: 1)
2008-11-01 15:42:42.655 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 15:42:42.668 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 15:42:50.778 MainServer::HandleAnnounce Monitor
2008-11-01 15:42:50.782 adding: MMPC as a client (events: 0)
2008-11-01 15:42:50.783 MainServer::HandleAnnounce Monitor
2008-11-01 15:42:50.784 adding: MMPC as a client (events: 1)
2008-11-01 15:43:52.704 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 15:43:52.721 Expiring 64 MBytes for 9448 @ Fri Oct 31 14:35:00 2008 => The O.C. "The Test"
2008-11-01 15:43:52.732 New DB connection, total: 3
2008-11-01 15:43:52.743 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:45:55.817 Using runtime prefix = /usr
2008-11-01 15:45:55.831 Empty LocalHostName.
2008-11-01 15:45:55.848 Using localhost value of MMPC
2008-11-01 15:45:55.867 New DB connection, total: 1
2008-11-01 15:45:55.877 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:45:55.879 Closing DB connection named 'DBManager0'
2008-11-01 15:45:55.881 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:45:55.884 New DB connection, total: 2
2008-11-01 15:45:55.885 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:45:55.889 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 15:45:55.910 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:45:55.913 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:45:55.915 DVBChan(3:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:45:55.916 DVBChan(4:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-01 15:45:55.921 New DB connection, total: 3
2008-11-01 15:45:55.925 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:45:57.175 Main::Registering HttpStatus Extension
2008-11-01 15:45:57.176 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-01 15:45:57.183 Enabled verbose msgs:  important general
2008-11-01 15:45:57.186 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 15:46:15.313 Using runtime prefix = /usr
2008-11-01 15:46:15.318 Empty LocalHostName.
2008-11-01 15:46:15.321 Using localhost value of MMPC
2008-11-01 15:46:15.348 New DB connection, total: 1
2008-11-01 15:46:15.363 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:46:15.381 Closing DB connection named 'DBManager0'
2008-11-01 15:46:15.382 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:46:15.388 New DB connection, total: 2
2008-11-01 15:46:15.389 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:46:15.394 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 15:46:15.412 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:46:15.416 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:46:15.419 DVBChan(3:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:46:15.421 DVBChan(4:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-01 15:46:16.670 Main::Registering HttpStatus Extension
2008-11-01 15:46:16.671 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-01 15:46:16.672 Enabled verbose msgs:  important general
2008-11-01 15:46:16.675 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 15:46:25.463 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 15:46:25.465 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 15:47:03.897 Using runtime prefix = /usr
2008-11-01 15:47:03.902 Empty LocalHostName.
2008-11-01 15:47:03.904 Using localhost value of MMPC
2008-11-01 15:47:03.922 New DB connection, total: 1
2008-11-01 15:47:03.936 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:47:03.940 Closing DB connection named 'DBManager0'
2008-11-01 15:47:03.942 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:47:03.946 New DB connection, total: 2
2008-11-01 15:47:03.947 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:47:03.971 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 15:47:04.019 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:47:04.023 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:47:04.028 DVBChan(3:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:47:04.034 DVBChan(4:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-01 15:47:05.311 Main::Registering HttpStatus Extension
2008-11-01 15:47:05.312 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-01 15:47:05.316 Enabled verbose msgs:  important general
2008-11-01 15:47:05.325 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 15:47:14.004 DB Error (Error clearing channel locks):
Query was:
DELETE FROM eit_cache WHERE status  = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-11-01 15:47:14.014 DB Error (JobQueue::CleanupOldJobsInQueue: Error deleting old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (272, 288, 320) AND statustime < '2008-10-30T15:47:14') OR (status in (304) AND statustime < '2008-10-28T15:47:14')
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-11-01 15:47:14.016 DB Error (HouseKeeper Cleaning TVChain Table):
Query was:
SELECT DISTINCT chainid FROM tvchain WHERE endtime > '2008-11-01T11:47:14' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-11-01 15:47:14.016 DB Error (Housekeeper Creating Temporary Table):
Query was:
CREATE TEMPORARY TABLE IF NOT EXISTS temprecordedcleanup ( chanid int(10) unsigned NOT NULL default '0', starttime datetime NOT NULL default '0000-00-00 00:00:00' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2008-11-01 15:47:14.022 New DB connection, total: 3
2008-11-01 15:47:14.022 Unable to connect to database!
2008-11-01 15:47:14.023 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
2008-11-01 15:47:14.059 New DB connection, total: 4
2008-11-01 15:47:14.060 Unable to connect to database!
2008-11-01 15:47:14.060 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-11-01 15:47:14.081 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-11-01 15:47:14.094 New DB connection, total: 5
2008-11-01 15:47:14.096 Unable to connect to database!
2008-11-01 15:47:14.096 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-11-01 15:47:14.120 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-11-01 15:47:14.137 Database not open while trying to load setting: CleanOldRecorded
2008-11-01 15:47:14.143 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

QSqlQuery::exec: database not open
2008-11-01 15:47:14.156 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-11-01 15:47:14.173 Database not open while trying to load setting: JobQueueCheckFrequency
2008-11-01 15:47:14.177 Unable to connect to database!
2008-11-01 15:47:14.183 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
2008-11-01 15:47:14.207 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
QSqlQuery::exec: database not open
2008-11-01 15:47:14.248 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-11-01 15:47:14.305 Database not open while trying to load setting: JobQueueMaxSimultaneousJobs
2008-11-01 15:47:14.306 Unable to connect to database!
2008-11-01 15:47:14.315 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-11-01 15:47:14.372 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-11-01 15:47:14.441 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
No error type from QSqlError?  Strange...
2008-11-01 15:48:17.865 Using runtime prefix = /usr
2008-11-01 15:48:17.953 Empty LocalHostName.
2008-11-01 15:48:17.981 Using localhost value of MMPC
2008-11-01 15:48:18.070 New DB connection, total: 1
2008-11-01 15:48:18.110 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:48:18.124 Closing DB connection named 'DBManager0'
2008-11-01 15:48:18.125 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:48:18.138 New DB connection, total: 2
2008-11-01 15:48:18.159 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:48:18.183 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 15:54:57.182 Using runtime prefix = /usr
2008-11-01 15:54:57.187 Empty LocalHostName.
2008-11-01 15:54:57.205 Using localhost value of MMPC
2008-11-01 15:54:57.224 New DB connection, total: 1
2008-11-01 15:54:57.232 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:54:57.234 Closing DB connection named 'DBManager0'
2008-11-01 15:54:57.236 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:54:57.239 New DB connection, total: 2
2008-11-01 15:54:57.240 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:54:57.245 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 15:54:57.270 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:54:57.303 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 15:58:20.901 Using runtime prefix = /usr
2008-11-01 15:58:20.984 Empty LocalHostName.
2008-11-01 15:58:21.020 Using localhost value of MMPC
2008-11-01 15:58:21.101 New DB connection, total: 1
2008-11-01 15:58:21.153 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:58:21.155 Closing DB connection named 'DBManager0'
2008-11-01 15:58:21.157 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:58:21.169 New DB connection, total: 2
2008-11-01 15:58:21.190 Connected to database 'mythconverg' at host: localhost
2008-11-01 15:58:21.214 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 16:08:26.860 Using runtime prefix = /usr
2008-11-01 16:08:26.865 Empty LocalHostName.
2008-11-01 16:08:26.866 Using localhost value of MMPC
2008-11-01 16:08:26.884 New DB connection, total: 1
2008-11-01 16:08:26.904 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:08:26.916 Closing DB connection named 'DBManager0'
2008-11-01 16:08:26.931 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:08:26.934 New DB connection, total: 2
2008-11-01 16:08:26.944 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:08:26.952 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 16:08:26.973 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:08:26.999 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:22:39.604 Using runtime prefix = /usr
2008-11-01 16:22:39.609 Empty LocalHostName.
2008-11-01 16:22:39.631 Using localhost value of MMPC
2008-11-01 16:22:39.653 New DB connection, total: 1
2008-11-01 16:22:39.661 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:22:39.666 Closing DB connection named 'DBManager0'
2008-11-01 16:22:39.671 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:22:39.679 New DB connection, total: 2
2008-11-01 16:22:39.683 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:22:39.692 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 16:22:39.711 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:22:39.714 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:22:39.725 DVBChan(3:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:22:39.732 DVBChan(4:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-01 16:22:39.745 New DB connection, total: 3
2008-11-01 16:22:39.750 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:22:41.009 Main::Registering HttpStatus Extension
2008-11-01 16:22:41.011 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-01 16:22:41.011 Enabled verbose msgs:  important general
2008-11-01 16:22:41.026 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 16:22:47.304 MainServer::HandleAnnounce Monitor
2008-11-01 16:22:47.784 adding: MMPC as a client (events: 0)
2008-11-01 16:22:47.785 MainServer::HandleAnnounce Monitor
2008-11-01 16:22:47.785 adding: MMPC as a client (events: 1)
2008-11-01 16:22:49.805 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 16:22:49.819 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 16:23:59.758 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 16:27:48.878 MainServer::HandleAnnounce Monitor
2008-11-01 16:27:48.881 adding: MMPC as a client (events: 0)
2008-11-01 16:27:48.881 MainServer::HandleAnnounce Monitor
2008-11-01 16:27:48.882 adding: MMPC as a client (events: 1)
2008-11-01 16:28:12.239 MainServer::HandleAnnounce Monitor
2008-11-01 16:28:12.240 adding: MMPC as a client (events: 0)
2008-11-01 16:28:12.249 MainServer::HandleAnnounce Monitor
2008-11-01 16:28:12.254 adding: MMPC as a client (events: 1)
2008-11-01 16:28:12.261 Reloading backend settings
2008-11-01 16:29:15.033 Using runtime prefix = /usr
2008-11-01 16:29:15.038 Empty LocalHostName.
2008-11-01 16:29:15.039 Using localhost value of MMPC
2008-11-01 16:29:15.057 New DB connection, total: 1
2008-11-01 16:29:15.066 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:29:15.068 Closing DB connection named 'DBManager0'
2008-11-01 16:29:15.070 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:29:15.073 New DB connection, total: 2
2008-11-01 16:29:15.074 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:29:15.079 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 16:29:15.104 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:29:15.107 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:29:15.108 DVBChan(3:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:29:15.110 DVBChan(4:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-11-01 16:29:16.360 Main::Registering HttpStatus Extension
2008-11-01 16:29:16.361 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-01 16:29:16.368 Enabled verbose msgs:  important general
2008-11-01 16:29:16.377 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 16:29:25.155 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-01 16:29:25.159 UPnpMedia: BuildMediaMap Done. Found 1 objects
2008-11-01 16:30:02.641 MainServer::HandleAnnounce Monitor
2008-11-01 16:30:02.644 adding: MMPC as a client (events: 0)
2008-11-01 16:30:35.115 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 16:30:35.127 Expiring 1411 MBytes for 9448 @ Fri Oct 31 15:30:00 2008 => Gilmore Girls "But I'm a Gilmore!"
2008-11-01 16:30:35.136 New DB connection, total: 3
2008-11-01 16:30:35.143 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:32:05.312 Using runtime prefix = /usr
2008-11-01 16:32:05.318 Empty LocalHostName.
2008-11-01 16:32:05.324 Using localhost value of MMPC
2008-11-01 16:32:05.347 New DB connection, total: 1
2008-11-01 16:32:05.355 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:32:05.358 Closing DB connection named 'DBManager0'
2008-11-01 16:32:05.367 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:32:05.374 New DB connection, total: 2
2008-11-01 16:32:05.378 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:32:05.387 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 16:32:05.400 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:32:05.409 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:32:05.415 DVBChan(3:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-01 16:32:05.421 DVBChan(4:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
QServerSocket: failed to bind or listen to the socket
2008-11-01 16:32:05.446 MediaServer::HttpServer Create Error
2008-11-01 16:32:05.450 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-01 16:32:05.456 Enabled verbose msgs:  important general
2008-11-01 16:32:05.465 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-01 16:36:16.936 Using runtime prefix = /usr
2008-11-01 16:36:17.025 Empty LocalHostName.
2008-11-01 16:36:17.053 Using localhost value of MMPC
2008-11-01 16:36:17.136 New DB connection, total: 1
2008-11-01 16:36:17.176 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:36:17.177 Closing DB connection named 'DBManager0'
2008-11-01 16:36:17.178 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:36:17.186 New DB connection, total: 2
2008-11-01 16:36:17.189 Connected to database 'mythconverg' at host: localhost
2008-11-01 16:36:17.227 Current Schema Version: 1214
Starting up as the master server.
2008-11-01 16:36:27.601 New DB connection, total: 3
2008-11-01 16:36:27.753 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:02:45.733 Using runtime prefix = /usr
2008-11-02 16:02:45.821 Empty LocalHostName.
2008-11-02 16:02:45.840 Using localhost value of MMPC
2008-11-02 16:02:45.914 New DB connection, total: 1
2008-11-02 16:02:45.967 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:02:45.972 Closing DB connection named 'DBManager0'
2008-11-02 16:02:45.974 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:02:45.988 New DB connection, total: 2
2008-11-02 16:02:46.009 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:02:46.033 Current Schema Version: 1214
Starting up as the master server.
2008-11-02 16:02:56.254 New DB connection, total: 3
2008-11-02 16:02:56.501 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:11:47.181 Using runtime prefix = /usr
2008-11-02 16:11:47.186 Empty LocalHostName.
2008-11-02 16:11:47.187 Using localhost value of MMPC
2008-11-02 16:11:47.205 New DB connection, total: 1
2008-11-02 16:11:47.223 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:11:47.226 Closing DB connection named 'DBManager0'
2008-11-02 16:11:47.228 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:11:47.231 New DB connection, total: 2
2008-11-02 16:11:47.232 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:11:47.264 Current Schema Version: 1214
Starting up as the master server.
2008-11-02 16:11:47.306 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-02 16:11:47.331 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-02 16:11:57.295 New DB connection, total: 3
2008-11-02 16:11:57.297 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:27:14.746 Using runtime prefix = /usr
2008-11-02 16:27:14.835 Empty LocalHostName.
2008-11-02 16:27:14.863 Using localhost value of MMPC
2008-11-02 16:27:14.993 New DB connection, total: 1
2008-11-02 16:27:15.019 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:27:15.020 Closing DB connection named 'DBManager0'
2008-11-02 16:27:15.021 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:27:15.032 New DB connection, total: 2
2008-11-02 16:27:15.046 Connected to database 'mythconverg' at host: localhost
2008-11-02 16:27:15.085 Current Schema Version: 1214
Starting up as the master server.
2008-11-02 16:27:25.501 New DB connection, total: 3
2008-11-02 16:27:25.648 Connected to database 'mythconverg' at host: localhost
2008-11-02 19:47:04.882 Using runtime prefix = /usr
2008-11-02 19:47:04.971 Empty LocalHostName.
2008-11-02 19:47:04.999 Using localhost value of MMPC
2008-11-02 19:47:05.141 New DB connection, total: 1
2008-11-02 19:47:05.167 Connected to database 'mythconverg' at host: localhost
2008-11-02 19:47:05.168 Closing DB connection named 'DBManager0'
2008-11-02 19:47:05.169 Connected to database 'mythconverg' at host: localhost
2008-11-02 19:47:05.179 New DB connection, total: 2
2008-11-02 19:47:05.200 Connected to database 'mythconverg' at host: localhost
2008-11-02 19:47:05.238 Current Schema Version: 1214
Starting up as the master server.
2008-11-02 19:47:15.720 New DB connection, total: 3
2008-11-02 19:47:15.777 Connected to database 'mythconverg' at host: localhost
2008-11-02 20:58:10.797 New DB connection, total: 4
2008-11-02 20:58:11.102 Connected to database 'mythconverg' at host: localhost
2008-11-03 17:12:23.968 Using runtime prefix = /usr
2008-11-03 17:12:24.057 Empty LocalHostName.
2008-11-03 17:12:24.091 Using localhost value of MMPC
2008-11-03 17:12:24.174 New DB connection, total: 1
2008-11-03 17:12:24.227 Connected to database 'mythconverg' at host: localhost
2008-11-03 17:12:24.228 Closing DB connection named 'DBManager0'
2008-11-03 17:12:24.229 Connected to database 'mythconverg' at host: localhost
2008-11-03 17:12:24.242 New DB connection, total: 2
2008-11-03 17:12:24.263 Connected to database 'mythconverg' at host: localhost
2008-11-03 17:12:24.276 Current Schema Version: 1214
Starting up as the master server.
2008-11-03 17:12:34.495 New DB connection, total: 3
2008-11-03 17:12:34.536 Connected to database 'mythconverg' at host: localhost

I've had a look through for the errors you mentioned but I can't see them.  It also appears to be saying that it connected to the database ok?

---

### Post by fenian on 2008-11-03
One quick question;did you change the IP address in both the bavkend and the frontend of mythtv?

---

### Post by Elijah2104 on 2008-11-03
> **fenian said:**
> One quick question;did you change the IP address in both the bavkend and the frontend of mythtv?

Well it's always been set to LocalHost as the client and backend are the same machined but not to rule it out I tried it anyway and still nothing.

---

### Post by fenian on 2008-11-03
The IP address should be set to 127.0.0.1 on the backend if both the frontend and backend are on the same machine and you are not connecting to this backend from a frontend on another machine.To do this start mythbackend setup and the first screen in the general section is where you set the IP address.

On the frontend you want to set the Hostname as localhost,do this start mythfrontend ,go to Utilities/Setup>Settings>General>second page (Database Configuration)
set the Hostname to localhost
also on this page leave the port field blank.

---

### Post by Elijah2104 on 2008-11-03
> **fenian said:**
> The IP address should be set to 127.0.0.1 on the backend if both the frontend and backend are on the same machine and you are not connecting to this backend from a frontend on another machine.To do this start mythbackend setup and the first screen in the general section is where you set the IP address.

On the frontend you want to set the Hostname as localhost,do this start mythfrontend ,go to Utilities/Setup>Settings>General>second page (Database Configuration)
set the Hostname to localhost
also on this page leave the port field blank.

Yes I've set it to this already to at least make sure it's not a routing issue.  The backend is set to 127.0.0.1 and the frontend is and always has been set to localhost and it still says there is a problem connecting to the master backend.

Previously, before I ran the update, the backend was set to it's fixed IP from the router and the frontend was set to locahost and this worked a treat.

Athough, the front/back ends are on the same computer I also plan to put the client on other remote machines so I will need to go back to the fixed IP when I get onto that part.

---

### Post by fenian on 2008-11-03
Did you run the reconfigure database command?

> sudo dpkg-reconfigure mythtv-database 

---

### Post by Elijah2104 on 2008-11-03
> **fenian said:**
> Did you run the reconfigure database command?

Sorry, yes I have and no change.  Interestingly, I've also noticed that when I go into the backend configuration, it also says that it couldn't connect to the master backend.

---

### Post by Scorpuk on 2008-11-06
> **fenian said:**
> Did you run the reconfigure database command?


When you ran this did it prompt you for the current mythtv databasse password, or has it created a new one for it?


Might be why the problems with:

> ...it also says that it couldn't connect to the master backend. 

Just a guess. (Check /etc/mythtv/mysql.txt - this will give you your database password)


Anywho.


Couple of sugestions:

1. Try the following command:

```
sudo /etc/init.d/mythtvbackend restart
```

Do this command twice and post the results please.

2. Install mythweb and see if that can connect to the backend.
3. If that works try a complete removal of frontend and then re-install it. (not sure how you do this in mythubuntu)

---

### Post by Elijah2104 on 2008-11-07
> **Scorpuk said:**
> When you ran this did it prompt you for the current mythtv databasse password, or has it created a new one for it?


Might be why the problems with:



Just a guess. (Check /etc/mythtv/mysql.txt - this will give you your database password)


Anywho.


Couple of sugestions:

1. Try the following command:

```
sudo /etc/init.d/mythtvbackend restart
```

Do this command twice and post the results please.

2. Install mythweb and see if that can connect to the backend.
3. If that works try a complete removal of frontend and then re-install it. (not sure how you do this in mythubuntu)

Ok, the username mythtv and the configured password definitely allow me access to MySql.  I double checked the password listed in the text file and it matches the one I was trying to use.  I then typed (just to be sure...)

```
mysql -u mythtv -p
``` with the necessary password and it gave me a mysql prompt.  Not knowing how to use mysql, I didn't do anything else from there except quit.

I typed in the command you suggested but it gives tells me command not found.  So, I then changed to the directory /etc/init.d and saw that there was a mythtv-backend listed in green (why green?) so I thought it could have been a typo but ```
sudo mythtv-backend restart
``` still gave me command not found.  If it wasn't already apparent, I'm a bit new to linux :)

I did try typing ```
mythbackend
``` and it gave me:

> 2008-11-07 18:07:21.301 Using runtime prefix = /usr
2008-11-07 18:07:21.302 Empty LocalHostName.
2008-11-07 18:07:21.302 Using localhost value of MMPC
2008-11-07 18:07:21.319 New DB connection, total: 1
2008-11-07 18:07:21.326 Connected to database 'mythconverg' at host: localhost
2008-11-07 18:07:21.328 Closing DB connection named 'DBManager0'
2008-11-07 18:07:21.351 Connected to database 'mythconverg' at host: localhost
2008-11-07 18:07:21.353 New DB connection, total: 2
2008-11-07 18:07:21.354 Connected to database 'mythconverg' at host: localhost
2008-11-07 18:07:21.357 Current Schema Version: 1214
Starting up as the master server.
2008-11-07 18:07:21.392 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-07 18:07:21.394 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-07 18:07:21.395 DVBChan(3:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-11-07 18:07:21.396 DVBChan(4:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
QServerSocket: failed to bind or listen to the socket
2008-11-07 18:07:21.408 MediaServer::HttpServer Create Error
2008-11-07 18:07:21.408 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-07 18:07:21.408 Enabled verbose msgs:  important general
2008-11-07 18:07:21.410 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-11-07 18:07:21.412 Failed to bind port 6543. Exiting.

I don't know if that means anything relevant?

MythWeb tells me: 

> Error
Unable to connect to the master backend at 192.168.0.3:6543.
Is it running?


I haven't tried a frontend removal yet as the other stuff didn't work and I assume it's a problem with my back end.  As it were.

---

### Post by Elijah2104 on 2008-11-07
> 
1. Try the following command:

```
sudo /etc/init.d/mythtvbackend restart
```

Do this command twice and post the results please.



I just went in to myth backend set up again and changed the IP address to 127.0.0.1 again (which I thought I'd left it at for now, already).  I restarted the machine, it took a little longer to boot for some reason.

Mythfrontend still gives the same problems so I tried your command again, except with the - in it.

```
sudo /etc/init.d/mythtv-backend restart
```

I did this twice, as requested.  This time I got:
> 
 * Restarting MythTV server: mythbackend
No /usr/bin/mythbackend found running; none killed.      [OK]

This was the same message both times.  Why was it returning command not found last time?  

Trying to connect to MythWeb from a remote computer (same as last time) only gives a page title of Welcome to MythWeb! but it sits, perpetually trying to load but no error this time.  From the local host, however, which I neglected to try before, it lods ok.  I can see all the recording schedules I've programmed in and the programmes I've recorded.

I will now try to re-install mythfrontend like you suggested, if I can work out how :)

---

### Post by Elijah2104 on 2008-11-07
This is what I did.  I went into the synaptic package manager and marked mythfontend for reinstallation and then I applied it.  When I went into mythfontend afterwards, it "blinked" when I tried to watch TV instead of giving the error message.  I tried some of the other options.  Music and DVDs worked ok as they always have, I don't believe I could view any recordings before, and I could see them now, nor see the programme guide whilst scheduling programmes, but it loaded this time.  It then hung again as I started to scroll through it.  So I rebooted.  When I tried again, it came back with the could not connect to master backend again.

So next I went back into synaptic package manager and marked Mythfrontend, Mythbackend and Mythbackend-master for reinstallation.  Then I went into mythtv set up.

I didn't mention before but it also gives me a message which I'd not seen back when it was working before the update.  It says

> WARNING:  MythTV has detected that the backend is running.

Changing existing cards input, deleting anything or scanning for channels may then the message ends???  Whilst in the setup programme, I went into look at the capture cards I have installed to check that it could still see them.  Selecting either of the cards caused setup to hang.

So I'm not sure if I'm any further forward or not to be honest but the bottom line is it still won't connect to the master backend to watch or record TV or view the recordings (it can't see them again now???) and it still says cannot connect, blah, blah blah.

---

### Post by Scorpuk on 2008-11-08
Heh my boob. It was mythtv-backend as you discovered. :D


Anywho getting the result that its not running twice will mean its not running.



Looking at the log you got when running mythbackend it doesnt look good...

> 2008-11-07 18:07:21.392 DVBChan(1:0) Error: Opening DVB frontend device failed.
eno: Device or resource busy (16)
2008-11-07 18:07:21.394 DVBChan(2:0) Error: Opening DVB frontend device failed.
eno: Device or resource busy (16)
2008-11-07 18:07:21.395 DVBChan(3:1) Error: Opening DVB frontend device failed.
eno: Device or resource busy (16)
2008-11-07 18:07:21.396 DVBChan(4:1) Error: Opening DVB frontend device failed.
eno: Device or resource busy (16)


Can you try the DVB cards in another program to ensure they are still working?


With mythbuntu you will probably have to install a desktop (ubuntu) where you could then install Kaffeine and see how it goes with your dvb cards.


It may come down to a reinstall of the backend too... Do you have a lot of recordings or wouldnt you mind loosing them? :o

Will have another think over a pint tonight :)

---

### Post by Elijah2104 on 2008-11-08
It wouldn't be the end of the world to lose the recordings.  I'd just be happy to get the poxy thing running again.

I noticed those messages too, I was hoping it just meant that "something" had them and wasn't letting go :)

In order to get the card working in the first place I had to follow the instructions from [here]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Installing") perhaps I should give those another go.

---

### Post by Elijah2104 on 2008-11-08
I remembered this from the card's installation instructions so I gave it a try.  This is the output

> dmesg | grep -i dvb
[   30.143325] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   31.022851] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   31.729725] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   31.729772] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   31.730091] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   31.844394] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   32.380784] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   32.380965] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   32.386656] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   32.947731] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:0a.2/usb3/3-1/input/input7
[   32.994429] dvb-usb: schedule remote query interval to 150 msecs.
[   32.994435] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   32.994696] usbcore: registered new interface driver dvb_usb_dib0700
[   44.525727]  [<ffffffff88bc3190>] :dvb_core:dvb_frontend_open+0x230/0x2a0
[   44.525745] Modules linked in: nfsd auth_rpcgss exportfs ipv6 powernow_k8 cpufreq_ondemand cpufreq_stats cpufreq_userspace cpufreq_powersave freq_table cpufreq_conservative container video output sbs sbshc dock battery nfs lockd nfs_acl sunrpc iptable_filter ip_tables x_tables ac sbp2 lp ieee80211_rtl ieee80211_crypt_ccmp_rtl ieee80211_crypt_tkip_rtl ieee80211_crypt_wep_rtl ieee80211_crypt_rtl mt2060 arc4 ecb blkcipher rtl8187 mac80211 dvb_usb_dib0700 dib7000p dib7000m dvb_usb dvb_core dib3000mc dibx000_common cfg80211 dib0070 eeprom_93cx6 hci_usb bluetooth snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm wmi_acer snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd nvidia(P) serio_raw parport_pc parport psmouse i2c_core button k8temp soundcore pcspkr shpchp pci_hotplug evdev ext3 jbd mbcache usb_storage sr_mod cdrom sg sd_mod pata_amd pata_acpi usbhid hid libusual ohci1394 ieee1394 forcedeth ata_generic ahci uhci_hcd libata scsi_mod ohci_hcd ehci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   44.525791] RIP: 0010:[<ffffffff88bc3190>]  [<ffffffff88bc3190>] :dvb_core:dvb_frontend_open+0x230/0x2a0
[   44.525837]  [<ffffffff88bbc6dc>] :dvb_core:dvb_device_open+0xcc/0x140
[   44.525887] RIP  [<ffffffff88bc3190>] :dvb_core:dvb_frontend_open+0x230/0x2a0


It looks a lot different to how it used to.  Does it mean anything to you?

---

### Post by Elijah2104 on 2008-11-08
Success!  By following the instructions to re-install the TV card, it has begun working again.

Thanks so much for your help.

---

### Post by Elijah2104 on 2008-11-08
Ok how do I mark this as solved?!

---

### Post by NT4usB on 2008-11-10
Thread Tools, upper right.

---

### Post by Elijah2104 on 2008-11-11
I must have looked that that about 15 times and completely missed it every time.  Thanks.

---

