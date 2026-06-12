---
title: "How do I automatically boot and then shut down at specified clock times?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-06-26
Hi Ubuntu Community:

I want one of my ubuntu machines to start up, log in the username and password at 6pm each day, then shut down at 11:59pm each day.

How do I do this? I don't want to touch the machine... I just want it to do this automatically.

Thanks, 
Phil Smith
Duluth, GA

---

### Post by brian_p on 2008-06-26
> **Phil Smith said:**
> Hi Ubuntu Community:

I want one of my ubuntu machines to start up, log in the username and password at 6pm each day, then shut down at 11:59pm each day.

How do I do this? I don't want to touch the machine... I just want it to do this automatically.

The only method I can think of to power on the machine is to train your cat to push the start button. Cron is worth looking at for powering down. Unless, of course, the cat is co-operative and a quick learner.

---

### Post by syczu on 2008-06-26
There is a application for this called Gshutdown for gnome and Kshutdown for KDE.

---

### Post by ercferret18 on 2008-06-26
i know how to do this on windows... but ubuntu, no clue.

---

### Post by whitethorn on 2008-06-26
Hi to get ur computer to start up, you can set a start up time in ur bios.  There's also another option to boot up on a network signal, if you have another computer which is on at the time. Then you can probably set up a root cron job to run the shutdown command. I'd add more I just don't have a clue how to set up the cron job.

---

### Post by Old Jimma on 2008-06-27
Hi:

I looked a gshutdown... it is nice... I don't see exactly how I can get it to start up Every Monday at 1am and then shutdown a computer every Monday at 4am.

The reason why I want to do this is because I'm going to start up and shut down 2 machines automatically to:

* make an automated backup of first,
* mount a file system on the second,
* store the backup on the first one, then
* shut them both down.

So, once I get this system set up, I don't want to touch it.

Does this make sense?

Thanks,
Phil SMith
Duluth, GA

---

### Post by brian_p on 2008-06-27
> **Phil Smith said:**
> Does this make sense?

Would you please clarify the starting up/bootong bit? Do you mean the boxes are plugged into the electricity supply but not switched on?

---

### Post by Old Jimma on 2008-06-27
Hi Brian:

Sure: here is what I hope is a clarification... I am lazy and want to automate the process of backing up one of my two ubuntu systems.

Specifically, I want:

1. the second computer to boot and 5 minutes later I want the 1st computer to boot, and mount a file system on the 2nd one... that is where the backup will be stored. I know how to mount nfs file systems. See: [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889))

2. the 1st computer will then back up its system (using [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)) to the mounted filesystem on the second computer.

3. the 1st computer will then shut down.

4 the second computer will shut down.

5. I will awaken 3 hours later and have a cup of coffee and be thankful for the ubuntu community for helping me be even more lazy than ever before.

Many thanks, Brian...

Best regards,
Phil Smith
Duluth, Ga

---

### Post by Vivaldi Gloria on 2008-06-27
> **Phil Smith said:**
> I don't see exactly how I can get it to start up Every Monday at 1am ...

My bios has such a setting. Have a look into your bios settings.

---

### Post by sydbat on 2008-06-27
Or just leave both boxes on 24/7. The power consumption is minimal and then you should be able to simply automate the backup for a time of your choosing. Personally, I would be a bit wary of turning them on/off as the backup may not be done at the time and you may end up losing data.

---

### Post by brian_p on 2008-06-27
> **Phil Smith said:**
> 
5. I will awaken 3 hours later and have a cup of coffee and be thankful for the ubuntu community for helping me be even more lazy than ever before. 

Indolence is a supported activity in Ubuntu:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

Any use?

---

### Post by cwii on 2008-06-27
I don't know but maybe there is a way to make it go to sleep and wake up when it needs to instead of just shutting down?

---

### Post by Big Wig !!! on 2008-07-26
SuperAwesomeTimer2000 Better than gshutdown:)

---

### Post by burtzacarach on 2008-07-26
Haha.:-k Wow.
So much for that question.#-o

---

