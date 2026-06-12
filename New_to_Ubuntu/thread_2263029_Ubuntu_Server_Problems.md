---
title: "Ubuntu Server Problems"
date: 2015-01-29
forum: New to Ubuntu
---

### Post by nick168 on 2015-01-29
Hi everyone,

**Background info on computer**: bought refurbished. Dell Optiplex 755. 1GB DDR2 RAM. 250 external hard drive (only hard drive, has Ubuntu Server and the grub bootloader installed). 

I installed transmission, apache2 with webdav for browser file sharing, and Samba for mounting shared drive on Windows computer. Also installed mythtv (haven't used it yet). Everything was working fine for a while (a week or two)  besides one time when the internet stopped working so I just reboot it and it was fine. But then all of the sudden today, I couldn't ssh into it with putty or my ssh app on my phone. However, I could still get on my domain name and access the shared files on my browser  (apache2 and webdav). So of course I reboot it, plugged a monitor in, and I got this "BUG" **see attached picture**

Someone please tell me this isn't a hardware issue and that I can fix it. 

Thanks! 
Nick

---

### Post by nerdtron on 2015-01-29
Seems like it hangs on determining network details. but we need more info on that like the dmesg log or the syslog.
Anyway, have you tried rebooting the server (not hard reset)? You can get to another screen by pressing Ctrl+Alt+F2, login to your credentials, then issue "sudo reboot".

---

### Post by nick168 on 2015-01-29
Alright so I plugged a monitor back into it, and let it run its own diagnostic. It reboot itself afterwards. Then I was able to login to my user and I even SSH'ed into it. Then I left the room, came back and I had the exact same BUG as in the picture. I went to reboot it again, so I hit Ctrl+Alt+F2 and tried logging in. When I hit enter for the username, nothing happened. Here's what I mean by that:

Hostname login: root
*BLANK*
*BLANK*
*NOTHING HAPPENS HERE*

You mentioned I need to get the logs... can I do that and post the logs on this thread using the recovery mode?

**EDIT:** Just realized that you can switch between screens with Alt+any F key. So I found the screen that shows boot procedure (with all the [ OK ]'s) and the very last thing says "Stopping System V runlevel compatibility". Does this mean anything? I've never seen it before this BUG started...

---

### Post by mastablasta on 2015-01-30
I think dmesg is recreated on boot. dont' know if it has any dmesg.old

otherwise oyu can attach them in the thread. by default they are under /var/log

---

