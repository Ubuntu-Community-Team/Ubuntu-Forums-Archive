---
title: "Scheduled boot: possible?"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by Priest Apostate on 2014-03-13
Is it possible to schedule a server to boot up (NOT reboot) at a certain time?

---

### Post by sotiris2 on 2014-03-13
That would have to be done via your bios if possible. There are some that have the ability to 'wake' in a specific time and after that ubuntu should boot by default. Alternatively you could have it via lan.

---

### Post by Lars Noodén on 2014-03-13
The Wake-On-LAN is called just that.  It's also abbreviated as WOL.  Most but not all network cards support it and you may have to adjust some settings in the BIOS.  Also for it to work, the machine sending the signal has to be on the same LAN, it won't work over the open Internet or even across two different LANs.  So if you can't set automatic startup with the hardware, you might be able to give the machine a wakeup call from another machine which is already on.  

Also about the built-in startup, be sure to check the time properly.  The system clock is usually running in UTC so your wakeup alarm may also have to be set UTC.

---

### Post by matt_symes on 2014-03-13
Hi

As stated, If your BIOS supports it, you can boot using the CMOS rtc.

Take a look at ```
rtcwake
```

.. or you can write directly to

```
/sys/class/rtc/rtc0/wakealarm
```

Below is a technique that i use. Assuming your BIOS supports it try this from the terminal

```
sudo bash -c "echo $(date '+%s' -d '+ 5 minutes') > /sys/class/rtc/rtc0/wakealarm"
```

Shutdown your PC and see if it wakes after 5 minutes. 

You can use absolute times as well. The times are in epoc time.

Kind regards

---

### Post by Priest Apostate on 2014-03-13
Thanks for pointing me in the right direction to research further!

---

