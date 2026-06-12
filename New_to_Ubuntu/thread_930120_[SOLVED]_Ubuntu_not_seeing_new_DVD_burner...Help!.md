---
title: "[SOLVED] Ubuntu not seeing new DVD burner...Help!"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by sillyboy on 2008-09-25
I installed a new LG DVD burner. An A-Open CD/DVD ROM was already installed.
Both are set to CS, and on the same ribbon cable.  Ubuntu is seeing the A-Open drive in Places>Computer. I tried to (test) use K3B and it only saw my source A-Open with the CD in it. K3B wanted to know if the A-Open drive was going to be the detination drive.  I put a blank CD in the LG drive, and it was not seen at all in K3B.

Any ideas??  Thanks... :confused:

---

### Post by sillyboy on 2008-09-25
> **sillyboy said:**
> I installed a new LG DVD burner. An A-Open CD/DVD ROM was already installed.
Both are set to CS, and on the same ribbon cable.  Ubuntu is seeing the A-Open drive in Places>Computer. I tried to (test) use K3B and it only saw my source A-Open with the CD in it. K3B wanted to know if the A-Open drive was going to be the detination drive.  I put a blank CD in the LG drive, and it was not seen at all in K3B.

Any ideas??  Thanks... :confused:

I am getting this text from terminal about ROMs:

[   24.401077] scsi 1:0:1:0: CD-ROM            AOPEN    COM5232/AAH PRO  1.05 PQ: 0 ANSI: 5
[   24.460726] Uniform CD-ROM driver Revision: 3.20
[   24.460798] sr 1:0:1:0: Attached scsi CD-ROM sr0

Now what??  I'm lost...:(

---

### Post by mc4man on 2008-09-25
In the long run I'd try to get yourself an 80 wire ide cable (almost smooth, basically the same as what your hdd(s) are using. In the meantime try  jumpering one to master and one to slave (typically end connector - master 

Your always better off having the burner at master position (will be set as /dev/scd0

Read here though - seems a 'true' cs cable masters at middle connector  - note you may not have a cs cable

[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)

---

### Post by sillyboy on 2008-09-25
> **mc4man said:**
> In the long run I'd try to get yourself an 80 wire ide cable (almost smooth, basically the same as what your hdd(s) are using. In the meantime try  jumpering one to master and one to slave (typically end connector - master 

Your always better off having the burner at master position (will be set as /dev/scd0

Read here though - seems a 'true' cs cable masters at middle connector  - note you may not have a cs cable

[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)

I am using a 80 wire cable. When I had the drives set at one M and one SL, neither one would show up and the red HD activity led would stay on bright and steady.  When I switched both drives to CS, just the one drive would show.

Is the LG drive to new for Ubuntu to recognize?

---

### Post by mc4man on 2008-09-25
> Is the LG drive to new for Ubuntu to recognize
Can't imagine that with ide drives, I just replaced my old plextor last week with a new liteon no problem.

Have you booted to your bios setup to see if both drives are shown?

Otherwise I might try just connecting the new drive only (at end connector as master) and seeing if 1. there's any boot error and 2. if it's detected by ubuntu.

What does ```
sudo lshw -C disk
``` show ?

---

### Post by sillyboy on 2008-09-25
> **mc4man said:**
> Can't imagine that with ide drives, I just replaced my old plextor last week with a new liteon no problem.

Have you booted to your bios setup to see if both drives are shown?

Otherwise I might try just connecting the new drive at end connector as master and seeing if 1. there's any boot error and 2. if it's detected by ubuntu.

What does ```
sudo lshw -C disk
``` show ?

I just rebooted the computer (both drives on CS) and both have showed up in Places/Computer. :) Imagine that!!!!! 

Thanks mc4man:)

---

### Post by mc4man on 2008-09-25
It's odd what a reboot sometimes does.
You might want to run thus to make sure everything is in order (no duplicates of drives)

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

If you run into any performance issues this can provide some useful info

```
grep 'ATAPI' /var/log/kern.log
```

---

