---
title: "Dual Boot Time Workaround"
date: 2009-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Tu1J4kXk8NUhMz on 2009-09-06
If any of you dual boot Ubuntu with Windows (or triple with OS X), you'll notice that your computer lives in a time warp. Here's why:

[http://ubuntuforums.org/showthread.php?t=1254464]("http://ubuntuforums.org/showthread.php?t=1254464")

(Thanks tgalati4)

Local time is right now. I mean right now...now. N-..Now. UTC is a base time from which all other time zones can be derived from by adding or subtracting hours. Windows finds the local time, then stores it in BIOS. Ubuntu then looks at the BIOS, and adjusts, assuming the time is not local but UTC (AKA GMT). 

Since I refuse to change other things to fit Windows standards, I hunted down how to switch Windows time to UTC.

[http://ccgi.maxpower.plus.com/2007/04/30/dual-booting-causes-clocks-to-go-mental/]("http://ccgi.maxpower.plus.com/2007/04/30/dual-booting-causes-clocks-to-go-mental/")

After a brief explanation, the author tells us to create a text file containing the following:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation]
"RealTimeIsUniversal"=dword:00000001
```

Save the file as **time.reg**, then double-click it. Hit "Okay" on those warnings; you know what you're doing. Reboot (making sure the time is proper before you do), and Windows should be alright. Test it by booting into Ubuntu then Windows to check the time.

In reading, I've found some users have issues with this solution. Nothing serious, just the time clock in Windows getting confused from time to time. I have yet to experience any of these issues, though.

If you'd prefer to change Ubuntu settings, here's the way to go:

[http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/]("http://www.shivaranjan.com/2009/06/20/how-to-prevent-ubuntu-linux-from-resetting-or-changing-computer%E2%80%99s-bios-or-hardware-clock/")

Open the Terminal and type in the following:

```
sudo gedit /etc/default/rcS
```

Hunt down the line which reads **UTC=yes**. Change **yes** to **no** and save. Again, best to check the time and reboot. And again, I don't cater to Microsoft or Windows system standards, so I haven't tried this. If anyone does, please post how well this works.

There you are. A couple simple solutions to an annoying (at best) issue when dual booting.

And BTW: If you ARE triple booting and need to adjust the Mac OS X time, you're on your own. You can try this:

[http://wiki.osx86project.org/wiki/index.php/Tips_And_Tricks#Use_Localtime_instead_of_Universal_for_RTC]("http://wiki.osx86project.org/wiki/index.php/Tips_And_Tricks#Use_Localtime_instead_of_Universal_for_RTC")

I suspect this is only a scripting work around. I couldn't find anything more effective than this. If anyone tries this, please post how it works.

---

### Post by Tu1J4kXk8NUhMz on 2009-09-17
I just upgraded to Windows Vista, and have experienced the problem of time jumping around in the clock. I am sticking to my guns, of course, but using the Unix workarounds might prove to be a more useful option for some. I would like to point out, however, that with Windows 7 in the near future a more appropriate Windows workaround may present itself.

I will poke around in my copy of Win7 to see if there is a viable option...

---

