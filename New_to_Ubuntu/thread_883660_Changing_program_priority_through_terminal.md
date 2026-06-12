---
title: "Changing program priority through terminal"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-08-08
Hi

I use rhythembox to play my music - its always jammed and crashed and i've had to force quit - and I think thats to do with all my music being stored on an external. 

But now when I do anything while playing music it goes very *shuddery* starting and stopping - I keep trying to change the priority through the system monitor and it says 'starting administrator' like it's going to ask me for a password - but then it and the system monitor disappear - and the priority is not changed...

how do I change rhythembox's priority to very high (-13) roughly - in the terminal?

also - any insight into why rhythembox always crashes and fails to start would be great - thanks.

---

### Post by bobbocanfly on 2008-08-08
You can use the 'renice' command to prioritise processes:

```
renice -<priority> <rhytmbox's pid>
```

As to why its crashing/locking. If you are using an old connection (USB 1.1) and playing high bitrate files, it may be a problem that Rhythmbox just cant get to the files quick enough, though I cant see this being a problem with compressed music (MP3, Ogg, AAC), only with lossless (Flac).

It could also be your drive is spinning down too much, so when you want to play music it has to spin up before you can access it (this can take a while). If rhythmbox is locking on startup, or when you hit play on a new song, this may be your problem. Try waiting a few seconds and see if it resolves itself.

You could also try a different player (Rhythbox isnt the best player going, IMO). You should try Banshee (sudo apt-get install banshee) and see if you still get the same problems.

---

### Post by mcduck on 2008-08-08
Remember to use "sudo" with renice if you want to increase a programs's priority (decrease the nice). Only root is allowed to set nice levels below 0..

But I agree with bobbocanfly that your probelms are probably resulting from something else than too low priority..

---

### Post by phantomjoker on 2008-08-08
is there a way to stop my disk 'spinning down too much'?

sorry if thats a silly question

---

### Post by ibuclaw on 2008-08-08
```
hdparm -B 200 -S 240 -M 254 /dev/sda
```
Sets the hard drive up for performance over power savings...
Should prevent spinning down unless...
[EDIT]
20 minutes idle. (Which will probably never happen, with various app fsync()'ing once every 5/10 minutes ;))


Regards
Iain

---

### Post by phantomjoker on 2008-08-08
THANKS - but I dont think my external is dev/sda   --  um how do i find out which hard drive is sda and sda1 etc? :S

---

### Post by drs305 on 2008-08-08
> **phantomjoker said:**
> THANKS - but I dont think my external is dev/sda   --  um how do i find out which hard drive is sda and sda1 etc? :S

You can probably determine it with:
```
df -Th | grep dev
```

Sample output:
```
/dev/sda2     ext3     34G  717M   31G   3% /home
/dev/sda3     ext3     30G  177M   29G   1% /media/sda3
/dev/sda5     ext3     29G  6.7G   22G  25% /media/av

```

---

### Post by phantomjoker on 2008-08-14
i got the response

> /dev/sdb1: Permission denied


---

### Post by drs305 on 2008-08-14
> **phantomjoker said:**
> i got the response

Not sure which post you were trying - the one I posted wouldn't generate any message. If you were trying the hdparm or renice commands suggested by others you probably need administrative powers to run them. Try preceding whatever command you used with "sudo".

If this doesn't solve things please post what command you are trying to use that generates the error (and what you are trying to do if it isn't obvious).

---

### Post by phantomjoker on 2008-08-14
No - when I enter the command

```
 hdparm -B 200 -S 240 -M 254 /dev/sdb1 
```

i got that message above... apparently i am not the 'owner' of my external and thus cant make permisional and other-such changes... ?!

---

### Post by drs305 on 2008-08-14
> **phantomjoker said:**
> No - when I enter the command

```
 hdparm -B 200 -S 240 -M 254 /dev/sdb1 
```

i got that message above... apparently i am not the 'owner' of my external and thus cant make permisional and other-such changes... ?!

What I was trying to suggest was that you would need to run the command as:
```

*sudo* hdparm -B 200 -S 240 -M 254 /dev/sdb1 

```
precisely because as a normal user you do not have the 'power' to make such changes...

---

### Post by phantomjoker on 2008-08-15
oh right - yer oops - that was obvious.... cheers.

---

### Post by phantomjoker on 2008-08-15
Well I got this message
> /dev/sdb1:
 setting Advanced Power Management level to 0xc8 (200)
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD failed: Input/output error
 setting acoustic management to 254
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD:ACOUSTIC failed: Input/output error
 setting standby to 240 (20 minutes)
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(setidle1) failed: Input/output error
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(identify) failed: Input/output error


So I don't think its worked - but the original problem isn't such a problem anymore so...

By the way - if that did do something, how do I change it back?

cheers

---

