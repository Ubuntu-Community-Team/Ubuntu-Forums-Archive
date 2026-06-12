---
title: "Playing a DVD"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-11
I never thought i'd have to ask this. I got VLC, but i don't know how to play a DVD. I go to file > open disc, and nothing.

---

### Post by pluckypigeon on 2008-07-11
> **adobrakic said:**
> I never thought i'd have to ask this. I got VLC, but i don't know how to play a DVD. I go to file > open disc, and nothing.

You need to add the Medibuntu Repos and then install libdvdcss2


```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```


```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


```
sudo apt-get install libdvdcss2
```

---

### Post by adobrakic on 2008-07-11
I did this, and i get this following error when I try to play a dvd:

```

Unable to open 'dvd:///dev/scd1'

```

---

### Post by mc4man on 2008-07-11
With the dvd in the drive run ```
sudo lshw -C disk
``` and see what turns up

---

### Post by adobrakic on 2008-07-11
```

ado@ado-desktop:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: SAMSUNG SV6003H
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: QQ10
       serial: 0427J1FT716102
       size: 55GiB (60GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=fcb1ec06
  *-cdrom:0
       description: CD-R/CD-RW writer
       product: LTR-48247S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: PPB1
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM GDR8160B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 0013
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
ado@ado-desktop:~$ 

```

---

### Post by mc4man on 2008-07-11
> *-cdrom:1
       description: DVD reader
       product: DVD-ROM GDR8160B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 0013
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open  [COLOR="Red"]<-[/COLOR]
Did you have a dvd in the drive?, status=open means no media detected in the drive.

---

### Post by adobrakic on 2008-07-11
meh, yeah i have it in the drive.
the dvd must be messed up.
thanks anyways, guys

---

### Post by SunnyRabbiera on 2008-07-11
try another media player?
like totem or xine?

---

### Post by adobrakic on 2008-07-11
I tried Totem, but it said I don't have permission to play it or some ****.
<- linux noob.
:(

---

### Post by SunnyRabbiera on 2008-07-11
well if so its probably because its totem gstreamer.
In synaptic remove it and replace it with totem xine... it works better.

---

### Post by adobrakic on 2008-07-11
Same thing. :/
I'm assuming it's not working because it's a burned DVD

---

### Post by mc4man on 2008-07-11
If the filesystem of the dvd isn't detected/supported (and then mounted) then you can't have playback. If you wish running ```
dmesg | tail
``` may show some info on the attempt.

Edit; to eliminate the condition of your drive/dvd laser, try a disk with a known filesystem/structure like a commercial dvd movie, also try a cd in that drive.

---

### Post by SunnyRabbiera on 2008-07-11
> **adobrakic said:**
> Same thing. :/
I'm assuming it's not working because it's a burned DVD

If its a disk you burned yourself, is it finalized?

---

### Post by alexcrossley on 2008-07-13
I am really suffering with similar problems.  I have 8.04 and an XPS1330 and I get the below output.  Basically, I cant read the DVD even when it is a real DVD?  Anyone able to help?

alex@XPS:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD writer
       product: DVD+-RW UJ-857G
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: Z111
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: SAMSUNG HM320JI
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 2SS0
       serial: S19FJ10PC25661
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=08000000

---

### Post by WRDN on 2008-07-13
Run:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

I had to do this to play DVD's myself, and hopefully it will work for you also.

---

