---
title: "Start up problem"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by Delricko on 2013-07-06
I'm having problems starting my netbook.  It's an Acer Aspire One and I run Lubuntu 12.10 and Windows 7 on it. Nowadays whenever I wish to start it I have to unplug it from the mains and then remove the battery for a few seconds before pressing the start button.  Whenever I close down I have to switch off the mains first otherwise when I press the start button nothing happens. This began as an intermittent fault but now is happening repeatedly.  Any help you may offer will be appreciated.

---

### Post by dino99 on 2013-07-06
is Lubuntu a real install ? or inside win7 via wubi ?

---

### Post by Double.J on 2013-07-06
Hi there!

sounds firmware/hardware to be honest. Just to rule out your installs - does it behave in the same way when shutting down in windows and lubuntu? and does it behave in the same way if you ask it to restart from windows an lubuntu? upon boot enter the BIOS and restart the computer from there - does the samething happen?

Some aspire ones are now a few years old, does it behave normally if the battery is completely removed? when batteries come to the end of their life it is common to experience powing on issues with them connected, it would also 'fit' with the progressive nature of the fault. From what you have described, I would say it's most likely.

When the system does eventually boot, is system time/date affected? this would be an indicator of the motherboard battery failing?

Additionally check (from the windows partition) if there are any bios updates for your netbook. This would be a last resort kind of thing after you've ruled out everything else; reflashing your firmware (BIOS) isn't risk free, especially on a board that is behaving unusually, and a failed bios patch although rare will leave the machine inoperable.

---

### Post by Delricko on 2013-07-06
Thanks for your replies.

Dino99,
The machine is dual boot.  W7 and Lubuntu operate separately.

gnu/mirow,
Hi there too,
It behaves in the same way when shutting down in windows and lubuntu.
It behaves in the same way if I restart from windows or lubuntu.

When it misbehaves, which is now all of the time, it doesn't get as far as BIOS.  I press the "on" button and nothing happens unless I remove the battery for several seconds (whilst disconnected from the mains) and then retry.

Re, "does it behave normally if the battery is completely removed?":
I just tried this and it seemed to make the situation worse.  
On mains only it would not start.
I disconnected the mains and went to battery only.  It required several battery insertions and removals before it would restart.  During one restart it went beyond BIOS but never opened Lubuntu.  It just stuck at the dark screen stage.

When the system does eventually boot the system time/date is OK, not affected.

I have a couple of Puppy distributions which run from CD and flashdrives somewhere.  I'll try one of those to see if it behaves the same and come back to you with the result.

My big fear is of course that the machine will shut down and then never restart.  I always back up data.  I'm being especially diligent in this area right now in anticipation of major problems.

---

### Post by Delricko on 2013-07-07
Since posting my last message I have tried Puppy operating from a USB  flashdrive.  It seemed to open and close on battery a little more  reliably than W7 and Lubuntu, allthough maybe that was just an impression rather than a  fact.  It still failed on several occasions.  It would not start up at  all with the mains adaptor plugged in, and required the adaptor out,  battery out, then reinsert battery procedure.

Inserting the  adaptor after start up seems to mess up the next start up, even if it's  removed before close down.  If I don't connect the adaptor during a  session there seems to be a 50-50 chance (but not a 100% one) that the  next session will start normally.

The battery still has a lot of  life in it and will run the machine for several hours (3+) when fully  charged, which it is most of the time.

This problem is definitely becoming more acute.

A Question (or two):
I  don't want to wait for this problem to completely disable the machine.   If I were to reload Lubuntu as the only operating system (ie throw  away, overwrite W7) would this desperate action be likely to offer any  improvement?  Would it help if I used a hard drive overwrite with zeros  and ones before doing so?

---

### Post by Rex Bouwense on 2013-07-07
If you are having the same problem with both OS and it appears once again when running Puppy from a CD, you may have a hardware problem.  I would back-up anything that you cannot afford to lose immediately.  Then you can experiment.  No one can really tell you with 100% certainty what will happen if you were to install Lubuntu over the entire disk.  However, I can say that I did install Lubuntu 12.10 on an Acer netbook and it works like a charm.  It had XP installed and was slow and would freeze.  Now its runs great.  XP is an old OS and is due to retire and I know nothing about Windows Seven.  Does Lubuntu run (and shutdown) without problems when you run it from a flash drive or CD or do you have the same result as you did when using Puppy?  If it does OK, then perhaps you could try installing it on the hard drive.  There is no need to over write anything on the hard drive.  The installation process will format the hard drive for you if you use the entire drive for installation.

---

### Post by Mark Phelps on 2013-07-07
Since the problem affects both OSs, removing either and replacing it with the other is not going to solve the problem, nor is it going to make anything better.

Generally speaking, when you can boot a PC and see the boot messages, but it then fails to get into an OS or all the way to a desktop, that is a sign of either corrupted filesystems or a failing hard drive.  The latter tends to be the case when the boot-to-desktop time starts to get really long.  The hard drive is failing on reading sectors and tried over and over -- taking a LOT longer to read all the startup stuff.

The problem with testing this from a LiveCD or Live USB is that both of those are going to be really slow.  However, if either runs without problems, that further implies that the hard drive is dying.

As to using Win7, it improved a LOT over Vista and is able to run OK on PCs that could not run Vista.  While you might be able to use it, there is no reason to believe that it will run any faster than the XP currently on the machine.

---

### Post by Delricko on 2013-07-10
Thanks everyone for your informed and helpful guidance.
 

 As a result of your advice I've been far better focussed with my investigations into this problem.  I have now established beyond all doubt that the problem presents with all operating systems regardless of whether driven from a CD, flash drive, or the hard drive.  I realise that this must absolve  Lubuntu from any responsibility.
 

 The defining factor is whether or not I plug the mains adaptor in.  If I do then the next start up will fail.  The &#8220;on&#8221; button does nothing until after I remove the mains adaptor and battery for several seconds, and then replace only the battery.  The netbook will only restart on battery power, never on mains.

 

 When the machine fails I do not see the boot messages.  Nothing happens at all until after removal of all power sources then reinsertion of the battery.

 

 I guess that this is a hardware problem.

 

 Thanks again everyone for your help.

---

