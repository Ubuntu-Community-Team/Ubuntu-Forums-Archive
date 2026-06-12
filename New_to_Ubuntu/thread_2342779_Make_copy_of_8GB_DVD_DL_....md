---
title: "Make copy of 8GB DVD DL ..."
date: 2016-11-09
forum: New to Ubuntu
---

### Post by cwmoser on 2016-11-09
My car uses an 8GB DVD for Navigation.
I ordered an update DVD but it sometimes comes up with a read error while in the car.
I want to copy this navigation DVD onto a blank 8GB DVD I have hoping that will work better.
Tried **Brasero**, **K3b**, and **K9copy** but can't get them to copy.
I was able to get the ISO file created on my hard drive and its size is 8.4GB.

Any suggestions on what works to burn this ISO file?????

---

### Post by oldrocker99 on 2016-11-09
A dual-layer DVD is 8.5 GB in size, so any of those programs **should** burn it successfully. Of course, you do need a dual-layer burner; you do have one, right?

---

### Post by scdbackup on 2016-11-10
Hi,

one should copy the data stream from the DVD into a disk file
and then submit it as "image" file to the burn program.

You report to already have done the copying. Nevertheless for
 completeness i describe this step too.
Assuming that your DVD drive has device file address /dev/sr0,
create the image file by this shell command:
```

dd if=/dev/sr0 bs=1M of=navi_dvd.img

```

Then use this file as "image" with your favorite GUI program, or
do in the shell:
```

xorriso -as cdrecord -v dev=/dev/sr0 -eject navi_dvd.img

```

If you have two DVD drives, you could copy directly from DVD to DVD:
```

dd if=/dev/sr0 bs=1M | xorriso -as cdrecord -v dev=/dev/sr1 -eject -

```

Have a nice day :)

Thomas

---

### Post by cwmoser on 2016-11-10
I get this error burning the image:

```

libburn : FAILURE : SCSI error condition on command 53h RESERVE TRACK: [3 72 01] Medium error. Session fixation error writing lead-in.
libburn : FATAL : Cannot reserve track of 8355577856 bytes
xorriso : FATAL : -abort_on 'FAILURE' encountered 'FATAL' during image writing
xorriso : NOTE : libburn has now been urged to cancel its operation
xorriso : FAILURE : libburn indicates failure with writing.
xorriso : NOTE : Gave up -outdev ''
xorriso : NOTE : Giving up for -eject whole -dev ''
xorriso : FAILURE : -as cdrecord: Job could not be performed properly.
xorriso : aborting : -abort_on 'FAILURE' encountered 'FATAL'


```

Seems every program I use emits this "Cannot reserve track of 8355577856 bytes"

Tried xorriso, Brasero, K3b, K9copy.  Is this some sort of protection associated with this DVD?

---

### Post by scdbackup on 2016-11-10
Hi,

> 
```

libburn : FAILURE : SCSI error condition on command 53h RESERVE TRACK: [3 72 01] Medium error. Session fixation error writing lead-in.

```
Is this some sort of protection associated with this DVD?   


No. Your DVD burner cannot cope with the DVD medium to which it shall burn.
The code "3 72 01" was issued by the burner. It is listed in SCSI specs as
what libburn quotes:
  "Medium error. Session fixation error writing lead-in."

"Lead-in" is the disc area before the payload area. It contains the
Table-Of-Content where the new payload track was about to be registered
as reserved.
"Medium error" means that the problem is in the relation between drive
and medium. (The pot calling the kettle black.)
The SCSI command 53h was issued to tell the drive and medium how many
blocks will be written.

You may prevent this in-advance reservation of the track by using option -tao.
```

xorriso -as cdrecord -v dev=/dev/sr0 -tao -eject navi_dvd.img

```
But probably a medium error will happen on the first payload write attempt
or at the very end of the burn run, when the size of the written track has
finally to be recorded in the lead-in area.

In any case try a fresh DVD+R DL medium, just to rule out that there is
an individual flaw with the medium.

Have a nice day :)

Thomas

---

### Post by cwmoser on 2016-11-10
Tried with a fresh DVD+R DL disc and got same error.
Tried it on both my DVD drives:  /dev/sr0 and on /dev/sr0.
The DVD drives have this on front:  "RW DVD+R DL"

This is what i get:

```

$ xorriso -as cdrecord -v dev=/dev/sr1 -tao -eject navi_dvd.img
xorriso 1.4.2 : RockRidge filesystem manipulator, libburnia project.

Drive current: -outdev '/dev/sr1'
Media current: DVD+R/DL
Media status : is blank
Media summary: 0 sessions, 0 data blocks, 0 data, 8152m free
Beginning to write data track.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
xorriso : UPDATE :    0 of 7968 MB written (fifo 99%) [buf   0%]   0.0x.
libburn : FATAL : SCSI error on write(0,16): [3 72 01] Medium error. Session fixation error writing lead-in.
xorriso : FATAL : -abort_on 'FAILURE' encountered 'FATAL' during image writing
xorriso : NOTE : libburn has now been urged to cancel its operation
xorriso : FAILURE : libburn indicates failure with writing.
xorriso : NOTE : Gave up -outdev ''
xorriso : NOTE : Giving up for -eject whole -dev ''
xorriso : FAILURE : -as cdrecord: Job could not be performed properly.
xorriso : aborting : -abort_on 'FAILURE' encountered 'FATAL'


```

---

### Post by scdbackup on 2016-11-10
Hi,

yes, the drive stated towards libburn that it recognizes the medium as
DVD+R DL and that it can take 8152 MiB = 8,547,991,552 bytes. Your image
is small enough. So libburn started writing.

But, as feared, the failure with option -tao happened with the first SCSI
write command. As soon as the laser shall change the medium, the drive
yells "failure". (Actually it lasted about 14 seconds until it yelled.)

This is not the first time that i see problems with DVD+R DL when the
drive gets older. It might also be that the quality of new media gets
worse.

An improbable possibility would be that the drives wand a layer break
position to be set. (The error code does not indicate this. But well ...)

Program growisofs sets that position and quite often fails at the
according SCSI command. Maybe you want to test whether your drives love 
one of these two:
```

growisofs -Z /dev/sr0=navi_dvd.img
growisofs -dvd-compat -Z /dev/sr0=navi_dvd.img

```
As said, a long shot.

Have a nice day :)

Thomas

---

### Post by cwmoser on 2016-11-11
I did try ...

```
growisofs -Z /dev/sr0=navi_dvd.img
growisofs -dvd-compat -Z /dev/sr0=navi_dvd.img
```

... but still no joy.  Hmmm.  Could it be both my DVD drives are bad or is it some bug in 16.04?

---

### Post by scdbackup on 2016-11-11
Hi,

> still no joy.

What was the error message of growisofs ?

The ones from xorriso surely were not about a bug in Linux but
a problem between drive and medium.
Our remedy attempts tried variations of the sequence of drive-to-media 
operations. But as it seems the first real change action on the medium 
triggers failure messages from the drive.

Did you already try DVD+R DL from another brand ?
(... and what is the cheapest new DVD drive you can get ?)


Have a nice day :)

Thomas

---

### Post by cwmoser on 2016-11-11
> **scdbackup said:**
> 

What was the error message of growisofs ?
...
Did you already try DVD+R DL from another brand ?
...
Thomas

I am using Kodak brand DVD RW +DL blank discs.

```

$ growisofs -dvd-compat -Z /dev/sr1=navi_dvd.img
Executing 'builtin_dd if=navi_dvd.img of=/dev/sr1 obs=32k seek=0'
:-? L0 Data Zone Capacity is set already
/dev/sr1: "Current Write Speed" is 2.5x1352KBps.
          0/8355250176 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/8355250176 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/8355250176 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=0h failed with SK=3h/SESSION FIXATION ERROR WRITING LEAD-IN]: Input/output error
:-( write failed: Input/output error

```

---

### Post by scdbackup on 2016-11-12
Hi,

all programs received the same error message from the drive
when trying to write.

Nevertheless, this message by growisofs
```

:-? L0 Data Zone Capacity is set already

```
which stems from
  [https://sources.debian.net/src/dvd%2Brw-tools/7.1-11/growisofs_mmc.cpp/#L1636](https://sources.debian.net/src/dvd%2Brw-tools/7.1-11/growisofs_mmc.cpp/#L1636)
indicates that the medium already had a layer break address set.
So growisofs did not try to set the end address of layer 1 by itself.

I.e. the intended experiment did not happen in this run.

Was it a second growisofs run on the same medium ?

If so: What error message did the first yield ?

If not: If this was a medium which was already used in previous burn
attempts, then re-try with a new one.

If it was already a new medium, then the medium state is unusual.

Have a nice day :)

Thomas

---

### Post by cwmoser on 2016-11-12
I ran this command **growisofs -dvd-compat -Z /dev/sr1=navi_dvd.img** again but with a fresh disc.
This is what I get:

```

...
4167663616/8355250176 (49.9%) @2.4x, remaining 21:44 RBU 100.0% UBU  85.7%
 4178280448/8355250176 (50.0%) @2.3x, remaining 21:40 RBU 100.0% UBU  85.7%
 4178280448/8355250176 (50.0%) @0.0x, remaining 21:43 RBU 100.0% UBU 100.0%
 4178280448/8355250176 (50.0%) @0.0x, remaining 21:47 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=1f2170h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error

```

---

### Post by cwmoser on 2016-11-12
I ran this command **growisofs -dvd-compat -Z /dev/sr1=navi_dvd.img** again but with a fresh disc.
This is what I get:

```

...
4167663616/8355250176 (49.9%) @2.4x, remaining 21:44 RBU 100.0% UBU  85.7%
 4178280448/8355250176 (50.0%) @2.3x, remaining 21:40 RBU 100.0% UBU  85.7%
 4178280448/8355250176 (50.0%) @0.0x, remaining 21:43 RBU 100.0% UBU 100.0%
 4178280448/8355250176 (50.0%) @0.0x, remaining 21:47 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=1f2170h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error

```

---

### Post by cwmoser on 2016-11-12
I ran this command **growisofs -dvd-compat -Z /dev/sr1=navi_dvd.img** again but with a fresh disc.
This is what I get:

```

...
4167663616/8355250176 (49.9%) @2.4x, remaining 21:44 RBU 100.0% UBU  85.7%
 4178280448/8355250176 (50.0%) @2.3x, remaining 21:40 RBU 100.0% UBU  85.7%
 4178280448/8355250176 (50.0%) @0.0x, remaining 21:43 RBU 100.0% UBU 100.0%
 4178280448/8355250176 (50.0%) @0.0x, remaining 21:47 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=1f2170h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error

```

At first I thought you identified that I needed a fresh disc - but it failed at 50%.



Tried a another fresh disc:
```

Executing 'builtin_dd if=navi_dvd.img of=/dev/sr1 obs=32k seek=0'
/dev/sr1: splitting layers at 2039856 blocks
/dev/sr1: "Current Write Speed" is 2.5x1352KBps.
          0/8355250176 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/8355250176 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/8355250176 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=0h failed with SK=3h/SESSION FIXATION ERROR WRITING LEAD-IN]: Input/output error
:-( write failed: Input/output error

```

And I get the same results using both my DVD drives.

---

### Post by scdbackup on 2016-11-13
Hi,

```

 4178280448/8355250176 (50.0%) @0.0x, remaining 21:47 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=1f2170h failed with SK=3h/WRITE ERROR]: Input/output error

```

Grrr. This time it worked up to the end of the first layer.

You need other hardware. Other burner and/or other media.

You could first try all your remaining DVD+R DL media whether one of them 
works completely. But if you consider to get a new burner (they are cheap 
nowadays) then you should keep some of the current media for that burner.

Have a nice day :)

Thomas

---

### Post by kingneutron on 2016-11-30
--I don't think -dvd-compat option is helping you.  Read up on growisofs, this is what I use to burn a UDF filesystem onto bluray:

# time growisofs -speed=6 -overburn -Z \
  /dev/bluray=/mnt/bluraytemp25/bdiscimage.udf

--Limiting the speed to (lower than, or equal to) what is listed for your media may help, using -overburn may really help...

---

### Post by gordintoronto on 2016-11-30
To me, it looks like the update DVD is copy-protected, by putting data outside the area your DVD writer can handle.

---

