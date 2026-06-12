---
title: "Can't Shutdown, Reboot, or Logout (Ubuntu 16.04). Recent Install"
date: 2016-05-16
forum: New to Ubuntu
---

### Post by reshuler on 2016-05-16
HI,

After a recent install of Ubuntu 16.04, my system is not able to Shutdown, Reboot, or Logout with a hang.  When running everything works as expected.  

During a Shutdown, Reboot, or Logout out there is message displayed that says "NMI watchdog: BUG: soft lockup - CPU5 stuck for 22s! [plymounthd].  This the cpu number changes from time to time.  There is also message that the about a stall on a cpu.

Occasionally, the system will Shutdown, Reboot, or Logout without issue, but this is very rare. 

I have to hold down the power button until the system shuts off in all cases.

Any help would be greatly appreciated.

System:
Dell Inspiron 15 7000 model 7579
16GB RAM
480GB SSD - holds '/', '/boot', '/boot/efi', and swap
960GB SSD - holds '/home'


Thanks,
Robert

---

### Post by houstonbofh on 2016-05-16
My first reaction is an unstable system. (Usually power supply) An example at [http://ubuntuforums.org/showthread.php?t=2205211](http://ubuntuforums.org/showthread.php?t=2205211)

That said, 16.04 has quite a few bugs, and I did find this in a few seconds of searching...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1530405](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1530405)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1495696](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1495696)

I would start with some CPU stress tests under 14.04 live-cd, and possibly replacing the power supply.  But keep an eye on launchpad as well.

---

### Post by wamacdonald on 2016-07-05
I have this same exact issue on similar hardware ([COLOR=#000000]Dell Inspiron 15 7000 model 7579)[/COLOR]. I've tested and had similar problems on Ubuntu 14.04 as well. Has anyone found a solution? Not able to suspend either, otherwise works fine.

Thanks

---

### Post by rokclimb15 on 2016-07-07
[http://askubuntu.com/questions/761312/ubuntu-16-04-skylake-not-able-to-shutdown-and-restart](http://askubuntu.com/questions/761312/ubuntu-16-04-skylake-not-able-to-shutdown-and-restart)

---

