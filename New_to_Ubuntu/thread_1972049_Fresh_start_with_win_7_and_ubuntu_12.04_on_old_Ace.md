---
title: "Fresh start with win 7 and ubuntu 12.04 on old Acer Aspire 5738"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by L Borealis on 2012-05-03
Hi everyone! I have a bunch of questions here, responses to some or all of then would be highly appreciated. I'm in the very beginning of the learning curve, but if possible some quick explanations (how does this work, why is this a good way etc.) along with the answers could help me get better.

I'm currently running Windows Vista and Natty on Acer Aspire 5738. I installed Natty (dual boot) because my Vista would sometimes freeze, with me being unable to do anything at all other than rebooting when it happened. Well, Natty has begun to freeze in exactly the same way, which is of course very frustrating. My theories are that it's either malware or some hardware problem. (Could it be something else?) My first question, therefore, is if I can and should check for hardware problems?

I plan on doing a completely fresh install on my computer, hoping this will solve the problem. (And make things run smoother in general, Vista isn't my favourite OS). I didn't do the original dual boot, so I'm pretty clueless on how it's done. I've had a look at how my hard drive is partitioned but it doesn't tell me much. My plan is to wipe it all, using DBAN or something similar. Will that take away the partitions as well? Is DBAN good or is there some better way?

After cleaning the drive, I want to install Windows 7 dual booted with Ubuntu 12.04. I found this guide [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) and thought it seemed easy and reasonable. I did notice it didn't set up any swap partition (I seem to have two of those right now) but instead it opted for a file. I have 4 GB RAM so I shouldn't need to do much swapping (am I correct on this?), but should I have a partition nevertheless? If so, how big? Is the guide a good way or should I do things differently? If so, I'd love step by step instructions or a link to that. 

I've got 320 GB HDD (so I might have Aspire 5738Z, not sure - terminal just says 5738 ) and I wonder how to best partition it. My home directory on Windows, which is where my files are right now,  seems to take up about 80 GB right now, but when I look closer I'm not  sure where the space goes, pictures account for about 26 GB but  otherwise I think it's other stuff than *my* files... it's not really tidy in there.

In the guide I read, one partition goes to Win 7, one to Ubuntu and one to storage of files. I have an external hard drive, so I'm more worried about not having space for programs than about not having space for files. On the other hand, I don't run any huge programs (no games or the like). On the third hand, I'll have some courses in programming at University, and would like to be able to use my computer for that - does that need much program space? Does it make any difference if it's in Windows or Ubuntu? And is it easy to resize partitions later on, or will it make a huge mess of everything?

Thanks a lot for your time, I hope you can help me!

---

### Post by Gremlinzzz on 2012-05-03
Does it run hot? if so may need just a cleaning;
Get a can of compressed air and blow the laptop out. Make sure it is off, unplugged and have the battery out (so that you do not turn it on by accident while cleaning it). Blow the air throughout the laptop making sure that you get where the vents are really good.
If the laptop still runs hot after blowing it out, you should either take it to a shop to get it cleaned .where they would take it apart to clean properly.:popcorn:

---

### Post by Dngrsone on 2012-05-03
You do have some sort of hardware issue going on there, and Gremlinzzz' suggestion is the best place to start-- get the dust out of your laptop and see if that helps.  After that, try running memtest86+ (it's included in Ubuntu installs and is a grub menu item uless you uninstalled it).

---

### Post by Mark Phelps on 2012-05-04
Freezing, especially when OS independent, is generally heat or disk problems.  Reinstalling is not going to fix either of these.

If the PC is running hot, then cleaning out the gunk, as already mentioned, will help.

If it's not running hot, then it's likely to be a failing hard drive.

If this is a laptop, how old is the drive and how often did you use the laptop?  Asking, because I have a laptop I used every day and the drives tended to last only 2-3 years each.

---

### Post by L Borealis on 2012-05-06
Hi everyone, and thanks for the replies!

The computer gets warm, but I'm not sure what's normal and what's hot. I'll try to clean it up a bit. 

The laptop is about three years old, and I've used it about daily, maybe a bit less... but I really hope I don't have to buy a new one. Maybe memtest could show that... I've never used memtest before, anything I should know? What results should I check for?

Ubuntu hasn't frozen in the last weeks now (I haven't really used Vista). Right now I decided to run a lot of things simultaneously just to put some stress on it (mostly films, youtube and and getting it to find files) and it's still running nicely. I'm quite sure there are much better ways to test my computer's responsiveness and freeze-tendencies, but I don't know them.

If it is a dust problem, or anything else that I can solve, I'll still reinstall everything, mostly to get rid of Vista but also to tidy things up in general. If I have to buy a new computer, I'll do a dual boot between Win 7 and Ubuntu as well. So any reply to the other questions is still appreciated!

---

### Post by Dngrsone on 2012-05-07
Memtest is pretty straightforward-- load it up and let it run.  Allow at least one full pass, a few is better.  If you get any failures, then you have a bad memory module (or, rarely, a bad Northbridge or memory slot).

---

### Post by Curtis6767 on 2012-05-07
Once you get the above issues sorted and you do your install, be sure to install Windows first.

If you already have the 12.04 CD or when you do acquire it, it is a must that you run Ubuntu from the LiveCD first before you install. In this way you can make sure that 12.04 will fetch the proper drivers for your system. 

There are dozens of threads on this forum started by notebook users where wireless failed to work with 12.04 leading to hours and sometimes days of sudo this or sudo that. I'm not sure how many of these situations have had happy endings.

GL

---

### Post by L Borealis on 2012-05-07
I ran memtest for two and a half hours. It passed twice and went through most of a third test. No errors anywhere, but the computer did get rather warm around the vents. Nothing critical, though, a bit above 50 according to lm-sensors. 

I also did the same thing with vista as I did before with ubuntu, i.e. putting stress on it by doing a lot of things simultaneously. When I plugged in a flash drive it finally gave up and froze, something that didn't happen with ubuntu. But maybe vista is just more sensitive...

I'll try to clean the laptop a bit and repeat it all, to see if it still freezes and if the temperature drops.

Meanwhile, anyone who has an opinion on swap partition vs swap file in my case? When I had a lot of things going on in ubuntu almost no swap was used, so I guess that I was right when I thought it's not used very much normally...?

Also, since everyone seems to agree upon hardware issue, is DBAN overkill? I do want a *fresh* start, so I'd like to get rid of everything on the drive, but maybe there's an easier way?

Thanks for your time!

---

### Post by Mark Phelps on 2012-05-07
IF it's a hardware issue related to a failing hard drive, then using dban, or any other disk wiping app, is not going to do anything to fix that.

Three years of daily use is quite good for a laptop, especially one that is running warmer than usual.  As I said, I've had to replace my hard drive twice now in a six-year-old laptop that I use daily.

IF you can find out the make and model hard drive, most manufacturers provide a downloadable utility you can run to check the health of the drive.  Unfortunately, most of those run in MS Windows.

---

### Post by Dngrsone on 2012-05-07
Ubuntu normally creates a swap partition, whereas Windows reserves some space as a swap file.

Ubuntu generally won't use swap, unless you are going to put it into hibernation, but I'd recommend making the swap the same size as your RAM.

---

### Post by L Borealis on 2012-05-16
Update:

Decided to skip Windows altogether, installed Ubuntu 12.04 LTS. Cleaned out the dust with compressed air and did a zero fill on the HDD before that. Computer still hangs. Memtest passed, SMART passed. (I even tried not using the first part of the HDD in case there were bad sectors there). Couldn't do Hitachi's own test, when I booted the CD it just kept loading the program. I'm currently monitoring CPU usage via Psensor and the top command, the one time the computer hanged and I could see the statistics CPU usage was around 30%, and it had been 100% before without problems. (But perhaps it was 100%, and Psensor didn't have tome to register it before the screen froze on me). Temperatures never go critical either. I'm going to start another thread later and see if I can find out where the problem is - meanwhile, if anyone sees this and has an idea or knows some good monitoring programs or tests I should try, it'd be great.

Thanks for all the replies!

---

### Post by Dngrsone on 2012-05-16
There are (rare) occasions when a RAM stick will pass memtest86+ and still be bad.  The reason why I usually recommend running memtest overnight is to catch some of those more intermittent memory problems; but like I said, sometimes a bad module will still pass but cause problems on a machine during normal use.

---

