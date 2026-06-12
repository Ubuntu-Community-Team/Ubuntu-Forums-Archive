---
title: "Unable to log on using password"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by condor 088 on 2012-04-06
This morning I had no problem logging on to ubuntu 11.10  This evening, I enter my password and nothing happens. I attempt to log on as a guest, and nothing happens; the same for logging on as other. What can I do to gain access to the program?  Thank you,  Bob Richards

---

### Post by donkyhotay on 2012-04-06
Can you log in using the terminal? Try pressing ctrl-alt-F2 which will bring you to the classic terminal and try signing in there. If you can't post the error message.

---

### Post by condor 088 on 2012-04-06
Thank you. I just reinstalled Ubuntu 11.10 on the drive.  Problem solved. I am using another drive with Win xp to access the net, due to ubuntu not recognizing my usb modem. Modem is Trendnet TFM-561U, which works well on win xp. ubuntu also does not recognize my Canon Pixma iP1800 printer, nor my scanner, Visioneer 9020. It however, does recognize my floppy drive but not the media in the floppy. Is ubuntu 11.10 a fairly stable unit, or would it be best to install a slightly older and more stable unit? I shall post this on a new thread in the morning. Thank you, Bob Richards

---

### Post by Dreamer Fithp Apprentice on 2012-04-06
You might also want to make sure that the state of the caplock and/or numlock keys are what you think they are and aren't changing "passWord8" to "PASSwORD".  Also try typing the pass in one character at a time and make sure you are getting exactly one asterisk or black dot or whatever for each character typed. Sometimes the keyboard itself can get flaky and you think you are typing "passWord8" but you are really entering "passssssWrd8".  You might try reseating the connector where the keyboard connects to motherboard or at the other end if you have a two headed cable connecting the two. You could check the keyboard by plugging it into another computer.

In the worst case if it turns out the system is completely borked, boot from another partition or a live disk and copy any data off of it you don't want to lose to another partition or disk and then reinstall. If you do this don't forget to look on the desktop (/home/usename/desktop) as well as home (/home/username/) and in any download directories you might have. Also any place you might have put any scripts such as /usr/bin.

p.s. added by edit:  Lol, I got sidetracked for  a few minutes while typing an answer and in the meantime you solved it.

---

### Post by d4m1r on 2012-04-07
To be honest, you seem to be using really ancient technologies (floppy?!) so I'd recommend sticking to an older release as well....Maybe 10.10 LTS?

---

### Post by Dreamer Fithp Apprentice on 2012-04-09
Oneiric has no problem with floppies, which are not so "ancient" as to be without uses. Nor would I expect it to be written with the intent to ignore any of your hardware simply because it wan't purchased yesterday. That sort of contempt for backwards compatibility is more a Windows trait and one of the main reasons to leave MS behind. However it is true that Ubuntu seems headed in the MS direction of "pop it up and dumb it down" so it is possible that d4m1r could be correct. Also I agree that Lucid is WAY more trouble free that Oneiric, so is Maverick for that matter, but I don't think hardware age has anything to do with it.

---

