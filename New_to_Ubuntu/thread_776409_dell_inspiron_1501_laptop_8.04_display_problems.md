---
title: "dell inspiron 1501 laptop 8.04 display problems"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by eugenemcl1 on 2008-04-30
Hi

Total newbie here so please bear with me.  I've installed 8.04 over vista, vista installed first.

Belarc advisor tells me that my display is :-

RADEON XPRESS 200M Series (Microsoft Corporation - WDDM) [Display adapter] Generic PnP Monitor (19.7"vis)

After an itermitttent time when logged into vista the screen goes haywire flashing random squares, lines, screen flashing.  I have to shutdown using the power button.  This never appened without linux on my laptop, please help

Thanks

Eugene :confused:

---

### Post by markharding557 on 2008-04-30
remove vista completley problem gone

---

### Post by eugenemcl1 on 2008-05-01
Not very helpful.....

Please review and give me some advice.:(:(

---

### Post by aberry5555 on 2008-05-01
I don't think this has anything to do with linux... unless you somehow managed to corrupt your hard-drive whilst installing which is unlikely and wouldn't usually give you these results if it had. As a precaution, to check, start up vista and, in the search box in the start menu, type in CMD. when you get a black box with a command line pop up type in ```
chkdsk /r
``` This program scans your hard-drive for errors and attempts to fix any corrupt files. It will only scan your windows partition and cannot be made to work with linux partitions. It'll ask you if you want to schedule a scan on your next reboot, answer yes and reboot, then let it scan. Once you're back in vista go back to that black box again (press start, type cmd in the search box) and type in ```
sfc /scannow 
```and let it run. SFC is a program that checks all system files to see if they are intact or corrupt and replaces them when needed, so if there are any you may need to stick your vista cd in to replace them. After this if you're still having problems then you'll need to send your laptop back to your manufacturer.

By the sounds of it, unfortunately, it's a hardware problem, not a software problem so I'm not sure any of this will help but it's worth a shot.

Good luck and let us know if this helps :)

---

### Post by eugenemcl1 on 2008-05-02
Thanks I'll try it this evening and let you know how I get on..

---

### Post by eugenemcl1 on 2008-05-07
> **aberry5555 said:**
> I don't think this has anything to do with linux... unless you somehow managed to corrupt your hard-drive whilst installing which is unlikely and wouldn't usually give you these results if it had. As a precaution, to check, start up vista and, in the search box in the start menu, type in CMD. when you get a black box with a command line pop up type in ```
chkdsk /r
``` This program scans your hard-drive for errors and attempts to fix any corrupt files. It will only scan your windows partition and cannot be made to work with linux partitions. It'll ask you if you want to schedule a scan on your next reboot, answer yes and reboot, then let it scan. Once you're back in vista go back to that black box again (press start, type cmd in the search box) and type in ```
sfc /scannow 
```and let it run. SFC is a program that checks all system files to see if they are intact or corrupt and replaces them when needed, so if there are any you may need to stick your vista cd in to replace them. After this if you're still having problems then you'll need to send your laptop back to your manufacturer.

By the sounds of it, unfortunately, it's a hardware problem, not a software problem so I'm not sure any of this will help but it's worth a shot.

Good luck and let us know if this helps :)
Hi

I ran the chkdsk /r and sfc /scannow.  No errors.
I have noticed it only happens when vista has gone ito hibernate / standby mode

Any ideas

Thanks

---

