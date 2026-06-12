---
title: "Zoom (meeting software) suddenly runs slowly (effectively useless)"
date: 2020-01-23
forum: New to Ubuntu
---

### Post by kbarber3 on 2020-01-23
I've been using Zoom without difficulty until this morning.  A long delay in comments arriving (both ways) led us to decide to end a meeting and restart.  On trying to restart the meeting, Zoom became so slow it had effectively hung completely.  No other web-using software (Firefox, Thunderbird) have any issues.

Just about any combination of shutting down Zoom, restarting computer, uninstalling & reinstalling Zoom has been ineffective.

On starting Zoom, both KSysGuard and System Monitor show 2 Zoom files.  Process ID 26946 uses 148K memory and 1896K shared memory, Process ID 26953 uses 132M memory and almost 120M shared memory.  Unfortunately I never looked at Zoom before I had trouble so have no idea whether these are as expected.

On trying to start a meeting, the KSysGuard Network History shows somewhere around 133KB/s Receiving (typically varying between 129 and 134 with occasional peaks & troughs.  Process ID 26953 increases to almost 160M memory and 137M shared memory.

System has Intel Core i5-9600K @ 3.7GHz, 6 core, GeForce GT 1030/PCIe/SSE2, GNOME 3.28.2, Budgie desktop on Ubuntu 18.04.3

If any more information is needed please give me an idea where/how to find it (and whether I need to install software to get to it).

Any help with this would be appreciated.  My knowledge of Linux is pretty slim (just changed from Windows 7), I don't see myself as any kind of power user or IT knowledgeable, my preference is to use Linux but to interact with it at the level of a Windows user, for whom it's a tool, not a matter of interest in itself.

---

### Post by kbarber3 on 2020-01-27
Definitely my bad.  Complete power down seems to have done the job where restart didn't.:oops:

---

### Post by kbarber3 on 2020-01-30
Looks as if I spoke too soon.  Zoom has gone back to hanging completely when I start a meeting (it gets to a black screen but doesn't go on to start the video, and all buttons are unresponsive).  I learn from a client trying to log in to a meeting that I am recorded as being present, but they get only a dark screen and no sound passes either way.  Neither restart nor complete power-down (including switching off the power supply unit in addition to the shut-down routine) change things.

Reading the hints for information required, I see I should have added that my Linux is factory-installed on a computer (Tuxedo) that was new in November 2019.

---

