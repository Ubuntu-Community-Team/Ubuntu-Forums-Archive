---
title: "How to schedule Ubuntu to turn on itself automatically from a suspension?"
date: 2015-10-10
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-10-10
Hello guys 
Is there a way which enables me to schedule Ubuntu to turn on automatically from a suspension? Let's say I suspend it by 10 PM and I want it to be turned on by 7 AM.
Thank you

---

### Post by tgalati4 on 2015-10-10
When the computer is sleeping, the CPU is halted, so there is no program that you can run to wake it.  However, many computers have a BIOS setting that allows boot at a specific time.  Boot into BIOS and look at your scheduling options.  

Another method is to use Wake-on-Lan.  Have another computer (such as a RaspberryPi) send the WoL wakeup packet at the appointed time to the sleeping computer.  Some routers have WoL capability, so look at your router as well.  Even your phone can send WoL packets, but I'm not sure there are scheduling options with the phone WoL apps.  That you will have to investigate.

---

### Post by mastablasta on 2015-10-12
actually rtcwake can do it: [http://linux.die.net/man/8/rtcwake](http://linux.die.net/man/8/rtcwake)

I am not sure exactly how it works (does it influence BIOS?!) anyway. the easiest way is to do it in BIOS/UEFI.

---

