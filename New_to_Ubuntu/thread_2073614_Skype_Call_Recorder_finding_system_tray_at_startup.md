---
title: "Skype Call Recorder finding system tray at startup"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by mdavis1231 on 2012-10-20
II have Skype Call Recorder listed in Startup Applications, and I'm having a problem with it finding the system tray within the allotted 10 seconds that it allows.  Is there any way that I can delay the startup to give it more time?  I've tried 'sleep 15 skype-call-recorder', but it doesn't seem to want to work in 12.04 LTS.

---

### Post by kostkon on 2012-10-20
The right syntax is:
```
sleep 15 && skype-call-recorder
```
Give it a try :P

---

### Post by mdavis1231 on 2012-10-20
> **kostkon said:**
> The right syntax is:
```
sleep 15 && skype-call-recorder
```Give it a try :P

Thanks!  I also found an alternate solution in #3 on this page:

[http://askubuntu.com/questions/28685/how-can-i-delay-a-specific-program-on-startup](http://askubuntu.com/questions/28685/how-can-i-delay-a-specific-program-on-startup)

---

