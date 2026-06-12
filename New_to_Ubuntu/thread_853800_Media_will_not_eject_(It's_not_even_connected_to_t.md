---
title: "Media will not eject (It's not even connected to the computer) [PIC]"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by alecwh on 2008-07-08
Hello,

I'm having an odd problem on my Ubuntu desktop. Yesterday, I plugged in my external drive (ALECBACKUP) to transfer some files, and after it completed, I accidentally unplugged the cord without first "ejecting" the drive. This happened a second time, too (don't ask me why...).

So now, there are two "ALECBACKUP" icons on my desktop, that will not disappear, and cannot be removed. I've tried "ejecting" them, but that does nothing.

Screenshot:

[IMG]http://img502.imageshack.us/img502/5775/screenshotfk2.png[/IMG]

Can someone help out?

---

### Post by st33med on 2008-07-08
Well try this:
```
umount /media/ALECBACKUP
umount /media/ALECBACKUP_

```

If that does not work, try adding an '-f' after 'umount' in those commands.

---

### Post by alecwh on 2008-07-08
It said: /sbin/umount.hal: /media/ALECBACKUP is not recognized by hal

But I did the "-f", and put a sudo in front of the commands, and it worked.

Thanks a lot!

---

