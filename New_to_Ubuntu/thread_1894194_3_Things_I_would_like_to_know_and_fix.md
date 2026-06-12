---
title: "3 Things I would like to know and fix"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by AlexTolic on 2011-12-12
Hey there again, still new to the forum and still using it as much as I like for help and learning, so bear with me.

The first question i have is : I once read that linux running machines, due to some reason, never really need to be shut down. Why is this?

Second thing is (which i tried to get help with but with no luck) sometimes when i log back in from suspend mode my laptop will instantly go back into suspend mode after the log in process finishes. Then when take it back out of suspend mode its already of the desktop. Then it dims out and brings up the login prompt. I login and then everything is fine. Curious to know if this is a very common bug with 11.10 or what.

And my last question is sometimes (and now more recently) right before a sound is to play out of my speakers a pop sound will come out. And know whenever i change the volume instead of hearing the normal sound effect that plays it just pops. Any fix for this bug.

---

### Post by guyver_dio on 2011-12-12
They say the same things about apple machines, I'd say it's all a load of ****, if you fiddle around enough on any OS eventually it may be worth shutting down or restarting to flush everything and start fresh. I've had applications on ubuntu that haven't opened properly but the process is still running. All of those kind of things that slow down your system it pays to just restart every now and again. Maybe it doesn't need to be done as much as windows. 

Another thing I've heard before is leave machines running for as long as possible because hard drive failures are most likely to happen during booting of a machine. I can't really say that is true, I usually shut down my machines every night and I've got hard drives that are like 8 or 9 years old in them and they still haven't died.

As for your second question I've had similar experiences on 11.10. It's like when it goes into suspend mode and then something pops up like wireless asking for password or some sort of prompt, I'll have to login, do whatever with the prompt then it'll take me back to the login screen again. It got annoying for me too so all I did was turn lock off when it goes into suspend mode. I'm the only one who uses this computer and only set up one account so I don't really need it to lock.

---

### Post by MadsRC on 2011-12-12
No matter what operating system you use, you need to restart it at some point. Goes for SetTopBoxes, Router, Computers and even had a SmartTV that once had to reboot to function properly. SmartPhones too.
 
Though, from my experience, Linux have to rebooted less frequently than Windows. The only time I've been prompted to reboot Linux was when I installed my proprietary Nvidia driver. My windows box asks me to reboot when  update and install certain applications.
 
Now, I don't know the techie explanation (Well, I've been told the answer once, but can't remember it.) but the above is from my experience using Ubuntu and Windows XP, Vista and 7.

---

### Post by lolpenguin on 2011-12-12
1) You have to reboot every now and then. Also not leaving your computer on saves power, while some people may leave their computers on sleep mode through the night. I, however, suspend or shut down.

2) This doesn't happen to me, and you have another (unanswered) thread on this.

3) Reported by other users. [[ubuntu] Speakers making a popping sound randomly throughout usage. (11.10)]("http://ubuntuforums.org/showthread.php?t=1892746"). This really could be a problem with hardware, or internal connections.

---

### Post by mastablasta on 2011-12-12
> **AlexTolic said:**
> The first question i have is : I once read that linux running machines, due to some reason, never really need to be shut down. Why is this?
.
 
 
that is maybe due to hibernation? hibernaiton will be on new win8. it's not completelly off but using very very little power.
 
Anyway usually servers are not rebooted often and they run linux. it's a bit differetn for desktop linux where soem updates might promt for reboot.
 
windows also don't really need to be shut down.
 
once i read an article (wish i knew the link) about how keeping your ocmputer on actually saves you money as the cost of electricity used is smaller than the damage of components that need to be replaced more ofted due to shut down and then reboot. it had a comprehensive test and then calculations (compared to other sites that may be spreading myths).
 
i too have 10+ year old disks still working. but they now started to show signs of aging. perhaps if i didn't shut it down as much they could last even longer?! :)

---

### Post by guyver_dio on 2011-12-12
> **mastablasta said:**
> that is maybe due to hibernation? hibernaiton will be on new win8. it's not completelly off but using very very little power.

Win7 also hibernates, it's like your machine almost turns completely off and you have to press the power button to get it back out of hibernate.

---

### Post by mosaic2s on 2011-12-12
> **AlexTolic said:**
> Hey there again, still new to the forum and still using it as much as I like for help and learning, so bear with me.

The first question i have is : I once read that linux running machines, due to some reason, never really need to be shut down. Why is this?

Second thing is (which i tried to get help with but with no luck) sometimes when i log back in from suspend mode my laptop will instantly go back into suspend mode after the log in process finishes. Then when take it back out of suspend mode its already of the desktop. Then it dims out and brings up the login prompt. I login and then everything is fine. Curious to know if this is a very common bug with 11.10 or what.

And my last question is sometimes (and now more recently) right before a sound is to play out of my speakers a pop sound will come out. And know whenever i change the volume instead of hearing the normal sound effect that plays it just pops. Any fix for this bug.

1st questions has been answered many times over. So answering 2 and 3rd point only.

If you are looking for a flawless performance, pl use 10.04 - the stable version. else check exhaustively through forums etc for hardware compatibility before using 11.10 or 11.04 - these contain latest cutting edge features but in experimental mode. So bugs remain.

However, feel free to file bug report.

---

### Post by haqking on 2011-12-12
> **mastablasta said:**
> that is maybe due to hibernation? hibernaiton will be on new win8. 

> **guyver_dio said:**
> Win7 also hibernates, 

Hibernation has been in windows since Windows 95 using APM and i think was called suspend to disk back then.  From Windows 98 it supported ACPI.

Hibernation is nothing new

---

### Post by mastablasta on 2011-12-12
> **haqking said:**
> Hibernation has been in windows since Windows 95 using APM and i think was called suspend to disk back then. From Windows 98 it supported ACPI.
 
Hibernation is nothing new
 
 
they were introducing it as a new feature that will shorten the boot time of windows 8. Hibernation as i- n computer is practically off. you then push power button and almost instantly it "boots" into working environment that is just like you left it before. 
 
the sleep function is not the same as it uses more power.
 
 
 
if this feature is so old and standardised how come it fails so often in Linux? hmm....

---

### Post by mastablasta on 2011-12-12
> **mosaic2s said:**
>  
If you are looking for a flawless performance, pl use 10.04 - the stable version. else check exhaustively through forums etc for hardware compatibility before using 11.10 or 11.04 - these contain latest cutting edge features but in experimental mode. So bugs remain.

 
Stable as in "all bugs are known but not necessarily fixed"?. Also older versions have odler kernels= older drivers= does not work on new hardware.
 
Problems with latest Ubuntu is indeed the experimental nature of new desktop enviroment (Gnome3+Unity). However if oyu look at for example Kubuntu - the latest KDE hin 11.10 has numerous bugs fixed that will stille xists in 10.04.
 
another example - been using 10.04 LTS. Sound worked sporadic and this was due to a bug. The bug was patched/fixed. but the fix was not made in 10.04. fix was there in 10.10 so i upgraded. sound now works reasonably well (hibernation can still cause it to dissapear, but reboot can bring it back).
 
so yes it was stable as in they knew were the bug is, they knew the fix for it but they didn't implement it.

---

### Post by haqking on 2011-12-12
> **mastablasta said:**
> they were introducing it as a new feature that will shorten the boot time of windows 8. Hibernation as i- n computer is practically off. you then push power button and almost instantly it "boots" into working environment that is just like you left it before. 
 
the sleep function is not the same as it uses more power.
 
 
 
if this feature is so old and standardised how come it fails so often in Linux? hmm....

yes i know the difference between sleep and hibernation.

as for so old, i was talking about windows and not linux, hibernation in Linux is only since 2.6 kernel i believe as in built in

[http://en.wikipedia.org/wiki/Swsusp](http://en.wikipedia.org/wiki/Swsusp)
[http://en.wikipedia.org/wiki/Hibernation_(computing](http://en.wikipedia.org/wiki/Hibernation_(computing))

Hibernation in windows is years old

---

### Post by 3rdalbum on 2011-12-12
> **AlexTolic said:**
> The first question i have is : I once read that linux running machines, due to some reason, never really need to be shut down. Why is this?

No sufficiently-stable operating system should need to be rebooted, except to apply updates. Windows is sorta like one big piece of code; if any part of it changes on disk due to system updates, you have to reboot so it will re-read the whole operating system again. With Linux, it's different independent pieces of software. If one piece of software changes on disk, it can just be restarted on its own.

But no, Windows shouldn't need rebooting either except for updates.

For the record, I rarely shut down my computer. I suspend it. The only time it needs rebooting is when there's a kernel update; that requires a reboot because it's a very low level of the operating system.

> Second thing is (which i tried to get help with but with no luck) sometimes when i log back in from suspend mode my laptop will instantly go back into suspend mode after the log in process finishes.

Tell me: Are you suspending and then immediately closing the lid? If so, then you're basically telling the system to suspend twice. After resuming the first time, the system sees "Oh, there's another call to suspend. I'd better do it".

Two options: Shut the lid ONLY and it will suspend. Or suspend, wait until the computer's fans have stopped turning, and THEN shut the lid.

> And my last question is sometimes (and now more recently) right before a sound is to play out of my speakers a pop sound will come out. And know whenever i change the volume instead of hearing the normal sound effect that plays it just pops. Any fix for this bug.

It sounds like overenthusiastic power management for your audio chip, but I have no idea how to troubleshoot it or fix it.

---

### Post by AlexTolic on 2011-12-12
Thanks for all the help and the interesting discussion that took place.

> **3rdalbum said:**
> 


Tell me: Are you suspending and then immediately closing the lid? If so, then you're basically telling the system to suspend twice. After resuming the first time, the system sees "Oh, there's another call to suspend. I'd better do it".

Two options: Shut the lid ONLY and it will suspend. Or suspend, wait until the computer's fans have stopped turning, and THEN shut the lid.



It sounds like overenthusiastic power management for your audio chip, but I have no idea how to troubleshoot it or fix it.

And thank you. The double suspend is something I guess ive been doing. And i will just have to look into the audio bug and power management.

Thanks to everyone

---

### Post by daemondign on 2011-12-12
Killer Q&A
To address the problem that you're having when you log back in from suspend mode, I would first start by asking if you're pressing the sleep button first then closing the lid? If not, then try adjusting you Power Options. Set them all to "Do Nothing," (when I press power button, when I press sleep button, etc) and just leave: "When I close the lid: Suspend." 
Not saying it will work, for sure. But it may help you narrow down the problem

 &#946;£@$™äñ

---

### Post by anewguy on 2011-12-12
Yes, depending on the manufacturer of the motherboard and their parts supplier, some of the components can "wear out" more quickly with power cycles.  The thing that is the real killer is something people do after a kernel update or some other update that requires a reboot - anything that might change system tables that aren't dynamic.  The thing they do is power off the system and immediately power it back on.  Nothing is worse - it can be like sending a power surge through you system.  Waiting 30 seconds isn't that long, and it allows time for "stray" voltages, etc., to drain out before power is applied again.  I once did a similar thing on a mainframe many years ago after spending 30+ hours straight updating the OS and making some changes on the weekend.  The result was $475 an hour (mind you, this was 35 years ago!) for vendor hardware support to come out on a Sunday night that was also a holiday.  Things have improved greatly in the last couple of years, but there are still many motherboards in service with the bad capacitors that went around a few years ago.  Every time one of those boards is power cycled it is a failure waiting to happen.

Depending on the OS, there are also ways to force a "cold" start that can also help.

Basically, any OS will need a reboot on a kernel change.  There can be other modules that might force a restart as well because they "hook in" to the system in the boot process, as well as anything which might require an update to a system table that is static.

The "double-hit" on hibernate sounds like a reasonable explanation for the symptoms show coming out of hibernation.  Indeed, Windows 7 has a different type of "sleep" - everything is basically off, yet pushing the space bar a couple of times or pushing the power button wakes it up, and it wakes up fast right back to where you were.  The one thing I haven't done yet is look for a setting to change a part of this behaviour - it will go into this "sleep" even with a user process running, such as the installation of software or the download of something big, so you come back an hour later and nothing has happened - you have to wake it up first!

The sound problem has been mentioned several times in the forum.  It could be a driver issue, it could be a chip issue, it could be a power issue, etc..  Your best bet is to take the motherboard model and the sound adapter chip type and do a search on the internet for those with popping sound and linux - something may turn up.

Dave ;)

---

