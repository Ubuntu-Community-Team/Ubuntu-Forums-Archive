---
title: "Xorg.0.log"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by ub newb on 2008-08-25
I hope I don't win the stupidest newb question award, but please tell me if this is something that I should expect to see with my ubuntu installatio? I have a log called Xorg.0.log and I have been looking for info to try and understand what it is and I seem to get the idea from what I have read that it is some kind of server configuration? 

Is this an expected part of the ubuntu desktop installation? Is there any reason that I should have this on my pc when I have no interest in running as a server? 




Here is the first part of the entry in this log. It is apparently an installation log? 


X.Org X Server 1.4.0.90 
Release Date: 5 September 2007 
X Protocol Version 11, Revision 0 
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2) 
Current Operating System: Linux MDdesktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 
Build Date: 13 June 2008  01:08:21AM 
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) 
	to make sure that you have the latest version. 
Module Loader present 
Markers: (--) probed, (**) from config file, (==) default setting, 
	(++) from command line, (!!) notice, (II) informational, 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 25 06:21:44 2008 
(==) Using config file: "/etc/X11/xorg.conf" 
(==) ServerLayout "Default Layout" 
(**) |-->Screen "Default Screen" (0) 
(**) |   |-->Monitor "Configured Monitor" 
(**) |   |-->Device "Configured Video Device" 
(==) Automatically adding devices 
(==) Automatically enabling devices 
(==) No FontPath specified.  Using compiled-in default.

Thank you very much for your time.

---

### Post by Nepherte on 2008-08-25
I'm not really sure what the question is but if you mean if it's normal to see a log file, then the answer is yes. A lot of programs/daemons/services keep log files. If you encounter a problem with a certain program, it is most likely logged in such a file. Though the existence of such a file, doesn't mean there actually is a problem. It might also contain warnings, version numbers, dates and times when the program is launched or shut down, etc...

Most log files are kept in the directory /var/log but other locations are possible as well.

---

### Post by porchrat on 2008-08-25
the X.Org server is the server for your X windows.  It has to do with your desktop and yes as Nepherte says, it needs a log file so that if something ever goes wrong with it you can look and there and see what happened.

---

### Post by amo-ej1 on 2008-08-25
This isn't an installation log, it is the output of the Xorg server startup (the graphical environment) if you scroll through it you will see the Xorg server try to locate your graphics card, your screen(s), your pointer, your mouse and certain font locations. Next to this some information regarding your graphics card will be printed (which settings detected etc etc). This is in general used to troubleshoot problems with an X server startup and it created/overwritten after each start of the X-server.

---

### Post by prshah on 2008-08-25
> **ub newb said:**
>  from what I have read that it is some kind of server configuration? 

This has nothing to do with a "server" as in a network.

In Ubuntu (linux), a lot of things are split into two parts; one, which interacts with you, and an invisible other, that interacts with the hardware/data/information. This second invisible part is called a server. For example:

a) scanning in Ubuntu is done using SANE: Sane runs in two parts, one is a server that does the actual scanning process etc, and a second front-end that takes parameters from you, passes it to the "SANE server" and receives the scanned file, which is shown to you.

b) MythTV stores information about programs and schedules in an invisible "MySQL server".

And so on... as you can see, the "server" is a logical concept, and refers to any program that "serves" information/data/services.

In this case, your entire GUI experience is provided by X; the X-server manages everything in the background, invisible to you, but the lifeblood of Window Managers and other programs that display stuff to you, take input from you, act on that, etc etc.

So in short, your desktop is not being mis-utilised!

---

### Post by ub newb on 2008-08-25
What wonderful and quick answers.

Especially you, prshaw. Your willingness to explain the basics is so kind. 

Thanks to you all!
This new ub newb world view is awesome-r by the day.:=D>

---

