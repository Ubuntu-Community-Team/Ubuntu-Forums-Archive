---
title: "&quot;panic occurred&quot; black screen of death? CPU relate?"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by abexman on 2013-06-25
[SIZE=2][FONT=arial]Hello, 

So within the past few weeks I have started getting a black screen [SIZE=2]of death, usually within an hour of turning on and using my laptop Ubuntu 12.04[/SIZE]hp pavilion dv6 laptop[/FONT][/SIZE][SIZE=2][FONT=arial]dv6-3210us[/FONT][/SIZE]. There does not seem to be a real pattern to it, even happening sometimes when I leave the laptop idle. The screen message seems to indicate some issues with CPU, though I am not sure how to interpret. I tried running some tests in BIOS (though did not complete) and changing BIOS settings (although there are not many options) and ran Windows7 on this dual boot machine without issue for a few hours. I have had this version of Ubuntu installed for over a year until this started happening. How do I troubleshoot? Are there other logs I can view?

This same machine had the bottom heat fan fail about a year ago, which I replaced. It always seems to run very hot, making me think there may be an issue with the CPU. Still why no problems in Windows or when I run tests? Should I reinstall Ubuntu?? Thanks!

Here are two instances of this crash - and the machine needs to be powered off/on after this.

[[IMG]http://s5.postimg.org/og4pm9803/1stblackscreen.jpg[/IMG]]("http://postimg.org/image/og4pm9803/")

[[IMG]http://s5.postimg.org/ab3hy6ocj/2nd_black_screen.jpg[/IMG]]("http://postimg.org/image/ab3hy6ocj/")

---

### Post by dino99 on 2013-06-25
first be sure it can breath some fresh air (removing dust is also a good idea), and maybe review the powersaving settings (ondemand for example)

---

### Post by abexman on 2013-06-28
I dont see any dust or anything in the vents. There are almost no options in the BIOS. I can add a screenshot here. I did not have anything about 
"on demand" enabled in BIOS or Ubuntu. Could this be this bug? I have no issues in Windows7. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989677](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989677)

---

### Post by abexman on 2013-07-02
It was Wuala - trying to sync some folders when the account was full. This drove the CPU mad apparently! Stopped the sync and now all is well.

---

