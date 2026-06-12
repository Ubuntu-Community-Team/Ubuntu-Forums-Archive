---
title: "Help with automating tasks in Ubuntu"
date: 2012-12-03
forum: Programming Talk
---

### Post by DirWhowhowho on 2012-12-03
Hello,

I am totally new to Ubuntu and Linux.  I do programming in windows so I think I've got a pretty good foundation to start learning.  I am however totally stuck on where to begin with what I want to do:

I would like to auto-start smartctl then badblocks after boot up for 6 hard drives.

I was thinking there would be some easier way to do this by editing the ttyx.conf files, getting all of them to run, but it seems that happens before I need it to.

Then I was thinking rc.local file, but don't know how to run on each tty (1-6).

Then I was thinking Upstart would be the way because it is non synchronous and won't wait for one thing to finish before beginning another.  But that's scary because scripting in Ubuntu seems hard.

Or maybe there's another way I haven't discovered?

Really, I just don't know what the best solve for this would be or even where to start.  Any idea?

Thanks!

---

### Post by Cheesehead on 2012-12-03
Scripting in Ubuntu is really easy. You already know most of it.

I think Upstart is indeed a good place to start, so you can start those tasks exactly where you want them during/after boot.

Alternately, you can script them into a udev rule, so a task will run every time the disk is newly detected (powerup, swap, etc.)

Have you taken a look at the Smartmontools wiki page? [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) Some good tips there, too.

---

### Post by Lars Noodén on 2012-12-03
[upstart](http://upstart.ubuntu.com/cookbook/) requires a little reading to get oriented with, but not much.  After that it is basic shell scripting just like you find elsewhere in the system.

---

### Post by d.atanasov on 2012-12-03
Hi, 
What about "cron" jobs. It can do a lot of stuff and is pretty easy. The hard thing will be the scripts which you have to create for powering up the HD. 
[http://en.wikipedia.org/wiki/Cron]("http://en.wikipedia.org/wiki/Cron")
cheers

---

### Post by SeijiSensei on 2012-12-03
If you want to run a script at boot, the easiest method is to add it to /etc/rc.local.  That script is the last thing run at boot.  By default it is empty.  Just add your command(s) or script(s) to the bottom of the file.  Anything put in this file will be run with root privileges.

Don't forget to use absolute paths ("/path/to/my/script").

---

### Post by DirWhowhowho on 2012-12-03
Changing the rc.local does seem like the easiest route.  However, I want each of the 6 tty's to be scanning a different disk all simultaneously.  Is there a way to specify which commands run in which tty?  ie.  /dev/sdc on tty1 /dev/sdd on tty2... etc.

does rc.local run only after login?

if I have all six tty's doing auto login, does rc.local execute 6 times (one for each?)

thanks for the help ever1!:P

Edit:
in windows it would look something like:
[B]
Case ttyNumber
        1 : badblocks -wvs /dev/sdc
        2 : badblocks -wvs /dev/sdd
        3 : badblocks -wvs /dev/sde
        4 : badblocks -wvs /dev/sdf
        5 : badblocks -wvs /dev/sdg
        6 : badblocks -wvs /dev/sdh
end case[/B]

---

### Post by SeijiSensei on 2012-12-04
You can spawn them all and have them run in the background.  They do not need separate ttys though you need to pipe their output to logs to see what is happening.  Something like this:

```

#!/bin/bash

for d in "sdc sdd sde sdf sdg sdh"
do
    /sbin/badblocks -wvs $d > /var/log/badblocks.$d &
done

exit 0

```

That will iterate over the device names, spawn a badblocks job for each device, and write the results to separate log files.

I take it you're not intending to do this each time the system boots, right?  These jobs will take a while to complete and eat up a lot of the machine's performance while running.  Try running the job for /dev/sdc manually and see what load it puts on the system.  If you run it in the background by appending the ampersand ("&"), you can then monitor the load with "top" while the job runs.  You can also run "tail -f /var/log/badblocks.sdc" while the badblocks job is running to monitor the log file.

---

### Post by DirWhowhowho on 2012-12-04
You can spawn them all and have them run in the background. 

**wow, cool that works! (i couldn't get the for loop to work but just writing out the lines is fine)**

That will iterate over the device names, spawn a badblocks job for each device, and write the results to separate log files.

I take it you're not intending to do this each time the system boots, right?  

**yep, it is the hard drive surface scan server.  it's only reason to exist.**

These jobs will take a while to complete and eat up a lot of the machine's performance while running.  Try running the job for /dev/sdc manually and see what load it puts on the system. 

**surprised what little strain it is on the resources, thought it might max out.**


If you run it in the background by appending the ampersand ("&"), you can then monitor the load with "top" while the job runs.  

**wow, that's helpful! (both the background operator and the command to monitor)  ty!**

You can also run "tail -f /var/log/badblocks.sdc" while the badblocks job is running to monitor the log file.

[B]unfortunately, its not writing anything to the log while in progress.  hopefully it will have something to log @ the end!

[/B][SIZE=2][COLOR=Purple][FONT=Arial][SIZE=2]thanks for the tips!  got me that much closer to getting this up and running.  The idea is to plug in drives, hit the power and walk away.  [SIZE=2]I'm also going to add out[SIZE=2]put from smartctl.  Everything is written to a shared folder which is monitored constantly with some VB script.  Any new files created will be parsed out and populat[SIZE=2]e a windows database.  [/SIZE][/SIZE][/SIZE]Ideally, I'd like to have the server shutdown after jobs are done.  [SIZE=2](ready for 6 more drives)

[SIZE=2]thanks again [SIZE=2]for th[SIZE=2]e help![/SIZE][/SIZE][/SIZE]
[/SIZE][/SIZE][/FONT][/COLOR][/SIZE]

---

