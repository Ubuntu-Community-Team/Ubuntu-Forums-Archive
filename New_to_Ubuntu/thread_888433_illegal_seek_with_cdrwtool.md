---
title: "illegal seek with cdrwtool"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by mvdberg112 on 2008-08-13
When formatting a CD-RW with cdrwtool, the error "illegal seek" appears.
I have searched on the forums, but did not find a real solution. Somewhere it told me to turn on DMA, but that is enabled by default.

I just upgraded to 8.04.1 Hardy. Kernel version is xxxx.20. 
What can I do?
Why does it happen?
And why, when I try to defne the number of blocks to a low value does the message "wait_cmd: Input/output error" show up?

```
root@emea-l3-mberg02:/home/michael# cdrwtool -d /dev/scd0 -q
using device /dev/scd0
1088KB internal buffer
setting write speed to 12x
Settings for /dev/scd0:
	Fixed packets, size 32
	Mode-2 disc

I'm going to do a quick setup of /dev/scd0. The disc is going to be blanked and formatted with one big track. All data on the device will be lost!! Press CTRL-C to cancel now.
ENTER to continue.

Initiating quick disc blank
Disc capacity is 295264 blocks (590528KB/576MB)
Formatting track
wait_cmd: Input/output error
Command failed: 04 17 00 00 00 00 00 00 00 00 00 00 - sense 00.00.02
format disc: Illegal seek


root@emea-l3-mberg02:/home/michael# cdrwtool -d /dev/scd0 -g
using device /dev/scd0
ok, want to get
1088KB internal buffer
setting write speed to 12x
writing fixed packets
border type	: 0
track mode	: 7
data block type	: 10
session format	: 32
packet size	: 32


root@emea-l3-mberg02:/home/michael# cdrwtool -d /dev/scd0 -t 4 -u 2000
using device /dev/scd0
setting speed to 4
mkudffs 2000 blocks
1088KB internal buffer
setting write speed to 4x
start=0, blocks=16, type=RESERVED 
start=16, blocks=3, type=VRS 
start=19, blocks=237, type=USPACE 
start=256, blocks=1, type=ANCHOR 
start=257, blocks=31, type=USPACE 
start=288, blocks=32, type=PVDS 
start=320, blocks=32, type=LVID 
start=352, blocks=32, type=STABLE 
start=384, blocks=1024, type=SSPACE 
start=1408, blocks=320, type=PSPACE 
start=1728, blocks=15, type=USPACE 
start=1743, blocks=1, type=ANCHOR 
start=1744, blocks=176, type=USPACE 
start=1920, blocks=32, type=STABLE 
start=1952, blocks=32, type=RVDS 
start=1984, blocks=15, type=USPACE 
start=1999, blocks=1, type=ANCHOR 
Writing UDF structures to disc
wait_cmd: Input/output error
Command failed: 2a 00 00 00 00 00 00 00 20 00 00 00 - sense 00.00.00
root@emea-l3-mberg02:/home/michael# cdrwtool -d /dev/scd0 -t 4 -u 2000
```

---

### Post by mjwhitfield on 2008-08-13
That's interesting, it's like you're getting CRC errors when you're trying to blank the disc.  Is it only happening with one CD or with all?

---

### Post by mvdberg112 on 2008-08-13
Thanks. It was happening with all CDs.
I kept a bit reading on the fora, and found this:

[http://ubuntuforums.org/showthread.php?t=129093](http://ubuntuforums.org/showthread.php?t=129093)

It reads:
> **dradul said:**
> ....Now, set up your drive:
```
sudo /etc/init.d/udftools start
```

This init script loads the kernel module and sets up the link between the block device ([FONT="monospace"]/dev/hdd[/FONT] in this case) and the virtual packet drive device [FONT="monospace"]/dev/pktcdvd/0[/FONT] (there is only one device defined and it gets the first alllocated name). If you want to know more, I strongly recommend you read the manual pages for [FONT="monospace"]mkudffs[/FONT], [FONT="monospace"]cdrwtool[/FONT] and [FONT="monospace"]pktsetup[/FONT].
....Wel, I read also this: 
[http://lists.opensuse.org/packet-writing/2003-08/msg00009.html](http://lists.opensuse.org/packet-writing/2003-08/msg00009.html)

There it said that I needed to run pktsetup., so I did this:
sudo pktsetup pktcdvd0 /dev/scd0```

sudo pktsetup -d /dev/scd0
and then
cdrwtool -d /dev/scd0 -q
```After this the format went well and the new volume was even automatically mounted!

I know that in the past I tried to use:
```
 pktsetup 0 /dev/scd0
 pktsetup 1 /dev/scd0
```
But for whatever reason, that did not work. It's quite a while ago when still running Gutsy 7.10, so I cannot tell what else I did or not did and why it did not work. Maybe just another little type at that time or a bug in 7.10.

---

### Post by cariboo on 2008-08-13
Have you tried wodim? there are some examples of hot to use it here:

[http://www.slitaz.org/en/doc/handbook/utilities.html](http://www.slitaz.org/en/doc/handbook/utilities.html)

Jim

---

