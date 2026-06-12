---
title: "cannot unmount usb drive/media"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by al.adab on 2011-11-01
apologies if a solution to this has already been posted - I can't find it:

I've installed Xubuntu 10.04 and cannot unmount any USB drive or external media (like a Sony Walkman). 

If I right-click on the media icon on the desktop and select "unmount volume", the following message pops up: 

[I]Unable to unmount walkman: 
The volume "WALKMAN" was probably mounted manually on the command line[/I]

Can you please help? Thanks.

---

### Post by enkay009 on 2011-11-01
Hmm... that's weird.

The error message sounds like a default/catch-all error message. So if the system that allows userspace mounting (gvfs) isn't able to unmount something it assumes that it was mounted outside the userspace. Or at least that's what I'm assuming.

Out of curiousity how did you mount it? Did you simply plug it in to your computer?

Are you able to unmount it as root?

---

### Post by al.adab on 2011-11-01
that's right, I simply plugged it in. I'm trying
[http://dl.dropbox.com/u/7138409/indicator-usb/indicator.html](http://dl.dropbox.com/u/7138409/indicator-usb/indicator.html)
and it works - to a certain extent: according to ubuntu the drive is not mounted, according to the drive (judging from its behaviour), it still is...

how do you unmount as root?

---

### Post by enkay009 on 2011-11-01
Alright so I want to be very careful with this. First figure out what the path to your walkman mount is. It might be /media/WALKMAN. Be sure you have the right path and then type the below. Swap out the path /media/WALKMAN for whatever the actual path is.

```
sudo umount /media/WALKMAN
```

---

### Post by al.adab on 2011-11-02
enkay009 thank you so much for your help and availability - I've decided to go for the 11.10 version of Xubuntu...
thank you again. 
I'll leave this open in case someone else has the same issue?

---

