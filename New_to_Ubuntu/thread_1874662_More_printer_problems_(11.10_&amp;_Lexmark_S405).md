---
title: "More printer problems (11.10 &amp; Lexmark S405)"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by MrLeek on 2011-11-03
Seems like lots of people are having printer issues since the upgrade to 11.10. Can't say I know for certain how I managed to get it to print when I first switched to ubuntu about 3 months ago (still new so be gentle).

Anyways I managed to get the drivers that can be downloaded from Lexmark to work (turns out there's a typo in the script that makes it all run - thanks to [https://answers.launchpad.net/ubuntu/+source/cups/+question/176071](https://answers.launchpad.net/ubuntu/+source/cups/+question/176071) in helping to get to the fix a little quicker.

Now it can scan in documents which I couldn't do before! But it still won't print! When you try to add the printer manually (or by running the script/driver) you get an error box (sorry, haven't worked out how to crop screenshots yet):

"The action is not supported by this backend. Please report a bug as this should not have happened. Provides postcript-driver not supported".

In newbie speak it's saying "well, I know what it is...but I don't have a clue on how to print stuff off it!". But how can I fix it?

---

### Post by jnorthr on 2011-11-04
it may be possible to gain further clues as to the mystery of this issue. If you can open a console terminal from START > ACCESSORIES > TERMINAL

then you can key in a command to look into the system log file. This is a file of audit messages that the kernel produces as it works thru the day. The messages that appear at the bottom of the log are the newest. We can see these messages by typing in the command

dmesg

which should spew loggile messages to your console. The last ones are most inportant. Once you learn how to do this, you can then play with your printer and see different messages that might appear in the log as a result of your tests. With those messages, we can more clearly understand your problem and offer suggestions.

UPDATE: see this link: [http://ubuntuforums.org/showthread.php?t=1869131](http://ubuntuforums.org/showthread.php?t=1869131)
item 10 may offer you more clues. thought i remembered someone else who had printer issues recently - theirs was a Canon printer, so it may not be quite as relevant, but you can see printer related messages there.

---

### Post by jnorthr on 2011-11-04
more clues here: if you click start?system tools > printing  then when the printer utility starts you can click the HELP menu choice which should give you a menu called trouble-shooting printing. This will be the same display of messages as seen in item 10 of my prior link.

---

### Post by MrLeek on 2011-11-09
Sorry jnorthr - been tied up helping to write a newbie guide to security ([http://ubuntuforums.org/showthread.php?t=1873643](http://ubuntuforums.org/showthread.php?t=1873643))!

Trying to make sense out of what I'm reading (still finding things a challenge) but I did pull out the following from one of the logs:

```
   	 	 	 	 	 	  [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.121" (uid=7 pid=18410 comm="Lexmark_S405 45 mrleek Test Page 1 PageSize=Letter ") interface="org.freedesktop.ColorManager" member="FindDeviceById" error name="(unset)" requested_reply="0" destination="org.freedesktop.ColorManager" (uid=120 pid=2103 comm="/usr/lib/x86_64-linux-gnu/colord/colord ")
 
```

Clearly something's not happy here! Following the link that you highlighted, I pulled this out:

```
   	 	 	 	 	 	                 "W [09/Nov/2011:19:01:32 +0000] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_S405_Gray__' has already been added", 
                "W [09/Nov/2011:19:01:32 +0000] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_S405_RGB__' has already been added"]

```


So I think i'm on the right track to identify the problem....got no clue how to fix it though!!

---

### Post by MrLeek on 2011-11-21
Dislike bumping...but there it is....:(

I've still got this problem. I've read up on how proposed bug fixes involving upgrading the kernel will fix this. I've also tried to install it via CUPS. I even tried the auto-detect - which picks up that I'm plugging in a printer, but there's no drivers available....and I've got the stupid drivers from Lexmark (which have been run countless times). If I read up on any more "solutions" that I need to spend time translating my eyes will bleed!

Fed up, confused...and this printer worked just fine with 11.04. In fact, I can connect it to my laptop and it's all configured within 2 minutes without me doing anything.

According to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872711) it's fixed.....except I'm in the exact same place I was when I started! 

Help??

---

### Post by funkyflo on 2011-12-28
I have the same problem with my  lexmark 2600 Series usb printer.
After I fixed an apparmour bug i still get error by 

[B]tail -f /var/log/auth.log

[/B]```

Dec 28 14:35:52 flo dbus[932]: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.81" (uid=7 pid=5695 comm="Lexmark-2600-Series 8 florian 001687 RG301826 Glin") interface="org.freedesktop.ColorManager" member="FindDeviceById" error name="(unset)" requested_reply="0" destination="org.freedesktop.ColorManager" (uid=102 pid=997 comm="/usr/lib/i386-linux-gnu/colord/colord ")


```What does that mean with the color manager? How can i get my lexmark 2600 series printer to work?
I use the latest ubuntu LTS 64 bit


Thanks
Flo

---

### Post by Sleepy-zz-John on 2011-12-30
> **jnorthr said:**
> more clues here: if you click start?system tools > printing  then when the printer utility starts you can click the HELP menu choice which should give you a menu called trouble-shooting printing. This will be the same display of messages as seen in item 10 of my prior link.

In my 11:10 Ocelot,  my "system tools" doesn't have a "printing" option.  There's "System Settings" -> "Printers" but everything is greyed out there and I can't find any HELP.   The basic question I have is how to get started on installing a printer.... any printer??

---

### Post by archimedes1981 on 2011-12-30
hi i have a problem with my HP deskjet. hardware is fine. works on WinXP. I used it previously on Mandriva. Since I installed Kubuntu 10 I can't install it. I downloaded lots of packages and stuff and tried hp-check and hp-setup. I however don't know how to interpret the terminal outputs I get like:
dmesg | grep parp
[   18.247704] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE,EPP]
[   18.248281] parport0: irq 7 detected
[   18.737877] parport0: Legacy device
[   18.738646] lp0: using parport0 (polling).

if only I knew what calls what I might be able to climb up to the problem.
Please help I need printer urgently.

HP Linux Imaging and Printing System (ver. 3.10.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)


--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)
  2         par         Parallel Port (LPT:)                                      

Enter number 0...2 for connection type (q=quit, enter=usb*) ? 2

Using connection type: par

error: No device selected/specified or that supports this functionality.

---

