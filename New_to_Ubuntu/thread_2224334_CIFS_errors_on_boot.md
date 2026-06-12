---
title: "CIFS errors on boot"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by stevecrt on 2014-05-15
Hi Guys

I managed to mount my network drives and they are all accessible without a problem, after adding the necessary lines to fstab.
My concern at this stage are these error messages on boot, some of which I can not capture.
Why are they appearing will these errors cause any problems that may damage my dives?
Thanks in advance for any help.
Steve

---

### Post by steeldriver on 2014-05-15
Hello and welcome to the forums

Boot error messages should get captured in the log(s) - you should be able to see what they were using

```

grep 'mount' /var/log/dmesg

grep 'mount' /var/log/boot.log

grep 'mount' /var/log/syslog

```

I can't think of any errors that would cause damage, if everything's working they're likely just informational

---

