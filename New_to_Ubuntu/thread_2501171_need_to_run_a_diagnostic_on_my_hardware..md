---
title: "need to run a diagnostic on my hardware."
date: 2024-09-25
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2024-09-25
i am currently reinstalling 20.04 into my other system, because of problems with my motherboard.  1 of the customer service reps isn't very good at his job.  is there software i can purchase or find open source that will give me at least a semi-reliable diagnostic of my hardware.  i need to know if i damaged any of my hardware with this last episode,   the operating system is currently installing and after it finishes i'd like to run a diagnostic, even if i have to google every line of the read out.  i just need to know if i have to replace any hardware.

---

### Post by him610 on 2024-09-25
Suggest you perform actions of this link then post results so others may review it and advise.
[https://ubuntuforums.org/showthread.php?t=2475932]("https://ubuntuforums.org/showthread.php?t=2475932")

---

### Post by cryofreeze666 on 2024-09-25
i would love to, but now i'm back to the original problem of not being able to access my o.s.  thought i fixed the original problem by wiping the hard drives, resetting the cmos, flashing the original bios, and reinstalling the o.s. but no dice, i'm back to this screen.

/dev/nvme0n1p2: recovering journal
/dev/nvme0n1p2: clean, 201321/15237120 files, 3920195/60918272 blocks

evidently this is from a hard shutdown, according to last time i posted this.

my question is this, if that is ready to be restarted, why aren't the numbers on both sides of the / the same?  i can't hit esc, type, no f keys work, nothing.  all i can do is get to the bios.  am i going to have to run this computer to that computer in order to run that link?

what i would really love to know is what is this and how do i deal with it?  is it automated, will it run till both numbers on both sides of the / are =?

are you asking for the inxi -bz info to that computer?

i can't install 7 to install 10, 7 freezes at the logo screen, 10 wont install unless there is an  operating stystem to install from, and i doubt even if i could install windows i'd have better results.

---

### Post by bobunderwood99 on 2024-09-25
> **cryofreeze666 said:**
> 

/dev/nvme0n1p2: clean, 201321/15237120 files, 3920195/60918272 blocks


That's normal (the result of a filesystem check).

Can you boot the system from a USB drive?

---

### Post by TheFu on 2024-09-26
> **cryofreeze666 said:**
> i can't install 7 to install 10, 7 freezes at the logo screen, 10 wont install unless there is an  operating stystem to install from, and i doubt even if i could install windows i'd have better results.

Sometimes hardware dies.  Maybe your SSD is dying?  The way to determine that is by booting off a flash drive with an Ubuntu installation ISO on it, install smartutils (or something like that), then run a few SMART tests with **smartctl**.  Be certain that SMART is enabled in your BIOS.  There are a number of posts in these forums with more details about SMART.   SMART should only be used on SATA/SCSI storage.  

If your storage is NVMe, there's a different program, **nvme**.  It probably needs to be installed too.

You've lost me throwing out random numbers to install.  42 freezes?  I don't understand.  7 programs cause the computer to freeze or is it 10 programs?  Are you certain it isn't 6 or 15 programs?   What are those numbers supposed to mean?   I'm probably just being dense.

---

### Post by cryofreeze666 on 2024-09-28
> **TheFu said:**
> Sometimes hardware dies.  Maybe your SSD is dying?  The way to determine that is by booting off a flash drive with an Ubuntu installation ISO on it, install smartutils (or something like that), then run a few SMART tests with **smartctl**.  Be certain that SMART is enabled in your BIOS.  There are a number of posts in these forums with more details about SMART.   SMART should only be used on SATA/SCSI storage.  

If your storage is NVMe, there's a different program, **nvme**.  It probably needs to be installed too.

You've lost me throwing out random numbers to install.  42 freezes?  I don't understand.  7 programs cause the computer to freeze or is it 10 programs?  Are you certain it isn't 6 or 15 programs?   What are those numbers supposed to mean?   I'm probably just being dense.


1) i understand, sometimes hardware dies, which is why i was asking about software diagnostics, one thing i am not short on is computers, so if i can connect one to another via a usb to search the other computers hardware i would love that.

2) took my secondary ssd and moved it to primary slot, am installing o.s as i'm typing.

3)7=win7, 10=win10, guess i took for granted you would know what i was saying.

---

### Post by cryofreeze666 on 2024-09-28
> **bobunderwood99 said:**
> That's normal (the result of a filesystem check).

Can you boot the system from a USB drive?

haven't tryed yet, cause i didn't think to check my ssd drive and see if it died (not even a year old).  am currently moving secondary ssd to primary slot and installing an o.s., if that doesn't work i'll try the usb, though i can run ubuntu from my sata cd/ dvd rom.

---

### Post by TheFu on 2024-09-28
> **cryofreeze666 said:**
> 1) i understand, sometimes hardware dies, which is why i was asking about software diagnostics, one thing i am not short on is computers, so if i can connect one to another via a usb to search the other computers hardware i would love that.

You can check storage for issues using **smartctl** for HDDs and SATA SSDs and **nvme** for NVMe SSDs. Thought I'd mentioned that. Sorry if I didn't.

> **cryofreeze666 said:**
> 
2) took my secondary ssd and moved it to primary slot, am installing o.s as i'm typing.

Ok. That seems harder to me, but it is a 1-way to check, unless the disk controller or NVMe controller are also bad.

> **cryofreeze666 said:**
> 
3)7=win7, 10=win10, guess i took for granted you would know what i was saying.
I seldom think of MSFT stuff.  It wasn't obvious to me. Sorry.  I've been on a mission never to use anything that runs on MS-Windows for nearly 15 yrs.  I'm down to 2 programs and one of those is used less than 1 week a year. Just never occurred to me, since this is a Linux forum.

I see the post is marked as SOLVED.  Please tell us why, so we can better help others and people who come here seeking answers can also understand what you found in their search for a solution too.

---

### Post by cryofreeze666 on 2024-09-29
> **TheFu said:**
> You can check storage for issues using **smartctl** for HDDs and SATA SSDs and **nvme** for NVMe SSDs. Thought I'd mentioned that. Sorry if I didn't.


Ok. That seems harder to me, but it is a 1-way to check, unless the disk controller or NVMe controller are also bad.


I seldom think of MSFT stuff.  It wasn't obvious to me. Sorry.  I've been on a mission never to use anything that runs on MS-Windows for nearly 15 yrs.  I'm down to 2 programs and one of those is used less than 1 week a year. Just never occurred to me, since this is a Linux forum.

I see the post is marked as SOLVED.  Please tell us why, so we can better help others and people who come here seeking answers can also understand what you found in their search for a solution too.

i still think of microsoft, because i've only recently severed my ties with their programs (last 2 or 3 months), thus the reason most of my posts are in the newbie section.  yes, i say i've thrown windows in the trash, but i guess it's more accurate to say the junk drawer of my desk (pretty much the same to alot of people) for the liberties they believe they are entitled to take.  so like you i intend to steer clear and make due, till there is something better.  right now, of the linux o.s.'s i've tried ubuntu 20.04 seems to be the most compatible with what i need as a balance between work and play of all the different makes and versions of the kernal.  but still having those two o.s.'s and finding out they didn't work either, did start me leaning in the direction of hardware failure.  my communication skills just suck, so i have difficulty putting thought into words.

1) THE REASON IT IS SOLVED, is because the switching of the hard drives.  i was able to install 20.04 on the secondary hard drive after i moved it to the primary slot and used it.

2) you're right if there had been something wrong with the slot, the second ssd drive may not have worked.  then i could have moved it back to secondary drive slot, and changed the boot order in the bios thereby killing 2 birds with one stone.  if it still didn't work, then the diagnostic program would have been my next step.  easy, in my opinion, doesn't always give results that remove the most possible causes.  also, when i built that case for it, i made it  20"h x 24"d x 30" l.  i always hate working in pre-made cases, normal size people have trouble in those case designs all the time.  i was able to pull the graphics card, and unscrew the covers for the m2 drives, pull the bad one, move the good one, and reinstall the graphics card in less than 10 minutes.  installing o.s. another 15 minutes or so.  the 15 minutes was unavoidable, because no matter what i needed the o.s.

everyone wants small and powerful. the reason i went big and powerful, (2 reasons) is this.  1) look at your hand, your thumb is the widest usually.  well people like to tease me because my index finger is wider than most peoples thumbs.  my pinky is really close to the size of others index fingers.  big also gives you the same outcome that i have, ease of physical maintenance.  i spent 10 minutes because, even my big a** could fit both hands inside my case. and 2) i have 7, 120mm fans on the top of my open air case for cooling gpu's.  

due to my horrible communication skills, i have to ask this.  do i need to chop this down, was i too wordy making sure i was understood?

---

