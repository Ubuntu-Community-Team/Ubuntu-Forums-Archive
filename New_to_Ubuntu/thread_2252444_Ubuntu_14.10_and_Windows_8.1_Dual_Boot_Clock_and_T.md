---
title: "Ubuntu 14.10 and Windows 8.1 Dual Boot Clock and Time Problem"
date: 2014-11-11
forum: New to Ubuntu
---

### Post by krishnandu.sarkar on 2014-11-11
Hi All, I'm facing time difference problem between Windows and Ubuntu.

First of all I'd like to say that I have already tried modifying /etc/default/rcS, but surprisingly it's already UTC = no. Still I'm facing a time difference of few hours and have no idea what to do.

In both the OS I have internet time sync enabled. If I sync time from one OS, it gets different in another OS.

---

### Post by T.J. on 2014-11-12
I consider this a bug when " UTC = no" is specified in rcS.  I've seen the same bug as far back as 2011.  Try checking /etc/adjtime to see if the clock line specifies UTC rather than LOCAL. Changing it to LOCAL should resolve the problems after you resync your computer's clock.  Unfortunately, while most operating systems function on Universal Time, Windows does not.

Best Wishes,
TJ

---

### Post by krishnandu.sarkar on 2014-11-13
> **T.J. said:**
> I consider this a bug when " UTC = no" is specified in rcS.  I've seen the same bug as far back as 2011.  Try checking /etc/adjtime to see if the clock line specifies UTC rather than LOCAL. Changing it to LOCAL should resolve the problems after you resync your computer's clock.  Unfortunately, while most operating systems function on Universal Time, Windows does not.

Best Wishes,
TJ

Thanks a lot. But /etc/adjtime file is not there in my system :(

---

### Post by oldfred on 2014-11-13
Have you tried resetting Windows to use UTC?

[https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)

---

### Post by krishnandu.sarkar on 2014-11-14
> **oldfred said:**
> Have you tried resetting Windows to use UTC?

[https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)

Nope. As I didn't wanted to change anything in Windows. It's ok I'll try that.

But I really do not have any idea, why Ubuntu is not using Localtime (I don't know what time it's using, local or UTC) instead of setting UTC=no in /etc/default/rcS

Also, as you can see in the URL provided by you, is not going to help much. As I can't disable Windows Time Service.

> **Note:**[COLOR=#333333][FONT=Ubuntu] This method was not initially supported on Windows Vista and Server 2008, but came back with Vista SP2, Windows 7, Server 2008 R2 and Windows 8/8.1.[/FONT][/COLOR]
> **Note:**[COLOR=#333333][FONT=Ubuntu] Windows Time service will still write local time to the RTC regardless of the registry setting above on shutdown, so it is handy to disable Windows Time service with this command (if time sync is still required while in Windows use any third-party time sync solution):[/FONT][/COLOR]

Arch works perfectly fine, but I have no idea what's the problem with Ubuntu.

---

### Post by kiran-sankar-das on 2014-12-11
I don't know if it is already solved or not but here is what solved my problem.

First set UTC=no in/etc/default/rcS and reboot.

This unlinks your system clock from hardware clock.

Now Sync system system clock with internet. (Just wait for sometime with internet connected and it does automatically).

Last remains is to set hardware clock to system clock as it is now not being set automatically after unlinking from system clock (UTC=no) so for that run following commands

> sudo hwclock --systohc

I think now, Windows which uses hw clock as default will show correct time.

---

