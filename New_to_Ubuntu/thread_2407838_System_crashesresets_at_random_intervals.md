---
title: "System crashes/resets at random intervals"
date: 2018-12-10
forum: New to Ubuntu
---

### Post by tomfielder on 2018-12-10
Hello. I'm experiencing an issue with Ubuntu where it is crashing/resetting at seemingly random intervals. I'm a web developer and recently switched my development environment to Ubuntu, so although I'm fairly new to Ubuntu (and Linux as a desktop), I am confident with the command line etc.

[B]The crash

[/B]My system can be stable for hours, then just suddenly reset while I'm working. It literally is as if I've pressed the reset button on the desktop case.

- This morning I worked for an hour, it reset at around 09:30, then reset twice more (both times within 10 seconds of logging in).
- I can walk away from my system while it is idle, then come back to find it has reset.

**Some info about my environment**

- 18.04.1 LTS (upgraded from Xenial when Bionic came out, not a clean install)
- Intel i7-6700
- Intel HD Graphics 530 with display port (was Nvidia geforce gtx 750 ti via HDMI using the tested Nouveau driver from Software & Updates -> Additional Drivers, more on that below)
- MSI Z170-A PRO motherboard
- Samsung NVMe SSD SM951/PM951
- 16GB RAM (2x8GB)

[B]When it started
[/B]
This problem has started since switching from my Nvidia Geforce GTX 750ti card to the onboard Intel 530 graphics. I switched because I was experiencing system lock ups (I could move the mouse but couldn't interact with the system in any other way) and other people in my office with a similar setup were working just fine with the onboard graphics. I no longer get the lock up.

[B]What I have tried
[/B]
- I have tried to reproduce the crash but without success.
- I have run memtest and had no errors.
- I have purged nouveau (I think).
- I have looked at various logs in /var/log but nothing jumps out at me.
- I have searched the web and this forum. I have found posts about i7-6700 not being supported, but I think that is outdated info.

[B]Other info

[/B]I'm a web developer. I'm pretty much running stock Ubuntu (other than tweaking to dark theme). I've installed Docker, Docker Compose, SmartGit, AWS CLI, Netbeans, Android Studio, Google Chrome, and probably a few other things.

Any help or advice would be greatly appreciated. If I can't get it working soonish I'll put the graphics card back in (and either try to solve the resulting crash or just put up with it..!).

Thanks.

---

### Post by Autodave on 2018-12-10
When you had the Nvidia card in there, what driver did you install for it and where did you get it from?

Your problem, at least to me, sounds more like a hardware issue.  Is the system overheating?  Fans clean and working properly?  I have seen similar problems caused by power supply issues and RAM issues.

Did you have any issues before you upgraded to 18.04?  I am assuming that you upgraded and did not do a clean install?

---

### Post by tomfielder on 2018-12-10
> **Autodave said:**
> When you had the Nvidia card in there, what driver did you install for it and where did you get it from?

Your problem, at least to me, sounds more like a hardware issue.  Is the system overheating?  Fans clean and working properly?  I have seen similar problems caused by power supply issues and RAM issues.

Did you have any issues before you upgraded to 18.04?  I am assuming that you upgraded and did not do a clean install?

- For the Nvidia card I installed the nouveau driver using Software & Updates -> Additional Drivers -> (the tested driver).
- I will monitor the system heat/fans, thanks for the suggestion.
- Yes, I upgraded to 18.04 (not a clean install).
- From what I can remember, Xenial didn't like the onboard Intel HD 530 graphics from i7-6700 (I think it was too new and not in the kernel, or something...). Hence why I ended up using the Nvidia card in the first place (it's an old card I had spare from an upgrade at home).

---

### Post by Autodave on 2018-12-10
That Nvidia card should have been using the 410.78 driver.  And that should have been available in the Additional Drivers area.  If not, it is available in the repositories.

After using (and loving) some derivative of Ubuntu for the past 10+ years (and on up to 13 machines) I have learned one VERY important thing: upgrading from one release to another *rarely *works well if at all.  

Every 2 years, a long term service release is made.  18.04 was the last one: released during the 4th month of 2018, hence the name 18.04.  The next LTS release will be in 2020 during the 4th month.  In the meantime, a new, short term release will be issued every 6 months.  These short term releases are only supported until the next short term release. However, the LTS releases are supported for 5 years.  It is always best to stick with the LTS releases. When it comes time to upgrade one of those, I have always found it easier and quicker to just backup what I need to keep, wipe out what is there, and do a clean install.

---

### Post by tomfielder on 2018-12-10
Thanks for the tip.

My system has reset twice since your post. I'm monitoring the temperature, but I'm not watching the number right at the time of crash so it's hard to know for certain... but from what I've seen, the temp usually idles anywhere between 28 degrees centigrade to 45. If the system was to reset due to overheating, would that information be logged anywhere?

---

### Post by Autodave on 2018-12-10
Probably, but that info is above my pay grade. :-)  One easy thing to do is to leave the side of the PC box off: that allows more air to circulate. When I find that that cures the problem, the fist thing that I do is run the memtest.  Since you already did that, I would be looking at the power supply.  How many USB items are connected?  Are they connected through a powered USB hub?  What is the rating of the PSU?

You didn't say how much RAM was in there.  And how many sticks of RAM.

---

### Post by tomfielder on 2018-12-10
The machine has 16GB of RAM (2x8GB sticks). I have a simple USB keyboard and USB mouse. Plus the monitor is also connected via USB (it has extra USB ports) - my phone is plugged in to one of those.

I'm unsure of the specifics of the PSU. I will find out, but I'm pretty sure it is overpowered for what my needs are.

I agree that it sounds like a hardware problem - but my only concern with assuming that is the case is that this particular crash has only started happening since swapping out the Nvidia card. Which would imply the fault is with... the motherboard or the CPU? I'm no expert in hardware so a bit out of my depth.

Another thought just occurred to me. I have dual boot on this machine with Windows. I will try booting into Windows and see if I get the same problem.

---

### Post by Autodave on 2018-12-10
Good idea trying Windows to see if the problem persists.  Assuming that it does, what I would try next would be to remove the second stick of memory and try.  If no more crashes, the removed stick is the villain. If it crashes, then remove the first stick and install the second stick into the slot just vacated.  Try again.  If it now works OK, the stick that is out is bad.

Are both sticks identical: size, manufacturer, looks?  If not, simply reversing the slots that they occupy can make them happy together.

---

