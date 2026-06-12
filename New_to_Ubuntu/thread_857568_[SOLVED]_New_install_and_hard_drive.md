---
title: "[SOLVED] New install and hard drive"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by gshockxc on 2008-07-12
Hi all.  I'm new to Ubuntu, and I'm putting it on an HP Pavillion ze4540 laptop.  I downloaded 8.04 last night, and burned the image this afternoon.  I'm doing a fresh install on a completely new HD.  I put the new HD in the laptop (didn't format or anything), put the CD in the drive.  The install menu came right up, I chose English, then "Install Ubuntu", and away it went.  The moving slider stayed on the screen for a while, then it stopped, and it eventually filled the slider.  The screen went blank, and then the cool bird background came up.  It's been up for at least the last 45 minutes, and I don't know what's going on.  Is it working, or is it stuck in some kind of loop?

I can hear the CD running and it seems to be doing something.  But I'm not getting any feedback about what's happening. 

Can anyone offer any suggestions?

TIA, 

-gshock

---

### Post by hyper_ch on 2008-07-12
when you see the cd boot screen, select to check the cd... maybe it was not burnt properly.

---

### Post by gshockxc on 2008-07-12
I burned it using ISO recorder.  Should I have used Infra recorder instead?

---

### Post by hyper_ch on 2008-07-12
no, run the cd check test

---

### Post by gshockxc on 2008-07-12
> **hyper_ch said:**
> no, run the cd check test

Results: Errors found in 2 files.  I think I know why.  I am using my work laptop which has a DVD RW, and I burned a CD RW.  Could that be it, or should I just wipe the CD-RW and try again?

---

### Post by WRDN on 2008-07-12
Try burning the image to the disk again at a slower speed, preferably 4x or slower.

---

### Post by gshockxc on 2008-07-12
Still having trouble.  I burned at a slower speed and checked the disk.  No errors found.  But it's still hanging up at the funky bird background.  Since this is a new HD do I need to do something different?

---

### Post by bushda on 2008-07-12
> **gshockxc said:**
> Still having trouble.  I burned at a slower speed and checked the disk.  No errors found.  But it's still hanging up at the funky bird background.  Since this is a new HD do I need to do something different?

I'd be surprised if it was. I'm almost positive that the problem is your CD. 

My desktop at home does not burn CD's properly for some reason, but my laptop burns them fine. Desktop is a DVD writer, laptop is a DVD ROM / CD writer. 

If you have another system, try burning it again using that system instead.

---

### Post by kansasnoob on 2008-07-12
I've had tons of problems just with CD readers! Smoke, dust bunnies, just plain dirt! I'd also never, ever use a RW disc for an OS .............. never anything but a brand new disc for an OS!

I've also found that sometimes, for no rational reason, that only a text/aka Alternate Install will work. In fact I just did one today where the DVD/CD drive (sata) would "spin out" every time it hit about 43%.

I even changed the BIOS boot sequence and tried an external CD ROM ......... no spin out but a dead stall!

Then I busted out my Alternate Install CD and had it going in no time!

I wonder if the installer doesn't get "stuck" on a hardware issue! Like today I was installing on a Intel BOXD201GLY2A mobo and after installation I did play hell getting the VESA driver to work.

I don't know for sure!

---

### Post by DGortze380 on 2008-07-12
> **kansasnoob said:**
> I've had tons of problems just with CD readers! Smoke, dust bunnies, just plain dirt! I'd also never, ever use a RW disc for an OS .............. never anything but a brand new disc for an OS!

I've also found that sometimes, for no rational reason, that only a text/aka Alternate Install will work. In fact I just did one today where the DVD/CD drive (sata) would "spin out" every time it hit about 43%.

I even changed the BIOS boot sequence and tried an external CD ROM ......... no spin out but a dead stall!

Then I busted out my Alternate Install CD and had it going in no time!

I wonder if the installer doesn't get "stuck" on a hardware issue! Like today I was installing on a Intel BOXD201GLY2A mobo and after installation I did play hell getting the VESA driver to work.

I don't know for sure!

x2

try the alternate cd

---

### Post by gshockxc on 2008-11-26
> **DGortze380 said:**
> x2

try the alternate cd

Months later, I stumble across my answer.  It helps if you use the HP PA-RISC alternate version.  

When all else fails, read the instructions.  Can't even count how many times I've been burned by that one.  You'd think that I would learn by now.

:(

---

