---
title: "How to move position of notification bubble for gwibber, music, wifi, etc"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by coldjeanz on 2012-02-21
Using Ubuntu 11.10

There is a small bubble that pops up near the upper right of the screen when you connect to a wireless network, the next song on your music player starts, a message is tweeted through Gwibber, etc. I would like to move it slightly lower but I don't see how to do this.

---

### Post by Krytarik on 2012-02-21
Please see this guide; but notice that there is no "slightly", only 'top', 'middle', or 'bottom':

[http://www.tuxgarage.com/2011/06/tweaking-notify-osd.html](http://www.tuxgarage.com/2011/06/tweaking-notify-osd.html)

Regards.

PS: Feel free to post back any issues you might encounter with the GUI I wrote, if you use that method, as I still haven't tested it with Oneiric 11.10.

---

### Post by coldjeanz on 2012-02-21
Thanks that got the job done.

However, I did the terminal method since it looked a lot easier.

Solved!

---

### Post by Krytarik on 2012-02-21
> **coldjeanz said:**
> However, I did the terminal method since it looked a lot easier.
Yeah, I second that :P ; at least if you don't change its position too often.

---

### Post by coldjeanz on 2012-03-06
Something is wrong. Ever since I installed this program the bubbles disappear extremely fast, I have it set at 10 seconds but the bubbles from Gwibber disappear after 2-3 seconds. I can't figure out how to remove the program either.

---

### Post by Krytarik on 2012-03-06
> **coldjeanz said:**
> Ever since I installed this program the bubbles disappear extremely fast, I have it set at 10 seconds but the bubbles from Gwibber disappear after 2-3 seconds.
That's because Gwibber sends out its notifications with a 2-sec. timeout, which is ignored by the default version of Notify-OSD; this is the related bug report - incl. a possible workaround stated in the comments, try that:

[https://bugs.launchpad.net/gwibber/+bug/799522](https://bugs.launchpad.net/gwibber/+bug/799522)

---

### Post by coldjeanz on 2012-03-08
Thanks again, fixed it. :)

---

