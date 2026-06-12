---
title: "Firmware error..."
date: 2008-07-10
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-07-10
Jul 11 13:25:31 PJ kernel: [29315.929623] ipw2200: Firmware error detected.  Restarting.


Any ideas as to what this error might be?

---

### Post by iaculallad on 2008-07-10
> **dunbrokin said:**
> Jul 11 13:25:31 PJ kernel: [29315.929623] ipw2200: Firmware error detected.  Restarting.


Any ideas as to what this error might be?

Maybe, the IPW2200 binary firmware image for Wireless driver does not support the cryptography in hardware. Try adding IPW2200 in your /etc/modprobe.d directory.

```
gksudo gedit /etc/modprobe.d/ipw2200
```

and paste the line of text below on gedit's open window. Save it then close.

```
options ipw2200 hwcrypto=0
```

Try to logout then log-back in and observe your /var/log/syslog file.

---

### Post by dunbrokin on 2008-07-11
> **iaculallad said:**
> Maybe, the IPW2200 binary firmware image for Wireless driver does not support the cryptography in hardware. Try adding IPW2200 in your /etc/modprobe.d directory.

```
gksudo gedit /etc/modprobe.d/ipw2200
```

and paste the line of text below on gedit's open window. Save it then close.

```
options ipw2200 hwcrypto=0
```

Try to logout then log-back in and observe your /var/log/syslog file.

OK, done all that...now what doe I look for in the syslog?

---

### Post by iaculallad on 2008-07-11
> **dunbrokin said:**
> OK, done all that...now what doe I look for in the syslog?

Check if it still spits the same message/error on your /var/log/syslog.

---

### Post by dunbrokin on 2008-07-11
> **iaculallad said:**
> Check if it still spits the same message/error on your /var/log/syslog.

Yep....

Jul 11 18:51:41 PJ kernel: [ 3124.688286] ipw2200: Firmware error detected.  Restarting.

---

