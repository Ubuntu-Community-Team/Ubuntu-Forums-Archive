---
title: "DVD Won't Recognize Backups (Video DVDs)"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by minger_88 on 2012-09-05
OK, long story short I just built a computer with 4 TB disc space to get all of my dvd backups out of the way. So, trouble is that my DVD drive doesn't recognize the backups. It **does** perfectly read music CDs. I can even burn DVDs using Brasero or whatever. That is all fine. I can even perfectly read "commercial" DVDs. However, when I put a burned backup in, it doesn't get recognized (it **was** working!), and it won't mount manually. 

So, basically I was having this exact same issue and was playing around with fstab. Eventually, somehow, doing *something* I got it working. It was glorious! I was ripping this same DVD a few different ways to see what encoder settings looked good through ps3mediaserver. . . .and then the power flickered and my computer restarted. When it booted back up, it didn't work again! ! ! ! Still, commercial DVDs and music CDs play fine, so I don't think its the drive. 

Here is what happens when I put the actual Dark Knight movie in:
```
 ~ $ sudo lshw
           *-cdrom
                description: DVD writer
                product: DVD+-RW ND-3650A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                logical name: /media/cdrom
                version: 105C
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready

```It shows up in Devices, works perfectly. Now, when I put the backup in, it doesn't show up in Devices. Here are some file outputs:
```
 ~ $ sudo lshw
           *-cdrom
                description: DVD writer
                product: DVD+-RW ND-3650A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 105C
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

```So it recognizes that there is 'a' disc in there, but it won't mount or recognize. 
```
~ $ sudo mount /dev/sr0 
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``````

~ $ dmesg | tail
[163710.115132] attempt to access beyond end of device
[163710.115134] sr0: rw=0, want=2052, limit=4
[163710.115137] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=512, location=512
[163710.115141] UDF-fs: error (device sr0): udf_read_tagged: tag version 0x0000 != 0x0002 || 0x0003, block 0
[163710.115144] UDF-fs: error (device sr0): udf_read_tagged: tag version 0x0000 != 0x0002 || 0x0003, block 0
[163710.115148] UDF-fs: warning (device sr0): udf_load_vrs: No anchor found
[163710.115150] UDF-fs: warning (device sr0): udf_fill_super: No partition found (1)
[163710.171668] attempt to access beyond end of device
[163710.171674] sr0: rw=0, want=68, limit=4
[163710.171677] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```Lastly, my fstab (you can clearly see all the tries)
```

#Trying to manually add the DVD Drive
#/dev/sr0 /mnt/cdrom auto noauto,user
#/dev/sr0 /media/cdrom iso9660 user, noauto 0 0
#/dev/sr0  /media/cdrom  auto  users,noauto,exec,utf8  0  0
#/dev/sr0 /media/cdrom auto rw,noauto,user,exec 0 0
/dev/sr0  /media/cdrom   udf,iso9660  users,noauto,exec,utf8  0  0
#/dev/sr0 /media/TEST iso9660,udf user,noauto,exec,utf8 0 0

```I'm starting to pull my hair out, so I appreciate the help.

---

### Post by shreepads on 2012-09-06
How did you create the backup disk? I suspect the rrot cause to be one of those infamous copy protect schemes...

---

### Post by minger_88 on 2012-09-06
I believe most of my backups were using AnyDVD. Thing is, I **swear** that it was working. In fact I have an encoded mp4 in my home right now from when I was trying different encoder options. I even loaded the backup successfully in my Windows 7 Laptop. Also works in PS3 -- I don't believe it to be the disc. 

Is there some special filesystem or something besides udf that I could try?

---

### Post by shreepads on 2012-09-07
Assuming you have libdvdcss up and running have a look at this:

[http://www.cmdln.org/2010/01/22/backing-up-disney-dvds/](http://www.cmdln.org/2010/01/22/backing-up-disney-dvds/)

I tweaked it a bit:

a. Insert the DVD and run
```
ddrescue –n –b 2048 /dev/dvd output.iso 
```

b. Play the output.iso using VLC. Assuming it plays well, note the chapters you're interested in

c. Run Handbrake on output.iso and select the relevant chapters

Don't know if this will work but worth a try I think!

---

### Post by minger_88 on 2012-09-07
No dice. . .
```
~ $ ddrescue -n -b 2048 /dev/sr0 output.iso


Press Ctrl-C to interrupt
rescued:      2048 B,  errsize:       0 B,  current rate:        0 B/s
   ipos:         0 B,   errors:       0,    average rate:        0 B/s
   opos:         0 B,     time from last successful read:       0 s
Finished         

```
This was very similar to what I got just trying **dd**. I get a infinitely small .iso file of apparently nothing when I **know** there is stuff on there. 

Again, these DVDs play fine in Windows and on the PS3 (what bothers me more is that they were being recognized on my computer).

---

### Post by SeijiSensei on 2012-09-07
Some DVDs use protection schemes other than CSS.  

I'd run a test with a known problematic DVD.  Try making a copy on your Linux box with Brasero or K3b.  Does it work?

---

### Post by shreepads on 2012-09-08
> **minger_88 said:**
> No dice. . .
```
~ $ ddrescue -n -b 2048 /dev/sr0 output.iso


Press Ctrl-C to interrupt
rescued:      2048 B,  errsize:       0 B,  current rate:        0 B/s
   ipos:         0 B,   errors:       0,    average rate:        0 B/s
   opos:         0 B,     time from last successful read:       0 s
Finished         

```
This was very similar to what I got just trying **dd**. I get a infinitely small .iso file of apparently nothing when I **know** there is stuff on there. 

Again, these DVDs play fine in Windows and on the PS3 (what bothers me more is that they were being recognized on my computer).


What happens if you use /dev/dvd instead of /dev/sr0 on the command line?

---

### Post by minger_88 on 2012-09-09
> What happens if you use /dev/dvd instead of /dev/sr0 on the command line?     Same Thing.

I was able to find a backup that reads fine. It shows up in Devices as soon as I pop it in. It seems to be properly recognized as udf, which is why I'm guessing it mounts.

```
 ~ > sudo lshw
*-cdrom
                description: DVD writer
                product: DVD+-RW ND-3650A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                logical name: /media/cdrom
                version: 105C
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted

```Then I try another that I just pulled out of my Windows Laptop that does read fine there and nothing. 
```
 ~ > sudo lshw
  *-cdrom
       description: DVD writer
       product: DVD+-RW ND-3650A
       vendor: _NEC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 105C
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```and manually trying to mount:
```
~ $ sudo mount /dev/sr0 
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you must specify the filesystem type

```and maybe some helpful debugging message:
```
~ $ dmesg | tail
[170568.621802] sr0: rw=0, want=1028, limit=4
[170568.621807] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=256, location=256
[170568.622485] UDF-fs: error (device sr0): udf_read_tagged: tag version 0x0000 != 0x0002 || 0x0003, block 0
[170568.622492] attempt to access beyond end of device
[170568.622495] sr0: rw=0, want=2052, limit=4
[170568.622498] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=512, location=512
[170568.622502] UDF-fs: error (device sr0): udf_read_tagged: tag version 0x0000 != 0x0002 || 0x0003, block 0
[170568.622505] UDF-fs: error (device sr0): udf_read_tagged: tag version 0x0000 != 0x0002 || 0x0003, block 0
[170568.622509] UDF-fs: warning (device sr0): udf_load_vrs: No anchor found
[170568.622511] UDF-fs: warning (device sr0): udf_fill_super: No partition found (1)

```

---

### Post by shreepads on 2012-09-10
Sorry, can't think of anything else that may be causing the problem... Did you look into Sensei's suggestion re a different encryption/ copy protection scheme?

One last roll of the dice would be to update the DVD drive firmware, but don't try that unless you're desperate...

---

