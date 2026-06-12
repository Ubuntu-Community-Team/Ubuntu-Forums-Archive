---
title: "Problems with regionset tool"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by rc547 on 2008-05-26
Hi,
I'm trying to use regionset to change from region 1 to region 2 and have one change remaining. When I type 'regionset' into Terminal with a valid (region 2) DVD in the drive I am given the option to change and I select region 2. It then asks me to verify the new mask. If I say no then I get no further options but if I say yes I get an error message and I don't know why.
This is all the info I have-

[I]
becca@becca-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: LAST CHANCE
vendor resets available: 4
user controlled changes resets available: 1
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2
New mask: 0xFFFFFFFD, correct? [y/n]:y
ERROR: Region code could not be set!
[/I]

Or if I tell it that the new mask is incorrect I end up with this instead-

[I]
becca@becca-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: LAST CHANCE
vendor resets available: 4
user controlled changes resets available: 1
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2
New mask: 0xFFFFFFFD, correct? [y/n]:n
becca@becca-laptop:~$ [/I]

Is there any way of changing the region?

---

### Post by rc547 on 2008-05-27
Oh and I forgot to say I get the same problem with sudo prefixed to the regionset command... sorry for the double post and being such a newbie!

---

### Post by mc4man on 2008-05-27
You do realize that after this your drive will be locked at region 2 and without a vendor reset will stay that way for good. The chances of getting a vendor reset range from slim to none, and if you have a mashitu drive then you'll only be able play region 2 dvds from now on. 
Why don't you run sudo lshw -C disk and post the drive model and if still inclined i'll suggest a way that may make that last reset.

---

### Post by rc547 on 2008-05-27
I get the following - 

[I]
becca@becca-laptop:~$ sudo lshw -C
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

[/I]

I'm OK with only being able to play region 2 DVD's but thank you for the warning!

---

### Post by mc4man on 2008-05-27
should have coded it , sorry
```
sudo lshw -C disk
```

---

### Post by rc547 on 2008-05-27
Here's the output from that -

[I]becca@becca-laptop:~$ sudo lshw -C disk
[sudo] password for becca: 
  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54161
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SBDO
       serial: SB3D04E5JW4Y6E
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=e249fa65
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-850S
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
becca@becca-laptop:~$ 

[/I]

It also briefly showed * PCI (sysfs) *
And I can't believe I was so stupid the first time!

---

### Post by mc4man on 2008-05-27
This may work, mashitu drives lock disk access when there's a region mismatch. Try putting either a region 1 dvd or a cd (of any type with data on it) in the drive and then running regionset. I've never run the count down so I'm not sure and the only mashitu drive I have I live with fact it only plays and reads from the set region.
If it doesn't work and I come across info on how to force the last change on mashitu I'll post back.

---

### Post by rc547 on 2008-05-27
I get the same thing with a CD-R containing .jpg files and a Region 1 DVD (the region it's currently set to) both with the DVD playing and not playing.
This could be a challange :) I'll have a look online to see what other movie players are compatible with Ubuntu... I'm sure I read somewhere that some freeware will play DVDs regardless of region but of course I could be wrong.

---

### Post by mc4man on 2008-05-27
@rc54in case you ck. back
> I'm sure I read somewhere that some freeware will play DVDs regardless of region
 That's absolutely true, most open source players are unaffected by region code mismatches except when certain structure protections are also present on title. 
The problem is that most matshita drives of recent years enforce RPC 2 beyond what's required, when a disk from another region is inserted the drive allows no access to encrypted sectors at all. No playback, ripping or reading. Basically case closed. The only exception atm for these drives (yours included) is on some mac laptops the drive can be flashed to RPC 1 (unlimited resets)
The only other choice is replace the drive or have a vendor reset done by manufacturer - unlikely they'll do it anyway

---

### Post by rc547 on 2008-05-31
I've sorted this by using a different Region 2 disk but I don't know why it wouldn't accept the first one... so I won't mark it as solved.
Thanks for the help!

---

