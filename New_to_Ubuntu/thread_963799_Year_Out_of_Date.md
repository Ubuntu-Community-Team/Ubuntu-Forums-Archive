---
title: "Year Out of Date?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by dachilleus on 2008-10-30
I rescued and old Dell Dimension from the University graveyard a while back thinking that it would make a great linux starter box.  When I finally got around to cleaning it up and running the install of Ubuntu 8.04 last weekend we got a blackscreen and message saying that the BIOS was old and the Year Out of Date message.

Do I need to flash/update the BIOS just to install Ubuntu?  Or is there a different Ubuntu option for download and install on older PCs?

Thanks for any assistance

---

### Post by egalvan on 2008-10-30
> **dachilleus said:**
> I rescued and old Dell Dimension from the University graveyard thinking that it would make a great linux starter box.   running the install of Ubuntu 8.04 last weekend we got a blackscreen and message saying that the BIOS was old and the Year Out of Date message.
HP ExpressCard
Do I need to flash/update the BIOS just to install Ubuntu?  Or is there a different Ubuntu option for download and install on older PCs?

Thanks for any assistance

Exact information on system specs would be helpful.

By all means update the BIOS to the latest for that model.

Also, replace the BIOS battery... this is almost always a flat 'button'-type cell, number 2032

And last but not least of the free/cheap options
give it a GOOD cleaning on the inside, with compressed air if possible.

---

### Post by aeiah on 2008-10-30
there arent versions of ubuntu for older machines, but there are distributions for slower ones, if you know what i mean. if it is old, you'll probably be best with xubuntu because it requires less system resources, but it will probably show you that error as well. updating the bios isnt that difficult. its usually just a matter of burning a few files to a cd and putting it in and booting from it like you would a livecd

---

### Post by dachilleus on 2008-10-30
Does this mean there is no way to install Ubuntu onto an older PC that yields this error?  The system seemed ot just hang on black screen and not do anything.  Will it acutally install or no?

I will try to upload system specs later - am at work in lab right now while machine sits obediantly in my garage.

---

### Post by snowpine on 2008-10-30
Hard to give you advice without knowing the system specs. For Ubuntu 8.04, I recommend a pentium 4 or better with at least 512mb of ram. I have successfully installed Ubuntu on a pentium 3 with only 256mb of ram by using the Alternate Install CD, but peformance was poor. Basically what I'm saying is I don't want you to jump through hoops to solve the bios issue, only to find out your system specs are too low. :)

There are many other options for old computers such as DSL or Puppy Linux. Without knowing the system specs, it is hard to make a specific recommendation.

---

### Post by overdrank on 2008-10-30
> **dachilleus said:**
> I rescued and old Dell Dimension from the University graveyard a while back thinking that it would make a great linux starter box.  When I finally got around to cleaning it up and running the install of Ubuntu 8.04 last weekend we got a blackscreen and message saying that the BIOS was old and the Year Out of Date message.

Do I need to flash/update the BIOS just to install Ubuntu?  Or is there a different Ubuntu option for download and install on older PCs?

Thanks for any assistance

Just a thought is the time set correct in bios? If the system has be inactive for a long time and the cmos battery is dead then the clock in bios may be wrong.

---

### Post by dachilleus on 2008-10-30
OK, Snowpine - I understand.  The PC is a P3 and probably no more than 512MB of RAM.  Its an old University bare bones Dell workstation.  I don't expect it to be an amazing performer.  We wanted to use this box as a testing ground for different install options etc before changing existing machines which are online.

---

### Post by dachilleus on 2008-10-30
> **overdrank said:**
> Just a thought is the time set correct in bios? If the system has be inactive for a long time and the cmos battery is dead then the clock in bios may be wrong.

Thats an interesting point I hadn't yet considered.  Will look into that once home.

So am I correct in understanding that this install should be possible - taking into account performance lags?

---

### Post by snowpine on 2008-10-30
> **dachilleus said:**
> OK, Snowpine - I understand.  The PC is a P3 and probably no more than 512MB of RAM.  Its an old University bare bones Dell workstation.  I don't expect it to be an amazing performer.  We wanted to use this box as a testing ground for different install options etc before changing existing machines which are online.

If that is the case, Ubuntu is a possibility, and Xubuntu should work pretty well. It's basically Ubuntu with a different desktop environment (Xfce instead of Gnome). No need to use something really bare-bones like DSL if you have a 512mb pentium 3.

There are various kernal boot options such as "acpi=off" that may help you out, but unfortunately I am not an expert. :(

---

### Post by the.phantom on 2008-10-30
i am not a expert
but on older systems the big key is memory !
i run ubuntu 8.04 on a 400 mhz pent and have 384 of memory

ya it is slow, but almost normal for surfing and e-mail

but a nice little test system for me and cost was free

takes a long time to do the install and you think it is hung.. just walk away for a hour ;-D

---

### Post by GuitarRocker2562 on 2008-10-30
Trust me, Ubuntu will perform fine. I have run Ubuntu on 500MHz Pentium computers with only 128MB of RAM, that is only a little slow. Your computer will run fine, just disable desktop effects. As far as the other problem, it sounds as if Ubuntu isn't even getting a chance to boot, the machine gives an error first. I would change the battery, reset the clock and possibly update the bios.

---

### Post by dachilleus on 2008-10-30
> **the.phantom said:**
> takes a long time to do the install and you think it is hung.. just walk away for a hour ;-D

OK - I will check the system battery and try installing again giving it more time.

Thanks guys.  I'll post an update after getting home and turning the box on again.

---

### Post by louieb on 2008-10-30
> **dachilleus said:**
> Does this mean there is no way to install Ubuntu onto an older PC that yields this error? 
Are you geting the BIOS date before 2000 message?

Just ignore it. 
May want to flash the BIOS for other reasons. I have a P2-400, 384 MB memory  whitebox bought in 1997 or so. Had to  flash the BIOS in order to use larger than a 30GB drive.  And to get it to boot to a CD without using Smart Boot Manager .The latest BIOS for that board was dated 1999 so I still get the message.

Ubuntu runs about as fast as XP on that PC.

---

### Post by egalvan on 2008-10-30
> **dachilleus said:**
> OK, Snowpine - I understand.  The PC is a P3 and probably no more than 512MB of RAM.  Its an old University bare bones Dell workstation.  I don't expect it to be an amazing performer.  We wanted to use this box as a testing ground for different install options etc before changing existing machines which are online.

OK, the 'year out of date' stuff is in reference to the SYSTEM CLOCK, not the date the bios was written.
 This is a 'sanity check'... if the year is too far back, it's probably wrong, and it may cause problems...

Saying you have a 'Pentium 3' or 'Pentium 4'  still doesn't give a lot of info.
I have a P3 running at 500Mhz with a 128KB cache, 
and I have another P3 running at 2.0Ghz with 2MB of cache.

Can they be honestly compared? And let's not forget that a Celeron may be lurking in there.

Apples to oranges to pears. One reason these kind of threads go on the way they do. "I ran fine with a P3"..."nuts, a P3 can't cut it"

I totally agree that RAM is the BIG factor. 
I would much rather 1000Mhz with 2MB cache, and 2GB RAM,
than 2.Ghz with 128KB cache and 128MB RAM.

the first is SLOWER, but will RESPOND faster, thus FEEL QUICKER.

A fast hard drive can also work wonders, Nothing like kicking up the RPM's from 4200 to 7200. Makes a BIG difference in the responsiveness, thus the FEEL.
 To say nothing of being blown away by 15,000!

I find that in these classes, AMP AthlonXP outruns Intel.

I would rate CPU speed as fourth.

Back to the machine in question...

Giving us the EXACT MODEL NUMBER AND SERIAL NUMBER can let us find the EXACT specs on the Dell Web Site.
 Of course, the machine may have been up-graded or down-graded, which is why it's good to ALSO get the exact specs as shown on the BIOS screen.

And another thing, if the machine is presently able to boot to a DOS screen, DON'T ERASE THAT  until you have up-dated the BIOS (if needed).
some of the older BIOS up-date routines only ran on DOS-type OS's.

So to re-cap...this is what I would do in a similiar situation...

Take the machine apart.
Dust EVERY-thing with compressed air.
Re-assemble the machine.

( Contacts can become corroded with time, and un-plugging and plugging back in can clean the affected parts. )

If there are boards you don't need (modem, for instance) leave it out.

Install new battery.

If needed, update the BIOS to the latest version.

Set the BIOS options to what you need. time, date, boot order, etc.

Wipe drive with DBAN (Darik's Boot and Nuke)

Boot Linux and enjoy!


ErnestG

( And if you find that it is not feasible to run Ubuntu, the give Puppy a try. The latest is 4.1, and it is a joy to use. Especially if you have more than 256M RAM )

---

