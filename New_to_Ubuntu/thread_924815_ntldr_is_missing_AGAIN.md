---
title: "ntldr is missing AGAIN"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by bkohler on 2008-09-19
okay, I feel like an idiot because there's a million threads on here about this problem, but I can't seem to find my answer in any of them.  

I dl'd the .iso file, burned it onto disc (properly, i checked and double checked) but can't seem to get it to boot.

I changed the boot order.

I just picked up this machine.  It's a dell optiplex gx270 with no OS

it's got a brand new HD and RAM and CD drive, everything works fine, but I can't get this boot disc to work.  

Only thing i can think of is that I'm NOT dual booting, there iscurrently no OS on this comp.  

anybody have a suggestion?  Maybe I should try downloading the file again from a different mirror?

---

### Post by bkohler on 2008-09-20
okay, i got past all of that with a really ridiculous mistake. 

I got Ubuntu to run from the disk, now I want to install it on my HD (it will be my only and primary OS) 

I went thru the install questions and setup, I don't know much about partitioning so i just selected to not partition and use the whole disk

I get an error 5 message after about 10 mins, saying there is a disk error either in my cd copy or a problem with my HDD 

it's only a 20gb HD, is this not sufficient?  Any suggestions on hardware setup?

---

### Post by egalvan on 2008-09-20
> **bkohler said:**
> okay, I feel like an idiot because there's a million threads on here about this problem, but I can't seem to find my answer in any of them.  

I dl'd the .iso file, burned it onto disc (properly,** i checked and double checked**) but can't seem to get it to boot.

I changed the boot order.

I just picked up this machine.  It's a dell optiplex gx270 with no OS

it's got a brand new HD and RAM and CD drive, **everything works fine**, but I can't get this boot disc to work.  

Only thing i can think of is that I'm NOT dual booting, there iscurrently no OS on this comp.  

anybody have a suggestion?  Maybe I should try downloading the file again from a different mirror?

I have a couple of gx270's, and had NO problem with Ubuntu. Runs GREAT!

You don't need any software installed to install software.
I've been doing that for over 30 years.
You just need something that the BIOS boot-strap can read and execute.

So first, have you tried the disk on another machine? Just to make SURE it's OK...

Second, boot your machine, and get into the BIOS.

What does the BIOS show as available drives?

You should have the hard drive and cd drive both showing.

And the cd drive should have blinked the access led during the boot...
if not, there is a problem.

I believe the gx270 series will boot from USB, so that will give  you a fall-back option.

And two final questions...

How did you "check the cd"?
How did you check that "everything works fine" ?

for example....
"checked md5sum integrity on the downloaded iso,
then ran the 'check cd for errors' menu choice"

"ran a stress-test (such as "Inquisitor" or Dell's hardware checker) on the hardware"

And one final thought,
please don't "feel like an idiot".
We all had to learn.
Torvalds had to learn.
Kernighan & Ritchie had to learn.
Raymond, Stallman, Hall, et.al. had to learn.
We can go from there....

---

### Post by bkohler on 2008-09-20
I guess the hour of the night was getting to me and i got frustrated. The install was getting hung up at about 30percent. I finally took the disk back out, wiped it off and tried one last time and the install went flawlessly. Wierd.  Once it was finalized i restarted to make sure it was all good and went right to bed before getting hung up on another problem at 2am.  Im sure ill have to search on here another ten times throughout the day as im tweaking and playing with my first linux experience.  Next up, adding my Linksys router/gateway to the machine! Wish me luck!

---

