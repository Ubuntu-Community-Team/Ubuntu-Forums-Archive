---
title: "External HDD Unplugged While Running GNU ddrescue"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by adam16 on 2013-10-05
I'm somewhat new to Ubuntu and am trying to recover data from a dead hard drive.  I already messed up one time, and after GNU Ddrescue recovered all of the data, I put what I thought was the old/bad hdd into the system and formatted it and was going to try to rewrite the data to it if it was usable.  But I actually formatted the hdd with the recovered image file instead...

I plugged it back in and have started the process all over (it took 6 days to finish the first time and that's on a system with a 3rd gen i7), but when I started the second attempt, I started getting a message that pops up saying hard drive failure is imminent, or something along those lines.  I went ahead with using gddrescue to make the recovery image, and today is day 5, so it should be almost finished, but my mom came in and yanked the external hdd, the destination drive, right out of the computer.

I'm new to GNU ddrescue and Ubuntu, has this totally corrupted the recovery?  Or can I still use the log file to resume the recovery where it left off?  I don't know if this makes any difference, but the terminal window running gnu ddrescue was open and running before my mom pulled the plug, now the terminal is minimized and will not open/restore.  I can open a new terminal, but I want the one that was doing the work.

Thanks in advance for your help...

---

### Post by whitesmith on 2013-10-05
For whatever it may be worth in hindsight, you now realize the importance of UPSing every  computer resource, especially when running critical tasks. I tried Drescue and had bad (=poor or no) luck with it. My favorite tool is SpinRite. This is commercial software from Gibson Research (grc.com). The cost of $89 may put off some readers, but SpinRite can read--and usually restore--just about every filesystem in existence, including Linux. The longest it ever took me to recover a damaged HDD was 3.5 days and I got everything back. My problem with Drescue was speed. I'm an open source advocate, but there are times when you have to be an apostate and reach for the credit card. Best regards.

---

### Post by adam16 on 2013-10-06
I don't mind the extra time it takes to run gddrescue, my question is, will the log file be usable to start recovering the HDD from where it left off when it was abruptly unplugged, or is there any way of knowing if its usable other than rebooting the computer (so I can remount the hdd that it won't recognize now) and just trying it and seeing what happens?

I've definitely heard SpinRite was the way to go, but I know it cannot restore the filesystem I'm trying to recover--it's the propietary encrypted PlayStation 3 filesystem that nobody on the net has seemed to figure out.  This is more of a project for my spare time than something I really have to get figured out...  Don't get me wrong, I've got thousands upon thousands of hours of saved game data that I would prefer not lose.  I also wanted to go ahead and just make a recovery image of the bad PS3 hard drive so I have it and can mess around with the bad hdd and try some things to get my save game data back that could result in having to format the hdd if it doesn't go as planned... 

(This part probably doesn't matter unless you're just interested in how I'm going to attempt to get my data)
I planned on saving the image to a hdd just in case this doesn't work... Then take the bad hdd and reinstall the OS on it through an update that could possible fix some of the errors without deleting the data.  There is also another way I read about where you can take a good hdd and have the ps3 format it and install the OS, the use that disk with gddrescue to recover any errors in the file system and then clone the boot sector back to the bad hdd... I don't know how I"m going to do all of this yet, but it's a project for my spare time... My main objective here is just to learn how to do this for future reference, in case there is ever a time that I have to recover important data.

---

### Post by adam16 on 2013-10-28
bump...  I just put this aside for the past month, but I'm going to start back on it today.  I'm going to just try blindly resuming gnu ddrescue and hoping the rescue image wasn't corrupted by the hard drive being unplugged.  I was just hoping someone had experience with an issue like this....

---

