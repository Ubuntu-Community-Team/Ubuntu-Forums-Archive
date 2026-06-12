---
title: "Will not turn off"
date: 2018-08-14
forum: New to Ubuntu
---

### Post by dave6 on 2018-08-14
Clean install of Mate, BUT, it will not turn off and takes "what feels like ever" to get to switching every thing off then stalls.

I don't "maybe" mind waiting on the thing, to hit the kill switch and give it a full OFF, but the first wait time "see first screen shot" if that could be lowered to 1 sec then turn off would be OK

Dave

---

### Post by Dennis N on 2018-08-14
Many others also have this annoying problem. Bug report:

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400)

Some further explanation in this post:

[https://ubuntuforums.org/showthread.php?t=2397009&p=13786681#post13786681](https://ubuntuforums.org/showthread.php?t=2397009&p=13786681#post13786681)

Also search with Google using the "a stop job is running for session c1" message to see many other reports.

---

### Post by dave6 on 2018-08-14
Hi Dennis N
Thanks for your reply, this time round I will try and get some thing done about it (Switch off, or the lack off)  Did I ever say I hate computers but they are an evil which is now required 
In your other post to me you stated.......
"search for

   DefaultTimeoutStartSec=
   DefaultTimeoutStopSec=
   TimeoutSec=

   and enter lower values

Good luck!

Could you explain more in how to "search for" ? please

Dave

---

### Post by Dennis N on 2018-08-14
You need to open **/etc/systemd/system.conf** in a text editor. To make changes, you need to have elevated privileges (sudo).

The comments at the start of the file (below) say you can edit this file. Be sure to remove the # at the start of the line if you change a value otherwise it won't be recognized. A changed file is below:

```
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See systemd-system.conf(5) for details.

[Manager]
#LogLevel=info
#LogTarget=journal-or-kmsg
#LogColor=yes
#LogLocation=no
#DumpCore=yes
#ShowStatus=yes
#CrashChangeVT=no
#CrashShell=no
#CrashReboot=no
#CtrlAltDelBurstAction=reboot-force
#CPUAffinity=1 2
#JoinControllers=cpu,cpuacct net_cls,net_prio
#RuntimeWatchdogSec=0
#ShutdownWatchdogSec=10min
#CapabilityBoundingSet=
#NoNewPrivileges=no
#SystemCallArchitectures=
#TimerSlackNSec=
#DefaultTimerAccuracySec=1min
#DefaultStandardOutput=journal
#DefaultStandardError=inherit
#DefaultTimeouttartSec=90s
DefaultTimeoutStopSec=5s
#DefaultRestartSec=100ms
#DefaultStartLimitIntervalSec=10s
#DefaultStartLimitBurst=5
#DefaultEnvironment=
#DefaultCPUAccounting=no
#DefaultIOAccounting=no
#DefaultIPAccounting=no
#DefaultBlockIOAccounting=no
#DefaultMemoryAccounting=yes
#DefaultTasksAccounting=yes
#DefaultTasksMax=15%
#DefaultLimitCPU=
#DefaultLimitFSIZE=
#DefaultLimitDATA=
#DefaultLimitSTACK=
#DefaultLimitCORE=
#DefaultLimitRSS=
#DefaultLimitNOFILE=
#DefaultLimitAS=
#DefaultLimitNPROC=
#DefaultLimitMEMLOCK=
#DefaultLimitLOCKS=
#DefaultLimitSIGPENDING=
#DefaultLimitMSGQUEUE=
#DefaultLimitNICE=
#DefaultLimitRTPRIO=
#DefaultLimitRTTIME=
#IPAddressAllow=
#IPAddressDeny=


```"search for" just means "look for". The file on this computer only has the first two of those items - "TimeoutSec=" is missing.

Change the number in those two items from 90s to whatever you want, and save the file. (I only changed one value)

Seemed to help in Ubuntu as there were no further delays in the shutdown time so far (maybe 10-15 boots since ). But in Manjaro, it seemed to do nothing.  So we'll see.

---

### Post by dave6 on 2018-08-22
Thanks Dennis N,  I got round to looking for that file and found it, but I am blowed if I know how to log in as sudo, or Root ?
As you know it is a "Read Only" file.  I try ed using the test editor pluma which comes in Mate, file system can't be seen.  So I then went computer / file system and then the rest.

Any help to tell me how to log in as Root or Sudo would be great
Dave

---

### Post by oldrocker99 on 2018-08-22
You might try nano, which is built-in. The menu buttons are not intuitive, but just look at them and you'll easily figure it out.
```
sudo nano [name of file]
```

---

### Post by Dennis N on 2018-08-22
You might as well learn to use nano text editor, which runs in the terminal. Practice on a some text file you make in your home folder with Pluma before actually trying it on the real thing.

cd to the folder containing the file to edit.
open file with:
**nano <filename>**
use **sudo nano <filename>** when you need to be root.

use arrows to navigate, use delete and backspace to erase characters.

when done, **Ctrl+O** will save changes. To quit, use **Ctrl+X**.

On the system file in question,

start the terminal.
cd to: **/etc/systemd/**
type: **sudo nano system.conf**

Navigate to the correct line, edit, save the changes, and quit.
You need to delete the # at start of line, and then change 90s to 5s
If you mess something up, quit without saving and start over.

Its easy.

---

### Post by dave6 on 2018-08-22
Thanks guys, did try it ! but nothing worked ? edited to happen ?

Dave

---

### Post by Dennis N on 2018-08-22
> **dave6 said:**
> Thanks guys, did try it ! but nothing worked ?

Dave
**cd** in the first step means 'change directory', so you start by typing 
```
**cd /etc/systemd**
```
Again, If you never used nano before,  I suggest you create a text file with Pluma to practice on.

---

### Post by dave6 on 2018-08-22
Dennis N, as you can see, I got the line changed down to 5 sec, but when  I turn the computer off and providing it don't freeze I hit the Esc key  and see this.

A stop job is running for Session c1 of user dave ( "clock" /1min 29s)

The first time I typed in cd to: etc/systemd.......... so now I know why nothing happen

There  is one thing I must say, back in the old days, you had a hard switch to  turn the computer off, I think it is time that came back, think of the  power that would be saved world wide

Dave

---

### Post by Dennis N on 2018-08-22
> as you can see, I got the line changed down to 5 sec, but when I turn the computer off and providing it don't freeze I hit the Esc key and see this.
A stop job is running for Session c1 of user dave ( "clock" /1min 29s)

You probably need to restart the computer - settings may only be read at startup. 

If it still stalls and says 1min 30sec for the time, then that suggests the settings in there aren't used, even though the comments at the top of the file say you can change the defaut timeout by editing the file. I haven't seen this message again since I changed the timeout in Ubuntu. But, I don't use the regular Ubuntu every day either, so I can't say for sure the change is working. 

The whole systemd thing is so complex. I still have Xubuntu 14.04 installed, and it runs perfectly and predictably with upstart. No systemd.

Manjaro had a systemd update, and I haven't seen the problem in that OS since then. Keeping my fingers crossed.

---

### Post by dave6 on 2018-08-23
Hi Dennis N:  I un-done it, then redone it as you said, then it worked, still does not stop it from freezing on turn off half of the time that I have turned this thing off and then back on, but when it is working I can hear the computer click ready for the hard switch off.

Dave

---

### Post by Dennis N on 2018-08-23
> **dave6 said:**
> Hi Dennis N:  I un-done it, then redone it as you said, then it worked, still does not stop it from freezing on turn off half of the time that I have turned this thing off and then back on, but when it is working I can hear the computer click ready for the hard switch off.

Dave

In my case, Ubuntu 18.04 always turned off by itself if I wait the 1 min 30 sec. Experts tell us frequent hard shut down with power switch is not good, and can have bad consequences. If had to use power switch to shut down, I would avoid using that OS on a regular basis - maybe install an older supported release like Ubuntu MATE 16.04 (I never saw this problem there) and try again with 18.10 or a later 18.04 point release. You could also try another Ubuntu flavor like Xubuntu or Lubuntu, or even try another Linux distro entirely. Closest to Ubuntu MATE is Linux Mint MATE. 

I booted Ubuntu again (haven't used it for a few days) and still good: normal shutdown, no delay at all. Haven't seen that stop job message reappear, so maybe some update helped? On the other hand, could have shutdown delay again next time.

---

