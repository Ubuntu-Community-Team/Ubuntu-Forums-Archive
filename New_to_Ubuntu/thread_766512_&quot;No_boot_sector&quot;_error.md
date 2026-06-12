---
title: "&quot;No boot sector&quot; error"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Tripawd on 2008-04-25
Hi,

I installed Ubuntu, or at least I thought I did, a few days ago on a totally new, unformatted unpartitioned hard-drive via CD.  Not running Windows at all.  I sort of assumed that during the installation the formating and partitioning would take place or I would be prompted to do it.  Ubuntu eventually loaded up fine, never gave me any options though, but I believe it was simply running off the CD.  At this point I wasn't thinking about the hard-drive because I figured the installation had taken care of it since I never saw any options for dealing with it.  Yesterday I downloaded all the updates and set about upgrading to 8.04, which worked fine until I got a message that I didn't have enough space to install it, which was my first clue something was wrong.  There was also a restart icon, which I decided to try.  Upon restarting, I receive an error message similar to the following:

"No boot sector found on internal HDD.  Insert OS disk and press any key to continue."

With the Ubuntu disk in, pressing any key simply generates the same message to repeat.  After looking around and not really finding anything that seems to address this specifically, I thought I would see if someone here can help me out, rather than trying a bunch of stuff on my own and hoping it eventually works out.  This may take the prize for most newbie question ever, but thanks to anyone who can point me in the right direction.

---

### Post by reeseslover531 on 2008-04-25
wait did you ever install ubuntu?  You have to run the installer on the live cd to install it.   Ubuntu doesnt install automatically

---

### Post by Tripawd on 2008-04-25
Right, I didn't ever install it apparently, however now all I get is the same error over and over again when attempting to start the process over.

---

### Post by orangemoose on 2008-04-25
"Out of disk space" most likely means that you are really running Ubuntu off of the live CD.  That means you never installed it in the first place.
And there just isn't enough space on the CD to install anything new!

Check: Remove the CD, power down, and then turn the PC back on.
You should see your friend, "No boot sector".

Step 2:
Installing Ubuntu on a fresh hard drive is the simplest scenario.

Place the Live CD in the tray.
Turn the power off.
Turn the power on.

Make sure that when the partitioning step presents itself you select the option that asks to use the whole hard drive.

When complete, remove the Live CD and reboot without it.  You should be running Ubuntu from the HD now and not the live CD.

Good luck!

---

### Post by Tripawd on 2008-04-25
Thanks...I'm not at my computer right now but that is what I will certainly try to do...the only part I'm wondering about is I already tried rebooting the computer with the live CD in the tray, and I still get the message about "no boot sector, insert OS disk and press any key" over and over again, this with the live CD in the drive.  Maybe I just need to go into the BIOS and tell it myself to boot from the CD first, or maybe I just need to burn a new CD.  Unfortunately I've been trying to install Ubuntu while not having time to pay attention to what was going on.  I'll give it a shot later today, thanks for the help.

---

