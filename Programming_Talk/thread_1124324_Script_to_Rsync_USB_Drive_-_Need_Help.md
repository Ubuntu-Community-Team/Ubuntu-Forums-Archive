---
title: "Script to Rsync USB Drive - Need Help"
date: 2009-04-13
forum: Programming Talk
---

### Post by Penguin Guy on 2009-04-13
I need some help writing a script to automatically rsync my USB drive. Rsync is a backup program for those that didn't know.

**Success! I got this working and wrote a short guide, you can find it [here]("http://ubuntuforums.org/showthread.php?t=1281418").**

*Thanks to everyone for all the help!*

---

### Post by hessiess on 2009-04-13
I made a post regarding this eact topic some time ago, unfortunately it no longer seams to exist. Basically you want to create a script to watch for the existence of /dev/disk (or whatever the device appears as) and have it run rsync.

---

### Post by Penguin Guy on 2009-04-14
Yes but how exactly do I make a script 'watch' something?

---

### Post by hessiess on 2009-04-14
You could set up cron to run the script automatically.

---

### Post by Penguin Guy on 2009-04-14
That seems like a very inefficent way of doing things, surely it would be possible to run a script when the system detects a USB device.

---

### Post by keithweddell on 2009-04-14
To run a script when the usb drive is mounted you need to look into udev rules. Try [this link]("http://reactivated.net/writing_udev_rules.html") for a starter.

For space used on the usb drive you probably need to look at the df or du commands.  I think they are available on a default install.


Keith

---

### Post by unutbu on 2009-04-14
Here is a thread which eventually succeeds in getting a backup script to run every time you plug in a USB drive. At the end, the OP summarizes the steps taken:

[http://ubuntuforums.org/showthread.php?t=1094342](http://ubuntuforums.org/showthread.php?t=1094342)

And to answer your other question: to check the amount of used space on that USB drive: type
```

df -h
```

---

### Post by Penguin Guy on 2009-04-15
Thanks, I have updated the first post. Is that correct?

---

### Post by unutbu on 2009-04-15
I don't think your udev rule will work. $KERNEL should be %k. (See /usr/share/doc/udev/writing_udev_rules/index.html). But besides that, your rule will make the script run when any USB device with a sd?1 partition is connected -- be it a small USB flash key, a USB camera, or the backup drive.

You probably want a udev rule which makes the backup script run only when a specific type of drive is connected. To do that, follow the instructions here: [http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864). If that doesn't work, post back here with your udev rule and the output of lsusb.

There are two steps to getting udev to work. First, write a udev rule which gets a command to run. Second, make the command do what you want. So, I suggest instead of using 
```

RUN+="/home/share/bin/cp_usb -%k"
```

how about try```


RUN+="date >> /tmp/udev.out"
```

This will print the date/time stamp to /tmp/udev.out.
You can then watch this file```


watch -n 4 tail -n 5 /tmp/udev.out
```

to see if your udev command is running. Once you get the udev rule to trigger when and only when you want it to, then you can start working on crafting your backup script.

---

### Post by Penguin Guy on 2009-04-15
Thanks, I'll look into that.

---

