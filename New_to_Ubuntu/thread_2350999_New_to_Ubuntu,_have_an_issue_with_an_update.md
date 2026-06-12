---
title: "New to Ubuntu, have an issue with an update"
date: 2017-01-30
forum: New to Ubuntu
---

### Post by jackaldj1 on 2017-01-30
I recently started using 16.04 LTS from a disc in the book Ubuntu Unleashed.  After it was installed, I looked for the updates from the system settings and installed the 4.4.0-59 update.  When i try to boot up using the 59 version, my keyboard and mouse do not work.  When I force a boot with the 4.4.0-21 version i have full function of my keyboard and mouse.  Any help/info on this issue would be appreciated.  I am running Ubuntu as a test to see how I like it compared to Windows.  I have this set up as a dual boot system setup; if that makes any difference.

Thanks in advance.

---

### Post by mastablasta on 2017-01-30
dual boot makes no difference. 

since keyboard also doesn't work, boot from live session after you booted form 4.4.0-59 kernel update. then go to /var/log on your disk and check the various logs for any errors. particulary dmesg, kernel.log perhaps a few others.  see if you can spot any errors regarding keyboard or mouse device.

are you using any special model keyboard? what about mouse?

---

### Post by jackaldj1 on 2017-01-30
I have a Razer Black Widow Chroma for the keyboard, and a Razer Naga Epic Chroma for the mouse.  I will look into the log errors soon.  Thanks.

---

