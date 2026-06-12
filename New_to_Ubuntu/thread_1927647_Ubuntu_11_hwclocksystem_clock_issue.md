---
title: "Ubuntu 11 hwclock/system clock issue"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by d4m on 2012-02-18
I'm a sorta new to linux, but I am very good with search engines.

I'm trying to run a small game server and I keep running into issues involving the system clock as well as the hardware clock which causes hiccups of lag in the game server at set intervals, roughly every 2-3 seconds or so.

What I've tried.
installed ntp, verified server is running, set multiple servers for time.
result: NTP doesn't seem to be able to handle the drift of the clocks.  My system clock drifts 9000ms per minute and NTP doesn't slew quickly enough to compensate.

Set a crontab to adjust the time every minute.  Time was set, but the server still lagged and ran slower than it should be.  Seemed like there was a slightly time slowdown in the game.  Removed the crontab entry when it didn't fix the issue.

installed adjtimex to try to get the clocks closer together for NTP.
Checked difference between hwclock and system clock.  The drift requires larger paramters for tick and freq than the hardware can handle.  Clock can only take up to 11000 ticks.  I need to set it to around 11700 to offset the time difference with adjtimex.  Doing a 11000 tick adjustment the drift is now only -70000ppm and not -181000ppm, but still to much drift for NTP to keep up with over a length of time.

I'm not sure what else to do.

Is this as simple as going to the store and getting a new CMOS battery for the mother board?  It is an old *** motherboard.  Pushing 6 years easily.

[EDIT]Replaced the CMOS battery since it was 5min and $5.  Couldn't hurt. Seems as it the hwclock doesn't not drift now.  3 minutes and not a second off drift, much better than before when you could see the drift just using a stop watch.  system clock still shows an error ppm of -73000 with adjtimex -c at tick 11000 freq 32000000

[EDIT2] Found only 1 CPU from dual core was being seen in /proc/cpuinfo.  Added boot parameters for nolapic, etc.  2nd core now seen.  Error PPMs dropped to -69000 now with same adjtimex settings.  hwclock does drift, but the drift is now maybe 60 seconds over the course of an hour.

Is there a jedi knight that can help this padawan?

---

### Post by d4m on 2012-02-23
Been a few days.  Don't mean to bump, but can anyone point me in the right direction?  

I've exceeded my knowledge and ability to search, and the solutions I did find I have tried to implement with limited success as I posted previously.


I have a temporary solution with crontab and adjtimex, but its just a band-aid.  I want to understand what is wrong and fix it.

[EDIT]
Something has changed with the clock.  adjtimex -c now shows only a -22000 PPM error without any updates or changes that I've made.  Both are getting closer, but still running slow.  Anyone know if the hp pavillion a1630n has any bios updates?  the hp site only seems to have windows support files.

---

