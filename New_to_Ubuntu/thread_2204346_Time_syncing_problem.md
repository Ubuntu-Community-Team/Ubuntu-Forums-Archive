---
title: "Time syncing problem"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by kaushik3 on 2014-02-08
My ubuntu doesnt sync with my local time it shows something else there ? how to make it show my local time

---

### Post by papibe on 2014-02-08
Hi kaushik3.

Are you using the desktop version or the server one?

You can set your time zone on the desktop version by going to:
```
System Settings -> Time & Date 
```
Or in the command line by running:
```
tzselect
```
Does that help?
Regards.

---

### Post by SAPTARSHI94 on 2014-02-08
open the terminal and type 
sudo ntpdate ntp.ubuntu.com 
and then reboot to get the perfect effect.
Does it help?

---

### Post by kaushik3 on 2014-02-08
ntpcommand not found

---

