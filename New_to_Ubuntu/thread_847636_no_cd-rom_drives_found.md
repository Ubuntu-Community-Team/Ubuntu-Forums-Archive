---
title: "no cd-rom drives found"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by plugugly on 2008-07-02
I posted this thread in hardware and laptops, where I thought it probably belonged, sorry about the double, this can probably be removed. 




Hello, I need some help. I have a Gateway 7330GZ laptop that I was doing a cleaning session on, I decided while I was playing around I would format and try Ubuntu, so I burned the boot disc and installed it as my only operating system.

I've been struggling ever since. I have had issues with it correctly working with anything on this laptop. I decided I would do dual boot and try to figure the sound and other stuff out while I had XP up and running again.

I discovered that it is not finding my cd-rom at all since the install. It lights up and spins up like normal, but no icon appears, if I try to use Audio sound Extractor, it gives me "No cd-rom drives found".

I searched here, but everyone wants the output of terminal command to help, and none looked like mine.

I'm a complete newb and would really like some help. Here's my terminal thing other people asked for in other threads:
 
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b1340fad-3b1f-4f65-bb17-224946f16208 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6b896adf-4afd-443f-bbd0-7302b4b0b99f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by nowshining on 2008-07-02
try going into my computer. etc..  i don't rem. what's it called in gnome, is there a cd-rom icon? if so right-click - mount, does it mount? I think tho it's called system, again i don't rem. I use KDE.

---

### Post by eapache on 2008-07-02
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```That's your cd drive. I can't see any errors with the config, but this isn't really my area.

The place nowshining was talking about is Places->Computer. It's worth looking at.

Sorry I can't be of more help.

---

### Post by editrix on 2008-07-03
I've been going through my own CD-burning hell, and am no expert, but I have discovered some things that might help.

What is the output of [COLOR="Red"]wodim --devices[/COLOR]? (That's 2 hyphens, not one dash.) You should get a line that looks like this:```
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'     rwrwrw : 'CyberDrv' 'CW078D CD-R/RW'
```

Your problem is not the same as mine, but I've come across posts like yours in searching my own problem. Click on the _Search these forums more easily_ link in my sig and search [COLOR="Red"]no cd-rom drives found[/COLOR]

---

