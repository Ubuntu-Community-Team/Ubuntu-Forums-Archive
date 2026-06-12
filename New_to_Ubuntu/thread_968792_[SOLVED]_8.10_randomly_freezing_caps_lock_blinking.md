---
title: "[SOLVED] 8.10 randomly freezing caps lock blinking flashing"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by nhasian on 2008-11-02
I upgraded from Ubuntu 8.04 to 8.10 using the alternate ISO, then using the update manager to get all the latest updates.  I never had 8.04 lock up on me and have been very please thus far.  since installing 8.10 my HP9500 notebook has been crashing very frequently.  Is anyone else experiencing this problem? What can I do to troubleshoot it?

I dont have much installed as far as software:

firefox, thunderbird, virtualbox, screenlets, ushare, hellanzb, wine, nvidia restricted drivers, and flash 10.  I think thats about all the software i have installed.

i am always running firefox so i thought that may be the culprit.  So on a cold restart as soon as Gnome finished loading i went to the Synaptic package manager to add Opera.  I never got that far because it crashed again already.

i know there are log files, but i wouldnt know what to look for.  Is this because i upgraded from 8.04 instead of a fresh install?  Or is there some problem with 8.10 that's causing it to crash?  I've seen some other threads about crashing too.

PS when the caps light blinks and everything becomes unresponsive, that means everythings locked up right?

---

### Post by asmoore82 on 2008-11-03
The blinking CAPS lock light is a sign of a kernel panic.
I would say a kernel panic on a production distro is almost always a sign
of failing hardware;
but the recent upgrade/overhaul leaves room for interesting things to go wrong ...

maybe the newer linux kernel that ships with 8.10 has a known hang up with that model of HP - HP has been notorious for power management bugs lately;
or maybe some old module for 8.04 is still getting loaded into the kernel for 8.10 ??

I would boot a liveCD after a crash and mount the drive and try to read the logs.

P.S. the most proper way to power off the system in this situation is by
using the magic sysrq keys ... [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

SysRq is the same as the Print Screen button on most keyboards and
to power off the system you could send a Sync and Off :

[Alt]+[SysRq]+s
[Alt]+[SysRq]+o

---

### Post by dhbabey on 2008-11-03
I'm seeing this exact same problem on a lenovoa thinkpad t61p...

looks like for many people its been going on since 8.04, however I never experienced this problem until I upgraded to intrepid 8.10

[https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless](https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless)
[https://bugs.launchpad.net/ubuntu/+bug/276990](https://bugs.launchpad.net/ubuntu/+bug/276990)

also
[http://ubuntuforums.org/showthread.php?t=832383&page=17](http://ubuntuforums.org/showthread.php?t=832383&page=17)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291044](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291044)

---

### Post by jpoRS on 2008-11-03
I have the same problem on a next to new (2 months old) System76, since upgrading to 8.10.   So I mean it isn't impossible, but that more or less rules out hardware, right?

jim

---

### Post by nhasian on 2008-11-03
dhbabey, I would click the "Thanks" button 10 times for you if I could.  I cant believe i didnt read the release notes.  I read release notes for every version of software i update.  It didnt occur to me that the **Operating System** would have release notes.  

I have the Intel Wireless 4965 network adapter and the driver in the kernel is what was causing the problem.  I enabled the *linux-backports-modules-intrepid* and no more lockups.

> **System lock-ups with Intel 4965 wireless**

The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.) 

---

### Post by Sequences on 2008-11-03
thanks, i just did that, hope this fixes the problem because i have been suffering from freezes as well.

---

### Post by jpoRS on 2008-11-03
I will try that, and If my computer is still here in the morning, then I guess it worked!

Thanks!
jim

---

### Post by Supermattt on 2008-11-07
> **nhasian said:**
> dhbabey, I would click the "Thanks" button 10 times for you if I could.  I cant believe i didnt read the release notes.  I read release notes for every version of software i update.  It didnt occur to me that the **Operating System** would have release notes.  

I have the Intel Wireless 4965 network adapter and the driver in the kernel is what was causing the problem.  I enabled the *linux-backports-modules-intrepid* and no more lockups.

Thanks pal ! That rocks !!!

---

### Post by trampas on 2008-11-13
I installed the backports and my laptop was stable for about 2 days but just kernel panic. I am a newbie thus I am not sure how to get the logs. However the kernel panic happened while working in 8.10. Thus I am tired of problems in 8.10 and will format and install 8.04 in the morning.

Trampas

---

### Post by Squonk07 on 2008-11-13
> **dhbabey said:**
> I'm seeing this exact same problem on a lenovoa thinkpad t61p...

looks like for many people its been going on since 8.04, however I never experienced this problem until I upgraded to intrepid 8.10

[https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless](https://wiki.ubuntu.com/IntrepidReleaseNotes#System%20lock-ups%20with%20Intel%204965%20wireless)
[https://bugs.launchpad.net/ubuntu/+bug/276990](https://bugs.launchpad.net/ubuntu/+bug/276990)

also
[http://ubuntuforums.org/showthread.php?t=832383&page=17](http://ubuntuforums.org/showthread.php?t=832383&page=17)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291044](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291044)

I gave this solution a spin.  Sadly, I have only an 802.11b network here at home, so next week when I return to my university (where I have been suffering almost continuous lockups) I'll evaluate the situation and report back.

I admit it was kind of dumb of me not to read the Release Notes. *bangs head repeatedly against wall* ](*,)  I won't make that mistake again.

---

### Post by Squonk07 on 2008-11-17
> **Squonk07 said:**
> I gave this solution a spin.  Sadly, I have only an 802.11b network here at home, so next week when I return to my university (where I have been suffering almost continuous lockups) I'll evaluate the situation and report back.

I admit it was kind of dumb of me not to read the Release Notes. *bangs head repeatedly against wall* ](*,)  I won't make that mistake again.

Quoting oneself is kind of n00bish, I know, but there you go. (Amazingly the spell checker seems to feel that "n00bish" is indeed a word as there doesn't seem to be a red line under the letters.)  As far as the solution goes, so far, so good.  I've been on several 802.11g networks here at college, and I haven't experienced one lockup yet.  I'd say this issue is probably resolved now for me.

---

### Post by davidb_ on 2008-12-02
Though it is probably pretty obvious based on the research done by the people in this thread, the following fixed the problem of kernel panics with 802.11n networks on my thinkpad x61:

sudo apt-get install linux-backports-modules-intrepid

Thanks!

---

### Post by dannytatom on 2008-12-03
Just installed it, hoping it'll work.  Oddly enough, it wasn't messing up when I updated from 8.04, only after I did a fresh install did it start freezing.

Anyway, just wanted to say thanks!

---

### Post by dannytatom on 2008-12-03
Hrmm, well that didn't stop it. :/

---

### Post by inacoma on 2008-12-07
> **dannytatom said:**
> Hrmm, well that didn't stop it. :/


did not work for me either.  NOT SOLVED ;)

ktp

---

### Post by stevelove on 2008-12-10
> **davidb_ said:**
> Though it is probably pretty obvious based on the research done by the people in this thread, the following fixed the problem of kernel panics with 802.11n networks on my thinkpad x61:

sudo apt-get install linux-backports-modules-intrepid

Thanks!

I also experienced this problem on a Lenovo 3000 N200. It never happened until I switched from DSL to cable internet. (Cable is from Comcast using a Motorola modem, DSL was from AT&T using a 2Wire modem.)

After installing linux-backports-modules-intrepid the random freezing has stopped. I no longer have this problem under normal day-to-day use.

However, I have noticed that it still occasionally occurs while the laptop is in Suspend mode.

---

### Post by jcm4 on 2008-12-22
> **davidb_ said:**
> Though it is probably pretty obvious based on the research done by the people in this thread, the following fixed the problem of kernel panics with 802.11n networks on my thinkpad x61:

sudo apt-get install linux-backports-modules-intrepid

Thanks!

Thanks! This solved it for me!

---

### Post by arvast on 2009-01-13
Thanks alot! :D

My computers been up and running for 4 days now :D Before that I had kernel crashes every 12-20 hours ;_;

Youd think this problem would have been solved included in a kernel update or something.

Anyway :p

---

### Post by Dj TweeX on 2009-01-22
I am useing an HP-mini with a clean install of 8.04 for about 2 weeks now & its happening to me. i do have an intel wireless card but i do not believe that is the problem. any other suggestions??
Yay! Thinktank!

---

### Post by Dj TweeX on 2009-01-22
Also it seems to be random. not actually triggered by any specific process.

---

### Post by KyleBrown on 2009-01-29
Thank you!

---

### Post by TechBeastie on 2009-03-01
Hi everybody,
I think I may have happened upon a definitive fix for this bug.  
First off, a bit of background:
My laptop has been afflicted by this delightful problem ever since I installed Intrepid a couple of months ago, and not having had the time to do anything about it, I've been getting along by keeping my wireless card (an Intel ABG3945) turned off and its drivers disabled.  Though obviously somewhat irksome, this workaround has proved to be 100% effective at banishing the "flashing Caps lock of death;" at least in my case, the problem only occurs when my wireless card is active*.  

This evening, however, I was in a situation where I needed to have wireless access, and after I was forced to reboot my machine for the the third time in 15 minutes, I decided that it was high time to sit down and figure out whether it was possible to actually fix this horrible glitch.  
I therefore dutifully went and installed the backports package - but because I had read that this "fix" was far from universally effective, I also went a step further, and downloaded the very latest version of the driver package for my hardware directly from the [linuxwireless.org]("http://linuxwireless.org/en/users/Drivers") site.  Running
```
modprobe -l *iwl* 
```
reveals that the wireless drivers my system is currently using (and has been using, for the past several hours, without any problems) are the ones supplied by the package from linuxwireless - so assuming that this new-found stability holds, I think that this may be another good fix to try (after all, installing the driver directly does essentially the same thing as installing the backports package - and the driver you get is much newer than the one bundled into backports (and hopefully less buggy as a consequence).  

Hope someone else finds this useful!

*Actually, I've encountered a similar but not-quite-identical type of catastrophic crash (in which the keyboard and/or mouse lock up, and appear to completely loose power) on a couple of Linux distros, and I've narrowed the cause of that aberration down to some feature of the power management/screensaver utilities.  In Ubuntu, for example, the problem can be vanquished by disabling all GL (3D) screensavers.  Don't ask me why.

---

### Post by SaintDanBert on 2009-12-17
> **asmoore82 said:**
> 
... blinking LED ...


Is there a list of all of these sorts of omens and signs that something is happening?

> **asmoore82 said:**
> 
... Kernel Panic ...


Is there magic we should configure so that we capture maximum information when a kernel panic happens? Sadly, my workstation and configuration are plagued by them whenever I run a type-N wireless connection.

> **asmoore82 said:**
> 
...
P.S. the most proper way to power off the system in this situation is by
using the magic sysrq keys ... [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

SysRq is the same as the Print Screen button on most keyboards and
to power off the system you could send a Sync and Off :

[Alt]+[SysRq]+s
[Alt]+[SysRq]+o


I also believe that one must wait "a few seconds" between commands.
Is there any visual indication that good things are happening?

What does one do if SysReq (in blue) requires an extra Fn-key (in blue) to activate?

Is this a multi-key chord -- press and hold ALT + press and hold SysReq + then press 's'?

I vaguely remember that there is a list of these magic keys somewhere can you refresh where they are documented?

Thanks,
~~~ 0;-Dan

---

### Post by FrancoNero on 2010-06-10
yeah and since this is still a bug in lucid, it's far from really being solved. plus, why does it occur randomly, i mean really randomly?

---

### Post by yamagami on 2010-06-25
Yes - still a nightmarish bug in lucid on my thinkpad T61P. 
everytime i think i know why it happens it happens in a different scenario. 
Turning off compiz, installing backports etc seem to make it happen less often.  But it still does happen still...
Grrr

---

