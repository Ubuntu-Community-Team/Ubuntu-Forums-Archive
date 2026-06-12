---
title: "Problems with Booting"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by Incarnation on 2011-12-26
Hello, I'm having some troubles booting into my computer properly. I'm using Ubuntu 11.10.

At the POST screen my PC is halts for a short period when it gets to "detecting IDE drives..."
Sometimes it halts for long periods and I have to restart my computer (using ctrl+alt+del or by powering my PC off and on again)

Then, when GRUB loads the first time I manage to get past the POST screen, Ubuntu gets stuck in the loading process and all I see is a blinking cursor for a long period of time.

At this point using ctrl+alt+del to restart doesn't work so I power off my computer and start it all over again trying to finally boot into Ubuntu.

I finally manage to boot into Ubuntu but the nice, high resolution splash screen (the one that says Ubuntu with the (four?) white dots underneath it) isn't displayed, instead I see an uglier lower resolution image, and finally I manage to get to the Ubuntu login screen.

--------------

This entire ordeal has happened to me twice so far, and I have no idea what's wrong with my PC. I'd appreciate any help I can get.
Oh, and, I'm more or less a complete newbie when it comes to Linux!

---

### Post by westie457 on 2011-12-26
> At the POST screen my PC is halts for a short period when it gets to "detecting IDE drives..."
Sometimes it halts for long periods and I have to restart my computer (using ctrl+alt+del or by powering my PC off and on again)


Hi at first glance it looks like the Hard drives are failing however that might not be the case.

Unplug the connections to each drive including the power and reconnect. Hopefully it is just a cable working loose or a build up of muck on the connectors.

As for the Graphics card try the above if it is not built into the motherboard.


If after you have tried these suggestions you still have the problems you will probably need new hard drives and graphics card.

---

### Post by BC59 on 2011-12-26
Check the HDD cable or change it, check the jumper or unplug the jumper.

---

### Post by Incarnation on 2011-12-28
Hello!

So I tried checking the cables and everything seems to be connected okay.
Lately my PC hasn't been giving me the boot-up problem but that's the  nature of the problem: sometimes it's there, sometimes it's not.

For some reason, now, the nice hi-res Ubuntu splash screen doesn't show up anymore. :sad:
I'm not sure why that is (perhaps because I powered off and restarted my  computer when it was (I'm pretty sure) stuck after it loaded GRUB and  began running Ubuntu).

I've already had one hard drive fail on me  before (wasn't being detected at the POST screen) ... I'm in a real  mess if this happens to the rest of my drives. :frown:

---

### Post by QIII on 2011-12-28
Don't just jump to the conclusion that it must be an hdd.  There are many other things it could be.  But eliminating simple hardware faults is a good place to start.  Unplug and open the case.  Touch one finger to the metal chasis and keep it there while you check.  Are the disk cables snug at both the disk and motherboard end?  Are all of the memory modules seated properly.  Are all the cables attached to the motherboard firmly?  Is the latch holding your CPU down in its proper position?  Is the heat sink fan plugged in?  Is your graphics card seated properly?  Check the motherboard carefully.  Is there any obvious damage?

Take your hands out of the case, plug it in and turn it on.  Enter your BIOS set up.  While you are doing that, make sure your heatsink fan is running.  In your BIOS setup, go to "pc health status" or whatever similar area your BIOS offers.  Check the CPU temperature and any other temperature readings.  Compare those with your machine's documentation.  Check the voltages.  Compare those to your machine's documentation.  Get out of the BIOS settings and allow your machine to attempt to boot.  Successful or not, shut down.

Restart and listen very carefully to the disks.  Your hard drives should spin up with a faint whine.  At some point they will begin to tick as the disk starts seeking.  That's OK if it's not loud clanking and scraping.  The optical drive will be a bit noisier.  It will whirr noticably.  Again, no foul as long as it doesn't sound like it's trying to fall apart.

If you can get to it, select memtest from the GRUB menu.  Let it run for 12 hours.  Sorry, it takes time to do it right.

Only then, after all of that, do we start to consider hard drive failure or system file corruption.

---

