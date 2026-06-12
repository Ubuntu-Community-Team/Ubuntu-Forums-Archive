---
title: "Script for a a startup of application"
date: 2017-12-23
forum: Programming Talk
---

### Post by clowcadia on 2017-12-23
Hi guys, just wondering how can i make a script executable when a certain program is started.
i sort want to make a script to turn off certain services while running an application for better processing

---

### Post by TheFu on 2017-12-23
I think file execute permissions are only checked at file-open time.  The way to prevent something from running is to either 
a) move it, stop the process (send the process a shutdown signal), disable the startup
or
b) prevent access (read and execute) to the file for the userid that it runs under.

For processes/daemons run by root, things are harder.  shutting down the running service should be sufficient almost always, at least until the next reboot or for things set to run every 24 hrs.  Some things are set to run "once and hour" or "once a day" ... those will keep trying to run until they finish successful. If they are spawned by crontab/anacron, those settings are in /etc/cron.*/ directories.  If they are controlled by systemd ... I honestly don't know. I've successfully avoiding knowing much about systemd to this point.

For things run by your own userid, dealing with file permissions should be sufficient.  Just remove both read and execute.  chmod -rx file/path.  Don't forget to put them back the way they were.

---

### Post by clowcadia on 2017-12-23
lol ok ill go into detail what i am trying to do, since i am not sure how to take that response. i am sorry i dont think i understand

what i am trying to do is due to my driver for rtl8821 is not provided from ubuntu, to make it work i had to use work around that run the wifi card at full power making my system hot, and i am assuming its doing alot of processing. so i want to disable it with "sudo modprobe -r rtl8821ae" when firefox shuts down and when it opens i want it to run "sudo modprobe rtl8821ea", and id like to use this idea to possibly stop services from running when i run ftb minecraft as its a ram hog, no issues so far running it simultaneously with all services up but i just want to do as much maintenance automatically when i use my ubunto os

---

### Post by TheFu on 2017-12-23
For a device driver, I'd just go into low-power mode when I didn't want to use it and full-power mode when I did.  There are scripts/examples in the /etc/pm/power.d/ directory on my system. Different releases might use slightly different locations.

For a wifi driver, I'd probably just use rfkill to disable it completely.

As for making any java program RAM or CPU efficient, I haven't a clue.  Been waiting for that to be possible since 1995-ish.
 
BTW, your reply seems to have a few typos for the modprobe stuff. Getting a few characters backwards is a huge problem.

Automatic maintenance that is shipped as part of the OS is good.  Doing things outside the built-in /etc/ settings is not so good. You'll lose those over time.  That might be good, since problems get solved all the time.  OTOH, I still accidentally hit the power key on my laptop, which shuts down the OS when I'd rather have it go into standby - they put the power key were the DELETE key belongs (idiots).  I fixed this problem in a prior install, but that fix either stopped working or didn't make it into a fresh re-install. Don't recall. I bet the same will happen to you. ;(  Customized system changes are usually lost between installs unless we are extremely careful.

---

### Post by clowcadia on 2017-12-23
Hmmm maybe use cloud for back up for custom sys changes. As for typos I use those exact commands and it work fine not sure what you mean. I've been pressing power button lots lately to force shut down when I did not have grub doing some silent error reporting due to unfamiliar rtl8821ae drivers. As for Java tea I wish there could be third party programs like using c++ to manage the ram used by it or something like that, but the more I think about it java would have to do more processing to allow those 3rd party programs to manage the ram locations java is using. And as for rfkill essentially yes I want to use it but automatic ly when Firefox ceases to exist as a job or something

---

### Post by TheFu on 2017-12-24
rtl8821ae or rtl8821ea?  THAT was the typo above. Details.

You can use namespaces to limit java.  Firejail would be an easy interface for that. It is built into the kernel. I'm pretty certain that JREs also have a method to limit RAM in different ways too.

Seems like you know what needs to happen.  Just create a little watch-dog script that looks for firefox running in the process table and takes whatever actions you want as the conditions change.  That is common stuff.   I'd probably just add that script to the startup for firefox and have it kill itself if firefox isn't seen in the process table for 20+ seconds.  [https://unix.stackexchange.com/questions/55318/watchdog-script-to-keep-an-application-running](https://unix.stackexchange.com/questions/55318/watchdog-script-to-keep-an-application-running) might be helpful.

---

### Post by clowcadia on 2017-12-25
Great thank you. I do sort of want to avoid a script that runs every second but that might not be avoidable, I just sort of wondering if I could get ubuntu to throw an action when there is Firefox open or close event. Java though I want to maximize the ram usuge as long as it doesn't create issues or redundancy. Oh man I believe it's easy sorry

---

### Post by TheFu on 2017-12-28
So [solved]? I can't tell from the last post.

---

