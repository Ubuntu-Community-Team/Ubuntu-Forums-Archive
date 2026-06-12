---
title: "creating a live usb for kali"
date: 2013-09-21
forum: New to Ubuntu
---

### Post by junk321123mail.com on 2013-09-21
so I'm pretty sure I'm doing everything right running under root tried it with fat and ntfs got the right driver but when I enter the dd command but all I get is the terminal hanging their [http://s1313.photobucket.com/user/junk321123/media/Screenshotfrom2013-09-20235131_zpsc437498c.png.html](http://s1313.photobucket.com/user/junk321123/media/Screenshotfrom2013-09-20235131_zpsc437498c.png.html)

---

### Post by junk321123mail.com on 2013-09-21
o wait haha it's working just really slow.... ok new question will the terminal tell me when it's done

---

### Post by Werne on 2013-09-21
Terminal will tell you when it's done, it will drop you back to the shell prompt along with a message that the 2.*GB of data has been transfered to /dev/whatever at some speed. But it won't work since you need to dd it straight to /dev/sdb and not /dev/sdb1, your flash drive won't even boot.

You can also monitor dd's current progress, open a new terminal (or terminal tab), assume root shell (sudo -i, or su if you have root access) and do the following:

Execute
```
pgrep '^dd$'
```
which will return dd's process ID, then execute
```
kill -USR1 xxxxxx
```
where xxxxxx is the process ID, it could be of varying length, it will print the current status on the terminal (or tab) where dd is running. Or if pgrep returns only one line of numbers (only one instance of dd running), you can execute this
```
kill -USR1 $(pgrep'^dd$')
```
I always use that last one.

---

### Post by Jonathan Precise on 2013-09-21
Try

```
dd if=kali.iso of=/dev/sdb
```

MAKE SURE THE USB IS /DEV/SDB AND NOT /DEV/_***x***_d**_*y*_**

For example, it can be /dev/sda or /dev/sdc, or in VERY RARE cases /dev/hda or /dev/hdb (USE WITH CARE!!!)

---

