---
title: "Help Modifiying SCSI Module"
date: 2007-06-02
forum: Programming Talk
---

### Post by carranzafp on 2007-06-02
Hi, I am writing some programs to be able to repair Hitachi Drives wich where "bad-flashed" and are stuck on a panic mode.  

On that panic mode the drives only answer to very few commands, and for detection only an ATAPI Inquiry will work.  

is there a way to patch the scsi module to skip all detection sequence and accept the drive only with the inquiry command?  What I need is to get the drive visible to start issuing commands that will repair the bad flash.

I think the scsi detection sequence do a lot of other commands to accept a LUN but no other command will be answered by the drive on that state.

Thanks for the time on reading.

---

