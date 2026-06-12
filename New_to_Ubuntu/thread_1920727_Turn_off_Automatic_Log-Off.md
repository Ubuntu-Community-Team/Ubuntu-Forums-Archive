---
title: "Turn off Automatic Log-Off?"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by SolarLune on 2012-02-05
Hello. I was wondering if there's a way to turn off automatic log-off - I was downloading a large file yesterday, and when I came back, I found that Ubuntu had automatically logged me off, and that the file did not continue downloading.

It must be simple, but I can't find it...

---

### Post by Frogs Hair on 2012-02-05
If using 11.10 open system settings > screen  and change the lock screen time .

---

### Post by mcduck on 2012-02-05
> **SolarLune said:**
> Hello. I was wondering if there's a way to turn off automatic log-off - I was downloading a large file yesterday, and when I came back, I found that Ubuntu had automatically logged me off, and that the file did not continue downloading.

It must be simple, but I can't find it...

There is no automatic log-off. If you mean that your screen is locked, you can adjust the time (or disable the feature) in power management. However all your programs and downloads should continue normally even when the screen is locked.

If you are actually dropped into the login screen, that would be a sign that there's some program that's causing your desktop to crash. The first thing to do would be checking the ~/.xsession-errors file for any indications about what might be causing this.

---

