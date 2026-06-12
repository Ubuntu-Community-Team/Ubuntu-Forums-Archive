---
title: "How to wake computer at FIXED time-of-day"
date: 2015-11-22
forum: New to Ubuntu
---

### Post by stan24 on 2015-11-22
New to Ubuntu (6 months), running 15.10.


I'm trying to run a Perl script on my plugged-in laptop every day at 1 am.  Using cron, I scheduled a job to run at that time but it did not run.  I suspected this was because the computer was suspended at 1 am. To test this, I changed the time to a few minutes after the then current time and cron successfully ran the job a few minutes later- so I know the cron setup is correct.


I then repeated the test, scheduling the job to run a few minutes later, but then I immediately suspended the computer.  When I checked an hour later, the job hadn't run.  After some research, I come to find that cron doesn't wake up the computer and the job is NEVER run.  Further research reveals that the cron alternate, anacron, will at least run such jobs when the computer eventually wakes up rather than simply ignoring them.


That's not acceptable.  I want the job to run at 1 am, not 8 am or so when I manually wake up the computer.  (The Perl script does some stuff on the internet, and my ISP has unmetered access during the early morning hours.  I live out in the sticks, so metered internet access isn't cheap.)


Other cron alternatives seem to depend on the computer to be running 24×7, or seem too difficult for a noob like me - like compiling source code.


More research led me to rtcwake, which lets you wake up the computer after a fixed AMOUNT of time, e.g., 3600 seconds.  This doesn't solve my problem because I'm not INTENTIONALLY putting the computer to sleep - it's doing that automatically after I stop using it for 10 minutes.  To use rtcwake, I'd have to remember to manually end every day with a command such as: sudo rtcwake -m no -l -t $(date +%s -d ‘tomorrow 01:00’).


So, back to my original question: Is there some way to tell the computer to wake up EVERY morning at 1:00 am from here on out so that cron will run my job?

---

### Post by Tadaen_Sylvermane on 2015-11-22
Is there a way to detect the suspend event and have it fire a script before it fully suspends itself? Maybe with upstart or systemd?

Old but workable? [http://askubuntu.com/questions/15712/how-do-i-run-a-script-command-on-suspend](http://askubuntu.com/questions/15712/how-do-i-run-a-script-command-on-suspend)

---

### Post by jim_deadlock on 2015-11-23
The BIOS usually has a scheduled boot feature so you can set it to power on at a certain time.

---

### Post by matt_symes on 2015-11-23
Hi

If your BIOS supports it, you can use *rtcwake* command. Maybe put a call to it in the file

```
/etc/rc.local
```

The above file get called at system boot time. You can then programatically poweroff the computer using the *shutdown* command.

Another option maybe to send a WOL packet to the computer at 1.00am from a smartphone if you can find some suitable smartphone WOL software. There does seem to be some. This will depend on whether your NIC supports magic packets.

But the best answer is from the previous poster. Look in the BIOS and see if you can set an alarm to wake to the PC at the time you need.

Kind regards

---

