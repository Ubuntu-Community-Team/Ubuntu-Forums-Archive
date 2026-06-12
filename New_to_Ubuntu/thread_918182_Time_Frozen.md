---
title: "Time Frozen"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-12
The time seems to keep freezing on my Ubuntu and I don't seem to understand why.  When I click on the time and go to Edit - Time Settings, the Manual configuration time seems to be working fine, moving along with the clock.

However, my taskbar's time just doesn't move.  I started my computer, it started at 4:55, went to 4:56, then completely stopped and it is 10-20 minutes later.  I tried restarting my computer... it sets the time at the correct time but does the same thing and stops a minute later.

Does anybody know what is going on?  I don't want to sync it with a server.

I am running Ubuntu Hardy.

Also, if anyone has any idea, the uTorrent and Wireless network logos on the taskbar occasionally dissapear (you can still click on them, but the logo dissapears and leaves an empty space).  Someone please help!!

Thanks

---

### Post by crazypenguin2008 on 2008-09-12
my time goes haywire anytime i have to restart....id love to find a fix for that problme. ive also had probles with icons vanashing as well....

---

### Post by RussW210 on 2008-09-12
I might have found a quick-fix penguin... I typed "sudo apt-get update" into the terminal and the clock is working again... whether or not it will stay that way when I restart I don't know but it fixed the time problem temporarily.

Anyone know any other way to fix other that apt-get update... wonder what I was missing...

---

### Post by bobnutfield on 2008-09-12
Are your installations on a laptop?  Do you get an error when you boot (just after the Grub boot starts) that says something along the order of:

> MBIOS BUG 8254: APIC not connected to timer

If so this is the root of the problem.  The same happens on my laptop, but I do not think there is a fix until some future kernel update fixes this bug.  The problem only seems to affect laptops.

---

### Post by crazypenguin2008 on 2008-09-12
mine is on my main desktop. hardy on all 3 pcs and it just does it on this one

---

### Post by bobnutfield on 2008-09-12
Well, so much for it only affecting laptops.  If you are not getting that BUG error report at boot, then it could be that your CMOS battery is getting weak in your motherboard.  That will cause the time to be intermittently perverted.

---

### Post by RussW210 on 2008-09-12
The time problem was happening on my desktop as well.  And my desktop is brand new as well as Ubuntu.  However, the "sudo apt-get update" seems to have solved my problem... restarted my computer and the clock keeps ticking along.  Not exactly sure what it updated though that fixed it.

---

### Post by crazypenguin2008 on 2008-09-12
ill have to try that when i get home sunday....

---

### Post by RussW210 on 2008-09-12
Anddddd the time seems to have stopped again.  I really don't understand this.  Anyone have any ideas?

---

### Post by paddyS on 2010-10-27
Mine seems to do the same but is also refusing to put new icons onto the panel too (eg skype when loaded).  It seems the whole thing is freezing and that is linked to the time issue

---

### Post by Geoff918 on 2010-10-27
I'd be curious if it's simply a software issue / taskbar issue, or if it is actually a systemic thing. I would tend to believe it's not systemic at all, but merely something to do with the taskbar.

Timing in a computer is extremely important, and I highly doubt that would be the only symptom appearing if it's systemic.

The next time the behavior shows itself, open up a terminal window and type the command "date" and see if the date is wrong (output will be in 24-hour format).

---

### Post by paddyS on 2010-10-28
Fixed it....

Deleted the panel2 directory in ~home/.gnome and then killed (and restarted) the panel and low and behold the whole thing works again.  Updating icons correctly and now keeps time.  Still works after two reboots so presuming this is a semi-permanent (at least) fix!

---

