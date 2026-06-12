---
title: "System time incorrect"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by Kestreln8144 on 2013-08-13
I have a dual-booting system for switching between Windows and Ubuntu. I recently switched to Windows and back, and now my system clock in Ubuntu is incorrect. It is currently 7pm, but it displays 2pm. I don't want to set it manually, and I can't see how to make it update to the correct time.

How can I fix this?

It would also be nice if anyone could explain how to prevent this from happening again. In Windows I can easily tell it to update the time if it's off, but I don't know how to make sure it doesn't happen in Ubuntu anymore.

---

### Post by lisati on 2013-08-13
It's been a while since I've been faced with a similar dilemma, so I might have forgotten something, but here goes anyway:

If you're using a "standard" Ubuntu installation, you can click on the date on the top task bar, then *Time and date settings*. From there, you'll should be able to find an option to set the date and time automatically from the internet.

---

### Post by Irihapeti on 2013-08-13
This sounds to me like the "BIOS clock set to UTC" issue.

If you look at /etc/default/rcS, do you see the following?

```
# assume that the BIOS clock is set to UTC time (recommended)
UTC=yes
```

That's recommended when you're running Linux only, but causes problems if you're using Windows as well. Windows assumes that the BIOS clock is set to local time.

Edit /etc/default/rcS and replace the "yes" with "no". You'll need to do this as root.

You may need to reboot before resetting the time.

---

### Post by Kestreln8144 on 2013-08-13
> **Irihapeti said:**
> This sounds to me like the "BIOS clock set to UTC" issue.

If you look at /etc/default/rcS, do you see the following?

```
# assume that the BIOS clock is set to UTC time (recommended)
UTC=yes
```

That's recommended when you're running Linux only, but causes problems if you're using Windows as well. Windows assumes that the BIOS clock is set to local time.

Edit /etc/default/rcS and replace the "yes" with "no". You'll need to do this as root.

You may need to reboot before resetting the time.

It was set to UTC=yes, so I changed it to UTC=no as you suggested. But after reboot, it still shows the incorrect time. Is there a way I can force it to recheck? Or might the problem be something else?

---

### Post by Kestreln8144 on 2013-08-13
Is it possible my firewall could be the problem? I have it setup in a particular way, and it might be blocking communication with the necessary servers.

EDIT: Yes, that appears to have been the problem. After temporarily disabling it and running the following command, the time corrected itself:
```
ntpdate time.nist.gov
```

---

### Post by Irihapeti on 2013-08-13
Glad to hear that it's working.

The port for ntp is UDP 123. You can set up your firewall to allow that.

---

