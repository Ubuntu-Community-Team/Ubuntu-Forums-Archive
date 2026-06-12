---
title: "[SOLVED] ntp activation"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2008-06-12
I have installed ntp using the Adjust Date Time applet, but am told I now have to 'activate' it.  How is this done, please.  Hardy user if that matters.

---

### Post by cariboo on 2008-06-12
Perhaps you've selected a server that requires some sort of activation. I just set it up using time.nrc.ca and I was never asked for anything. Maybe you should try a different time server.

Jim

---

### Post by Dedoimedo on 2008-06-12
Hello,

Does this help:

sudo /etc/init.d/ntpd start

Cheers,
Dedoimedo

---

### Post by Dumpy Dumpster on 2008-06-12
Thanks both, the 'start' worked a treat.

---

### Post by CCC999 on 2008-12-19
For others that may be mis-lead, after installing NTP, close the clock applet. Then open the clock as if to adjust the time. The interface may have changed, allowing you to select a time server. For me, I did not have to activate anything, nor open terminal.

---

### Post by crashcoredump on 2009-01-21
I see this is an older thread but I too when configuring my Ubuntu box as both a client and server needed to close the time GUI and edit the /etc/ntp.conf manually and restart ntpd with 
root@frobnitz:~# /etc/init.d/ntp restart
 * Stopping NTP server ntpd                                                [ OK ] 
 * Starting NTP server ntpd                                                [ OK ] 
root@frobnitz:~# date
Wed Jan 21 18:17:57 PST 2009

Good advice 
Thanks

---

### Post by Andrew_P on 2009-08-06
> **Dedoimedo said:**
> Hello,

Does this help:

sudo /etc/init.d/ntpd start

Cheers,
Dedoimedo

:confused:
I tried this in Ubuntu 8.10 (Intrepid Ibex) and it didn't work:  there's no "ntpd" in /etc/init.d

Instead, try this:
     sudo /etc/init.d/ntp start

To restart the ntp daemon without rebooting, type:
     sudo /etc/init.d/ntp restart

---

