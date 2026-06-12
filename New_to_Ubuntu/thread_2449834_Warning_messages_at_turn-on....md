---
title: "Warning messages at turn-on..."
date: 2020-09-02
forum: New to Ubuntu
---

### Post by Innernet on 2020-09-02
Hello.
A few times along years, a brief message showing that the temperature of the system went beyond safe figures...
A few times along years, telling a BIOS problem was detected...  Well, that is as much discernible.
How to stop the thingy from disappearing in order to read the whole message as an attempt to understand/read the whole thing ?

It is a Compaq CQ57 if relevant.  It would be great if hitting the space bar, or any key, or the trackpad suspends the screen...and resume at the next hit...

Are such warnings logged somewhere ?  Is Ubuntu involved or should not even post this here ?

---

### Post by TheFu on 2020-09-02
```
dmesg
```
or 
```
journalctl -b
```

May want to get good at file redirection too.  [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) explains. Just page down a few times. Any beginning Unix text would have the same information in the "redirection". This is a basic skill for anyone running Unix/Linux.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is another resource, 100% free, no hassle to get. They don't want your name or email. That book is sold in normal bookstores around the world too, if you want dead trees.

Many BIOS warnings are about hardware you don't have. It isn't really a warning, just a notice they didn't see something that may have caused issues for some people.  Sometimes BIOS warnings are about slightly incompatible hardware and what the OS is doing to correct it. Sometimes the corrections impact performance and sometimes they do not.

Some GUI DEs have some sort of log viewer application too.  I don't know anything about those, so look in the "Ubuntu handbook" or Ubuntu User's Guide" for the release and DE your system runs.

---

### Post by Innernet on 2020-09-02
Thanks, TheFu.
The command dmesg did generate many lines of a report; but I did not foresee the same fail I fall often.  My brain does not understand the report. ](*,)  Not your fault.

---

### Post by TheFu on 2020-09-02
Thermal warnings matter a little if they are for the CPU. In the last 15+ yrs, desktop CPUs always throttle back when they get too hot. That impacts performance, but probably is not harmful to the CPUs.  I had an i7 CPU that would throttle 2 cores all the time when doing video transcoding tasks.

Other parts inside the computer having thermal warnings is cause to take action.  First, clean out all the dust.  Next monitor the temperatures in different components and different parts of the system.  Look up the "optimal" temperatures for each.  For example, for HDDs, the temperatures of 40 or less degC are desired.  I have some running at 44 and 45 now.  Last month, I put in a new fan to pull air over the tray that holds 4 HDDs. For a number of reasons, I set the fan to run "silent", which it is, but because it isn't cooling the HDDs sufficiently, at the next reboot, if I remember, I'll turn up the fan a few hundred RPMs.  It is at 750 rpm now.  Faster spinning fans are noisier, so there is a trade-off.  OTOH, HDDs that are too hot have shorter lifetimes.  Each HDDs tracks the temperature.

Inside the case, motherboards will have temperature sensors a few different places, so get the "sensors" package for your motherboard working.  You may need a case fan or two or three, depending on what the temperatures show.  I've never had more than 1 case fan and the PSU fan  ... until this drive tray thing.  I'm not counting the CPU fan/cooler in that list.  I don't use "hot" GPUs, so those are never really a concern to me.  In fact, none of my GPUs has a fan on them, just heatsinks. That assumes I'm not just using the built-in iGPU that most intel CPUs bring along.

If cleaning all the dust doesn't get the CPU to stop throttling and you've solved all the other case/GPU/HDD cooling problems, then the last thing is to replace the CPU thermal grease. That stuff does wear out.  Look online for how to remove it, clean it well, put new on and put everything back exactly the way it was.

Of course, I'm assuming the computer isn't sitting in direct sunlight or outside or has stuff blocking the fan ports - even unused fan ports.  It should be in a climate controlled location most of the time.  I keep my computer room warm in the summer (26 degC) and cool (17 degC) in the winter, approximately. A little warmer in summer and a little cooler in winter. Computers need about 4 inches around them on all sides, including front, back, and top, for airflow.

As for understanding logs, it takes a little time of looking at them to become more comfortable. I remember when my eyes glazed over seeing that stuff a few decades ago.  Not anymore.  The trick is to actually read the lines and look up any terms you don't understand.  Sometimes that isn't any help either, but at least it won't be completely unfamiliar next time.  Lines to look at carefully have *warning*, *error*, or *critical* in them. Usually, there might be just a few of those in total. The look at about 10 lines above that, figure out what was happening, check the timestamps, are they related?

Oh - **dmesg -T** will show timestamps.  All the commands have all sorts of options and there is a help system on your machine which should have the manual page for each command and all options.  **xman** is sometime used to browse that information.

---

### Post by Autodave on 2020-09-03
I believe that he has a laptop, but the same things generally apply: make sure ventilation can get through the machine.  Do not place it on something soft that can restrict air flow.  When I have to use one of my laptops for an extended period and I have nothing to put it on, I have a plastic cutting board that I picked up at Walmart to put it on.  A laptop cooling table would be even better.

---

