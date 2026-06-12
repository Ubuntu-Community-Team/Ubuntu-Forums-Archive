---
title: "What's wrong with my Ubuntu?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-10-20
I had Ubuntu for quite some time awhile back (7.10 and 8.04). Recently I had to go back to Windows for some reasons and the other day I went back to Ubuntu 8.04. I haven't really touched Ubuntu at all other than the Updating all the updates in the update manager. I have encountered two problems that I faced quite a lot in 8.04 before, but I cannot remember if this happened in 7.10. Randomly I just lose sound for everything which requires me to reboot my machine to regain sound back. The other problem is when I am done using firefox (any version) and I close it out and come back later and try to open it it will not open. I go to System Monitor to view the processes and there it multiple firefox ones. They all say 'sleeping' so I kill the processes and try to open firefox and nothing happens. This requires me to reboot as well.

I am not sure if these problems have happened to others, but I find it strange they happen to me. Like I said, I cannot remember if this happened on 7.10, but I doubt it. Hopefully 8.10 will fix these problems for me.

---

### Post by eternalnewbee on 2008-10-20
> **ImThatNerd said:**
> I had Ubuntu for quite some time awhile back (7.10 and 8.04). Recently I had to go back to Windows for some reasons and the other day I went back to Ubuntu 8.04. I haven't really touched Ubuntu at all other than the Updating all the updates in the update manager. I have encountered two problems that I faced quite a lot in 8.04 before, but I cannot remember if this happened in 7.10. Randomly I just lose sound for everything which requires me to reboot my machine to regain sound back. The other problem is when I am done using firefox (any version) and I close it out and come back later and try to open it it will not open. I go to System Monitor to view the processes and there it multiple firefox ones. They all say 'sleeping' so I kill the processes and try to open firefox and nothing happens. This requires me to reboot as well.

I am not sure if these problems have happened to others, but I find it strange they happen to me. Like I said, I cannot remember if this happened on 7.10, but I doubt it. Hopefully 8.10 will fix these problems for me.
Hi there.
you could try: sudo apt-get update.
If that doesn't solve it, for FF you could try to un- and then reinstall.
Can't help you with the sound issue.
And yes, hopefully 8.10 will not have these issues.
Good luck.

---

### Post by Nepherte on 2008-10-20
> **ImThatNerd said:**
> Randomly I just lose sound for everything which requires me to reboot my machine to regain sound back.
That's probably the pulseaudio issue. Set everything in system > sound > preferences to alsa *or* fix pulseaudio (see [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578))

---

