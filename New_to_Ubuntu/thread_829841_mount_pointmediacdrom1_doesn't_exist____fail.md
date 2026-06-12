---
title: "mount point/media/cdrom1 doesn't exist    fail"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by hazman on 2008-06-15
cdrom not recognised as i get when booting
mount point/media/cdrom1 doesn't exist    fail

---

### Post by bumanie on 2008-06-15
Post the teminal output of > gksudo gedit /etc/fstab

---

### Post by hazman on 2008-06-15
this is the out put
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a9f7d025-07ab-4ae1-818d-026976e0fbeb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c21c999a-844d-36b4-acfb-b16315e0a520 none            swap    sw              0       0
/dev/scd0        /media/cdrom0   udf,iso9660,noauto,exec,utf8 0 0
/dev/scd1        /media/cdrom1   udf,iso9660,noauto,exec,utf8 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

its an external pcmcia cdrom

---

### Post by bumanie on 2008-06-15
TRy adding what I've put in red
/dev/scd0 /media/cdrom0 udf,iso9660,[COLOR="Red"]user,[/COLOR]noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660,[COLOR="Red"]user,[/COLOR]noauto,exec,utf8 0 0[COLOR="Black"][/COLOR]

---

### Post by hazman on 2008-06-15
it now says when booting
 unknown mount filesystem utf8 as well as mountpoint /media/cdrom1  doesn't exist fail
theres power to cdrom but cannot find cdrom

---

### Post by Joeb454 on 2008-06-15
It looks like it's saying that the directory "/media/cdrom1/" doesn't exist, so could you try running ```
sudo mkdir /media/cdrom1
``` And then see if that part of the error disappears :)

---

### Post by bumanie on 2008-06-15
Here's the line regarding the cdrom from my /etc/fstab
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 that's why I suggested the 'user' addition as it seemed to be the difference (other than the device names of course). Change it back to how it was before, ie delete the two user additions you added and I guess you'll have to make new mount points for your cdrom drives.

---

### Post by hazman on 2008-06-15
i made the directory cdrom1. now when booting it says:-
unknown mount filesystem type utf8

---

### Post by bumanie on 2008-06-15
Presumably cdrom0 works as all the error messages you've posted concern only cdrom1, could there be a problem with cdrom1? My be you could swap the two drives around and see if the same error still occurs. If the error transfers to cdrom0, it will show that cd drive is problematic, if it still shows that cdrom1 is the problem, the issue will be with the connector or a data bus or some-such on the motherboard.

---

### Post by hazman on 2008-06-15
the errors on boot have dissappeared but but when i try to use cdrom it says no cdrom can be found.the power light is on and the light on front of cd tray flashing.and i dont under stand why theres two referrences to cdrom i.e cdrom0 and cdrom1

---

### Post by Joeb454 on 2008-06-15
Do you have 2 different CD drives?

As bumanie mentioned, the fact you have cdrom1 suggests you also have cdrom0.

If so, do you get the same error in your other CD drive?

---

### Post by hazman on 2008-06-15
no just 1 cdrom but 2 card slots slot [1] has wireless card in and [2] has cdrom plugged in

---

### Post by Joeb454 on 2008-06-15
I see :)

I can't think why it wouldn't find the medium (i.e. disc) in the drive :confused: have you tried with a different disc, just to check that the 1st isn't faulty :)

---

### Post by hazman on 2008-06-15
i know it was a pain when i ran xp on here having to install driver in dos before attempting to install.but theres power there its just wont play cd's tried a couple now and swapped the 2 cards round tp see it was that

---

### Post by hazman on 2008-06-15
how do i mount a cdrom and how do you  mark a post solved

---

### Post by TeoBigusGeekus on 2008-06-15
1)Put the cd in the drive and close the tray. It will be automatically mounted.
2)Go to thread tools and select Mark as solved.

---

### Post by hazman on 2008-06-15
looks like cdrom not working tried that and nothing happens

---

### Post by TeoBigusGeekus on 2008-06-15
What's in the cd rom?

---

### Post by rraj.be on 2008-06-15
Try this

```
sudo mount /dev/sr0 /media/cdrom
```

Hope it helps you.

---

### Post by hazman on 2008-06-15
i've tried a data disc and an audio disc

---

### Post by Joeb454 on 2008-06-15
I believe you also started [this thread]("http://ubuntuforums.org/showthread.php?t=829841"), which could possibly be considered a duplicate. Just a note that this is against forum policy.

Other than that, "Thread Tools" at the top of this page to 'solve' your thread.

Do you have another CD Drive you could try?

---

### Post by TeoBigusGeekus on 2008-06-15
What happens if you go to 
/media/cdrom0 or /media/cdrom1 (depending on the name of your drive).
Can you see any contents?

---

### Post by hazman on 2008-06-15
used this sudo mount /dev/sr0 /media/cdrom says device doesn't exist

---

### Post by bapoumba on 2008-06-15
Threads merged.

---

### Post by Robertjm on 2008-06-15
FWIW: When I insert a CD or DVD in my drive it automatically mounts it as /media/scd0

Robert

---

### Post by hazman on 2008-06-15
when i use 
wayne@ubuntu:~$ sudo mount /dev/sr0 /media/cdrom
[sudo] password for wayne: 
mount: special device /dev/sr0 does not exist
wayne@ubuntu:~$ 



sorry if caused a problem by asking similar question just thought that might be the problem not being able to mount it SORRY as my original post had sort of been resolved as   i no long got a fail on boot and wasn't sure how to mark it solved

---

### Post by hazman on 2008-06-15
when i used this command 
sudo mount /dev/sr0 /media/cdrom
it said special devive doesn't exist.so i had a look in dev and found sda,sda1,sda2 and sda5.but when i looked in fstab the cd rom are 
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0 0
so am wondering if i have to create these dirctories for it to point to cdrom

---

### Post by impert on 2008-06-15
If you only have one cdrom drive, perhaps you could try deleting or commenting out the line that says
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

using sudo gedit.

Just a suggestion - I don't know if it will work.

---

### Post by mc4man on 2008-06-15
Why don't you try running these and see if you can find the device and if so what the logical name(s) are
```
sudo lshw -C disk
```

```
 sudo lshw -html > hardware.html
```  - will create a file in home dir.,double click to open in web browser

---

### Post by hazman on 2008-06-15
this is only reference i can find to cdrom
id:	
pccard
description: 	PCCARD-IDE
vendor: 	FREECOM
physical id: 	
0
version: 	REV836
slot: 	Socket 1
resources:	
irq	:	4

---

### Post by mc4man on 2008-06-15
Unfortunately I don't have a pcmcia slot on my machines so no experience there. I'd try after booting up unplugging then plugging in the card and see if anything shows up running lspci
There is a package pcmciautils - you could ck and see if it's installed (probably is)
It's a somewhat hard thing to search - try FREECOM pcmcia
Mostly find old posts - some talk about editing in some info to /etc/pcmcia
Sorry can't find more

---

### Post by hazman on 2008-06-15
Thanks any mc4man

---

### Post by mc4man on 2008-06-15
maybe try using nopcmcia as a boot parameter  (I'd assume with drive hooked up at boot)

---

### Post by hazman on 2008-06-17
just wonder how i could associate files using terminal and gksudo gedit/etc/fstab which gave me
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a9f7d025-07ab-4ae1-818d-026976e0fbeb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c21c999a-844d-36b4-acfb-b16315e0a520 none            swap    sw              0       0
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0 0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
but when i try to munt it i get
wayne@ubuntu:~$ sudo mount /media/cdrom0
mount: special device /dev/scd0 does not exist
wayne@ubuntu:~$ 

so i looked in dev and found no reference to it but there was to /dev/fdo
so i wondered if i had to make a reference to it but how

---

### Post by tipiglen on 2008-07-04
try this:
[http://ubuntuforums.org/showthread.php?p=5318658#post5318658](http://ubuntuforums.org/showthread.php?p=5318658#post5318658)

best of luck
ed

---

