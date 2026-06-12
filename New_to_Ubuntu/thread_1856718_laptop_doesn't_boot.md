---
title: "laptop doesn't boot"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by enuckon on 2011-10-08
Recently a Sony laptop started shutting off the power during boot time at the ubuntu logo screen.  It doesn't go any further.  Pushing the power button right after this is even worse: the laptop doesn't even show POST messages losing power after two-three seconds.  After pressing the power button for 30 seconds and restarting I sometimes get as far as the ubuntu logo screen and laptop shuts itself off again.  8.10 is installed and has been stable for about two years.  Brand new AC adapter brought no cure.  I would appreciate any sugesstion or references on how to get it back on track. Thanks!

---

### Post by Lisiano on 2011-10-08
Might I suggest installing Ubuntu 11.04 or 11.10 which is released in a few days (The 13th of October) or a few weeks, there is some confusion on the date.
[Ubuntu 8.10 reached EOL]("https://wiki.ubuntu.com/Releases") (End of Life) so you will not get any updates for it. Also will be a good test to see if it's hardware related (By booting off the LiveCD) or software related.

---

### Post by enuckon on 2011-10-08
> **Lisiano said:**
> Might I suggest installing Ubuntu 11.04 or 11.10 which is released in a few days (The 13th of October) or a few weeks, there is some confusion on the date... Ubuntu 8.10 reached EOL 

Thanks.  Would I be able to keep all the 8.10 files?  From my experience a clean install is more reliable than an upgrade.

---

### Post by Redblade20XX on 2011-10-08
Can you put another os on the laptop to see if this is really a software problem or a hardware fault (maybe dieing hdd)? :)

- Red

---

### Post by enuckon on 2011-10-08
> **Redblade20XX said:**
> Can you put another os on the laptop to see if this is really a software problem or a hardware fault (maybe dieing hdd)? :)

- Red

Thanks.  I have tried to boot from the 8.10 installation CD (guess it also doubles as a LiveCD) and nothing was different except for some extra 10-15 sec crunching from the CD drive.  Then the laptop goes quiet without any progress or messages on screen.

---

### Post by Redblade20XX on 2011-10-08
So you didn't get into a live session? Can you post the computer's information (specs)?

- Red

---

### Post by WasMeHere on 2011-10-08
Seems to me that it is a hardware fault. The computer should boot from your live disk without a hdd. Can you run memtest from the grub menu?

---

### Post by enuckon on 2011-10-08
The LiveCD works on a windows laptop, but doesn't boot my Sony ubuntu laptop.  Nothing happens except for LED blinking.  With or without LiveCD, I could not even get any POST or other messages -- the screen stays dark.  I could not get to the logo after my last ten or so restarts.  The model is Sony Vaio PCG-8Q5L.  Hopefully, HDD is not the cause.  No POST output means that the boot process doesn't even get to the point when it needs HDD or CD drive.

---

### Post by WasMeHere on 2011-10-08
> **enuckon said:**
> The LiveCD works on a windows laptop, but doesn't boot my Sony ubuntu laptop.  Nothing happens except for LED blinking.  With or without LiveCD, I could not even get any POST or other messages -- the screen stays dark.  I could not get to the logo after my last ten or so restarts.  The model is Sony Vaio PCG-8Q5L.  [COLOR="Red"]Hopefully, HDD is not the cause[/COLOR].  No POST output means that the boot process doesn't even get to the point when it needs HDD or CD drive.
I think HDD is *not* the cause, so you should be able to read your private files. I think there is something wrong with the power, motherboard, cpu or memory, but I am no hardware expert. Maybe some local guy can have a look at it.

---

### Post by Lisiano on 2011-10-10
A simple test. Once you get to a POST, just press the Pause button (Pause/Break) and wait, if the oddity happens, it's related to the PSU or Motherboard.
Also try removing the RAM, battery and if you can, the CMOS battery (Looks like a ordinary 5V watch battery, cause it is) and keep it that way for a minute or half. Everything beside the CMOS battery is accessible, I don't remember the default place for a CMOS battery on a laptop. This will reset your BIOS just in case you did something there or it found some sort of weird inconsistency like new RAM. Now assemble it in reverse. Do the test with the POST screen.
There is also a possibility that your screens ribbon cable tore/came off. To check that, if you can, attach a 2nd monitor to it and turn it on. Everything should be on that 2nd monitor instead. If it's not, find some Fn button that changes the screens. If you can't attach a 2nd monitor, either read up on how to disassemble laptops or find a local hardware guy as telepresence is not that advanced yet.

The HDD has no role during the POST except the enumeration, a PC can boot without a HDD. To pass the POST, it needs at a bare minimum: RAM, PSU, Motherboard, CPU. That is all. Everything else is optional but recently they also require GPUs.

> Thanks. Would I be able to keep all the 8.10 files? From my experience a clean install is more reliable than an upgrade.Yes, recent versions of Ubuntu detect your home folder and don't touch it, I'd recommend renaming your user folder since there might have been a lot of changes and using them on a newer version of Ubuntu might cause more problems than you wish to deal with. Also the old config files will give you a way to remember what you have set up (Read Compiz and the likes).
And as a side note, upgrading from 8.10 to 11.04/11.10 would take a LOOOOOOOOOOOOOOOONG time since you can't skip versions, unless you do LTS to LTS upgrades.

---

### Post by sarwiz on 2011-10-10
Also, while you have the batteries out of the unit, press and hold the power button for 30 seconds, this is a hard reset just in case there is a software issue causing something  to shut down. I do lean toward the fault being hardware related, though, maybe in the mobo.

---

### Post by enuckon on 2011-10-14
Thanks for all the suggestions.  Appreciate it very much.  I don't know what was and is wrong yet.  I let the laptop rest for a few days and then it started off the live CD, which it couldn't do before.  Memtest off the CD found no errors.  Now I know the HDD and memory are working.  I rebooted without live CD and it went up normally as before -- the system and everything else is up and running.  Not sure though if I will be able to restart it.  I have tried to revive it with many attempts before without much success and now it came back by itself.  It took a few days of rest.  Don't know though if that's important.  Could it be that dying CMOS battery needs some time to accumulate enough power?

---

### Post by Lisiano on 2011-10-14
(From desktop experience) It can also prevent you from even booting it till the POST. The battery is usually non-rechargable so by letting it rest, you just let the electrons spread out a bit more evenly. You should check the CMOS battery with a voltmeter or if its inaccessible, call a tech specialist as laptops are hard to open up (beside the panels on the bottom)

---

### Post by enuckon on 2011-10-14
I am not so sure that CMOS battery is responsible for this malfunction.  When the laptop didn't boot, it did it either by not going through even the POST and remaining dark, or sometimes, after going through the POST it died at the Ubuntu logo with the loading bar under the logo half through.  These two outcomes were consistent and the result was the same -- dark, quiet laptop with just two LEDs on.   If it manages to boot, then it is dead stable -- never fails.

---

### Post by enuckon on 2011-10-14
> **Lisiano said:**
> ... you just let the electrons spread out a bit more evenly.

Cool.  You made it sound like exact science.

---

### Post by Lisiano on 2011-10-15
Sorry. Worded it a bit wrong (Was on my phone)
[quote=enuckon]When the laptop didn't boot, it did it either by not going through even the POST and remaining dark, or sometimes, after going through the POST it died at the Ubuntu logo with the loading bar under the logo half through.[/quote]
That's exactly what happens when the CMOS is dead, it boot's up to the POST, does the POST CMOS test, fails and (On desktops) beeps the error code for it, sadly not all laptops/notebooks/netbooks "beep". Also currently this is a rare problem as now motherboard manufacturers made it so that if the CMOS test fails, the PC will boot with the factory defaults, after 2002 I believe. Most batteries are good up-to 4-5 years btw.
Well anyway, glad it works now. I'd still take it to a tech if I were you (Or diagnose myself if I could open up the laptop)

---

### Post by enuckon on 2011-10-17
Thanks!  Unfortunately, the laptop doesn't boot again with the same symptoms.  Where would one find the CMOS battery in a Sony Vaio A-190 (this is the correct model number)?  I have opened several compartments at the bottm and haven't found any.

---

### Post by enuckon on 2011-10-17
Looks like this link would do: [http://laptoprepair.ca/news/10707.html]("http://laptoprepair.ca/news/10707.html")
According to this site, in order to see the battery one has to remove the keyboard and palm rest.  Whether this is enough to replace it is hard to say.

---

