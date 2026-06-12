---
title: "Regular disk access when idle"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by silkstone on 2008-06-24
Running Hardy - When the machine (desktop PC) is idle, the HD is being accessed every few seconds. The HD light flashes and I can hear disk activity. I can't believe it should be doing this, and it must be wearing out the drive. I've read somewhere of a problem with Hitachi drives (which this is) but that related to laptops.

Any ideas please?

---

### Post by sdennie on 2008-06-24
Someone else asked something similar in the following thread: [http://ubuntuforums.org/showthread.php?t=833301](http://ubuntuforums.org/showthread.php?t=833301).  Read the warning carefully in that if your machine crashes and you've made these changes, you could loose several minutes of work.

---

### Post by silkstone on 2008-06-24
Thanks vor - although I'm not using mythtv and this is a desktop machine - does that make any difference?

I don't know how to check what is causing the disk access, nor how to edit the mount options, so any advice would be appreciated.

Also, is this just an annoyance or is it really likely to harm the drive?

---

### Post by sdennie on 2008-06-24
It doesn't matter if it's a desktop machine or what flavor of Ubuntu you are using.

It's probably just an annoyance, but you can determine if it's causing problems by looking at this thread (specifically, the second post): [http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570).

If you do decide to make the changes, the mount options are easy to change:

```

gksudo gedit /etc/fstab

```

You will see some lines that look approximately like this:

```

UUID=4f6dd9e5-b752-4323-ae35-20ae1bfaa77e /               ext3    relatime,errors=remount-ro 0       1

```

Note the "ext3" on that line.  Any line that says "ext3" needs to have the commit interval changed.  So, for example:

```

UUID=4f6dd9e5-b752-4323-ae35-20ae1bfaa77e /               ext3    relatime,errors=remount-ro,commit=300 0       1

```

Hope that helps.

---

### Post by silkstone on 2008-06-24
Thanks again.

I've just followed the instructions in your linked thread, and my Load Cycle Count is 502. I'll check it again tomorrow.

If that means that there have only been 502 load cycles on the drive since it was new, I don't have a problem - the machine is 18 months old and has been running Hardy for about a month.

---

### Post by sdennie on 2008-06-24
Yeah, if your Load_Cycle_Count is that low after that long, then the disk activity is an annoyance and probably not harmful.

---

### Post by silkstone on 2008-06-24
I decided I couldn't stand the noise of disk access every few seconds so I've added the 'commit=50' to the entry for dev/sda in fstab.

I think that's helped.

What is the downside of this? What have I done? :)

---

### Post by sdennie on 2008-06-24
If you've also done the things to /etc/sysctl.conf in the original link, you've essentially just delayed most disk writes for up to 50 seconds.  The only downside of this is that if your system completely crashes, the power goes out, or you hold down the power button, you could lose any information within the last 50 seconds.

Also note, if you've changed the commit time to 50s, and you've made changes to /etc/sysctl.conf, you may want to set that to ~50s as well.  So, where there is a very large number (30000?), replace that with 5000.  50s is actually a decent compromise (I run at 60s when on AC power).

Hope that helps.

---

### Post by silkstone on 2008-06-24
I haven't changed the sysctl.conf file - just the fstab entry. Do I need to do both?

At the moment the disk light still flashes, but there is less audible disk activity.

---

### Post by sdennie on 2008-06-24
That's completely up to you.  You could try it and see if you prefer having the /etc/sysctl.conf changes.  If not, it's very trivial to revert them (just erase those 3 lines from the file and reboot is the easiest way).

---

### Post by silkstone on 2008-06-24
Thanks vor. If ever I'm in Buenos Aires I'll buy you a drink or two. :)

---

### Post by silkstone on 2008-06-25
I think I may have found the cause of the problem. I've looked at kern.log and that has hundreds of entries like this...

```
Jun 25 10:10:05 silkstone-desktop2 kernel: [ 1390.904179] hub 5-0:1.0: over-current change on port 1
Jun 25 10:10:06 silkstone-desktop2 kernel: [ 1391.894623] hub 5-0:1.0: over-current change on port 1
Jun 25 10:10:07 silkstone-desktop2 kernel: [ 1392.885052] hub 5-0:1.0: over-current change on port 1
Jun 25 10:10:08 silkstone-desktop2 kernel: [ 1393.875491] hub 5-0:1.0: over-current change on port 1
Jun 25 10:10:10 silkstone-desktop2 kernel: [ 1395.113538] hub 4-0:1.0: over-current change on port 1
Jun 25 10:10:10 silkstone-desktop2 kernel: [ 1396.103993] hub 5-0:1.0: over-current change on port 1
Jun 25 10:10:11 silkstone-desktop2 kernel: [ 1397.094425] hub 4-0:1.0: over-current change on port 1
Jun 25 10:10:12 silkstone-desktop2 kernel: [ 1398.084866] hub 5-0:1.0: over-current change on port 1
Jun 25 10:10:13 silkstone-desktop2 kernel: [ 1399.075298] hub 4-0:1.0: over-current change on port 1
Jun 25 10:10:15 silkstone-desktop2 kernel: [ 1400.313341] hub 5-0:1.0: over-current change on port 1
Jun 25 10:10:16 silkstone-desktop2 kernel: [ 1401.303782] hub 4-0:1.0: over-current change on port 1
Jun 25 10:10:17 silkstone-desktop2 kernel: [ 1402.295187] hub 4-0:1.0: over-current change on port 1
Jun 25 10:10:18 silkstone-desktop2 kernel: [ 1403.284645] hub 4-0:1.0: over-current change on port 1
Jun 25 10:10:19 silkstone-desktop2 kernel: [ 1404.275069] hub 4-0:1.0: over-current change on port 1
Jun 25 10:10:20 silkstone-desktop2 kernel: [ 1405.265506] hub 5-0:1.0: over-current change on port 1
Jun 25 10:10:21 silkstone-desktop2 kernel: [ 1406.255940] hub 4-0:1.0: over-current change on port 1
Jun 25 10:10:22 silkstone-desktop2 kernel: [ 1407.246375] hub 4-0:1.0: over-current change on port 1
Jun 25 10:10:23 silkstone-desktop2 kernel: [ 1408.236815] hub 5-0:1.0: over-current change on port 1
```

As you can see, it is updating every second. Any ideas what this may be? I have recently installed an internal card reader and also a 4-port USB PCI card.

---

### Post by sdennie on 2008-06-25
That would certainly cause increased disk activity.  I would try pulling the cards individually and see which is causing the problem.  There may be a "knock it off" kernel option to fix the dmesg spam.

---

### Post by silkstone on 2008-06-25
I've removed the card reader - that seemed to be the problem, and now kern.log is not updating all the time. :)

---

