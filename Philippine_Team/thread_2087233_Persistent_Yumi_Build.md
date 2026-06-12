---
title: "Persistent Yumi Build"
date: 2012-11-23
forum: Philippine Team
---

### Post by juceasar on 2012-11-23
hi everybody, i joined the forum just yesterday and im so glad to know that there are so many pinoys using ubuntu/linux system. i joined the forum  to ask a question but i ended up doing it myself. i was supposed to a ask for your help to make a yumi in a usb but i became hesitant and searched first from previous threads and as lazy that i can be i stopped browsing on the 10th page. and yesterday while already in front of the computer all ready to make a question i suddenly asked myself instead that i havent tried my best yet. 

ok. heres what i wanted: a yumi build with persistent linux. i want to put [COLOR=Blue]ubuntu 12.04, zorin6lite, winxp sp3 installer, HBcd, and xbmcbuntu[/COLOR]. i used [COLOR=Red]yumi  [/COLOR]http://www.pendrivelinux.com/yumi-multiboot-usb-creator/  and [COLOR=Red]casper creato[/COLOR]r [http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/) and isos of each of those i want to include using a 4gb lg xstick. and my problem yesterday was i could not make it persistent. there was no problem with booting and such and the problem really is how do i make the linux persistent. and so finally this morning i was able to make a connection between the casperrw and the linuxboot. its just a matter of adding persistent tag line along the append line in the linux cfg. 

yeah im so happy with what i have right now and i can really do more with ubuntu and yumi. i guess everybody should have a yumi build as well.

---

### Post by BillSnow on 2012-11-23
"and so finally this morning i was able to make a connection between the casperrw and the linuxboot. its just a matter of adding persistent tag line along the append line in the linux cfg."

Can you please explain exactly what you did to achieve this?

I have tried about a hundred different ways to add persistent to the various config files and have yet to make a single YUMI persistent OS...

---

### Post by BillSnow on 2012-11-24
Nevermind... I feel a bit stupid.

This whole time I've been trying to figure out the random appearance of the config file within notepad. On a whim I opened it in winword and it's plain as day...

---

### Post by juceasar on 2012-11-24
its good to know you already got it. so have you tried if you already have a persistent live linux? i have no internet yesterday so i read your post just this morning. one thing im going to work on later is how to remove the install this icon. thanks and have fun with your yumi yummy

---

### Post by BillSnow on 2012-11-25
Yep... I tried it and it's working...

I can't manage to remove the "install this" either...

Only real problem I'm having is the boot speed and overall speed of the persistent system.

Without persistence, the drive boots up in less than 10 seconds and it runs fast enough that you wouldn't think it's off of a usb (because it's loaded to memory).

With persistence however, it takes about 4 minutes to boot, and the system runs slow as can be.

I'm testing making a casper-rw ext2 partition instead of the casper file in hopes that it'll run faster...

P.S.
- Finished formatting and installing (was installing when I posted first part of this)... It stills runs insanely slow with persistence activated...

Any idea what's going wrong?... Nobody mentioned this that I've found. People even make larger than 4 gig casper partitions for it.

I changed the cfg file to add another boot option. The basic non persistent and a copied version with different name and persistent option. When I do standard start on same exact system it's fast and responsive. Persistent is slow and sluggish.

---

### Post by juceasar on 2012-11-25
well i have mine running relatively fast before and after inclusion of casper to the usb. somehow im getting around 20 second slower boot when i added casper but no noticeable difference once inside ubuntu and installed media codecs afterwards to play hd movies and audio. i have an intel laptop with 2.0ghz dual core cpu, 2gb ram and 128mb vga(i dont know if this helps so you can make comparisons)

and right now im messing around with the removal of the install icon(finding clues for a workaround). i found this thread here  [http://ubuntuforums.org/showthread.php?t=2077841](http://ubuntuforums.org/showthread.php?t=2077841) and  [http://ubuntuforums.org/showthread.php?t=1573791](http://ubuntuforums.org/showthread.php?t=1573791) 

ill be working on it in the morning(till i get it right hopefully) and im guessing we're in different time zones. so best of luck and keep posting

---

### Post by BillSnow on 2012-11-25
How large is your casper file / partition?

My system specs shouldn't be holding anything back...
Doing all this on Samsung laptop 2.3GHz dual core, 6Gb DDR3, 1GB graphics...

I'll have to try shrinking my casper partition and seeing if that fixes anything... As it's 4 gig... I don't really need all that much considering I can use the rest of the jump drive for base storage (32 gig drive)...

No time to change anything right now... Just speculating...

---

### Post by juceasar on 2012-11-25
hey bill. i was able to remove the install icon but first i made my live account have all privileges/administrator and then i opened synaptic, marked ubiquity for removal and click apply.alls well with my ubuntu. 

p.s. my casper is just 1gb as i intend to use this only as my fail safe os and to carry around when i go for repairs. made with 4gb lg usb stick(dunno if this makes any difference with performance) also i preformatted the usb to fat32 before making yumi build. 

best regards and happy tweaking

---

### Post by x34460 on 2012-12-01
i have been wrestling with this for quite some time and am ready to seek help.

- i intend on having bodhi linux as the distro with persistence.
- have added "persistence" tag after ***each instance*** of "append" in bodhi.cfg as the instructions indicate: 
[URL="http://www.pendrivelinux.com/yumi-multiboot-usb-creator/"]ADDTL NOTES-
(3.) Add the word persistent to the end of each append line; (the line that starts with the word append).[/URL]
- added "persistence" tag after "append" in linux.cfg

settings are still not being saved.

maybe someone can copy/paste their linux.cfg and/or "distro".cfg files so i can compare. 

any help is appreciated.
thanks.

---

### Post by x34460 on 2012-12-01
ok, wow... it's just really, really slow.

i made a separate ext3 casper-rw partition to see if that would make any difference but it appears to not work.

time to consider other options.

---

### Post by Unebrion on 2013-01-06
Hello all, I found this post while googling. I'm having the same problem. I have 12.04 on my jump drive trying to make it persistent. 

this is my current code if I delete my casper file that I created it will launch fine, but if I make a change like changing the background then reboot it no longer boots

Any help is appreciated 

```
# Simple Menu Created by Lance http://www.pendrivelinux.com for YUMI - (Your USB Multiboot Installer)
menu title Ubuntu 12.04 Boot Menu
menu background /multiboot/ubuntu1204/isolinux/splash.png
MENU MARGIN 10
MENU VSHIFT 12
MENU ROWS 6
MENU TABMSGROW 12
menu color title 1;36;44 #66A0FF #00000000 none
menu color hotsel 30;47 #C00000 #DDDDDDDD
menu color sel 30;47 #000000 #FFFFFFFF
menu color border 30;44	#D00000 #00000000 std
menu color scrollbar 30;44 #DDDDDDDD #00000000 none

default live

label live
  menu label ^Run Ubuntu from this USB
  kernel /multiboot/ubuntu1204/casper/vmlinuz
  append cdrom-detect/try-usb=true noprompt boot=casper floppy.allowed_drive_mask=0 ignore_uuid live-media-path=/multiboot/ubuntu1204/casper/ initrd=/multiboot/ubuntu1204/casper/initrd.lz splash persistent --
label live-install
  menu label ^Install Ubuntu to a Hard Disk
  kernel /multiboot/ubuntu1204/casper/vmlinuz
  append cdrom-detect/try-usb=true noprompt boot=casper floppy.allowed_drive_mask=0 ignore_uuid live-media-path=/multiboot/ubuntu1204/casper/ file=/cdrom/preseed/ubuntu.seed only-ubiquity initrd=/multiboot/ubuntu1204/casper/initrd.lz splash persistent --
  
MENU SEPARATOR  
label <-- Back to Main Menu
 kernel vesamenu.c32
 append /multiboot/syslinux.cfg 
```

---

