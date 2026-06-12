---
title: "[SOLVED] vista clock?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-05-06
i know this may not have anything to do with ubuntu but i thought id ask incase anyone here has experienced similar problems

first i had vista installed on this laptop then i shrunk the partition and put ubuntu gutsy beside it  (all was good)

then vista stopped working so i deleted the vista partition

when hardy was released i installed hardy on the old vista partition

then once hardy was all configured i installed vista onto the partition that gutsy was on

then i had to reinstall and reconfigure grub



now my problem is when i reinstalled vista something went wrong and now the clock gets screwed up every time i shutdown
(it is set for the correct time zone and i set the time right, but then when i reboot it still says the correct timezone but the time is actually like 5 hours off)

i figure it might have something to do with dual booting ubuntu (maybe)

anyway does anyone here have any ideas what the problem could be?

---

### Post by subzero316 on 2008-05-06
No wonder Vista is a waste of 'TIME'....:lolflag:

---

### Post by inportb on 2008-05-06
A possibility is that Windows sets the system clock to match the current timezone while Linux sets the system clock to match UTC. During Ubuntu installation, you have the option to set the system clock to the current timezone, in case Windows is also installed. At least, I see this option when I use the alternative installer.

---

### Post by ilrudie on 2008-05-06
I only used the alternate installer for Hardy but in Gutsy the UTC option was in the LiveCD installer so there is a good chance it is still there.  I would guess inportb is correct about Ubuntu using UTC and Vista using local time.  Try editing the /etc/default/rcS file which probably looks like this:
```

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no
```

Change UTC=yes to UTC=no and reboot.  Now Linux should assume your hardware clock is set to local time instead of UTC.

---

### Post by dar25 on 2008-12-04
I had the same issue on my T60 latpop with Vista and Ubuntu dual boot.
Every time i would run Vista after using ubuntu the clock would be out of whack.

Setting UTC to no in the config file above helped resolve it for me.

---

