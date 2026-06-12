---
title: "Computer is running fast"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Hitchhiker42 on 2008-11-15
Okay, so I am fully aware that this is the weirdest problem ever, and that most people have no problems with their computers being fast, but listen to my tale of woe and see if you don't agree that it's a problem in this case.

The Rig:
AMD64 3200+, 2 GB RAM, 2 Optical Drives connected the mobo via IDE, and 2 HDs connected via PCI to IDE adapter card. First HD is 30 GB and has Windows XP. Second HD is 500 GB with 4 partitions, Vista/Hardy/Swap/Storage.

The Setup:
So while testing out some new USB speakers, I believe I jostled the IDE adapter card whilst unplugging my normal set of speakers. I discovered this when Hardy crashed (needless to say, I was fairly shocked). So I turned off the computer, determined the problem and wiggled the adapter card til it was back in the sweet spot again, and booted to XP, where I ran the Magical Jellybean Keyfinder, uninstalled Office 07 and futzed around a bit on the net.

The Problem: 
When I booted back to Hardy, everything was running faster than it should. the usual orange status bar that shows while booting was going back and forth faster than usual, the Wanda the Fish applet was swimming at double speed, and the clock was gaining about 1 minute every 20 seconds, causing the screen saver to come up after about 1.5 minutes, and also go through its animation way faster than usual. Furthermore, I can't connect to the internet, even though it was working in XP, and it will tell me that there was an error in authentication whenever I try to get in and fiddle with the network settings. I tried rebooting with no luck, but at the moment, I have the computer turned off. If someone could tell me what the heck is going on, and how to fix it, I'd really appreciate it.

---

### Post by Mardoct909 on 2008-11-15
Umm... I'm not sure if this is a feasible explanation, but here goes:

Your BIOS clock is too fast. Why? Maybe it's broken, maybe the PSU is giving it too much power. 

I do know that all the computer's sense of time is derived from your BIOS clock, and things set to happen on schedule - like the addition of a minute to the clock or the screensaver being evoked - is measured against the BIOS clock.

How could you fix this? No idea.

---

### Post by tvtech on 2008-11-15
okay, heres the deal, not to disparage mrdoct909.  bios computers are typically crystal oscillators and usually quartz at that for specific reasons. it keeps incredibly accurate time "which cannot be changed once the oscillator has been manufactured. They are powered typically by a battery on the motherboard, in netbooks and certain newer computers they are powered by a long charge capacitor, they have longer life than batteries and typically hold a slow drain charge much much longer and theoretically will never build a memory.... if windows isn't having a problem I highly doubt it's your systems clock, but just in case pop your battery off your motherboard and see what happens, on an XP boot. 

anyways.  linux has it's own internal clock and you can set it, change it and tweek it it sounds like your time reference has been changed or that it is not referencing your computers system time.  {this would make sense since you popped a hot board off a pci bus. your lucky your computer didn't **** the bed right then and there. I've toasted some pretty expensive hardware this way}  I think the command to check this is hwclock  

check out username@localhost:~$info hwclock for all the listed commands and switches for this package.  also check out the man page for it and you should be able to fix from there.  man hwclock. 

this is going to be troublesome but it should be straight forward.

---

### Post by Mardoct909 on 2008-11-15
You learn something new every day.

---

### Post by tvtech on 2008-11-15
> **Mardoct909 said:**
> You learn something new every day.

I try to never go to bed before I learn my new thing for the day.  I once didn't sleep for two weeks.

---

### Post by Crafty Kisses on 2008-11-15
So I'm guessing your on the 64-bit version of Ubuntu, run the following command:
```
sudo gedit /boot/grub/menu.lst
```
You should see a text-editor pop-up, you need to look for this line in the menu list:
```
kopt=root=/dev/hda5 ro # kopt=root=/dev/hda5 ro console=tty0
```
Remember the information in your GRUB menu list will be different than above, but anyway you need to add the following to the "kopt" line: 
```
no_timer_check
```
So once you're done, it should look like something similar to this:
```
kopt=root=/dev/hda5 ro # kopt=root=/dev/hda5 ro console=tty0 no_timer_check
```
Save the GRUB menu list file, and reboot and see if that sets things back to normal.

---

### Post by Hitchhiker42 on 2008-11-15
Actually, I'm running 32 bit Ubuntu. Does that make a difference to your instructions? (What exactly does adding that line do, by the way?)

I'm about to give the hwclock command a shot and will report back (probably later as I only have time for a little bit of troubleshooting before work).

---

### Post by Hitchhiker42 on 2008-11-15
SOLVED!

I mentioned the problem I was having to my dad, and he suggested I unplug the computer for about a minute, then boot it again. This did the trick (I had just turned off the computer, but hadn't unplugged it.) This seemed kinda odd that it would be a hardware issue when Linux was presenting problems and XP wasn't, but I'm not about to question good fortune.

Thanks for all your help!

---

### Post by InfectedWithDrew on 2008-11-15
> **tvtech said:**
> I try to never go to bed before I learn my new thing for the day.  I once didn't sleep for two weeks.

Off-topic, but that's impossible.  The human body drops dead if it does not sleep for nine days.

And I'd also like to say that I think this is hilarious.

What's wrong?
MY COMPUTER IS TOO FAST!

---

