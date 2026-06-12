---
title: "HOWTO: Solve WD MyBook power management issues"
date: 2008-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by usu4rio on 2008-06-28
Hi,

I just bought a [Western Digital MyBook Essential]("http://www.wdc.com/en/products/products.asp?driveid=353") (only USB2.0) 1TB external HD.


It has no power switch, therefore its operation is a bit tricky:
- As soon as a switch the main power on the HD, it spins on.
- If it's not connected to an *active* USB port it switches off after 1 sec. That is, if the computer is not ON the HD switches off :)
- When I start the computer the HD starts again :)
- If I want to switch the HD down, I umount it first and then disconnect it from the USB port (the computer is actually a laptop so this is rather simple) :)

The HD is SMART ready, so I can access its configuration with smartctl and hdparm commands (the HD is /dev/sdb):

```

$ sudo smartctl -a /dev/sdb -d sat -T permissive
$ sudo hdparm -I /dev/sdb

```

**The problem:**

However even though I set the power management option with hdparm

```

$ sudo hdparm -B 254 -S 240 /dev/sdb
or
$ sudo hdparm -B 255 -S 240 /dev/sdb

```

the HD spins down after just a second (!) if not accessed, and thus the Load_Cycle_Count has increased rapidly in just a couple of days :(

```

$ sudo smartctl -a /dev/sdb -d sat -T permissive | grep 'Load_Cycle_Count'
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       814

```


**The solution:**

The only solution I've found (so far) is to keep on accessing the HD to prevent it from spining down. I've created this script in /usr/local/bin/mybook :

```

#!/bin/bash
FILETMP=/media/store/.temp

while true
do
        while [ -f $FILETMP ]
        do
            touch $FILETMP
            sleep 0.5s
        done

        sleep 10s
done

```

"/media/store" is the path for the mounted partition of the HD (change to yours). The scripts checks whether this file exist first to accessing it, so if you umount the HD you will let it enter its sleep modes.

And a I've added the next two lines to /etc/rc.local:

```

# prevent mybook to spin-down
/usr/local/bin/mybook &

```

Before you execute the script, the very first time, you should create the .temp file:

```

sudo touch /media/store/.temp

```

I hope this helps someone,

usu4rio

---

### Post by cross157 on 2008-11-08
thank you so very much for this work.

I set up everything up as you have, but forgot to change the /media/store/.temp to the correct path. I have it correct now, but the hard drive powered off last night and I can't get it back on. Any ideas how to get it back on? Thanks again

---

