---
title: "Automated software update, now Ubuntu won't boot"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by kyoseki2 on 2014-07-18
Ok, I let Ubuntu install about 200Mb worth of automated updates just now and it no longer boots, I get to the point I assume the desktop manager would start and instead I just get a frozen cursor icon in the top left hand corner of the screen.

This is using Ubuntu 14.04 afaik, the only thing that's not remotely close to a stock install is that I'm using the 340 nvidia drivers from the xorg-edgers guys.

I can't change runlevel, so how do I even begin to figure out what the hell has gone wrong this time? I'm getting really tired of a multiple hour debugging session every time I make a minor update to the install.

Thanks.

---

### Post by coffeecat on 2014-07-18
So you use a bleeding edge PPA which by its very nature is likely to cause instability in your system and then you complain about having to find out what's gone wrong?

I'm just guessing here, but a 200MB update probably included a new version of the kernel - I saw a kernel update yesterday so I'm sure that's what it is - and perhaps the xorg-edgers nvidia driver doesn't work with the latest kernel. If so, simply boot into the previous kernel and either wait for an update from xorg-edgers before re-installing the newest kernel, or disable the xorg-edgers ppa, uninstall the 340 nvidia driver and install the repository version of the nvidia driver.

---

### Post by buzzingrobot on 2014-07-18
Yep, the new kernel is 3.13.0-32. I see that nvidia-340 at the PPA was built on 9 July.

Updates aren't telepathic. If a user has modified a system, they won't know it.

Remember, PPA's are not officially supported.

---

### Post by Rob Sayer on 2014-07-18
What post #2 said.  Try booting into the previous kernel.  If you have dual boot the grub menu is where that is and it's accessible.  If single boot hold down the shift key while booting to get the menu.

Installing from untested sources is a common noob mistake.  Don't use an external ppa if you don't know what you're doing.  If the program in question is in the ubuntu repos use those unless newer versions in an external ppa have some feature you just cannot live without.  The stuff in the main repos is beta tested.

However, don't enable the Proposed repo if you don't really know what you're doing.

While I don't always agree with what this guy says on other parts of his blog, this is good noob info:

[https://sites.google.com/site/easylinuxtipsproject/fatalmistakes](https://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

---

### Post by kyoseki2 on 2014-07-18
The only reason I was using the 340 drivers is because of problems with the nvidia-current (304?) and 331 drivers, neither of which, for some reason, ever wanted to let me run nvidia-settings (I get an invalid pointer error).

340 was working fine up until the update, which, yes, appears to have an updated kernel that doesn't like it.

nvidia-current doesn't seem to like the v32 kernel at all, I get a "warning, your graphics cards and/or displays could not be detected, you'll have to configure these yourself" followed by chasing my tail with a dialog box asking if I want to use a generic config or a backed up config that refuses to go away regardless of which options I select - this is assuming I can get anything other than a completely black screen in the first place - strangely, this dialog box appears on my secondary monitor, so clearly it knows there are two attached to the system.

I've managed to get v30 of the kernel up and running with the 331 drivers, so I'll muddle through with those until 340 gets rebuilt for the new kernel.

Thanks.

---

### Post by buzzingrobot on 2014-07-18
The current kernel in 14.04 is in the 3.13 series. I've had no problems with the 331 driver and nvidia-settings when I've used them with that kernel.

When the 3.2 series was released, I couldn't get any Nvidia driver working on any distribution using any kernel in that series.

---

### Post by kyoseki2 on 2014-07-18
Hmm, well as far as I know, I'm not doing anything clever outside of using the 340 drivers, which I've stripped out using apt-get purge nvidia*, but 331 seems to be very flaky.

eg.:
$ nvidia-settings*** Error in `nvidia-settings': free(): invalid pointer: 0x00007f94b024c623 ***
Aborted (core dumped)


With nvidia-current, if I boot up into the 3.13.32 kernel, I get a low res log in screen but can't progress any further than that (I log in and it fails to go to the desktop, just sits there on the orange triangles screen).

Almost any change I make invariably results in a black screen, with or without the ability to drop to the command prompt runlevel, it really is quite infuriating.

---

### Post by kyoseki2 on 2014-07-18
Ok, so here's a peculiar thing.

340 freezes at the cursor just prior to lightdm startup under normal boot with 3.13.30 & 3.13.32, but if I boot either 3.13.30 or 3.13.32 into recovery mode and then immediately just resume a normal boot, it starts up fine.

Since it (the recovery mode dialog box) warns me that video drivers don't always work correctly without a hard boot, I'm assuming that there's something starting up with a regular boot that isn't starting up with a recovery boot.

Any ideas what that might be or how I'd go about figuring it out?

---

