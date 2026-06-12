---
title: "Ubuntu to Xubuntu desktop change, now no volume control"
date: 2013-12-16
forum: New to Ubuntu
---

### Post by sbcwinn on 2013-12-16
I switched destops to from Ubuntu 13.10 (64) to Xubuntu because I am using a machine with limited resources. Afterr the change everything worked except the volume control. There is sound but very low and I cannot adjust the volume in any application. I did try to use Pulse Audio but although the volume sliders moved, I still cannot use the volume control. 

Can anyone help?

Thanks!

---

### Post by vasa1 on 2013-12-16
See [https://lists.ubuntu.com/archives/xubuntu-devel/2013-December/date.html](https://lists.ubuntu.com/archives/xubuntu-devel/2013-December/date.html) for a lot of posts on what seems to be related to your issue.
Then, there's a video by quidsup ([http://youtu.be/RkKjjKp6iyw?t=1m49s](http://youtu.be/RkKjjKp6iyw?t=1m49s)) which includes a fix (which I haven't tried):
```
Sound Indicator Fix:
sudo sed -i 's!Exec=/usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service!Exec=/usr/lib/indicator-sound-gtk2/indicator-sound-service!' /usr/share/dbus-1/services/indicator-sound.service

```

---

### Post by PaulW2U on 2013-12-16
> **sbcwinn said:**
> Afterr the change everything worked except the volume control.

See [https://bugs.launchpad.net/ubuntu/+source/indicator-sound-gtk2/+bug/1208204](https://bugs.launchpad.net/ubuntu/+source/indicator-sound-gtk2/+bug/1208204). 

Much has been reported and written about this bug. ](*,)

---

### Post by sbcwinn on 2013-12-17
Wow what a great community. Thanks so much for the help and the education.

---

### Post by mörgæs on 2013-12-20
The fix is in **proposed** now and is expected to enter the default repository soon. After that you will just have to apply the normal updates.

---

