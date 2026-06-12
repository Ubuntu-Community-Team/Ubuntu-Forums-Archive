---
title: "start up failure"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by lemured on 2011-10-24
ubuntu karmic

HELP :(

i cannot start up. 
means cannot do anything, except starting wind-puke-ows :(

when trying to start ubuntu it tells me that it won't, pressing 
ctrl D
would make it try again, but same result.
my apologies, cannot restate the exact message [on screen, not as a window] now as it'd mean to restart again, which i cannot do right this moment.

the whole trouble began with an almost normal start up, but i had to go via set up and set time and date right [time & date had been changed]. 

this worked once.

today the same, but instead the above happened.

i get to the panel to choose from [ubuntu, ..., windows...]. choose ubuntu. enter.
ubuntu-emblem shines. then the above.

windows works but i don't want to be forced using it...!

anyone any idea? please? :(

i'll follow with the exact words on the screen next time, if necessary.

thanks,

  a sad lemured

---

### Post by kaldor on 2011-10-24
Is this a fresh Ubuntu install or have you been using it for a while? 9.10 is pretty outdated by now.

---

### Post by lemured on 2011-10-24
> **kaldor said:**
> Is this a fresh Ubuntu install or have you been using it for a while? 9.10 is pretty outdated by now.

i've been using it for some time, yes, i have to update,
but i wouldn't think that the cause for a start-up problem could lie there...?
new installing, yes, i can imagine quite an array of potential problems, but a failure 
to start?

then again, i might be so wrong....

---

### Post by kaldor on 2011-10-24
Nope, that shouldn't be any reason for a problem in booting. Even if your OS is outdated, you still have every right to expect it to work properly.

Did you apply an update or do anything with your system before this happened? When was the last time you did a reboot?

---

### Post by lemured on 2011-10-27
hi kaldor, sorry for replying so late,
am travelling and wasn't online for 2 days.

meanwhile i figured the following:
it's connected with time- and date-setting.
the screen-message appearing simply reads that booting failed and that a maintenance shell has been fired, waiting for ages results in nothing, neither does a retry.
ctrl alt del brings me to settings, and here it is that i see that date and time are incorrect. after correcting and saving this i'm able to boot. 
however, this had worked already once before, later i had to repeat the procedure as time and date had been reset again.

currently it's working.

to answer your questions, no, i did not yet attempt an update, and i'll have to wait with it for a couple more days.
reboot: today. 2 days ago before that.

i hope all this may sound recognizable to you, for me the constant time-resetting doesn't make any sense, and neither this to be the root of the problem, although correcting it enables it to boot.

thank you in any case, i should be able to read here again the day after tomorrow.

be well,

     lemured



> **kaldor said:**
> Nope, that shouldn't be any reason for a problem in booting. Even if your OS is outdated, you still have every right to expect it to work properly.

Did you apply an update or do anything with your system before this happened? When was the last time you did a reboot?

---

### Post by cryptotheslow on 2011-10-27
It sounds to me like it is actually your PC hardware is not retaining the time.

When you Ctrl-Alt-Del from the maintenance shell you are actually rebooting the entire PC - not doing something specific within Ubuntu. So that time setting you are updating is your PC hardware clock.

If this a desktop type PC then - it is most likely that the lithium battery on the motherboard is no longer holding charge, or the BIOS setting reset jumper is incorrectly set. Typically the battery is an easily replaced flat button type of battery. Although some motherboards do have manufacturer specific battery packs, it is not that common.

Usually when that battery looses power the BIOS date defaults to 01-01-1970 00:00:00. However, it may be that your BIOS defaults to nothing stored at all, or something that makes no sense. Which could explain why the operating system will not load as it senses that the date/time is just not sane and bails out (either by design or by panic).

Let us now more about your PC & Motherboard particularly if you need more help :D

---

### Post by lemured on 2011-11-23
> **cryptotheslow said:**
> It sounds to me like it is actually your PC hardware is not retaining the time.

When you Ctrl-Alt-Del from the maintenance shell you are actually rebooting the entire PC - not doing something specific within Ubuntu. So that time setting you are updating is your PC hardware clock.

If this a desktop type PC then - it is most likely that the lithium battery on the motherboard is no longer holding charge, or the BIOS setting reset jumper is incorrectly set. Typically the battery is an easily replaced flat button type of battery. Although some motherboards do have manufacturer specific battery packs, it is not that common.

Usually when that battery looses power the BIOS date defaults to 01-01-1970 00:00:00. However, it may be that your BIOS defaults to nothing stored at all, or something that makes no sense. Which could explain why the operating system will not load as it senses that the date/time is just not sane and bails out (either by design or by panic).

Let us now more about your PC & Motherboard particularly if you need more help :D


hi, and apologies to you and the others for the late reply, but i haven't been online much in the recent weeks.

no, it's a netbook, and it seems with the last correction of time and date the problem has been solved. for some reason. needed several times. the ways of the digit are mysterious.
although i still don't quite understand what the problem was, my thanks to all for the advise. i'll mark this thread as 'solved.'

---

